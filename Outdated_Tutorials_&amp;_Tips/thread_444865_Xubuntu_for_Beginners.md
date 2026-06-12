---
title: "Xubuntu for Beginners"
date: 2007-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by spunout on 2007-05-15
[SIZE="6"][COLOR="RoyalBlue"]Xubuntu 6.10 for Beginners[/COLOR][/SIZE]

[SIZE="4"][B][COLOR="RoyalBlue"]
Introduction[/COLOR][/B][/SIZE]

This document is intended to aid fellow *nix virgins by answering a few practical questions that would otherwise require separate searches through vast amounts of online information.  It should be noted that this is a barebones practical guide for PC users and is nothing more than well-intentioned advice from one novice to another.  No attempt is made to introduce *nix in a general way, or even to address every practical question that can arise during setup.  The following information, it is hoped, will allow most beginners to get up and running faster.  Feedback is encouraged.

The following issues are addressed:

	[LIST=1]
[*]Installation
[*]	Display Resolution
[*]	Internet - Direct PPPOE Connection
[*]	Internet - Via a Router
[*]	Thunar Network Browsing
[/LIST]

[SIZE="4"]**[COLOR="RoyalBlue"]1. Installation[/COLOR]**[/SIZE]

Installation is straight-forward.  Once you have booted from the LiveCD and the desktop is visible, double click the Install icon before doing anything fancy, because somehow the icon dissapears and you have reboot to see it again.

If your screen looks awkward and low-res, you can right-click to customize the bottom panel (panel 2) and remove it or reposition it to the side so that the Back and Forward buttons are visible during installation.  

