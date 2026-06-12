---
title: "python &quot;command not found&quot; error"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by smalleeepc on 2011-10-18
Running Ubuntu 10.10 on an Asus Eeepc900


Following Shannon Vanwagner's instructions (at [http://www.humans-enabled.com/#!/2009/12/how-to-tether-your-verizon-droid-as.html]("http://www.humans-enabled.com/#%21/2009/12/how-to-tether-your-verizon-droid-as.html")) for tethering your droid, I got the "command not found" error when trying to run his python setup script command:

**sudo: ./install_droidtethersv.py: command not found**

I've set my PYTHONPATH variable to point to the folder where the **install_droidtethersv.py** script exists.  I checked the version of python that I'm running:

python v2.6

Do I need to install the latest python version?  

Thanks

---

### Post by smalleeepc on 2011-10-18
Update... I "think" the python version is v2.6 (that is what it says when I run a "pyhon" command from the bash shell) when I tried to install python v3.1.  What I got instead was a error:  package already installed.

Thanks

---

### Post by smalleeepc on 2011-10-18
Well, 12 hours later and I finally got it to work.  But I don't actually know what I did to get it to work.  Here's what I did (** indicates a change from the first attempt 12 hours ago):

**(1)Moved the PY script from my pendrive to local directory on the computer
(2)updated my .profile with the following command
       ** export PYTHONPATH=/home/brad/Downloads/Droid-Tether-SV**
(3)ran chmod command inside my (bash) shell (note that the permissions for the PY file below were "**-rwxr-xr-x**" on the pendrive before the file move (I think), but went to "**-rw-r--r--**" at the new destination after the move):
        [B]sudo chmod +x ./install_droidtethersv.py
[/B](4)finally ran the script...
        **sudo ./install_droidtethersv.py**

Anyway, I'm glad I was able to hang in there and figure it out.  The linux tether issue for me has kept me using windows for the past year or so (ugh).  I'm running Asus Eeepc900 with 16gb solid state drive.  I plan on developing a website using this netbook and Drupal or Joomla or other opensource tools.  Hoping I don't run into any harddrive space issues.

My background is software engineer in aerospace (mostly software test).

smalleeepc

---

### Post by smalleeepc on 2011-10-20
Update... from my other thread success ("where is the Ubuntu desktop") I am now online using my motorola droid tethered USB to my Asus Eeepc900 netbook.  I am using the azlink droid app.  I followed Shannon Vanwagner's process as outlined above (which is just running his python script).

I know longer have to find a wifi spot (eg Starbucks) and buy products to obtain unsecured wifi access (although I'm not sure my current phone is secure... at least the openvpn setup didn't seem to happen... below is snapshot from terminal window output from the "Droid-Tether-SV" launcher app):

[INDENT][sudo] password for brad: 
adb: no process found
openvpn: no process found
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
Thu Oct 20 14:29:22 2011 OpenVPN 2.1.0 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Thu Oct 20 14:29:22 2011 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Thu Oct 20 14:29:22 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Oct 20 14:29:22 2011 ******* WARNING *******: all encryption and authentication features disabled -- all data will be tunnelled as cleartext
Thu Oct 20 14:29:22 2011 TUN/TAP device tun0 opened
Thu Oct 20 14:29:22 2011 /sbin/ifconfig tun0 192.168.56.2 pointopoint 192.168.56.1 mtu 1500
Thu Oct 20 14:29:22 2011 Attempting to establish TCP connection with [AF_INET]127.0.0.1:41927 [nonblock]
Thu Oct 20 14:29:22 2011 TCP connection established with [AF_INET]127.0.0.1:41927
Thu Oct 20 14:29:22 2011 TCPv4_CLIENT link local: [undef]
Thu Oct 20 14:29:22 2011 TCPv4_CLIENT link remote: [AF_INET]127.0.0.1:41927
Thu Oct 20 14:29:23 2011 Peer Connection Initiated with [AF_INET]127.0.0.1:41927
Thu Oct 20 14:29:24 2011 Initialization Sequence Completed

[/INDENT]Apparently, Shannon has updated his process (apparently not the python script though):

[INDENT]Update(thanks for comments!): 12-13-10 adb does not come with the new  SDK by default so you have to add it via the Android SDK and AVD  Manager.

[/INDENT]I'll try some of the other suggestions mentioned on his site and get back to you all.  I'm thinking that the lines

[INDENT]adb: no process found
openvpn: no process found
[/INDENT] 

will reverse to ON/FOUND

regards,

smalleeepc

---

### Post by smalleeepc on 2011-10-22
Everything was working hunky dory and then my cat sat on the keyboard today for who knows how long.  Later when I tried to use the laptop it was unresponsive.  I then did a hard reboot (pressed the power button for a few seconds).  I've heard that this is not recommended because it can cause the OS to become corrupted.  And so when it rebooted, couldn't see "File Manager" app and the wireless networking was disabled (I probably disabled after I got tethering to work, so).

Anyway, when I went to double-click the desktop launcher "Droid-Tether-SV" it didn't do anything (it is supposed to open a terminal window and run some commands in it.  Here is the contents of the launcher:

[INDENT][Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Name[en_US]=Droid-Tether-SV
Exec=/home/brad/DroidTetherSV/droidtethersv
Icon=/home/brad/DroidTetherSV/droidtethersv.png

[/INDENT]I then went and disconnected my wifi connection to Starbucks and retried the launcher... no success.

I then disconnected the usb tether, rebooted, reconnected the tether, then tried again.... no success.

I then reran the python install script and repeated the steps above... no success.

Is it possible that the cat - Prescilla - messed with some setting that makes my account unable to run programs?  I right-clicked the launcher icon and clicked "Open" and it still didn't do anything.  Perhaps some setting makes the command "Terminal=true" go ignored??

Anyway, I don't think I can leave my laptop open anymore lest I risk becoming severely crippled again.  But closing the lid causing the laptop to go to standby and so a bit more work has to be done to get online again (close the existing terminal window, then find the launcher in the desktop and click it again).

Thanks for listening,

smalleeepc

---

### Post by smalleeepc on 2011-10-22
Okay.  Finally got online again (yay - for those that are listening :-)

Here's what i had to do (the below was supposed to happen automatically when one double-clicks the launcher icon, but nothing happens... perhaps the mouse pad is not recognizing the double-click):

(1)open the** Droid-Tether-SV.Desktop** desktop launcher in a text editor, and from that I can see that it is starting a terminal window (bash shell) and running an executable file "**droidtethersv**"... here is the contents of the launcher file:[INDENT][Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Name[en_US]=Droid-Tether-SV
Exec=/home/brad/DroidTetherSV/**droidtethersv**
Icon=/home/brad/DroidTetherSV/droidtethersv.png
[/INDENT](2)open the **droidtethersv** executable in a text editor and the actual shell commands are:[INDENT]sudo killall adb openvpn
sudo adb forward tcp:41927 tcp:41927
sudo cp /home/brad/DroidTetherSV/resolv.conf /etc/
sudo openvpn --config /home/brad/DroidTetherSV/azilink.ovpn
[/INDENT](3)opened a terminal manually and then entered the shell commands above (in step (2)).... success!!!!!!

So I guess it's still easier for me to stay in my truck and do all of the above manually than driving to Starbucks and having my dog bark outside 'cause they don't let dogs inside :-)

Thanks for listening,

smalleeepc

---

