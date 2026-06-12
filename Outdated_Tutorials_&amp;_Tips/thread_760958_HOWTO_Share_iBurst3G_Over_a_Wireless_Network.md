---
title: "HOWTO: Share iBurst/3G Over a Wireless Network"
date: 2008-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by dclough on 2008-04-20
After browsing these forums and elsewhere on the internet, I eventually managed to set up a secure wireless network to share my iBurst internet connection.  Hopefully this HOWTO will save others the pain of figuring it out themselves.

What this HOWTO achieves:

[LIST]
[*] A DHCP server that allocates IP addresses
[*] A WEP encrypted wireless network
[*] Internet sharing to a computers with a registered MAC address
[/LIST]

Unfortunately if your wireless card does not support Master mode, then this tutorial will not work for you.  You can find out more about whether your card supports master mode here: [WifiDocs: Master Mode]("https://help.ubuntu.com/community/WifiDocs/MasterMode")

This HOWTO was tested on an Atheros card (Netgear WG311T), but should in theory work for other cards.

What you'll need:

[LIST]
[*]You'll need to make sure the following packages are installed: [FONT="Courier New"]**dnsmasq, dhcp3-server, madwifi-tools**[/FONT].

[*]In addition you'll have to install [Webmin]("http://www.webmin.com/"). The Debian package is a available at: [http://www.webmin.com/download.html]("http://www.webmin.com/download.html")
[/LIST]

I have assumed that you already have the ppp internet connection set up. If you're using an iBurst USB modem you can find the drivers [here]("http://sourceforge.net/projects/ibdriver/") and installing them is as easy as following the README.  Just make sure that no directories have spaces in their names.

[B][SIZE="2"]
Step 1: Setting up the DHCP server[/SIZE][/B]

This can be done using the command line, but I found the GUI presented by Webmin far more intuitive to use.  So first we need to install Webmin.  Their official steps for installation are found [here]("http://www.webmin.com/deb.html") but we'll step through them anyway.

[SIZE="2"]**1.1: Setting up Webmin**[/SIZE]

First we make sure we have all the required packages installed packages.

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

Then we install webmin

```
dpkg --install webmin_1.410_all.deb 
```

You can now access Webmin by opening Firefox and going to the address "[FONT="Courier New"]https://localhost:10000/[/FONT]" or you can substitute localhost with your computer's name.  You must log in with a user that has access to admin privileges with the sudo command (usually your normal ubuntu username and password).  If you haven't already installed dhcp3-server, then install it now and in Webmin click "Refresh Modules" on the left.

[SIZE="2"]**1.2 Setting up the DHCP Server**[/SIZE]
In Webmin select "Servers" > "DHCP Server" from the left panel.

We now want to create a new subnet, so under "Subnets and Shared Networks" click "Add a new subnet". Fill in the following details:

[LIST]
[*]**[FONT="Courier New"]Subnet description: home_network[/FONT]**
[*]**[FONT="Courier New"]Network address: 10.42.42.0[/FONT]**
[*][FONT="Courier New"]**Netmask: 255.255.255.0**[/FONT]
[*]**[FONT="Courier New"]Address ranges: 10.42.42.10 - 10.42.42.30[/FONT]** (basically choose how many IP addresses you want to have available for allocation)
[/LIST]

Then leave everything else on default, scroll down and click create.  You will now see your new subnet under  "Subnets and Shared Networks".  Now click on the Icon or IP address, then scroll down and click on "Edit Client Options".  Fill in the following blocks:

[LIST]
[*][FONT="Courier New"]**Subnet mask: 255.255.255.0**[/FONT]
[*]**[FONT="Courier New"]Default routers: 10.42.42.1[/FONT]**
[*][FONT="Courier New"]**Broadcast address: 10.42.42.255**[/FONT]
[*][FONT="Courier New"]**DNS servers: 10.42.42.1**[/FONT]
[/LIST]

*Note: Make sure that you've moved the radio button away from the "Default" option to the text box for each of the above fields otherwise you'll lose the information.*

Once you've entered in the values click "Save", and click "Save" again on the next screen.

Lastly we need to tell the DHCP server which network interface to listen to, so click on "Edit Network Interface". Then select the network which with be used to share the internet connection and click "Save".  For wireless it will usually be wlan0 or ath0 (for Atheros cards).

