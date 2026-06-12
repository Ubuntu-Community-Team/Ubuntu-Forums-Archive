---
title: "How do I remove GRUB?"
date: 2016-01-18
forum: New to Ubuntu
---

### Post by ryan_reyes on 2016-01-18
Hey there,

So recently I decided I was going to dual-boot my windows 8.1 work laptop with Ubuntu. A few days later I decided I'm better off removing Ubuntu from my laptop and just using the live USB, so I removed the Ubuntu partition. When I turn on my work laptop I get this: *"[COLOR=#111111][FONT=Ubuntu]Gnu grub version 2.02 beta2-9 Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions." [/FONT][/COLOR]*[COLOR=#111111][FONT=Ubuntu]When I type exit it takes me to the windows boot manager and I can get into windows, but how do I get rid of grub?

P.S. I cannot edit the boot order in the bios because it is locked with a supervisor password.[/FONT][/COLOR]

---

### Post by oldfred on 2016-01-18
I do not know if efibootmgr will work on a locked system. If your company locked system, you should not have installed another system on it.

From Ubuntu live installer, in live mode, you need to remove the /EFI/ubuntu folder in the ESP. Otherwise some UEFI will add the Ubuntu entry back again.

Then you need to remove ubuntu entry from UEFI:
       Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[URL="http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743"]http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743

[/URL]
You may need to change boot order also, you want Windows entry first:
      
 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 2,1


     [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