When setting up a Win*/*nix dual-boot system it's simplest to install on completely separate hard-drives, with the Primary Master being the (installed) Win* system drive.  The next simplest arrangement is predefined partitions where the Win* installation is already complete.  Manual partitioning of the *nix system with GParted requires more advanced understanding of *nix partition requirements.

[SIZE="4"][COLOR="RoyalBlue"]**2. Display Resolution**[/COLOR][/SIZE]

Once the installation is complete you may find that the resolution of your display can't go as high as you know the hardware will allow.  If you're not sure of the make and model of your VGA device, open a terminal (Applications>System>Terminal) and type in the following (minus the dollar-sign prompt):

```
$ lspci
```

*[SIZE="1"][COLOR="Sienna"][This command will LiSt any Peripheral Component Interconnect devices on your machine.][/COLOR][/SIZE]*

You should see something like this:

```
spunout@demo:~$ lspci
...
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
...
```


Now type:

```
$ sudo dpkg-reconfigure -phigh xserver-xorg

```
*[SIZE="1"][COLOR="Sienna"][The sudo command allows you to execute commands as another user (the default is the root user or superuser.)  You can think of this command as either SuperUser DO, or as a homophone of Pseudo because you essentially assume a pseudonym with the command.  The command dpkg-reconfigure reconfigures packages after they have already been installed. the -p option sets the priority of questions asked during the reconfiguration.  Setting the option to  -phigh removes all but the high-priority questions from the process, making your life much simpler.  The xserver-xorg portion of what you typed refers to the already-installed software package that you are about to reconfigure.  xserver-xorg is responsible for the Window System display. Xubuntu uses the X Window System display server, which has the advantage of being light-weight compared to Gnome or KDE, for example.][/COLOR][/SIZE]*

In the example above we see an nVidia video card is present so you would select 'nv'.  If your manufacturer doesn't appear in the list you may have to use the trial and error method, rebooting in between attempts.

Once you have selected the manufacturer, you are prompted to put marks next to the resolutions that you'd like X to try and use.   Only mark the highest resolution(s) that you and your hardware can use comfortably.

When you reboot all should be well.  If the reconfigure doesn't give the desired results, run the dpkg-reconfigure command again.

[SIZE="4"][COLOR="RoyalBlue"][B]
3. Internet - Direct PPPOE Connection[/B][/COLOR][/SIZE]

If you are not using a router but have a wired connection on an active ADSL service that you want to use, then open a terminal and type the following command:

```
$ sudo pppoeconf
```

*[SIZE="1"][COLOR="Sienna"][This command lets you set the Point-to-Point Protocol Over Ethernet CONFiguration.  Just follow the instructions onscreen.][/COLOR][/SIZE]*

Now open Firefox and using the menu find your way to the advanced preferences (Edit>Preferences>Advanced) and select the Network tab.  Under Connections hit the Settings button.  Select the option labelled Direct connection to the Internet.  Nothing else should be selected on this page.

[SIZE="4"]**[COLOR="RoyalBlue"]4. Internet - Via a Router[/COLOR]**[/SIZE]

If you have a wired connection through an ADSL (Asymmetric Digital Subscriber Line) router then you must first set up your router (follow the instructions given by your router manufacturer.)   Your configuration may differ, but this document will assume DHCP (the Dynamic Host Configuration Protocol.)  This is an automatic configuration for computers that use TCP/IP (Transmission Control Protocol/Internet Protocol.)

Open the Network Settings window (Applications>System>Networking) and confirm that the Wired Connection has a check next to it and says Address: DHCP.  Hit the Properties button if either isn't the case, and make it so.  Next select the DNS tab and click the ADD button next to DNS Servers.  Type in the Primary and Secondary DNS numbers given by your Router Manufacturer or ISP.  DNS stands for Domain Name System.

Now open Firefox and using the menu find your way to the advanced preferences (Edit>Preferences>Advanced) and select the Network tab.  Under Connections hit the Settings button.  Select the option labelled Auto-detect proxy settings for this network.  Nothing else should be selected on this page.

If it works then you should make the Network Settings reload every time you reboot your machine.  To accomplish this you will need to edit a file.  Here's the command:

```
$ sudo mousepad /etc/dhcp3/dhclient.conf
```

*[SIZE="1"][COLOR="Sienna"][This command opens the Dynamic Host CLIENT CONFiguration file with the 'mousepad' text editor, but you can use 'vi' or 'nano' or another editor if you'd prefer.][/COLOR][/SIZE]*

The pound symbol (#) designates comments, so you will need to remove it if it appears before any line you are modifying.  Look for something like the following and replace the placeholder DNS numbers with your own.

```
prepend domain-name-servers 1.2.3.4, 1.2.3.5;
```

Don't forget the comma in between the two DNS numbers and the semi-colon on the end.  And, again, be sure to remove the pound (#) if one precedes this line.

Reboot and then launch Firefox.  You should now be online--otherwise, carefully redo all steps in this section until it works.

[SIZE="4"][COLOR="RoyalBlue"][B]
5. Thunar Network Browsing [/B][/COLOR][/SIZE]

Open the Shared Folders window (Applications>System>Shared Folders) and install any missing packages as promted.  Once the window is open click on the General Properties tab and choose the appropriate Domain/Workgroup name.  WORKGROUP is a common choice.

Open Synaptic (Applications>System>Synaptic Package Manager) and install fusesmb.  If you can't find it then you may need to enable the Universe repository (Settings>Repositories) and then hit the refresh button.


Open a terminal and edit the modules that load at bootup:
```

$ sudo mousepad /etc/modules
```

Ensure that the word fuse appears on the list and then save, close, and reboot so the changes you've made so far take effect.

Modify User Settings (Applications>System>Users and Groups.)  Select your user name and click on Properties.  Click on the User Privileges tab and ensure the following item is selected:

Allow use of fuse filesystems like LTSP Thin Client blockdevices.

Now, close the User Settings and create a permissive folder using these commands in a terminal:

```
$ sudo mkdir /media/network
$ sudo chmod a=rwx /media/network
$ sudo chown 'whoami':fuse /media/network
```

[COLOR="Sienna"]
*[SIZE="1"][The command mkdir/media/network MaKes a DIRectory within the existing directory 'media' and labels it 'network.'  The command chmod a=rwx /media/network  CHanges MODe such that All users have permission to Read, Write, and eXecute the /media/network directory.  The Command chown 'whoami':fuse /media/network CHanges OWNership of /media/network to the individual named 'whoami' while simultaneously placing it under the group fuse.  NOTE: replace 'whoami' with your user name, without quotes.][/SIZE]*[/COLOR]

Reboot and Modify User Settings again (Applications>System>Users and Groups.)  But this time click Manage Groups.  Select fuse from the list and click on Properties to confirm membership.  If there's a check next to your user name then everything is good.

Next open Autostarted Applications (Applications>Settings>Autostarted Applications) and click on Add.  Name and Description fields should be something clear such as Network or FuseSMB Network, or such like.  In the Command Line field enter:

```
fusesmb /media/network
```

Finally, create a shortcut in Thunar (Applications>System>Thunar File Manager.)  Navigate to the media folder (File System>media) and drag the network folder to the side pane (shortcuts pane.)

Reboot one last time and test your Network Browsing within Thunar.

---

### Post by Pollywoggy on 2007-05-16
The Thunar Network Browsing does not work.  Let me see if I can show you what happens to /media/network after a reboot:

drwxr-xr-x 2 root root    4096 2007-05-13 17:14 iso
?--------- ? ?    ?          ?                ? network

What if instead of /media/network, we used /mnt/network  ?

---

### Post by Pollywoggy on 2007-05-16
I rebooted again and I think perhaps it is alright now.

---

### Post by spunout on 2007-05-16
> **Pollywoggy said:**
> 
drwxr-xr-x 2 root root    4096 2007-05-13 17:14 iso
?--------- ? ?    ?          ?                ? network

What if instead of /media/network, we used /mnt/network  ?

It shouldn't make much difference where you put it.  But you need to change owner because it shows root as the owner and group. Did you miss this step, perhaps?  

```
$ sudo chown pollywoggy:fuse /media/network
```

Obviously you need to replace 'pollywoggy' with your Linux user name.  Try it again and let me know.

---

### Post by Pollywoggy on 2007-05-16
Thanks I think it is alright now.
It was your tutorial that got me to try xfce4 and I like it, especially for my laptop.  It's much nicer than IceWM

---

### Post by RandyNose on 2007-05-20
I tried it, and it's no go. I've got xubuntu setup on a Toshiba 4100XDVD laptop. Fresh install. 
I'm getting this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070520133758
I DID have Linspire4.5 on the machine, but figured I'd try this one out. I would also like to get this thing working with DVD's, I know that it's old hardware, but it should still work.

---

### Post by Pollywoggy on 2007-05-20
> **RandyNose said:**
> I tried it, and it's no go. I've got xubuntu setup on a Toshiba 4100XDVD laptop. Fresh install. 
I'm getting this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070520133758
I DID have Linspire4.5 on the machine, but figured I'd try this one out. I would also like to get this thing working with DVD's, I know that it's old hardware, but it should still work.

Did xubuntu finish installing?

If it did, open a console and then make a file ~/.xinitrc  with these commands:

cd ~
touch .xinitrc

open that file with your favorite text editor (I use vim) and put this in the file:

exec xfce4-session

in the file and then use the command 'startx'
If xfce does not start, post the errors here.

You can also try configuring xserver-xorg if you have not done that

sudo dpkg-reconfigure xserver-xorg
but make sure the package installed first.

If Linspire installed, it is probably possible to get xubuntu to install, though you might have to use the alternate install iso.

---

