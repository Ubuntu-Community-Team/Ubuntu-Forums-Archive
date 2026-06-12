---
title: "Problems with grub"
date: 2017-07-09
forum: New to Ubuntu
---

### Post by gr1nch on 2017-07-09
Hi guys, i have a question
i install windows 8.1 and ubuntu 16.04 lts
the problem is when i turn on the computer starts automatically windows 8.1
to use ubuntu i have to use F9 and select the ubuntu and grub starts,

my question is, how can i do for grub starts before windows

pd. sorry for my english, my native language is spanish but i have problems with spanish forums and i don't use translate

saludos!:)

---

### Post by yancek on 2017-07-09
Are they both UEFI installs?  If so, you can set the Ubuntu option to first boot priority with the efibootmgr command from Ubuntu.  Boot Ubuntu and run this command and post the output here:

```
sudo efibootmgr
```

---

### Post by gr1nch on 2017-07-09
hi,
i type that command and this appear 
[IMG]https://ibb.co/fkZsUa[/IMG] [https://ibb.co/fkZsUa](https://ibb.co/fkZsUa)
i restart the computer and nothing happened
when i start my computer and don't touch anything windows starts, 
when i press F9 this appears
[IMG]https://ibb.co/dEaMNv[/IMG]https://ibb.co/dEaMNv

and this appears
[IMG]https://ibb.co/bCqGpa[/IMG]https://ibb.co/bCqGpa

the thing is i want grub start first, how can i do?:(

---

### Post by Dennis N on 2017-07-09
Your first image tells you the current booted system is entry 0000 (BootCurrent: 0000).

To make that first in boot order (instead of 0002, which is Windows), run:

```
sudo efibootmgr -o 0000,0002
```

then reboot and see what you get.

---

### Post by yancek on 2017-07-09
> i restart the computer and nothing happened

Something did happen, you got the output we needed and you posted a link to it now you just have to follow the suggestion above by DennisN to make the change.

---

### Post by gr1nch on 2017-07-09
nope dude, apparently the changes are applied, but when i restart doesn't save the changes

---

### Post by yancek on 2017-07-09
Are you referring to the command suggested by DennisN?  You should post the command and output here so members can take a look.  The command I originally suggested doesn't do anymore than output information and does NOT make any changes while the second command suggested should change.

---

### Post by gr1nch on 2017-07-09
Yes yancek, i talk about the command suggested by Dennis,
here is the screenshot
[https://ibb.co/coxSxv](https://ibb.co/coxSxv)

---

### Post by yancek on 2017-07-10
That's a bit weird, your ubuntu (0000) is first in boot order so I'm not sure what the problem is because it should boot the Ubuntu menu first.  You might try the second ubuntu entry (0003) and reboot to see if that works although this is just a guess.  I've seen a number of posts recently with two ubuntu entries in the efi output but I only have one on my system so...?  If this doesn't work, you might need to download and run the 'boot repair' software and run it with the Create BootInfo Summary parameter selected.  That should give a link to the output which you can post here.

---

### Post by Dennis N on 2017-07-10
Could be because computer is an HP (seen in screenshots), which is known to "customize" the UEFI to boot to Windows and override user. Not saying this is the case - posts by OldFred contain info on HP and this. It may just be bypassing the first entry.

---

### Post by oldfred on 2017-07-10
If an HP or several other brands, they want to only boot "Windows Boot Manager" by description. That is a violation of the UEFI spec.
But there are multiple work arounds, depending on your configuration.
I think most of work arounds are in link in my signature.

Many just use the fallback or hard drive boot entry which still works. That may say hard drive or something similar in UEFI and uses /EFI/Boot/bootx64.efi in the ESP - efi system partition. 
So we copy shimx64.efi to bootx64.efi. Boot-Repair now will do this if you check the "Use the standard file" option in advanced options.

       HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
[/URL]
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076) 
    [URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]        
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

