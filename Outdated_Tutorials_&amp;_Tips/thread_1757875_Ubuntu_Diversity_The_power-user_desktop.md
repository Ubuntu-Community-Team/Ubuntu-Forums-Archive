---
title: "Ubuntu Diversity: The power-user desktop"
date: 2011-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by fatalGlory on 2011-05-13
The following tutorial is an update of one I did a couple of years ago called [Minimalistic Ubuntu From Scratch](http://ubuntuforums.org/showthread.php?t=1201273)

[size="3"]**Why this tutorial?**[/size]

Ubuntu as a distribution has gotten a some bad press on Slashdot, etc. lately.  This is mostly tied up with the switch to the Unity desktop in 11.04 Natty (released about two weeks ago at time of writing).  I know how bad it got, because I'm one of the Ubuntu fans that got very nervous about Ubuntu's future and decided to try a couple of other distros and see what my options were if I decided to switch.  I'm no stranger to distro-hopping.  Over the years I've run Ubuntu, Debian, Fedora and Arch, each as my primary distro on all my computers simultaneously for a minimum six months (and obviously tested some others).  In my opinion, Ubuntu in 2011 still has all the same strengths that it always had: great driver support, good balance between stable and up-to-date packages, sensible default configurations, impressive flexibility.  So I'm writing this tutorial to beg the power-users like me not to desert Ubuntu.  Debian and Arch have their own strengths, but everything we started using Ubuntu for is still there.

I've got two computers at home, a laptop and a desktop.  The laptop is running a totally stock Natty install with the Unity desktop, because I'm trying to keep an open mind (and I definitely think Unity suits smaller screens/resolutions better than my dual-monitor desktop).  This tutorial is about how I use the Ubuntu Alternate CD to create a fast, finely-tuned power-user desktop to do all my main work on.  In an attempt to reach out to power-users who have raised an eyebrow at Unity, I call it: ***Ubuntu Diversity***.  After all, Ubuntu is a community which allows and thrives on diversity.  As one of my favourite authors, Ravi Zacharias, said, only in the Trinity do we find the unity in diversity that explains all existence, only at the cross of Christ do we find the ultimate unity of the diverse aspects of who God is.  At the cross of Christ we see God's love displayed, evil condemned, justice wrought and mercy and grace given to all who believe.

[size="2"]**Step 1:**[/size] Install base system from Alternate CD
You'll have to grab the Alternate CD (latest at time of writing is 11.04 Natty) to install the base system (no desktop, no lamp stack, pretty much just enough to use apt-get).

**1.1 - Preamble**
After booting the Alternate CD, select your language then choose **Rescue a Broken System** from the menu.  You'll have to tell it your country and your keyboard layout, then it will configure a bunch of stuff including DHCP, so you have network access.  Next you'll have to choose a hostname and set up your time zone info.  Finally a bunch of hardware detection occurs.

**1.2 - Partitioning and Installation**
At this point, you'll be shown some info about the partitions detected (or not detected) on the system.  Whichever it is, choose **Go Back** to be taken to a list of system rescue tasks.  Choose [b]Install Base System[b] from the list.  From here the steps are very similar to the standard ubuntu desktop install, just follow the instructions to set up partitions and install the base system.

**Optional Step: Setting up WiFi from the command line**
Currently, my desktop machine can only access the internet via the wireless network in our house (unless I lug it all the way to the other end of the house where the router is).  If you're in a similar predicament, fear not, configuring WiFi without a GUI is actually not that difficult.  I'm only covering WPA encrypted networks here, because that's all I have to work with.

First, install wpa_supplicant:
```
sudo apt-get install wpasupplicant
```
Now we need to generate the WPA shared key that will be used to authenticate on the network.  Normally your WiFi manager would ask you for a passphrase, but when using this method, we have to give it the key that is usually generated from the passphrase.  Run this command to generate the key:
```
wpa_passphrase NETWORK_SSID
```
where NETWORK_SSID is the name of your network (e.g. you can change it in your router settings, on many routers it defaults to "WLAN" or "wireless" or something like that).  You will be prompted to enter the passphrase you want to generate a key from, type in the password and press enter.  Your output should look something like this:
```
asdfasdfasdf
network={
	ssid="NETWORK_SSID"
	#psk="asdfasdfasdf"
	psk=90e9e74a72d51d1074d9fe0ac33c6a92b12cx1c7940e863ab56dc66bcb482b24
}
```
where "asdfadsfasdf" is the password you entered (no that's not my real password).  Write down the long hex string after "psk=", we will need that in a moment.  To set up the wireless interface, we need to edit /etc/network/interfaces, so run:
```
sudo nano /etc/network/interfaces
```
add the following code to the bottom of that file:
```
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid NETWORK_SSID
    wpa-psk 90e9e74a72d51d1074d9fe0ac33c6a92b12cx1c7940e863ab56dc66bcb482b24
```

Obviously replace NETWORK_SSID with the name of your network and the hex string with the one you generated using wpa_passphrase.  With this file configured, restart the system and log back in:
```
sudo shutdown -r now
```
If all went well, you should now have wireless network access.  Try a ping to check, if not you'll have to do some troubleshooting online or find a way to get a wired connection.

**NOTE:** if you install a network manager once your desktop is operational (e.g. network-manager-gnome or wicd) you will need to edit /etc/network/interfaces again and delete the wlan0 config you've just added.  If you leave it there, the two will conflict.

[size="2"]**Step 2: Adding a Desktop Environment**[/size]
After you finish installing the base system and reboot, you're left with a login prompt.  Enter your username and password and you get given a command line.  This is technically a complete linux system, but doesn't let us do much.  We need to add a few things in order to make our computer feel like it belongs in the post 1970s.

**2.1 - X Server**
An X server is the program that actually displays a graphical desktop on your linux machine, to install one, run the following command:
```
sudo apt-get install xserver-xorg
```

**2.2 - Login Manager**
The login manager takes your username and password at bootup, then launches your desktop environment.  I'm using the LXDE login manager, called lxdm.  It is lightweigh, uses the openbox window manager and easy to customize (uses glade ui files).
```
sudo apt-get install lxdm
```

I also crafted a custom logout dialog for this install (more useful for Openbox than XFCE, which has its own).
[http://resplect.com/script_repository/exit-dialog.tar.gz](http://resplect.com/script_repository/exit-dialog.tar.gz).  The logout command is XFCE specific in my version, but you can easily edit the python script to change the commands for your system.  Also, to run the shutdown command as a non-privleged user (DO NOT DO THIS IN A SERVER ENVIRONMENT), you will need to run this:
```
sudo chmod +s /sbin/shutdown
```

**2.3 - Window Manager (XFCE)**
I've already tried installing the stock Ubuntu Natty then installing the xubuntu-desktop package on top, it was easy, but felt a bit weighty for my liking, lots of stuff I just don't need (e.g. the update manager and software centre, I prefer to just use apt-get from the command line, and I have my own webspace so I'm unlikely to ever use ubuntu one for storage).  So instead, I'm going to install the vanilla XFCE desktop environment:
```
sudo apt-get install xfce4
```

I was very torn between XFCE and Openbox for this install.  Openbox is a little more minimalist, but XFCE takes care of more of the basic stuff I always install anyway (like a wallpaper-setter, file manager, etc).  You're power users, feel free to branch out.  For the same reason, I won't go into a lot of detail here about tweaking the appearance of the desktop, that's for you to have fun with.

**Step 2: Utility Applications**
This is just some stuff you are going to want to install before logging into your new desktop environment.  My choices are listed below, tweak away.
A Terminal Emulator: terminator
A Text Editor: vim/geany
GUI Authenticator: gksu
```
sudo apt-get install terminator vim geany gksu
```
With those installed, reboot and when the system comes back up you will be able to log in to you XFCE desktop via SLim.

**Step 3: Adding Sound Capabilities**
My full sound solution these days calls for ALSA and PulseAudio.  I get that some people still don't like PulseAudio.  That's ok, remember, this is the Diversity desktop ;)

**3.1 - Possible step: installing ALSA**
If you installed the XFCE desktop like me, ALSA should already be installed, if you went with something more sparse like Openbox, you may need to install it manually.  To install ALSA and enable sound, install these packages:
```
sudo apt-get install alsa-base alsa-utils
```

**3.2 - Installing PulseAudio**
In either case, PulseAudio is not installed by default.  Install it if desired with the following command:
```
sudo apt-get install pulseaudio pavucontrol
```
pavucontrol is a fine-grained volume control application.  I like to always keep a launcher for it in my panel so I can quickly access the volume levels for all my applications.

**Step 4: Adding Permissions**
In order to do a lot of day-to-day stuff, we need to add our user to various groups on the system:

To add your user account to these groups run:
```
sudo usermod -a -G audio,video,disk,cdrom,fuse,floppy *your_username*
```
**NOTE:** to get these permissions to apply, we need to log out and log back in.

**Step 4.1: Enable CD/DVD Mounting for Users**
To enable non-root users to mount CD/DVD devices, you will need to add entries to /etc/fstab:
```
sudo nano /etc/fstab
```
Add the following entry to the end of the file:
```
/dev/scd0    /media/cdrom0    auto    user,noauto    0    0
```
If you have more cd/dvd drives, just add entries for each one (e.g. replace /dev/cdrom0 with /dev/cdrom1).  If it does not already exist, you will need to create the /media/cdrom0 directory then set the permissions on it to allow users in the cdrom group to read it:
```
sudo mkdir /media/cdrom0
sudo chown root:cdrom /media/cdrom0
```
Now, if you click on a disk drive in your file manager (e.g. Thunar on XFCE), or when a disk is inserted, it should get automounted.

**Step 5: Adding some basic applications**
I installed some basic applications to enable me to actually get stuff done with this machine, just a favourites list of mine really:
```
sudo apt-get install firefox mplayer vlc audacious libreoffice evince geany gimp inkscape file-roller eog build-essential
```

Firefox: web browser
Mplayer: media player/encoder with heaps of options
VLC: media player with less options but a nice GUI
Audacious: Library-less, lightweight music player
Libreoffice: suite of office applications (word processor, spreadsheet, presentations, etc.)
Evince: Document viewer for PDFs, etc.
Eye of Gnome: Image Viewer
GIMP: Advanced image editor
Inkscape: Vector graphics editor
Geany: Text Editor/Simple Programming IDE
File-Roller: gui frontend for several archive file types
Build-Essential: Ubuntu package containing basic gear for doing software development (gcc, make, etc.)

**Step 7: Checking the Memory Footprint**
With all this stuff done, its time to see the fruits of our labour and see just how little memory our new lean-and-mean, ubuntu-from-the-ground-up system uses.

**7.1 - Install conky**
Conky is a nifty and lightweight little system monitor, install it with:
```
sudo apt-get install conky
```
The default conky looks a bit bland, I have a favourite conkyrc file to style it with.  You can use mine or edit it up if you like, download and copy to ~/.conkyrc: [http://resplect.com/script_repository/conkyrc](http://resplect.com/script_repository/conkyrc)

**7.2 - Check your results**
Reboot so you get a picture of your system truly at idle, no extra apps running.  To do this, use the command:
```
sudo shutdown -r now
```
The *-r* means reboot, if you want to shut the system down, use *-h* instead.
After the reboot, login, then run conky with Alt-F2, it will tell you your current memory usage, cpu usage, chunkiest apps, etc.  Come here and tell us all your results!

***I get 154MB of memory in use after a clean boot.***

**Wrapping Up - Some Beautification Notes**
A screenshot of the final product is below, for those interested, here's the list of theme content:
Icons: Faenza
GTK theme: Clearlooks
Media Player: Audacious

[img]http://resplect.com/artwork/desktops/ubuntu_diversity_screenshot.jpg[/img]

---

### Post by Kivech on 2011-05-16
Excellent guide. I'm definitely going to try this one out.

I was more or less looking for something like this.

Also, you might want to mention that Audacious has a WinAmp skin mode, which allows you to use custom made classic WinAmp skins. Some of those are pretty awesome (check the WinAmp site, just make sure you don't try the *.wal skins, because those don't work on Audacious).

Cheers!

---

