# Busy-bee
import 'package:flutter/material.dart';
import 'package:google_maps_flutter/google_maps_flutter.dart';

class HomeScreen extends StatefulWidget {
  @override
  _HomeScreenState createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  late GoogleMapController mapController;
  final LatLng _initialPosition = LatLng(37.7749, -122.4194); // Example location
  final Color highlightColor = Color(0xFFF9C74F);

  void _onMapCreated(GoogleMapController controller) {
    mapController = controller;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Bussy Bee'),
        backgroundColor: highlightColor,
      ),
      body: Stack(
        children: [
          GoogleMap(
            onMapCreated: _onMapCreated,
            initialCameraPosition: CameraPosition(
              target: _initialPosition,
              zoom: 14.0,
            ),
            myLocationEnabled: true,
          ),
          Positioned(
            top: 20,
            left: 10,
            right: 10,
            child: TextField(
              decoration: InputDecoration(
                filled: true,
                fillColor: Colors.white,
                hintText: 'Where to, Busy Bee?',
                prefixIcon: Icon(Icons.search),
                border: OutlineInputBorder(
                  borderRadius: BorderRadius.circular(10),
                  borderSide: BorderSide.none,
                ),
              ),
            ),
          ),
          Positioned(
            bottom: 30,
            left: 10,
            child: FloatingActionButton(
              onPressed: () {
                // Add locate me functionality
              },
              child: Icon(Icons.my_location),
              backgroundColor: Colors.white,
              foregroundColor: Colors.black,
            ),
          ),
          Positioned(
            bottom: 30,
            right: 10,
            child: ElevatedButton(
              onPressed: () {
                // Add ride booking functionality
              },
              style: ElevatedButton.styleFrom(
                primary: highlightColor,
                padding: EdgeInsets.symmetric(horizontal: 30, vertical: 15),
              ),
              child: Text(
                'Ride Now',
                style: TextStyle(color: Colors.black),
              ),
            ),
          ),
        ],
      ),
    );
  }
}
import 'package:flutter/material.dart';

class BookingScreen extends StatelessWidget {
  final Color highlightColor = Color(0xFFF9C74F);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Booking & Payment'),
        backgroundColor: highlightColor,
      ),
      body: Padding(
        padding: EdgeInsets.all(20.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              'Your Ride Details',
              style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
            ),
            SizedBox(height: 10),
            Card(
              child: ListTile(
                leading: Icon(Icons.person),
                title: Text('Driver: John Doe'),
                subtitle: Text('Car: Toyota Prius\nETA: 5 mins'),
              ),
            ),
            SizedBox(height: 20),
            Text(
              'Fare Summary',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),
            SizedBox(height: 10),
            ListTile(
              title: Text('Base Fare'),
              trailing: Text('\$5.00'),
            ),
            ListTile(
              title: Text('Distance Cost'),
              trailing: Text('\$10.00'),
            ),
            ListTile(
              title: Text('Discount'),
              trailing: Text('-\$2.00'),
            ),
            Divider(),
            ListTile(
              title: Text('Total'),
              trailing: Text('\$13.00'),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: () {
                // Add booking confirmation logic
              },
              style: ElevatedButton.styleFrom(
                primary: highlightColor,
                padding: EdgeInsets.symmetric(vertical: 15),
              ),
              child: Center(
                child: Text(
                  'Confirm Booking',
                  style: TextStyle(color: Colors.black, fontSize: 18),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}
import 'package:flutter/material.dart';

class SettingsScreen extends StatelessWidget {
  final Color highlightColor = Color(0xFFF9C74F);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Settings & Customization'),
        backgroundColor: highlightColor,
      ),
      body: ListView(
        padding: EdgeInsets.all(20),
        children: [
          ListTile(
            leading: Icon(Icons.account_circle),
            title: Text('Profile'),
            subtitle: Text('Edit your details and preferences'),
            trailing: Icon(Icons.edit),
            onTap: () {
              // Navigate to profile edit screen
            },
          ),
          Divider(),
          SwitchListTile(
            title: Text('Dark Mode'),
            value: true,
            onChanged: (bool value) {
              // Toggle dark mode
            },
          ),
          ListTile(
            leading: Icon(Icons.notifications),
            title: Text('Notifications'),
            subtitle: Text('Manage alerts and messages'),
            onTap: () {
              // Navigate to notifications settings
            },
          ),
          ListTile(
            leading: Icon(Icons.payment),
            title: Text('Payment Methods'),
            subtitle: Text('Manage your payment options'),
            onTap: () {
              // Navigate to payment settings
            },
          ),
          ListTile(
            leading: Icon(Icons.privacy_tip),
            title: Text('Privacy Settings'),
            subtitle: Text('Manage location and data sharing'),
            onTap: () {
              // Navigate to privacy settings
            },
          ),
          ListTile(
            leading: Icon(Icons.help),
            title: Text('Support'),
            subtitle: Text('FAQs and contact support'),
            onTap: () {
              // Navigate to support
            },
          ),
        ],
      ),
    );
  }
}
