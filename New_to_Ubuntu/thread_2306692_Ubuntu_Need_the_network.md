---
title: "Ubuntu Need the network"
date: 2015-12-17
forum: New to Ubuntu
---

### Post by Stephen_Wilkerson on 2015-12-17
Help please...  I've installed Ubuntu via my mac on an SD card to boot my Raspberry Pi 2 ( a miracle to say the least!)
It's boots.  
Now I need network access and everything I try to install "apt-get" doesn't finish because I'm not on the network.  Every article I've found on line doesn't seem to be my case.  I'm on my home address and I know:

wpa_ssid "<YOUR_WIFI_NAME>"
wpa_psk "<YOUR_PASSWORD>"

What can one do?

---

### Post by Frogs Hair on 2015-12-17
Wifi on a Pi requires a dongle style usb device and there may be packages required before the device can work. Use a wired connection if available to install what you need . My wired connection works automatically on the Pi, but beware of any device limits(number of devices) on your network. Yes, you will need a network password to enable the wireless as with any other device.

---

### Post by Stephen_Wilkerson on 2015-12-17
Yes ok it has a Wifi antenna and I know it works because i also have a Rasbrian SD card and when I boot to that on the PI all is one with the world.  However I'm now working on ubuntu.  
When you say wired connection are you referring to the Ethernet connector on the PI.  If yes then if I connect directly to the router upstairs and boot I will have the exact same problem I have now in that I won't be able to connect to the internet without some form of a command that give the router the SSID and password.  Am i missing something?
And thanks for posing a reply....

---

### Post by Frogs Hair on 2015-12-17
> are you referring to the Ethernet connector on the PI. Yes I was, and there is not much help I can provide regarding your own network security(password). I run Raspbian and that requires no password when using the Ethernet connector although wireless does. Does the router have a user interface either on the administrators computer or a login page where  the password can be viewed and changed ? I write administrator because we have a computer on a home network which the router is connected to.

---

### Post by Stephen_Wilkerson on 2015-12-17
Ok I kind of understand.  There seems to be solutions out there like:
[http://askubuntu.com/questions/522842/ubuntu-14-04-connect-to-a-wifi-network-using-command-line](http://askubuntu.com/questions/522842/ubuntu-14-04-connect-to-a-wifi-network-using-command-line)
However I don't have iwconfig on my copy of ubuntu.  when I try and install iwconfig it can't find the package.  So maybe the question is how do I install iwconfig given that I don't have a internet connection on the Pi.  I'm working from a Mac and can write files to a thumb drive, but don't know what I need or for that matter what I'm doing.

Maybe I should just give up on ubuntu and move on.  Raspbrian works fine and I should be able to use ROS with that.  I think that will be my solution to this thread.

---

