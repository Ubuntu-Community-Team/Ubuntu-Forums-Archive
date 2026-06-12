---
title: "I've made a really big mess, please help!"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by frida2 on 2013-11-29
Hi there,

I'm really, really new to Ubuntu and I don't know much about computers, so please be patient with me. If I need to provide any more information, please let me know and I'm happy to provide it! I'm running Ubuntu 13.04 Raring Ringtail.

I've been trying to install and use a DeDRM tool, but I've been having problems doing so. I was following some directions that said I needed a version of Python 2.7, but *not* anything Python 3.0 or later (because 3.0 versions are missing some necessary libraries?). I tried to install Python 2.7.5.6, but it didn't work. I thought it was probably because I had the later version of Python, so I went through terminal and removed Python 3.3, so I could install the earlier version. But now that I've uninstalled Python 3.3, a lot of things were removed with it, including terminal and the Ubuntu Software Center. I have no idea how to fix this problem now. I would just take my computer somewhere to have a professional do it, but I live abroad and don't speak the language here. 

Please, please help me if possible. I would really appreciate any advice on this. If there's any more information I could provide, please let me know. Thanks,

---

### Post by thatredbird on 2013-11-29
can you get to the terminal by typing ctrl alt f1?

---

### Post by fantab on 2013-11-29
Do you have a 13.04 install DVD/USB with you? If you don't have then perhaps you can download it from somewhere and make yourself a ubuntu DVD/USB.

Do you see a Boot - Menu? If you do then perhaps you can try Recovery Mode, it will be listed under 'Advanced Options' in the menu...
After you've booted into 'Recovery Mode'... follow the instructions here: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
This page shows a screen-shot of how 'Recovery mode' interface looks: [http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/](http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/)

From Root Shell run the following commands:
```
apt-get update
apt-get install ubuntu-desktop --reinstall
apt-get dist-upgrade
```

If you don't have connection to the net then just run:
```
apt-get install ubuntu-desktop --reinstall
```

If for some reasong '*apt-get install ubuntu-desktop --reinstall*' doesn't work then just use '*apt-get install ubuntu-desktop*'

Let us know what happens...

---

### Post by oldfred on 2013-11-30
We cannot help on any issues with removing DRM as that is against the Code of Conduct that you agreed to to be part of forum.

But you never un-install the default version of python in Ubuntu. Essential parts of Ubuntu run on python. And new versions of Ubuntu are in the process of converting to python3 only, but still have a few bits that use python2, so now both versions are required. 
Above posts should help on getting python and other parts restored.

If recovery mode does not work, you will need live installer to chroot into your system to update it.

---

### Post by Irihapeti on 2013-11-30
Given that support for 13.04 runs out in January, it might be worth thinking about installing 13.10, especially if 13.04 proves difficult to fix.

---

### Post by frida2 on 2013-11-30
Hi there, 

Thanks for the response! I went to the boot menu and found Root Shell. When I enter apt-get update, or any of the other commands, I get some messages that say "failed to fetch http:/tw.archive.ubuntu.com/...etc". Attached is a photo of the messages on the screen. 

Is there anything else I can try? I'd take it to a shop and have a professional look at it, but I'm living abroad and I don't speak the language here. 

I'm not sure that I can use an install CD for my computer. When I bought it, it had Windows 8 preinstalled, and it was a HUGE ordeal to uninstall that and put Unbutu on. I took it to a computer shop and had them do it. From what I've read, it's very difficult to use an Ubuntu install CD for computers preinstalled with Windows 8. Would that still apply in this case? I think the people at the shop completely uninstalled Windows, but I'm not entirely certain.

---

### Post by frida2 on 2013-11-30
Hi there, 

Thanks for the response! I went to the boot menu and found Root Shell. When I enter apt-get update, or any of the other commands, I get some messages that say "failed to fetch http:/tw.archive.ubuntu.com/...etc". Attached is a photo of the messages on the screen. 

Is there anything else I can try? I'd take it to a shop and have a professional look at it, but I'm living abroad and I don't speak the language here. 

I'm not sure that I can use an install CD for my computer. When I bought it, it had Windows 8 preinstalled, and it was a HUGE ordeal to uninstall that and put Unbutu on. I took it to a computer shop and had them do it. From what I've read, it's very difficult to use an Ubuntu install CD for computers preinstalled with Windows 8. Would that still apply in this case? I think the people at the shop completely uninstalled Windows, but I'm not entirely certain.

---

### Post by steeldriver on 2013-11-30
Networking is not enabled by default in the recovery shell - if you have a wired LAN connection, it should be fairly easy to get going by exiting to the main grub menu and selecting the 'Enable networking' option first - once it's done, it should drop you back to the same menu where you can THEN select 'Drop to root shell' - after which try the apt-get commands again

The good (and somewhat surprising) news is that apt is functioning at all, since a lot of that depends on python as well - I was all set to tell you you'd need to download and reinstall the missing packages as .deb files using dpkg.

---

### Post by 3rdalbum on 2013-11-30
If you are using a wired Ethernet connection, you'll need to run "dhclient" from the root shell first, to actually start the connection.

---

### Post by frida2 on 2013-11-30
What is the command line I should use for dhclient?

---

### Post by Iowan on 2013-11-30
It's been awhile...
*Try* **sudo dhclient eth0**

---

### Post by GGG83kf on 2013-11-30
Hi frida2, if you are still struggling with this problem, here are something that may help. You can (1) boot into Ubuntu normally, (2) login as a user and connect to internet, (3) logout and press Ctrl+Alt+F1, which should bring you to a console, (4) login and run the suggested commands, (5) logout the console and press Ctrl+Alt+F7 to return to unity.

---

### Post by frida2 on 2013-12-01
Ha, actually it hasn't been a while, since I'm not familiar at all with computers - as the fact that I removed Python clearly shows :redface: I tried "sudo dhclient eth0", but I only got a message that said "File exists." Any other way to run dhclient from the root shell?

---

### Post by steeldriver on 2013-12-01
Have you gone through the 'Enable networking' boot menu? if so then iirc it sets up a default DHCP connection - I don't recall having to run dhclient manually - you can check the network status with

```
ifconfig
```
or more specifically (assuming 'eth0' is the name of the wired interface)
```
ifconfig eth0
```

and check that the interface has a valid IPaddress. You can also try a ping test

```
ping -c4 google.com
```

If that doesn't time out then you should be good (both connectivity and DNS name resolution are up) in which case you can go ahead and run the apt-get commands

---

### Post by fantab on 2013-12-01
> **fantab said:**
> Do you have a 13.04 install DVD/USB with you? If you don't have then perhaps you can download it from somewhere and make yourself a ubuntu DVD/USB.

Do you see a Boot - Menu? If you do then perhaps you can try Recovery Mode, it will be listed under 'Advanced Options' in the menu...
After you've booted into 'Recovery Mode'... follow the instructions here: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
This page shows a screen-shot of how 'Recovery mode' interface looks: [http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/](http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/)

From Root Shell run the following commands:
```
apt-get update
apt-get install ubuntu-desktop --reinstall
apt-get dist-upgrade
```

If you don't have connection to the net then just run:
```
apt-get install ubuntu-desktop --reinstall
```

If for some reasong '*apt-get install ubuntu-desktop --reinstall*' doesn't work then just use '*apt-get install ubuntu-desktop*'

Let us know what happens...

If you haven't cleaned up your 'apt' cache then there is a good probablity that you still have the package 'ubuntu-desktop' in your cache. You can just run '*sudo apt-get install ubuntu-desktop*' to install it without networking.
Have you tried it?

---

