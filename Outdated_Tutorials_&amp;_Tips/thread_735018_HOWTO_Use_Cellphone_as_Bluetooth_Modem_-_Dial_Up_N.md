---
title: "HOWTO: Use Cellphone as Bluetooth Modem - Dial Up Networking"
date: 2008-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by sherl0ck on 2008-03-25
This guide shows how to use a Verizon LG-vx8300 cellphone as a bluetooth modem for Ubuntu 7.10! Tested using a Macbook Core2Duo but should work for  similar devices with the Verizon plan or perhaps others..

_**1. Pair/Bond CellPhone To Computer**_
	- First we need to have pair/bond your cell phone to the computer.
	- Navigate to System>Preferences>Bluetooth Preferences
	- Change 'Mode of Operation' to 'Visible and Connectible From Other Devices'
	- Choose an Memorible Adaptor Name and Class of Device
	- Quickly, from your cellphone Go To Menu>System&Tools>Bluetooth>Highlight 'Add New Device'>Settings>Discovery Mode>On
	- Your Phone Should Find Your Computer Bluetooth Adapter Name>Highlight and Click OK/PAIR.
	- It will prompt for PIN, enter it>OK. Ubuntu's Bluetooth Preference will prompt for the same. Enter it there>OK
	- Finally Ubuntu should now say 'Device Bonded' and your cell phone will ask 'Always Connect/Always Ask', choose 'Always Connect.
	- From Bluetooth preference, in the list of bonded devices, choose your cell phone and click 'Set Trusted.'

_**2. Configure PPP client and Cellphone Network Connections**_
	- For this to work properly the cellphone needs to be in 1X Only Mode.
	- From Cellphone Go to Menu>Press 0>Enter '000000'>Network Select>Mode Preference>Choose 1X Only - Click OK and CLEAR to the main screen.
	- Install the Gnome-PPP client ```
sudo aptitude install gnome-ppp
```
	- Next will need to add some options to PPP client so authentication works correctly.
	- In Ubuntu ```
sudo nano /etc/ppp/options
``` and add 

		refuse-chap
		refuse-mschap
		refuse-mschap-v2
	
	- Press Ctrl+X and Y to Save and Exit.

**_3. Set up a Connection From the Computer to The Cellphone Bluetooth Modem_**
	- First we need to find out your cellphones MAC address, either by finding it from the phone or scanning for it.
	- In the Phone, Go To MENU>Settings & Tools>Bluetooth>Highlight 'Add New Device'>Settings>My Phone Name. Remember the BT Address XX:XX:XX:XX:XX:XX
	- Alternative in the Phone, Go MENU>Settings & Tools>Bluetooth>Highlight 'Add New Device'>Settings>Click Discovery Mode.
	- Quickly in a terminal type ```
hcitool scan
``` or ```
sudo hidd --search
``` and get MAC address. 
       	- Next, we need to find out what port the bluetooth modem in the cellphone is under.
	- Use this command ```
sudo sdptool browse XX:XX:XX:XX:XX:XX
``` and look for a section named "Service Name: Bluetooth Modem" and then under that look for Channel.
	- Next we actually create the connection from cellphone to computer over bluetooth.
	- Use this command ```
sudo rfcomm connect 0 XX:XX:XX:XX:XX:XX channel
``` - '0' setting the device, then the MAC address, and finally the Channel Number.
	- Example ```
rfcomm connect 0 12:34:56:78:90:FF 8
``` - Keep This terminal open, if you do not recieve a prompt back.
	- To check ```
sudo rfcomm show 0
``` should return valid output.
	
**_4. Configure Gnome-PPP and Networking_**
	- First we need to stop Network Manager, as it tends to do what it wants.
	- To stop ```
sudo /etc/dbus-1/event.d/25NetworkManager stop
``` and ```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
```
	- And for good measure, ```
sudo ifconfig eth0 down
``` and ```
sudo ifconfig ath0 down
```
	- From a terminal execute ```
sudo gnome-ppp
``` and a window should appear.
	- Username for Verizon is your phone number with @vzw3g.com. So for example - [email]1234567890@vzw3g.com[/email]
	- Password = vzw
	- Phone Number = #777
	- Click Setup, and under the Modem Tab, Change the device to /dev/rfcomm0 -  Leave everything else as is.
	- Click Connect and your phone should show signs of data transfers, and with luck you should receive an IP and DNS server address.
	- If ```
 sudo ifconfig ppp0
``` returns an IP, and ```
route
``` shows your correct default gateway. You should be on the net now.
	- Note, the Gnome-PPP box stays open and says dialing, but terminal output shows an dynamic IP address.
	- To disconnect, close out Gnome-PPP, through the GUI and ```
sudo rfcomm release 0
```
 	- And restart NetworkManager if nesscary. 
	- And Enjoy =)

_**5. FYI**_
	- For the future to make more permanent you could edit ```
sudo nano /etc/bluetooth/rfcomm.conf
```
	- Uncomment rfcomm0 section, and change bind to yes device to MAC, and channel to correct value.
	
- To troubleshoot pairing perhaps editing ```
sudo /etc/bluetooth/hcid.conf
``` and changing security to auto, and pairing to multi. but I believe Bluetooth Preference should take care of this.
	- NOTE: This connection uses your cell phones plans minutes as far as I can tell. Best after 9PM and on weekends. 

[U][B]6. Links/References
[/B][/U]
	- [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
	- [http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)
	- [http://www.appleology.com/2006/09/27/setup-bluetooth-dun-with-your-verizon-mobile-and-your-mac/](http://www.appleology.com/2006/09/27/setup-bluetooth-dun-with-your-verizon-mobile-and-your-mac/)
	- [http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/)

---

### Post by PCFascist on 2008-04-04
Thanks for posting this! it was a great guide to figure this out with.


My cellphone a SE k800i seems to hang up right when the modem answers at 8 seconds into the call, anyone have an ideas?

---

### Post by knagode on 2010-01-14
I try to connect to the internet with my phone and get the following code:

Jan 14 20:24:31 laptop pppd[5168]: pppd 2.4.5 started by root, uid 0
Jan 14 20:24:31 laptop pppd[5168]: Using interface ppp0
Jan 14 20:24:31 laptop pppd[5168]: Connect: ppp0 <--> /dev/rfcomm0
Jan 14 20:24:31 laptop pppd[5168]: PAP authentication succeeded
Jan 14 20:24:31 laptop pppd[5168]: LCP terminated by peer
Jan 14 20:24:34 laptop pppd[5168]: Connection terminated.
Jan 14 20:24:34 laptop pppd[5168]: Modem hangup
Jan 14 20:24:34 laptop pppd[5168]: Exit.

Phone stay connected for 3 seconds and then hangs up ... Someone know where is the problem?

---

