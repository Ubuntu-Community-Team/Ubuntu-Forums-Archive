---
title: "dual boot, ubuntu fails to load after upgrade"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by cardinal2 on 2014-04-07
Greetings from a new user,

there's a problem i'm trying to solve and here are some facts:

- there is a dual boot set up on this lenovo thinkpad e530, belonging to a friend of mine
- it used to load windows 7 and ubuntu 12.04
- an upgrade of ubuntu was attempted after which ubuntu no longer loads - it shows ubuntu boot graphics and just when you would expect it to load up, the screen turns black with only a small dash in the top left corner, leaving you with the whole thing totally unresponsive
- now i've followed steps for boot repair installation via live usb ubuntu install, donwloaded boot-repair, used the simple, one-click recommended option but only to reboot to exactely the same results
- the ubuntu pastebin file that boot-repair gave me is at [http://paste.ubuntu.com/7217585/](http://paste.ubuntu.com/7217585/)

gettin real desperate, many thanks in advance. hope i didn't break any codes of conduct.

---

### Post by oldfred on 2014-04-07
If you are getting black screen you are usually past what Boot-Repair can help with.

You had 12.04 which is the LTS or long term support?
12.10 expires in April 2014. Not sure of day, but it is about to expire.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Often black screen is video driver issue. But normally Intel does work.

With Intel usually nomodeset does not work, you need other settings but this shows how to edit grub menu to add boot parameters.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

