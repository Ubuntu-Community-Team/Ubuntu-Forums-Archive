---
title: "Seeing Hard Drives"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by ralinux on 2013-03-25
I am running Ubuntu 12.04, 64 bit version, using the Gnone desktop.

I am having a problem seeing other drives on my system - be they internal SATA drives and petitions or external usb drives.

Around 50% of the time when I boot up, all drives are visible and mountable.  However, the other 50% of the time the drives are not visible whatsoever on the system (e.g. on the desktop, in Computer or in Places), although they do show in GParted.

My question is: How can I get the drives to show if they don't appear on boot-up (other than by completely rebooting the system and hoping for the best)?

Thank you, in advance, for any assisatnce!

---

### Post by Bashing-om on 2013-03-25
ralinux; Hi !

Oh My // That could be any number of things; IRQ conflicts ? Buss contention ? controllers all confused or messed up ... many many things.
Ubuntu logs most everything that happens on the system in some log some where. Do this in an attempt to narrow things down.
```
sudo cp /var/log/dmesg /var/log/dmesg-debug1
``` when the system is fully functional.
When the system next has problems mounting the external devices run the code to make another file of the current situation:
 ```
sudo cp /var/log/dmesg /var/log/dmesg-debug2
``` [debug1 ->debug2].
Then compare the two files for differences. This procedure may point to the nature of the problem.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by ralinux on 2013-03-25
Hi Bashing-om

Thanks for the suggestion.  I have made log file as suggested (the drives aren't showing at the moment), and shall do the same again when they appear back.

At 984 lines, however, this will take some cross-checking!!

Thanks again - will update if I get anywhere.

---

### Post by Bashing-om on 2013-03-25
ralinux;
Roger that !
Even though the files are Large, I prefer to take a bit of time and look through them carefully //there does exist means to filter the files for desired conditions. The "grep" utility is great; For instance:
```

dmesg | grep -i error
dmesg | grep -i warn
``` or some other parameter than "error or warn"[INDENT=2]
logs tell many tales

[/INDENT]

---

### Post by ralinux on 2013-03-25
Thanks again, Bashing-om

I will certainly give that a try.  However, since posting this topic this morning, I haven't seen the other drives appear at all (after about 5 re-boots), so it might be some wait!

I'd be interested to learn whether you or other users have come across this problem before.

Thanks again for your help - hopefully I might see them tomorrow!!!  :)

---

### Post by Bashing-om on 2013-03-25
ralinux; 
well, let's see if we can hasten things up a bit. See what dmesg has to say about any usb devices; 

```
dmesg | grep -i usb
```
mine (working) looks like this:
> 
sysop1@1204-a:~$ dmesg | grep -i usb
[    0.234502] usbcore: registered new interface driver usbfs
[    0.234552] usbcore: registered new interface driver hub
[    0.234618] usbcore: registered new device driver usb
[    0.497334] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.497547] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.508031] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.508207] hub 1-0:1.0: USB hub found
[    0.508393] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.508615] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.566138] hub 2-0:1.0: USB hub found
[    0.566309] uhci_hcd: USB Universal Host Controller Interface driver
[    0.566408] usbcore: registered new interface driver libusual
sysop1@1204-a:~$
 
In your case we are looking for warnings and errors.
==> hope this helps

---

