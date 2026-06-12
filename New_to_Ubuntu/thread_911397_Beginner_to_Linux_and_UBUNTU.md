---
title: "Beginner to Linux and UBUNTU"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by justbailey on 2008-09-05
Hello, I am a beginner to Linux, taking the slow plunge toward freedom.  I currently am double booting in a vm with xp and ubuntu via the wubi install.  I read through a lot of the beginner documentation, which helped, but did not answer a few specific questions I have.  A few questions I have:

1.  My Logitech optical, usb mouse works, but not the scroll wheel in the middle.  Are there drivers i need to grab, how do I do that.

2. My processor is running at 70-90% and all I have running is Firefox.  This did not happen in XP and I thought Ubuntu was easier on hardware than windows, is this because I am dual booting?

3.  The dir /host/ubuntu/disks/boot is using 16.5 GB.  Is this normal?  A boot sector that takes 16 GB, seems excessive to me.

4.  Are there any network troubleshooting tools that anyone finds essential in a Linux/Ubuntu environment?  Does IFCONFIG use switches like IPCONFIG, is there a traceroute, stuff like that.  

Any help would be greatly appreciated as I am trying to get familiar with this new and exciting world!!

-Justin

---

### Post by HermanAB on 2008-09-05
You probably have a desktop search utility running.  Uninstall Beagle to free your processor.

---

### Post by jbrown96 on 2008-09-05
I'm a little confused about how you are running Ubuntu. Did you install it with Wubi and then reboot into Ubuntu, or are you using virtualization like vmware or virtualbox? 
1. I haven't had a problem like this since 7.04, so maybe it's just a problem with you xorg.conf file. Could you paste the output from the following command (use the terminal: applications-->accessories-->terminal) ```
cat /etc/X11/xorg.conf
```
2. let's take a look at processor usage. In a terminal ```
top
``` Paste back with the output. This program constantly updates so let it run for a while (maybe post the output from a couple different times) then press "q" or Crtl+c to quit then copy-paste. 
3. I'm not familiar with how Wubi partitions but let's look at the partitions and disk usage. ```
sudo fdisk -l
``` There is a very nice disk usage analyzer in apps-->accessories. Try to scan file system. Note that any removable media (flash drives, CDs, Windows partitions that are mounted) will show up and skew the results, so remove them first. Post a screen shot (I believe Alt+PrtSc will grab a screen shot of a single windows).
4. man pages are great for this. ```
man ifconfig
``` for wireless you may be interested in iwconfig ```
man iwconfig
```

---

### Post by Shazaam on 2008-09-05
1. Look at your xorg.conf (/etc/X11/xorg.conf) and look for this...
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```
The line you need to look at is the Emulate3button line. If yours is missing or says "false" you need to edit/add the line.

---

### Post by philinux on 2008-09-05
In ubuntu use this.

System>prefs>search and indexing. The app is called trackerd.

Turn it off see if that helps performance.

---

### Post by Nepherte on 2008-09-05
4. traceroute, ping and route are also available.

---

### Post by tuxulin on 2008-09-05
> 1. My Logitech optical, usb mouse works, but not the scroll wheel in the middle. Are there drivers i need to grab, how do I do that.

2. My processor is running at 70-90% and all I have running is Firefox. This did not happen in XP and I thought Ubuntu was easier on hardware than windows, is this because I am dual booting?

3. The dir /host/ubuntu/disks/boot is using 16.5 GB. Is this normal? A boot sector that takes 16 GB, seems excessive to me.

4. Are there any network troubleshooting tools that anyone finds essential in a Linux/Ubuntu environment? Does IFCONFIG use switches like IPCONFIG, is there a traceroute, stuff like that.

Any help would be greatly appreciated as I am trying to get familiar with this new and exciting world!!

1, see [http://ubuntuforums.org/showthread.php?t=286124](http://ubuntuforums.org/showthread.php?t=286124) 

for bluetooth mouse
[http://ph.ubuntuforums.com/showthread.php?t=695333](http://ph.ubuntuforums.com/showthread.php?t=695333)

2, run ps aux in terminal and see which program is eating your cpu time
3, this one is new plus it cant be correct. i dont understand the path /host/ubuntu/disks/boo
4, for most linux commands and usages you can type the command --help, visit any linux command man site or [http://linuxdevcenter.com/linux/cmd/](http://linuxdevcenter.com/linux/cmd/)


Tuxulin

---

### Post by justbailey on 2008-09-08
Shazam,

I get this when I try to view that directory

bash: /etc/x11/xorg.conf: No such file or directory

Any ideas?

thanks

---

### Post by The Cog on 2008-09-08
It's a capital 'X': /etc/X11/xorg.conf

For traceroute, I rather like mtr.

---

