---
title: "Setting up ndiswrapper with BT Voyager 1055"
date: 2008-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Strangewayz on 2008-08-12
[FONT=Arial][SIZE=2]As a newcomer to Ubuntu and Linux in general and having scoured the internet for assistance (and struggled) in setting up my wireless, on Ubuntu 8.04 Hardy Heron, I have put together this guide which I hope other noobs will find useful. The guide is written for users with a GNOME desktop, as I am new to Linux myself and am just getting to grips with the commands under GNOME, so apologies for all you KDE fans out there. It’s worth noting that this works every time on a fresh installation and I have also got it working under Ubuntu Studio 8.04 (although there is no ndiswrapper icon on the tool bar in Studio so connection has to be made using network settings).[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]The guide should be the same whichever wireless adapter you have (I cannot see why it would not work if you had the correct drivers but someone more experienced in Linux is probably going to correct me on this) – you will just need the .inf and .sys driver files which should be installed under windows (mine were located here - “C:\Program Files\BT\BT Voyager”).[/SIZE][/FONT]
 
**_[FONT=Arial][SIZE=2]Step 1[/SIZE][/FONT]_**
 
[FONT=Arial][SIZE=2]Using the file manager in Ubuntu I mounted my windows xp drive and navigated to the above folder. Select the relevant driver files (for the BT Voyager 1055 they are usb8023.sys, RNDISMP.sys and bcmrndis.inf) and copy them to the Ubuntu desktop.[/SIZE][/FONT]
 
**_[FONT=Arial][SIZE=2]Step 2[/SIZE][/FONT]_**
 
[FONT=Arial][SIZE=2]Install the latest version of ndiswrapper. I used the Synaptics package manager, searched the cd for packages and selected ndisgtk which also installed the other two ndiswrapper files however you can use the command line – sudo apt-get install ndisgtk[/SIZE][/FONT]
 
**_[FONT=Arial][SIZE=2]Step 3[/SIZE][/FONT]_**
 
[FONT=Arial][SIZE=2]In Terminal type “cd Desktop” which will move you to the desktop directory and type[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]sudo ndiswrapper –i bcmrndis.inf (you will be asked for your user password and you should get an error message which states it will create the file anyway – just ignore and carry on with next steps).[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]This will copy the bcmrndis.inf to the ndiswrapper folder.[/SIZE][/FONT]
 
**_[FONT=Arial][SIZE=2]Step 4[/SIZE][/FONT]_**
 
[FONT=Arial][SIZE=2]Type: [/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]sudo cp –v usb8023.sys RNDISMP.sys /etc/ndiswrapper/bcmrndis/[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]This will copy the sys files to the ndiswrapper folder.[/SIZE][/FONT]
 
**[FONT=Arial][SIZE=2]Extra step if you are using this guide to install a different wireless adaptor otherwise skip to next step:[/SIZE][/FONT]**
 
[FONT=Arial][SIZE=2]Type:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]lsusb //Note: Is lowercase L[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]This will bring up a list of all the attached devices for your usb ports. Locate you wireless device in the list and you will see a set of numbers next to it – for BT it was 1690:0715. Make a note of these two numbers.[/SIZE][/FONT]
 
**_[FONT=Arial][SIZE=2]Step 5[/SIZE][/FONT]_**
 
[FONT=Arial][SIZE=2]You must now create the hardware configuration file by typing:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]sudo gedit /etc/udev/rules.d/99-custom.rules[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]This will open the text editor for GNOME (KDE users replace gedit with kate) with a blank page. Copy the attached text and save and exit the text editor.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]#START**[/SIZE][/FONT]
[FONT=Arial][SIZE=2]BUS=="usb",[/SIZE][/FONT]
[FONT=Arial][SIZE=2]SYSFS{idProduct}=="0715",[/SIZE][/FONT]
[FONT=Arial][SIZE=2]SYSFS{idVendor}=="1690",[/SIZE][/FONT]
[FONT=Arial][SIZE=2]RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"[/SIZE][/FONT]
[FONT=Arial][SIZE=2]#END**[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Please note the single and double quotes on the RUN line which need to be included or your configuration file will not work. If you are installing a different adapter you will need to substitute the two SYSFS numbers above with the ones for your card (see extra step above). After running lsusb BT Voyager shows as 1690:0715 with the first 4 numbers being the idVendor and the second set being the id Product[/SIZE][/FONT]
 
**_[FONT=Arial][SIZE=2]Step 6[/SIZE][/FONT]_**
 
[FONT=Arial][SIZE=2]Check the installation by typing:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]sudo ndiswrapper –l //Note: Is lowercase L[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]You should see a message stating Driver: installed and Device: present. This means you have successfully setup the wireless adaptor (if you don't see Device: present unplug your adapter, plug back in and run the above command).[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Type:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]sudo depmod –a[/SIZE][/FONT]
[FONT=Arial][SIZE=2]sudo modprobe ndiswrapper[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]On the top toolbar, at the right hand side (near the date and time), there will be a icon of a terminal. Left click here and you should see the wireless networks in your area. Click on the network you wish to associate to. If you have security setup up on your router you should be presented with a window to enter your security key.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I had some difficulty with this as I could not connect to my router when security was enabled (even though the router and wireless dongle both support all the current encryption methods) so I had to disable my security through the router and change the mac address table so that only my adapter's mac address can connect to the router. I know this is not the safest of options as mac address spoofing is quite simple to do but it will do for now until I get chance to conduct further tests on the security.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]In order to connect to your network each time you boot type:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]sudo gedit /etc/modules[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]And add ndiswrapper to the list that appears in the editor, save and close.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]I hope some users find this useful and I'd like to point out that I can't claim credit for the above as I gathered it from a variety of web sources and pieced it together for this guide, once I had got it all working.[/SIZE][/FONT]

---

### Post by sdennie on 2008-08-12
Good looking guide.  Moved to Tips and Tutorials.

---

### Post by Strangewayz on 2008-08-13
Thanks vor.

---

### Post by ripmax on 2010-03-12
Hello, I'm new to linux and have been trying to get my laptops wireless working but with no go and last night I followed this tutorial to get my voyager 1055 usb adapter working with xubuntu 9.10 instead and everything went well and worked first time, but now this morning when I turned on my laptop (with the voyager still plugged in) and the system crashed at the login screen and I ended up having to hard reboot it holding down the power button.
After rebooting it did the exact same thing again (crashed), so I unplugged the voyager and rebooted, this time it booted up normally and after I logged in I plugged the voyager back in and as soon as I did the system crashed again.
I uninstalled the driver, rebooted and reinstalled following this tutorial again but this time I had no wireless options in the network manager even though using "sudo ndiswrapper -l" shows that the drivers are install and hardware is detected and rebooting the laptop just causes it to crash again.
Any help would be appreciated.
Thanks
 
Edit: I now have it working perfectly :)

---

