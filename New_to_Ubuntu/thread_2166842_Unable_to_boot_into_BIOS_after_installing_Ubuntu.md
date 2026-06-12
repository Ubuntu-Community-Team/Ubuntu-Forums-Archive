---
title: "Unable to boot into BIOS after installing Ubuntu"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by gabe2 on 2013-08-11
Hello,

So I just installed Ubuntu 12.04 (64-bit) on my 2nd hard drive, careful to manually create partitions and load the boot stuff on that drive thanks to a nice tutorial. Now, I know the OS is on my 2nd hard drive, but I am suddenly unable to boot into BIOS to switch the boot order and let GRUB tell me which OS to choose. After the first time I booted up, I got a screen asking me which OS to load, but only Windows 7 was available. There was an option to go into settings using the F8 key, but I didn't see anything useful, so I just booted into Windows 7 (and I wanted to make sure my Windows was fine, and it is). Now, that screen doesn't even come up any more.

What am I missing or doing wrong here? Every time I reboot now, it just goes into Windows 7 after a longer-than-usual OS loading screen right after POSTing. It's making me a little nervous that I can't get into BIOS because I also do a little overclocking and now I can't access it should something go wrong. I'm not going to have to unhook my computer, lug it out, open it up and unplug my 2nd hard drive, am I?

While I obviously want my BIOS back, will EasyBCD allow me to boot both Windows 7 and Ubuntu at the same time so I can switch between them? For that matter, *CAN* I switch between them? Is there another way?

Thanks!

---

### Post by grahammechanical on 2013-08-11
Ubuntu cannot prevent you from loading the BIOS becasue the BIOS is accessed before the Grub boot menu, which itself is accessed before any attempt is made to load Ubuntu.

How did you access the BIOS before you installed Ubuntu? What instructions does the motherboard user guide give for accessing the BIOS? If you were accessing the BIOS to do that overclocking by means of some Windows utility then you need to find out how to access the BIOS directly by pressing some key as the machine runs its POST. And then select which drive has boot priority.

Regards.

---

### Post by gabe2 on 2013-08-11
Did it the old-fashioned way, pressing the DEL key at POST. Before installation, all I did was change the boot order so it read my DVD first so I could install Ubuntu. Now, despite hitting the DEL key multiple times at POST, it just seems to refuse to go into BIOS. I'm aware that BIOS is completely isolated from either OS and shouldn't be affected, but I'm at a loss here.

---

### Post by gabe2 on 2013-08-11
OK, I didn't realize that the /home partition should pretty much take up the rest of my second hard drive, so I intend to reinstall Ubuntu. I went into disk management on Win7 and deleted all the partitions so I could start over, but this time I ***CAN*** access BIOS using the DEL key at POST. So, there's *something* going on after installing Ubuntu that's preventing me from accessing BIOS, but I can't figure out what or why.

By the way, I was able to boot into Ubuntu by pressing F12 and changing the boot order, but apparently it won't remember it? Also, am I correct in assuming that GRUB is installed on Win7 and possibly the cause of taking longer than usual to boot up Win7? That would explain why it's still doing that despite deleting Ubuntu from my 2nd hard drive.

*EDIT* I am suspecting this has something to do with the bootloader and after doing some more researching, I'm not the only one who's experienced this issue, but still have yet to find a fix.

For the record, btw, my mobo: Gigabyte Z68X-UD3H-B3 (1.0). BIOS version is F10.

---

### Post by oldfred on 2013-08-11
Thead closed. New thread created.
[http://ubuntuforums.org/showthread.php?t=2166920](http://ubuntuforums.org/showthread.php?t=2166920)

---

