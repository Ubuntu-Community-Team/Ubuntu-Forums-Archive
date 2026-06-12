---
title: "Changing Grub Boot Order"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by loseby on 2013-07-11
Linux is my secured OS and used for banking etc mostly.  PC is dual boot with Ubuntu on a seperate hard drive and Win7 on another.

Want to change boot order. I have done this previously but for the life of me I cant recall exactly how. Pretty sure it was some program I downloaded and used that to edit the order...... I am not comfortable with the terminal

Any help ?

---

### Post by VMC on 2013-07-11
```
/etc/default/grub
```

Look for this line:

"GRUB_DEFAULT=0"

edit: afterwards you need to run "[FONT=Bitstream Vera Sans Mono][SIZE=3][COLOR=#000000]update-grub" , I believe. I edit my grub differently. Just my recollection.
 
Here's a link that may help :
[/COLOR][/SIZE][/FONT][Grub2 Configuration]("http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html")

---

### Post by Rex Bouwense on 2013-07-11
> **loseby said:**
> 
Want to change boot order. I have done this previously but for the life of me I cant recall exactly how. Pretty sure it was some program I downloaded and used that to edit the order...... I am not comfortable with the terminal

Any help ?
You are probably talking about GRUB customizer.  See here:
[http://www.ubuntugeek.com/how-to-install-grub-customizer-in-ubuntu-13-04.html](http://www.ubuntugeek.com/how-to-install-grub-customizer-in-ubuntu-13-04.html)

---

### Post by oldfred on 2013-07-11
You may have used Grub Customizer, but I prefer the method suggested by VMC above.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[URL="http://ubuntuforums.org/showthread.php?t=2076205"]http://ubuntuforums.org/showthread.php?t=2076205

[/URL] New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

[URL="http://ubuntuforums.org/showthread.php?t=2076205"]
[/URL]
 HOWTO: Grub Customizer Updated for grub 1.99 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[URL="http://ubuntuforums.org/showthread.php?t=2076205"]
[/URL]

---

### Post by loseby on 2013-07-11
something went funny before ( before posting my question ) and after rebooting I cant get into Windows. It was strange , it took ages for Ubuntu to close and I pulled the switch after 5 minutes.  Managed to get back here .

This PC has a hell of a lot of stuff I want.......and I know more backups etc 

After this scare I think I will just wait for GRUB to appear and select windows to boot .... hopefully it will this time

---

### Post by oldfred on 2013-07-11
Never force a shutdown, remember the Elephants.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Anytime something funny happens, it is a reminder that your backups must be current.
      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