Now if you click "Start Server", the server should start. But we don't need to do this now.  The DHCP server should now be set up and we can start up the wireless network.

[B][SIZE="2"]
2. Setting up the Wireless Network[/SIZE][/B]

First we stop the standard Network Manager:

```
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
We now set up the wireless network. This part is specific to an Atheros Card, and ath0 and wifi0 should be replaced with your system equivalents.

```
sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode ap
```
Other wireless cards may be configured by using "iwconfig wlan0 mode Master". This makes the wireless card act as though it's an access point.  We now set up the network specifics:

```
sudo iwconfig ath0 chan 5 			#or whatever channel you choose
sudo iwconfig ath0 essid Your_Network_Name 
sudo iwconfig ath0 key 1234567890			#any 10 digit hex number
```
The last line sets up the WEP encryption.  On my computer using an ASCII passphrase didn't seem to work but that can be chosen using "iwconfig enc s:13Char-Psswrd" where "13Char-Psswrd" is any 13 character password.

We're now ready to enable the network with

```
sudo ifconfig ath0 up 10.42.42.1 netmask 255.255.255.0
```

[SIZE="2"]**3. Setting up the Internet Sharing**[/SIZE]

We now work with the iptables that tell the computer how to handle other computers on the network.  We begin by flushing/clearing the iptables that we'll be using:

```
sudo iptables -t nat -F PREROUTING
sudo iptables -t nat -F POSTROUTING
```

We now tell the computer to accept packets from itself

```
sudo iptables -t nat -A PREROUTING -i lo -j ACCEPT
```

And to accept packets from only your computers on the network. For each computer on the network you have to type in the following line but inserting that computer's MAC address. In this example the MAC address is 00:90:4B:F0:F0:88.

```
sudo iptables -t nat -A PREROUTING -m mac --mac-source 00:90:4B:F0:F0:88 -j ACCEPT
```

We now prevent any unauthorised computers from having access to the internet connection with the following:

```
sudo iptables -t nat -A PREROUTING -j DROP
```

*Note: if you don't want this extra level of security, then simple don't perform the last 3 commands shown here and everything will work, only any computer that connects to the network will have internet access.*

Lastly we set up the part that will share the internet connection where [FONT="Courier New"]ppp0[/FONT] is your ppp connection to the internet:

```
sudo iptables -t nat -A POSTROUTING -o ppp0 -s 10.42.42.0/24 -j MASQUERADE
```

This uses IP Masquerading to share the internet connection with the other computers on the network.

We're now ready to start up the dhcp server and the service that controls the masquerading

```
sudo /etc/init.d/dhcp3-server start
sudo /etc/init.d/dnsmasq start
sudo sysctl -w net/ipv4/ip_forward=1
```

To be honest, I don't know what the last command does, but without it my internet doesn't share properly.

Other computers should now be able to connect to your wireless network and access the internet.

[SIZE="2"]**4. Stopping Internet Sharing**[/SIZE]

We first stop the core services:

```
sudo /etc/init.d/dnsmasq stop
sudo /etc/init.d/dhcp3-server stop
sudo sysctl -w net/ipv4/ip_forward=0
```

Then we flush the ip tables:

```
sudo iptables -t nat -F PREROUTING
sudo iptables -t nat -F POSTROUTING
```

Then we reset the network card to its normal state

```
sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
```

*Note: If you are not using an Atheros card then use "iwconfig wlan0 mode Managed".*

And lastly we re-enable the Network Manager:

```
sudo /etc/dbus-1/event.d/25NetworkManager start
```

You should now be able to use your wireless network card normally.

**[SIZE="2"]5. General Information[/SIZE]**

The internet connection sharing will not necessarily be active when your computer is restarted.  For reason it can be extremely useful to put section 2 & 3 into a shell script called "start_internet" and section 4 into another script called "stop_internet". This way you can quickly start and stop your internet sharing whenever you want.

Sources:
[http://tumbleweed.org.za/2007/06/04/sharing-a-3g-connection-with-ubuntu](http://tumbleweed.org.za/2007/06/04/sharing-a-3g-connection-with-ubuntu)
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)
[http://ubuntuforums.org/showthread.php?t=335465](http://ubuntuforums.org/showthread.php?t=335465)

---

