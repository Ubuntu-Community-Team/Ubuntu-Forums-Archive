---
title: "Howto: Setup the CX6600 on Ubuntu Edgy"
date: 2006-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-12-11
**Introduction**
I have written guides for this printer before and I have just had to setup the scanning part again so I am going to rewrite it for Edgy with some new things such as the udev stuff included.

The scanning section from my old guides was put together from material on the [www.clasohm.com](www.clasohm.com) blog ([permalink to article](http://www.clasohm.com/blog/one-entry?entry%5fid=12616)). Most of this stuff is still useful and has been invaluable to the creation of this guide.

For this guide you will need apt-get and a text editor. I use vim as my text editor of choice so if you prefer another simple replace vim with the other editor in any commands below.

**The Printer Part**
The CX6600 is now fully supported by Ubuntu out of the box so just open the Gnome Printer Manager and add a printer - it should appear as a detected printer if you have it turned on and plugged in and the driver that is automatically selected works great.

Could it be any easier?

**The Scanner Part**
To use the scanner you will need SANE (Scanner Access Now Easy) so lets install that now.
```
sudo apt-get install sane-utils sane
```
When that finishes we need to edit a text file to access the scanner and we should check a few things for good measure. Lets check some things first.
```
cat /etc/sane.d/dll.conf | grep epson
```
If that command returns epson then thats fine. If not you need to edit that file and add epson to it.
```
sudo echo "epson" >> /etc/sane.d/dll.conf
```
The next thing to test is the udev rules.
```
cat /etc/udev/rules.d/45-libsane.rules | grep CX-6600
```
If that returns something like "# Epson Corp.|Stylus CX-6600" then we can continue.

We now need to add a line to the epson backend config file to make it look for our scanner.
```
sudo echo "usb 0x4b8 0x813" >> /etc/sane.d/epson.conf
```

Once this is all done we can restart the udev daemon and test out the setup.
```
sudo /etc/init.d/udev restart
```
```
scanimage -L
```
This should give you a line about your scanner. If it tells you there are no scanners detected you probably have a permissions problem and should try that command as root to confirm it.

To get a GUI for the scanner you can install xsane which is a scanner program for Gnome.
```
sudo apt-get install xsane
```

**Uninstallation**
To uninstall this you can delete the printer in the Gnome Printer Manager and use apt to uninstall sane.
```
sudo apt-get remove --purge sane-utils sane
```

**Troubleshooting**
I will be editing and updating this guide as things come to light but if you want help from me please post in this thread as then I will actually notice it - don't email me or start a new thread as its annoying and its better to keep everything about this in one place.

If you are having permissions problems check all the udev stuff is working and that you ran all the commands correctly. If you can scan as root then this post should help you: [http://ubuntuforums.org/showpost.php?p=2151505&postcount=26](http://ubuntuforums.org/showpost.php?p=2151505&postcount=26) [Thanks to Patient0 who came up with this one]

---

### Post by rdmost on 2006-12-24
I followed your instructions and they worked fine, with two exceptions.  First, in testing 45-libsane.rules, I needed to grep for CX-6600 rather than CX6600 to get a match.  Second, xsane belongs to root rather than my user account.  Even though it is shown as having both read and execute privileges for all groups and users, I can only run it as root.  Any ideas would be appreciated.

---

### Post by Haegin on 2006-12-27
Thanks for catching that error - I have corrected it now.
When you try and run xsane as your normal user what happens? Does it scan for devices and fail to find them or does it just not run? Try in a console and look at the output.
If it is a permission error then try
```
sudo chmod a+rwx /usr/bin/xsane
``` and then try and start it again.

Hope this helps

---

### Post by rdmost on 2006-12-27
Unfortunately, adding write permission to the existing read and execute permissions has no effect.  Any attempt to scan as a regular user produces the error message "no device available".  I can scan images from the CX6600 using sudo and then afterward revise the permissions on the files the scan creates.  It's a nuisance, though, and I would prefer to be able to scan those images as a regular user.  If any new ideas occur to you, please pass them along -- I will be more than happy to try them out!

For whatever reason, Edgy seems to be a lot more finicky about granting permissions than Dapper was.  I followed your previous instructions for installing the scanner driver for the CX6600 under Dapper, and that worked without a hitch.  For what it's worth, I did not upgrade from Dapper to Edgy but instead did a clean new install.

BTW, I should have complimented you on your instructions.  They are clear, unambiguous, and easy to follow.

---

### Post by Haegin on 2006-12-29
Thanks for the compliment - are you using Ubuntu 6.10 (Edgy)? If so try re running the commands to get the scanner working. Does printing work fine? If not then you may have a problem with the device (hopefully not). Also is the scanner local (i.e. attached to your machine)? If not then there are further steps to make it work over the network. The udev stuff should set all the permissions when you plug the device in so you may want to check those files for any obvious typos.
On final thought is to run lsusb in a terminal. On my machine I get
```

$ lsusb
Bus 005 Device 002: ID 04b8:0813 Seiko Epson Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

```
The only interesting line is the first one and the numbers before the name (04b8:0813). You can see these are used in the guide quite a bit so make sure your lsusb entry for the printer includes the same numbers. Note - in the guide they are 0x4b8 and 0x813.
Finally check you are in the scanner group - I think you should be by default but worth a check.

---

### Post by rdmost on 2006-12-29
Thanks for the suggestions.  They didn't solve the problem, but they did narrow it down.

First, in response to your questions:  (1) I'm using Ubuntu 6.10; (2) re-running the commands didn't make any differrence; (3) the printer is connected locally and works just fine (it was recognized and configured during the initial installation of 6.10); (4) I checked the files and didn't find any typos; (5) as normal user I am a member of the scanners group.

Now the more interesting stuff:  (1) when I restart udev, the only response is " * Loading additional hardware drivers...  "; (2) when I subsequently issue the scanimage -L command as a normal user, it responds with "No scanners were identified. . .", but when I issue that same command preceded by sudo, it responds with "device `epson:libusb:005:010' is a Epson CX6600 flatbed scanner"; (3) the response to the lsusb command (with or without sudo) does NOT include the CX6600, but (4) when I issue the command sane-find-scanner (no sudo), it responds with, among other things, "found USB scanner (vendor=0x04b8, product=0x0813) at libusb:005:010".

So it appears that the problem isn't really finding the scanner but (probably) having access to the proper files with appropriate permissions.  The (modified) file epson.conf in /etc/sane.d has read permissions for everyone, but write and execute permissions only for the owner (root).  All of the files in /usr/bin whose names start with sa or xs have read and execute permissions for everyong.  Presumably, there is a file somewhere used by xsane that has read and/or execute permission for its owner (root) but not for others.  Any ideas where to look?

---

### Post by Haegin on 2006-12-29
Before sane used udev it used hotplug so you could try the following:
```

sudo mkdir /etc/hotplug
sudo mkdir /etc/hotplug/usb
touch /etc/hotplug/usb/libsane.usermap
echo "libusbscanner 0x0003 0x04b8 0x0813 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000" > /etc/hotplug/usb/libsane.usermap
```
Though I had hoped this was not necessary.

Does everybody need to do this? If you used the guide and did not need this please let me know.

---

### Post by rdmost on 2006-12-29
That was included in your previous instructions for Dapper, so I had already tried that, and it had no effect.  (I subsequently had deleted the hotplug subdirectory, including its usb subdirectory and the libsane.usermap file, so I tried it again just now, but the result was the same.)    The only interesting result is that I have to precede the touch and echo commands with sudo in order to get them to work.  More and more, this looks like a problem with permissions, but I don't know which other files xsane uses, and so I can't check their settings.

---

### Post by ricegf on 2006-12-30
> **rdmost said:**
> I followed your previous instructions for installing the scanner driver for the CX6600 under Dapper, and that worked without a hitch.  

I'm still on Dapper (as Edgy has a fatal bug in the nVidia nForce 430 driver :( ), but I can't seem to locate the previous instructions referenced above. On what should I search?

> **rdmost said:**
> BTW, I should have complimented you on your instructions.  They are clear, unambiguous, and easy to follow.

I agree, they are a model of clarity - so much so that I decided to try them on Dapper just for the heck of it. All went swimmingly until I tried the coup de grâce: 

ricegf@pluto:~$ scanimage -L
device `epson:libusb:001:003' is a Epson Unknown model flatbed scanner
ricegf@pluto:~$ sudo scanimage -L
device `epson:libusb:001:003' is a Epson Unknown model flatbed scanner
ricegf@pluto:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04b8:0813 Seiko Epson Corp.
Bus 001 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 001: ID 0000:0000
ricegf@pluto:~$

Any additional suggestions would be appreciated immensely.

---

### Post by Haegin on 2006-12-31
[quote="ricegf"]I agree, they are a model of clarity - so much so that I decided to try them on Dapper just for the heck of it. All went swimmingly until I tried the coup de grâce:[/quote]

That looks like its working fine - have you tried running 
```
xsane
```
and scanning something? If it can't find a scanner when it starts its probably a permissions problem. Note - these instructions should work for Dapper and should work better than my other instructions as Dapper is meant to use udev not hotplug (though I have had success both ways).

[quote="rdmost"]That was included in your previous instructions for Dapper, so I had already tried that, and it had no effect. (I subsequently had deleted the hotplug subdirectory, including its usb subdirectory and the libsane.usermap file, so I tried it again just now, but the result was the same.) The only interesting result is that I have to precede the touch and echo commands with sudo in order to get them to work. More and more, this looks like a problem with permissions, but I don't know which other files xsane uses, and so I can't check their settings.[/quote]
The thing that does make me wonder is that the lsusb command doesn't show the scanner - can you try running
```
dmesg > dmesg_output.txt 
```
straight after unplugging and replugging the multifunction printer and uploading that file so I can take a look - it's almost as if the pc isn't sure the cx-6600 exists.

---

### Post by ricegf on 2006-12-31
> **Human Prototype said:**
> That looks like its working fine - have you tried running 
```
xsane
``` and scanning something? 

Yes, xsane works great.  Thanks!

George

---

### Post by rdmost on 2006-12-31
> **Human Prototype said:**
> The thing that does make me wonder is that the lsusb command doesn't show the scanner - can you try running ```
dmesg > dmesg_output.txt 
``` straight after unplugging and replugging the multifunction printer and uploading that file so I can take a look - it's almost as if the pc isn't sure the cx-6600 exists.

I ran the command, and the resulting file is (I hope) attached.  However, I ran it as both a normal user and as root, and it produced EXACTLY the same results.  Similarly, the lsusb command doesn't show the scanner, even if I issue the command as root.  Given that "sudo xsane" works but "xsane" doesn't, wouldn't it make sense to expect differences?

After sending this message the first time, I found out that the file did NOT upload because it exceeded the size limit (27 KB versus a limit of 19.5).  Is there a particular portion of the file you would like to see?

---

### Post by Patient0 on 2007-02-08
Thanks for such a cool post.

I have stepped through it and am still suffering,  I can run xsane but no device found unless I'm root, in which case it works!

Obviously permissions but I am unsure where to start (Newbie Alert)

---

### Post by Haegin on 2007-02-08
[QUOTE="rdmost"]
I ran the command, and the resulting file is (I hope) attached. However, I ran it as both a normal user and as root, and it produced EXACTLY the same results. Similarly, the lsusb command doesn't show the scanner, even if I issue the command as root. Given that "sudo xsane" works but "xsane" doesn't, wouldn't it make sense to expect differences?
[/QUOTE]
Sorry for not getting back to you - if you can read through it and see if there is anything about the scanner or about new usb devices being recognised. Also try a different usb port and cable.

[QUOTE="Patient0"]
Thanks for such a cool post.

I have stepped through it and am still suffering, I can run xsane but no device found unless I'm root, in which case it works!

Obviously permissions but I am unsure where to start (Newbie Alert)
[/QUOTE]
Firstly thanks for the appreciation. The permissions thing has to be the most common problem. Firstly did you do all the udev stuff, are you using Edgy (I think I have other guides around for the older Ubuntus), did you definatly restart udev? Did all the udev commands report success (or at least not fail). I tried to make the guide pretty much cut and paste so you don't have to edit files and things but that does mean errors can go unnoticed - try all the udev stuff again and see if it all works fine. Also check you are in the scanner group and  possibly the plugdev group.

If you are still having problems post again and I will try and help more. If I don't reply within three days or so please bump as I probably missed the email to tell me there were replies (sorry again rdmost).

---

### Post by Patient0 on 2007-02-09
> **Human Prototype said:**
> Sorry for not getting back to you - if you can read through it and see if there is anything about the scanner or about new usb devices being recognised. Also try a different usb port and cable.


Firstly thanks for the appreciation. The permissions thing has to be the most common problem. Firstly did you do all the udev stuff, are you using Edgy (I think I have other guides around for the older Ubuntus), did you definatly restart udev? Did all the udev commands report success (or at least not fail). I tried to make the guide pretty much cut and paste so you don't have to edit files and things but that does mean errors can go unnoticed - try all the udev stuff again and see if it all works fine. Also check you are in the scanner group and  possibly the plugdev group.

If you are still having problems post again and I will try and help more. If I don't reply within three days or so please bump as I probably missed the email to tell me there were replies (sorry again rdmost).

I stepped though the code making sure everything worked (should this be done as root?) everything worked and works as root.  But running xsane says no scanner?

Yes I'm using U-E-E-6.10.

Just a note  other forums refer to permissions on /dev/usb/scanner0, but I don't have /dev/usb could this be related?

---

### Post by Haegin on 2007-02-10
I don't know whether there should be a /dev/usb/scanner node as my scanner is on my server which is broken after a power cut corrupted the hard drive. I do know however that I never needed to do anything to that device node to get my scanner working.

Did you check the groups etc? Is the user you are using the one originally set up for the system (during the install)?

---

### Post by Patient0 on 2007-02-10
I am using the first install accout and I have made sure it is a member of the scanner group.

I know its permissions but I can't find out where!  I can: sudo xsane but this gives me a locked file that requires the ownership to be change before I can do anything with it!  Bit of  a pain really!

Thanks for the reply.  If I come up with anything  I will post here for other to see!

---

### Post by rdmost on 2007-02-10
> **Human Prototype said:**
> Sorry for not getting back to you - if you can read through it and see if there is anything about the scanner or about new usb devices being recognised. Also try a different usb port and cable.

Don't worry about it.  This is not a particularly high priority, and I appreciate your guidance, whenever you can provide it.

I'm going to attach the file in two parts, which I should have thought of before.  However, I don't think it's going to tell you much.  I repeated the process as superuser (under which xsane works), and the file that was generated is identical -- diff showed no differences whatsoever.

Here is the first half of the file.

---

### Post by rdmost on 2007-02-10
And here is the second part of the file.

---

### Post by Haegin on 2007-02-11
OK, that all seems to match up. Can you just cat the following files in a terminal to check they contain more than one line and then chown them to root:
```

sudo su
cat /etc/sane.d/epson.conf
cat /etc/sane.d/dll.conf
cat /etc/udev/rules.d/45-libsane.rules
chown root:root /etc/sane.d/epson.conf
chown root:root /etc/sane.d/dll.conf
chown root:root /etc/udev/rules.d/45-libsane.rules
chmod 544 /etc/udev/rules.d/45-libsane.rules
chmod 544 /etc/sane.d/epson.conf
chmod 544 /etc/sane.d/dll.conf

```
If any of the files are only one line or don't look right then you may not have all the sane packages installed.

---

### Post by Patient0 on 2007-02-11
Ok so I have been playing around and have a fix until the next reboot:

(please bear in mind I am new to linux!  so some of it may not be good practice)

- Open terminal
- sane-find-scanner
- Make a note of the found USB scanner line, specifically the two numbers after libusb:
- sudo nautilus
- Go to the folder: /dev/bus/usb and then to the folder that matches the first number
- Open permissions of the file tat matches the second number and change the group from root to scanner and make sure it has rw values

This should then work.

Just a note xsane will produce an error on close.  To fix this just take the tick out of save preferences in the preferences menu.

However the libusb address changes on reboot and it appears the permissions are also reset.

I know this isn't a cure maybe it goes some way to finding one!

---

### Post by rdmost on 2007-02-11
> **Human Prototype said:**
> OK, that all seems to match up. Can you just cat the following files in a terminal to check they contain more than one line and then chown them to root:
```

sudo su
cat /etc/sane.d/epson.conf
cat /etc/sane.d/dll.conf
cat /etc/udev/rules.d/45-libsane.rules
chown root:root /etc/sane.d/epson.conf
chown root:root /etc/sane.d/dll.conf
chown root:root /etc/udev/rules.d/45-libsane.rules
chmod 544 /etc/udev/rules.d/45-libsane.rules
chmod 544 /etc/sane.d/epson.conf
chmod 544 /etc/sane.d/dll.conf

```
If any of the files are only one line or don't look right then you may not have all the sane packages installed.

Actually, I was able to access all of those files without having to become superuser.  All of them have meaningful content (containing either epson or epson 6600).  Furthermore, all three of them (1) already are owned by root, (2) belong to group "root", and (3) have their permissions set to "rw-r--r--".  Consequently, even when I'm logged in as a normal user (i.e., don't belong to the "root" group) I should still be able to read those files.  The only additional privilege that root has is the ability to write these files, which shouldn't be an issue here.

---

### Post by rdmost on 2007-02-11
Following Patient0's instructions, I get exactly the same response:  it works until reboot, at which time the group reverts to root.  At least we're getting consistent results, which presumably means we have the same problem.

Thanks for the work-around.  It's much preferable to changing file ownerships and permissions after the fact.

---

### Post by Ex-XP on 2007-02-13
The machine is detected, but the system tells me that no scanner can be found when I start up XSane:

mmcclellan@Avalon:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 015: ID 0830:0061 Palm, Inc. 
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04b8:0813 Seiko Epson Corp

How might I work out a permissions problem?  Many thanks for any help you can provide.

-M

---

### Post by Haegin on 2007-02-13
I am glad the temporary fix is helping you use your kit while we try and sort out the deeper problem. I used to have to do this under dapper when my udev wasn't set up correctly (I didn't know that I should be using udev or how to set it up back then) so you are both probably best off starting looking into udev and if you can get it to log everything to its own log file which you can check it would def help - if you want a hand looking at the logs just gzip it up and send it my way.

Ex-XP - have you followed the guide for the scanner in the original post? If so the best place to start is to read the rest of the thread as almost all of it so far is about permissions problems. Try everything mentioned there and if you can find no permanent solution then there is a temporary solution (which you can also do from the command line as it is simply changing permissions on the device node). Let me know what works for you and if you have to use the temporary fix please let me know if that works as well.

I am currently really busy building a PC but when that is done I will see if I can install edgy on an old box and see if I can reproduce some of the problems everybody seems to be experiencing.

You all could also try writing a shell script to change the permissions on that device node whenever you boot if the CX6600 is always plugged in.

Good luck to you all. Please keep me informed and I will help wherever I can.

---

### Post by Patient0 on 2007-02-13
Ok, so not one to be beat, I have done a little bit of snooping. I have found out that the scanner is always on the 005 bus, only the device number changes. So after learning a few more commands I run the folloowing straight after rebooting:

#sudo chgrp -hR scanner /dev/bus/usb/005


This worked so onto finding an automated way of delivering this line, remembering it needs root access. My solution was to do this:

- Open terminal
- sudo -s -H
- scanimage -L
- record the two numbers after libusb, the first is the bus number
- cp /etc/rc.local /etc/rc.local.bak
- gedit /etc/rc.local
- before: exit 0 - type: chgrp -hR scanner /dev/bus/usb/005 (insert your bus number instead of 005)
- close and save
- reboot

Remembering that if xsane errors when closing then it is due to saving preferences issues, just go in preferences and untick save preferences.

If this is bad practice then please tell me. But it has seemed to resolve the problems.

That to all who have helped -- Linux Rules!

---

### Post by Haegin on 2007-02-13
Wow - that is a much nicer way of doing it than my way (script run on login using gnome-startup) which breaks if I don't login to gnome. Well done!

Hopefully we can get udev sorted but this should fix it for people who can only scan as root for the time being.

Nice one!

---

### Post by Patient0 on 2007-02-13
> **Human Prototype said:**
> Wow - that is a much nicer way of doing it than my way (script run on login using gnome-startup) which breaks if I don't login to gnome. Well done!

Hopefully we can get udev sorted but this should fix it for people who can only scan as root for the time being.

Nice one!

Thanks HP!

Not bad for an ex M$ engineer. 

There is no going back now!

Linux
:guitar:

---

### Post by Haegin on 2007-02-13
[quote="Patient0"]Not bad for an ex M$ engineer.[/quote]
Welcome to the light

---

### Post by rdmost on 2007-02-19
> **Patient0 said:**
> 
Remembering that if xsane errors when closing then it is due to saving preferences issues, just go in preferences and untick save preferences.


Thanks for the guidance -- everything works fine now, except for the errors at closing.  

Unfortunately, that appears to be a catch-22.  I can uncheck "save device preferences at exit," but unless I've used sudo to start xsane, that generates an error message when I try to apply it and then click OK:  "Failure to create file:  Permission denied."  And I get the same error message twice again when I close xsane.  Granted that's a small inconvenience, but it would be nice not to have to put up with it.  

I did make that change after starting a session with sudo, and that didn't generate any error messages.  Furthermore, it retained the setting for subsequent sessions so long as I start them with sudo xsane rather than just xsane.  Unfortunately, it doesn't carry over to sessions where I don't invoke the sudo command.

Did you do something differently to be able to eliminate the error messages and actually change the setting for regular (i.e., non-sudo) sessions?

---

### Post by teaker1s on 2007-02-19
or use epsons own iscan program

---

### Post by Patient0 on 2007-02-19
No, nothing different as I recall check this:

- terminal
- xsane
- alt-s
- uncheck save device preferences at exit

that should work but if not let me know you access on the same page (I remember toying with these too).

---

### Post by rdmost on 2007-02-20
> **Patient0 said:**
> No, nothing different as I recall check this:

- terminal
- xsane
- alt-s
- uncheck save device preferences at exit

that should work but if not let me know you access on the same page (I remember toying with these too).

Unfortunately, that's the same process I've followed.  And I just repeated it to make sure.  I'm guessing it's a permissions issue once again -- do you recall which file the xsane settings are saved in?

---

### Post by Haegin on 2007-02-21
I would imagine if you can find out what prefs file it is writing to and then chmod that to be world writeable it may fix it but take a note of the original permissions so you can change it back if needed.

---

### Post by doubtful wisdom on 2007-02-25
Have tried to install and use CX-6600 scanner since November 2006 in Edgy.  No success, but I know nothing about Linux.  Found this thread and tried yet again with no success.  The response to  the line asking the backend config file to look for the scanner is that I do not have permission.  

I have no idea how to proceed.  The commands that I entered in terminal are nothing like DOS, but they were accepted until the above happened.

---

### Post by Haegin on 2007-05-23
Are you running as root to run those commands (use sudo).

---

### Post by Haegin on 2007-06-06
I finally found the source of all the permission problems!!!

NOTE: I am doing this on Feisty because I upgraded - it should work just fine for Edgy (and Dapper) as far as I know.

It seems there are two different version of the CX6600 floating around with different Bus IDs. Some are 0813 and some are 0805. Because of this you need to check which you CX6600 is by using lsusb and looking for 04b8:0813 or 04b8:0813.
Once you know this open the /etc/udev/rules.d/45-libsane.rules
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
and find CX-6600 and see whether the entry in that is for your version of the CX6600 or for the other version.
If you are not sure replace all the current stuff about the CX-6600 with the following:
```

# Epson CX-6400 | Epson CX-6600
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0805", MODE="664", GROUP="scanner"
# Epson CX-6400 | Epson CX-6600
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0813", MODE="664", GROUP="scanner"

```
Then save and close this file and restart udev
```
sudo /etc/init.d/udev restart
```
You will also need to check the epson.conf file to ensure that has the correct product ID so open that and check the second set of numbers on the usb line corresponds to your version of the CX6600
```
sudo gedit /etc/sane.d/epson.conf
```
Save and close this file and try running xsane again and let me know how you get on.

---

### Post by sookydo on 2007-06-22
hello all this is my first post on ubuntu forums.
I apologize if this is misplaced or not in the flow of current threads.  I have been reading this tutorial on how to get the Epson CX6600 to work with Edgy (which is pretty easy to do in KDE settings).  

But since I upgraded to Feisty (Kubuntu), I don't see this model listed specifically like it was in edgy eft.  With Edgy, it was just a matter of Sytems Settings --> Printers--> Add Printer --> selecting the model from the list and BAM!  Easy as pie.   

i wonder if anyone else has this issue with Feisty?  **Why oh why **has this great all-in-one printer been omitted from the driver group?? By the way, I was able to get the scanner working pretty well with xsane as root...so at least the |hard| part was taken care of!!

---

### Post by Haegin on 2007-06-22
As far as I know it is totally supported in feisty and it is working fine for me. When you plug in and turn on the printer run dmesg in a terminal and paste the last 20 lines of output here. Also please post the output from lsusb. Don't forget to wrap them in code tags (put [code ] before it and [ /code] after it without the spaces).

If you want to use the scanner as your normal user please try using the program in this post - it will setup most SANE supported epson scanners on Ubuntu so you are ready to go and I am still looking for testers. I have used it fine on my PC with a CX6600 and it worked fine so there is no real reason for it not to work.

Hope this helps.

---

### Post by sookydo on 2007-06-22
wow, so responsive!  i love this community.

last 20 lines of dmesg:
```

[56539.408000] scsi 4:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 P        : 0 ANSI: 2
[56539.412000] sd 4:0:0:0: Attached scsi removable disk sda
[56539.412000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[56717.008000] usb 4-4: USB disconnect, address 8
[56717.008000] drivers/usb/class/usblp.c: usblp0: removed
[58696.372000] usb 4-4: new high speed USB device using ehci_hcd and address 9
[58696.516000] usb 4-4: configuration #1 chosen from 1 choice
[58701.520000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev        9 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0813
[58701.520000] scsi5 : SCSI emulation for USB Mass Storage devices
[58701.520000] usb-storage: device found at 9
[58701.520000] usb-storage: waiting for device to settle before scanning
[58706.520000] usb-storage: device scan complete
[58706.520000] scsi 5:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 P        : 0 ANSI: 2
[58706.520000] sd 5:0:0:0: Attached scsi removable disk sda
[58706.520000] sd 5:0:0:0: Attached scsi generic sg1 type 0

```

my lsusb:
```

[Bus 004 Device 009: ID 04b8:0813 Seiko Epson Corp.
Bus 004 Device 004: ID 0ecd:a100 Lite-On IT Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 04f2:0111 Chicony Electronics Co., Ltd
Bus 001 Device 006: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

```

---

### Post by Haegin on 2007-06-22
Ok, well it has definitely found the printer when you plugged it in so we know it is probably not a hardware problem.
First go into System>Administration>Printing and delete any failed attempts at making the CX6600 work.
Next see if it comes up in the auto-detected printers box, if so select it and follow the wizard.
If it does not then see if it appears in the "Use another printer by specifying a port" drop down box.
Let me know if neither one works.

Also please let me know if you use that scanner program and if it works.

---

### Post by sookydo on 2007-06-22
I see no previous instances of this printer installed. 

Using KDE, the print wizard asks me to select what type of connection.  I select local/USB.  Next dialog: local port selection.  Under the USB heading/subsection the Epson Stylus 6600 is there.  I click the model once to highlight, click next, and then I am presented with a manufacturer column and a model column.  Plenty of epsons, but there is not a single model that rings remotely of: stylus, cx or 6600

In this same dialog window, there are two checkboxes: raw driver and postscript printer.  There is a button to browse for a driver driver manually.

In gnome, which I guess you use, this exact model is listed?  arrhhhhgg!

---

### Post by Haegin on 2007-06-22
No, not "arrhhhhgg!", just a nice little learning experience...

Now, can you run up adept and see if you have cupsys-driver-gutenprint installed
OR (if you prefer)
run the following in a konsole
```

sudo apt-get install cupsys-driver-gutenprint

```

That package should provide the driver for the epson CX6600, after installing it try adding your printer again.

---

### Post by sookydo on 2007-06-22
```

duke@emachine:~$ sudo apt-get install cupsys-driver-gutenprint
Reading package lists... Done
Building dependency tree
Reading state information... Done
cupsys-driver-gutenprint is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

i figured I already had gutenprint installed....tried to add the printer again, but the cx6600 is not listed.  any other ideas?

---

### Post by Haegin on 2007-06-22
You could try following these instructions here:
[http://tonywhitmore.co.uk/blog/2007/03/29/using-the-cups-web-interface-on-ubuntu/](http://tonywhitmore.co.uk/blog/2007/03/29/using-the-cups-web-interface-on-ubuntu/)

When that is done go to [http://localhost:631](http://localhost:631) and try adding the printer there. Sorry but it's the best I can suggest at the moment - I will keep thinking though

---

### Post by sookydo on 2007-06-22
thanks alot.  i appreciate your help.  i never knew that CUPS had a browser interface to administer the printers.  keep you posted.

---

### Post by sookydo on 2007-06-29
followed the steps as suggested -->
[http://tonywhitmore.co.uk/blog/2007/03/29/using-the-cups-web-interface-on-ubuntu/](http://tonywhitmore.co.uk/blog/2007/03/29/using-the-cups-web-interface-on-ubuntu/)

Accessed the CUPS browser console using [http://localhost:631](http://localhost:631).


I went to the ADD PRINTER tab, followed the subsequent steps of selecting from a list of detected interfaces.  

I selected the interface USB#1, just like KDE's wizard found.  

The next dialog actually had the exact model/driver I  needed: 
EPSON Stylus CX6600-CUPS+GUTENPRINT v5.0.0.99.1 (en)

then I hit ADD.

Prompted for username/password

I entered credentials for the first account set up on this system.

THEN, it prompted me again!  So I entered credentials again. 

Now, the browser is just spinning and spinning (Firefox) looking like it is about to timeout, but never does...just keeps saying "transferring data from local host" in the bottom of browser window.  

I have also tried using root credentials, same result.  

Honestly, I am at wit's end.  I have been using all kinds of Debian distros for a few years now, and I have never had such difficulty with a printer.  please help.

---

### Post by Haegin on 2007-06-29
Ok,

Re-reading his instructions I can see how they could be confusing.
Open the cupsd.conf file and make the following changes:
Browsing Off => Browsing On
Listen localhost:631 => #Listen localhost:631
On the line before the Listen bit you just edited add "Port 631"
Now save the file and exit.
Next add cupsys to the shadow group
```

sudo adduser cupsys shadow

```
And retry the web interface

---

### Post by Haegin on 2007-07-17
I am now hosting the guide on my newly renovated website. I will link back to here (and previous versions of this guide) for reference and keep a thread for each Ubuntu version open to discuss any problems but I think its finally cracked with the udev stuff for scanning which has sorted out the last big headache for the scanning side of things.

[http://hjmills.co.uk/computers/linux/cx6600.php](http://hjmills.co.uk/computers/linux/cx6600.php)

---

### Post by DavidFourer on 2007-09-27
> **Patient0 said:**
> 
- Open terminal
- sane-find-scanner
- Make a note of the found USB scanner line, specifically the two numbers after libusb:
- sudo nautilus
- Go to the folder: /dev/bus/usb and then to the folder that matches the first number
- Open permissions of the file tat matches the second number and change the group from root to scanner and make sure it has rw values

This worked on my Epson CX5000 printer/scanner in Feisty.  Xsane runs and finds the scanner, which works very nicely.  I'm too tired to go any further.  It's taken me all afternoon to get this far.  My notes are here if you want to look through it: [https://home.comcast.net/~davidfourer/xsane_permissions](https://home.comcast.net/~davidfourer/xsane_permissions)  The printer ran perfectly.  Plug in, auto-detect, print.

---

### Post by Peter The Plumber on 2007-10-18
Good Morning,
  Thank you for writing a very easy to follow and good; as it works; tutorial. I used this to set up scanning on 7.04 with an Epson CX-5000.  I have one thing to add because the following didn't produce anything for me and sane-find-scanner didn't either. After this step

The next thing to test is the udev rules.
```
cat /etc/udev/rules.d/45-libsane.rules | grep CX-6600
```
If that returns something like "# Epson Corp.|Stylus CX-6600" then we can continue.

I added the proper code to /etc/udev/rules.d/45-libsane.rules manually. I looked up the usb id on the Sane website, guessed that the vendor and model id would be close and got it right by trial and error. I simply copied another entry and replaced the unique information with my own.

This didn't do anything for me?? Don't know why. 
Once this is all done we can restart the udev daemon and test out the setup.
```
sudo /etc/init.d/udev restart
```

After a reboot it worked!
```
scanimage -L
```
This should give you a line about your scanner. If it tells you there are no scanners detected you probably have a permissions problem and should try that command as root to confirm it.

Xsane found it and it scans now!
To get a GUI for the scanner you can install xsane which is a scanner program for Gnome.
```
sudo apt-get install xsane
```

Best Regards,
Peter

---

### Post by doug1212 on 2007-11-19
In gutsy there seems to be a bug in /etc/udev/rules.d/45-libsane.rules that prevents scanner recognition.
Follow the link below for a patch that should be fix.

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/134853](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/134853)

Doug.

---

### Post by bean77 on 2007-11-29
Would the directions be the same for a CX 7400?  I am having problems with the scanner although the printer works just fine.

---

### Post by Paulo Gonçalves de Barros on 2007-11-30
Hi, everyone,
 
    I am a total newbie to Linux. I used to bear with Windows since the 95 version. However, after feeling  the bitter taste of Windows Vista Ultimate in my fingertips for the lat two weeks (my HP machine came with it "for free"), I have decided to take some action and switch to Linux. Right now, I am still installing 5-buttons mouse and other stuff, but also my Stylus Cx6600. The problem is that I am accessing it remotely. It is installed in a Windows XP machine. 
    I have skimmed through the threads posted here, but have not found steps on how to set up the printer in case it is remotely located. I tried to do it myself. The printer was detected by Ubuntu  and I could even send a print job to it. However, it did not print anything. It just kept on loading papers and spitting them out without a single word in them. I had to shut it down manually and clean the job queue through Windows XP (I don't know how to see the printer queue using Ubuntu yet).
   I was wondering whether any of you could tell in which of the posts I could find information that could help me, direct me another thread that might contain helpful information for me or just provide me some assistance directly.

   Some extra information that might help you guys help is:

   - I have lately installed Dog guard, but did not have time to configure it yet, so I have it disabled now. I think it should not be affecting anything, but you never know.

   - My Ubuntu version is (Gutsy Gibbon) 7.10.

   By the way, I am really impressed with the amount of helpful information I could find in terms of setting up stuff online for Ubuntu. I am really optimistic about this O.S. change! :)

    Thank you everyone for the attention and help.
    Best.

---

### Post by bean77 on 2007-12-01
Here is what I just got...please tell me what else I need to do!

```
sane-find-scanner
```

```
lydia@lydia-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0838) at libusb:005:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

---

### Post by bean77 on 2007-12-01
So then I did 

```
scanimage -L
```

```
lydia@lydia-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

---

### Post by bean77 on 2007-12-03
From the very first post, I am following along to set up my scanner with SANE.  I get to here:

```
sudo echo "usb 0x4b8 0x813" >> /etc/sane.d/epson.conf
```

And it says "permission denied"

Bus 005 Device 003: ID 04b8:0838 Seiko Epson Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

---

### Post by doug1212 on 2007-12-23
Try editing manually,

```
sudo nano /etc/sane.d/epson.conf
```

```
usb 0x4b8 0x813
```

don't forget to hit enter at the end of the line and save.

Doug.

---

### Post by Haegin on 2007-12-23
Looking at your lsusb output it appears you don't have a CX6600 but have one of the newer Epson printers. Because of this you will need to add
```

usb 0x4b8 0x838

```
to the /etc/sane.d/epson.conf file. You will also not need to edit the UDev rules provided the SANE project supports your scanner. If you have any more problems then check the SANE project website to make sure your scanner is supported.

---

### Post by doug1212 on 2007-12-23
> **Human Prototype said:**
> Looking at your lsusb output it appears you don't have a CX6600 but have one of the newer Epson printers. Because of this you will need to add
```

usb 0x4b8 0x838

```
to the /etc/sane.d/epson.conf file. You will also not need to edit the UDev rules provided the SANE project supports your scanner. If you have any more problems then check the SANE project website to make sure your scanner is supported.

Well spotted, I've got my eye test booked ;)

Doug.

---

### Post by coldReactive on 2009-08-16
> **Patient0 said:**
> Ok, so not one to be beat, I have done a little bit of snooping. I have found out that the scanner is always on the 005 bus, only the device number changes. So after learning a few more commands I run the folloowing straight after rebooting:

#sudo chgrp -hR scanner /dev/bus/usb/005


This worked so onto finding an automated way of delivering this line, remembering it needs root access. My solution was to do this:

- Open terminal
- sudo -s -H
- scanimage -L
- record the two numbers after libusb, the first is the bus number
- cp /etc/rc.local /etc/rc.local.bak
- gedit /etc/rc.local
- before: exit 0 - type: chgrp -hR scanner /dev/bus/usb/005 (insert your bus number instead of 005)
- close and save
- reboot

Remembering that if xsane errors when closing then it is due to saving preferences issues, just go in preferences and untick save preferences.

If this is bad practice then please tell me. But it has seemed to resolve the problems.

That to all who have helped -- Linux Rules!

What if scanimage -L gives the following message and no libusb?

```
device `pixma:04A91734_514865' is a CANON Canon PIXMA MP190 multi-function peripheral

```

---

### Post by Uchiha_madara on 2009-08-17
thanks dude ...but i have a Question ...

can we implement these steps on later versions of ubuntu (Gusty , Hardy and Juanty) or not ?

---

### Post by onnod on 2009-08-17
FWIW, the CX-6600 is plug n play on Jaunty. I have never had issues.

---

