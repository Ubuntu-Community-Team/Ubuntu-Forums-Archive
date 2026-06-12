---
title: "Private Internet Access VPN not working"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by m9ke2 on 2014-07-21
I could use some help getting a new installation of Private Internet Access vpn running.   I am running xubuntu 14.04


These are the directions from PIA I followed to install ([https://www.privateinternetaccess.com/pages/client-support/#linux_ubuntu_openvpn_12_04](https://www.privateinternetaccess.com/pages/client-support/#linux_ubuntu_openvpn_12_04))
 Ubuntu Linux 12.04: OpenVPN via Network Manager Setup
1. Open a Terminal, and run: sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome. This will prompt for both your password, and a Y/n answer, please provide it with your password, and Y
2. Once installed, open System Settings, then Network
3. Press the + symbol to add a new connection, and select the VPN Interface, then press Create
4. Choose OpenVPN as your VPN Connection Type, and press Create


The following will walk you though all configuration steps needed for the PIA VPN.
1. Gateway: Select one of the Hostnames provided on the NETWORK PAGE
2. Authentication
Type: Password
Username: The username provided with the PIA account
Password: The password provided with the PIA account


CA Certificate: Downloaded this ZIP FILE and extract the ca.crt file to somewhere it won't be deleted. We suggest your Home folder. If you extract this to your home folder, when searching for it, please click on your username on the left side, which will take you right to the home folder, then select the ca.crt file from the options on the right.
Advanced: Under the general tab, check the Use LZO data compression
IPv4 Settings:
Method: Automatic (VPN) Addresses Only
Press Save. If you chose to have your password saved it may ask for you to verify your password to open your keyring.
######


All the above seemed to go fine.  I rebooted and checked my ip address.  No change. It looks liks vpn is not starting or not connecting.
synaptic package manager shows: 
openvpn
network-manager-openvpn
and network-manager-openvpn-gnome
are all installed


Double checked installation by:
me:~/Desktop$ sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openvpn is already the newest version.
openvpn set to manually installed.
network-manager-openvpn is already the newest version.
network-manager-openvpn-gnome is already the newest version.
network-manager-openvpn-gnome set to manually installed.
The following packages were automatically installed and are no longer required:
  dconf-editor dconf-tools gnome-extra-icons loadlin python-cracklib
  session-migration
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I would appreciate any pointers from the community!

---

### Post by mooreted on 2014-07-21
That's the hard way and I only got it to work a couple of times. I installed the PIA VPN beta app and it works great:

[https://www.privateinternetaccess.com/forum/index.php?p=/discussion/1940/pia-vpn-app-linux-beta/p1](https://www.privateinternetaccess.com/forum/index.php?p=/discussion/1940/pia-vpn-app-linux-beta/p1)

---

### Post by m9ke2 on 2014-07-21
Thank you mooreted.  I will follow the directions you point me to and report back on this thread.  Again, thanks for your reply!

---

### Post by m9ke2 on 2014-07-21
mooreted, you are right.  That was the hard way.  I followed the directions you gave me.  The install was uneventful.  I rebooted and selected Private Internet Access from my Applications menu and checked my IP.  Sure enough it was different.  

However on my first PIA install, I specified a different location.  

And looking at Settings-Network connections I see that the VPN I created on my first install supposedly has never been used. That can't be right.   I am now  connecting thru the VPN I created on my second install  (following your directions).

These conditions lead me to believe there are remnants of my first install still present on my computer.

Tomorrow I will parse thru these and try to figure out how to configure the new installation to point to a given location, make sure I am using OpenVPN etc.  Also I hope to get rid of old bits I installed on my first installation.

I will report back to this thread with results.

mooreted you really helped me out.  I spent half of today fooling around with this install and trying to get the techsupport folks on PIA's chat to understand what I was trying to do.  Following your directions I was connecting thru the vpn in a matter of minutes.

Thanks!
m9ke

---

### Post by mooreted on 2014-07-22
You are welcome, I had the same problem. Ubuntu seems to lose the VPN settings in Network Manager and I never could figure out how to make it work again. I'm glad they made the app for us.

---

### Post by m9ke2 on 2014-07-22
As i figure this out I will document what I find before closing this thread.  I hope this might help someone else having the same problem with PIA.

The install I did yesterday works.  There is no real GUI to it.  Instead there is an entry in my applications menu (xubuntu) that appears to do nothing, but really toggles the vpn on and off.  When on, there is a green icon (red if disconnected) in the panel on top of the screen.  The vpn is controlled and configured from that icon.

One setting that has me wondering is the VPN kill switch, which delivers the message below when turned on:

"Please only enable VPN Kill Switch if you really need it.  The Kill Switch requires modifying the Operating System's network settings and can in rare cases cause connectivity issues.  This feature WILL NOT work if you use MORE THAN ONE network interface on your computer simultaneously.


Are you sure you wish to enable VPN Kill Switch?"

Not sure what is meant by 'more than one network interface'.  Anyone have thoughts on that?

---

### Post by mooreted on 2014-07-22
I just use the green icon. I have never tried the kill switch. I have visions of a glitch in my Internet connection that triggers the kill switch and me spending the next few days trying to figure out how to get my connection back.

---

### Post by m9ke2 on 2014-07-23
After looking into it I think the kill switch cuts off the users connection to the net if the vpn connection is lost.  

This seems intended to keep the user safe if the vpn connection drops unexpectedly and the user does not notice.

---

### Post by mooreted on 2014-07-23
Yeah, that is what it's meant to do. I just don't trust it to work.

---

### Post by killabee44 on 2014-10-25
Guys, I had some problems with this installer and finally got it sorted. I installed it and did not get any errors. The only problem was that I could not find the launcher icon anywhere. Not under any app folders. It would not auto load at startup either. 

Finally I saw where they said that "- The installer will create an application launcher entry in ~/.local/share/applications"

But I could not launch the application by double-clicking it. I also tried to type the name of the launcher in the command line but still was not working. 

I then had the idea to drag the icon to the task bar, and then it showed up. I thought I was done, but when I clicked on it and got the following error: 

"Couldn't load file:/htpc1/.local/share/applications.pia_manager/pia_tray.64/runtime/1.3.2-beta/libtide.so, error: libjpeg.so.62: cannot open shared object file: No such file or directory"

I then installed libjpeg62, and it FINALLY worked by clicking on the green icon on the taskbar. 

Ok, it doesn't seem to be working after all. There seems to be some kind of encryption issue with the ubuntu home folder.. Does anyone know how to get around this? Thanks.

After a reboot I can't even pull up the settings.

Im running Ubuntu 14.04..

---

