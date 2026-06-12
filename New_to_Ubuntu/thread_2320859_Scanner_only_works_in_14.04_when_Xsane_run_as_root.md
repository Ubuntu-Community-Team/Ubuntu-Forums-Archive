---
title: "Scanner only works in 14.04 when Xsane run as root"
date: 2016-04-18
forum: New to Ubuntu
---

### Post by swarup on 2016-04-18
I have a Canon lide 220 scanner, and am running Ubuntu 14.04. The scanner works fine, but only gets detected by Xsane when run as root. And if I run Xsane as root, then images that are scanned cannot be opened unless I am root. 

Reading up on this issue of permission problems with usb scanners, the Ubuntu recommendation is "Add saned to the group which owns your scanner device". But seeing the below output, you can understand that my scanner is owned by "root" and not by any group--

```
$ getfacl /dev/bus/usb/001/006
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/006
# owner: root
# group: root
user::rw-
group::rw-
other::r--
```

There was a [bug report]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/180794") about this back in 2008 with Hardy: "Only root has access to scanners connected to the USB port!! So if you use "SUDO sane-find-scanner" "SUDO scanimage -L", everything works fine. This is very annoying ...". The bug was fixed in Hardy, but has it resurfaced in Trusty? Although not apparently for everyone. [Here is someone]("http://gsusmonzon.blogspot.com/2015/06/canon-lide-220-in-ubuntu-1404.html") who is using my Canon lide 220 scanner with Trusty 14.04 and was able to ensure his user has access to the bus with "sudo chmod u+w /dev/bus/usb//" . In his case "sudo chmod u+w /dev/bus/usb/003/003". But that is not working for me; when I execute this command and then run xsane as my user, it reports "no devices detected".

Someone please guide me how to change the permissions so that my own user can open Xsane and it will detect the scanner.

---

### Post by DuckHook on 2016-04-20
Hi swarup

I'm fumbling a bit here because I don't own a Canon lide 220, but you are correct in not wishing to run scanner as root. Let's start by first getting my own head wrapped around what you are saying. Please confirm the following:

1. The scanner works without further drivers or tweaks so long as you invoke Xsane with sudo.
2. Your version of 14.04 was a fresh install and not the result of a series of upgrades since '08.
3. You added the ppa described in your link and installed the extra apps and libraries.
4. You determined that your scanner is on USB Bus 001 and is Device 006
5. You did: sudo chmod u+w /dev/bus/usb/001/006

The last step concerns me. It ought to be unnecessary to allow write access to general users for this device. Did you follow the alternative suggestion by Tim Theis in the comments section of your same linked webpage? Adding yourself&#8213;not as root&#8213;but in your own account to the *scanner* group sounds like a far better solution if only for safety reasons.```
sudo usermod -a -G scanner swarup
```...assuming your primary username is swarup. If not, use your real username. Reboot and see if that works.

Also, please confirm that I understand pts 1 - 5 above properly.

---

### Post by kurt18947 on 2016-04-20
I'm not familiar with Canon but this problem sounds similar to one that Brother has had in the past -- scanner only works with SUDO privileges. Here is the Brother fix, I wonder if it is applicable to Canon as well.
[INDENT][B]
I cannot use my USB scanner  with a normal user.[/B] 


The Brother Linux scanner driver works only with a superuser by default.
To use it with a normal user, you will have to make some settings.
[URL="http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html"]Setting for normal users

[/URL]Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10**1.** Open "/lib/udev/rules.d/40-libsane.rules" file.**2. **Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".    
  
  The lines to be added---------------------------          
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"  [COLOR=#0000ff]These would need to be changed to Canon idVendor[/COLOR]


     **3.** Restart the OS.[URL="http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html"]


[/URL][http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

[/INDENT]

---

### Post by swarup on 2016-04-20
Many thanks to both of you for your kind help. Duckhook, your five points are all correct. I will add that even after adding the ppa extra apps and libraries described in my above link, xsane did not work even with sudo. But after having added those, and then in addition doing "sudo apt-get -y dist-upgrade", after that when I would start xsane with sudo, then it would recognize the scanner and work properly-- but only as root. And for three days I scoured the net and implemented whatever tips I could find from other posts, trying to get the scanner to be recognized without starting xsane as root. That is, with xsane as normal user. This was all prior to starting this thread. And I had tried both of the things mentioned above ie what you Duckhook have mentioned, as well as what Kurt has mentioned. But the problem remained that the owner of the scanner remained "root" and not any group-- so when there was no group owning the scanner, then adding me to that group didn't have any benefit. But after receiving your posts this morning I was going to try "sudo usermod -a -G scanner swarup" again, and then reboot and see what happens. Before doing so, for the heck of it I tried just starting up xsane as a regular user to see what happens-- and out of the blue it is working as a regular user. I had left if for three days, in exasperation not wanting to waste any more time on it. And now out of thin air it is working perfectly-- not as root but as regular user. So the problem is solved, and I am baffled. I do not understand why it is working now, except to say that I tried many, many things three days ago and perhaps at one point I may not have rebooted before testing. And now in the interim I've rebooted and the needed change was implemented. Whatever may be the case-- problem solved :-)

(If anyone comes to this thread seeking a solution for the Canon scanner, you can see the full steps I took [here]("http://ubuntuforums.org/showthread.php?t=2258489&page=2"). But as I say, when I did those steps the only thing that was accomplished at that time was the ability to scan with xsane running in root. It remains a bit of a mystery to me how the scanner has begun working with my normal user. But it may have to do with the addition I made to /etc/sane.d/genesys.conf, as noted in the referred post. Best of luck!)

---

### Post by DuckHook on 2016-04-20
Glad it all worked out for you. Have a cookie. ;)

---

### Post by mpb_ on 2016-11-30
I encountered the same problem: xsane requires root on my Ubuntu 14.04 box.  I'm not sure why.  I don't scan that often.  But this time I decided to investigate.

```

$  lsusb | grep Canon
Bus 001 Device 013: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25

$ ls -l /dev/bus/usb/001/013 
crw-rw-r--+ 1 root root 189, 12 Nov 30 20:24 /dev/bus/usb/001/013

$ sudo chmod o+rw /dev/bus/usb/001/013 

$ ls -l /dev/bus/usb/001/013 
crw-rw-rw-+ 1 root root 189, 12 Nov 30 20:24 /dev/bus/usb/001/013

```

After the above "chmod" command, xsane can now be run as non-root.  This is a temporary fix, as the next time I unplug the scanner, the permissions will probably reset.

Another temporary solution: use "chgrp" instead of "chmod", and set the group to the group of the user who runs xsane.

Perhaps I should add that I use the Openbox window manager, not Unity desktop environment.  This may be why I encounter the problem.

---

