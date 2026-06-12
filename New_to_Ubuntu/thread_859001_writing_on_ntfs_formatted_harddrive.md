---
title: "writing on ntfs formatted harddrive"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by shakujou on 2008-07-14
Is there a program that I can install to backup files onto an external HDD?  I'm moving to another computer, and really need to back up files from my old 7.04 install.  Since it's a friend's HDD, I can't format into ext3.

---

### Post by ChameleonDave on 2008-07-14
No particular program is needed.  Simply plug it in, and you should be able to transfer files.

Is it failing to automount?  In that case, we can do it manually.  Plug it in and do "sudo fdisk -l".

---

### Post by shakujou on 2008-07-14
It says I don't have permissions to write to this folder when I try and transfer files over to the drive.  

I otherwise displays the files perfectly, and I can open and access them with no problems.

---

### Post by ChameleonDave on 2008-07-14
> **shakujou said:**
> It says I don't have permissions to write to this folder when I try and transfer files over to the drive.  

I otherwise displays the files perfectly, and I can open and access them with no problems.
OK.  The drive is mounted as root, so you have to be root to transfer files to it.

Also make sure that you mount it as "ntfs-3g" and not just "ntfs".

So, use "sudo mv" instead of just "mv".  Or if you are using a graphical file manager, start it with "gksudo nautilus" or "kdesudo konqueror", or suchlike.

---

### Post by mcduck on 2008-07-14
Just one thing you should remember: NTFS isn't able to store Linux/Unix-style file ownerships & permissions.. So if you make a backup to NTFS you should compress the files into a .tar.gz archive and copy _that_ to the NTFS drive.. That way when you extract the files again their ownerships and permissions will be correct..

---

### Post by shakujou on 2008-07-14
Sorry, but it's been awhile since I used Linux... and the reason is because my install got somewhat damaged during a thunderstorm, which complicated a lot of things.  Much of which comes with the inability to use terminal.  

Is there a graphical way to do this?

---

### Post by ChameleonDave on 2008-07-14
> **mcduck said:**
> Just one thing you should remember: NTFS isn't able to store Linux/Unix-style file ownerships & permissions.. So if you make a backup to NTFS you should compress the files into a .tar.gz archive and copy _that_ to the NTFS drive.. That way when you extract the files again their ownerships and permissions will be correct..
Good point! although it does only apply to configuration files and suchlike.  He doesn't need to worry so much about his movies and suchlike.  They can all just be given the right permissions en masse when they are transferred back.  And it's not necessary to gzip the tar archive.  LZO can be used for faster compression on huge files, or no compression at all.

---

### Post by ChameleonDave on 2008-07-14
> **shakujou said:**
> Sorry, but it's been awhile since I used Linux... and the reason is because my install got somewhat damaged during a thunderstorm, which complicated a lot of things.  Much of which comes with the inability to use terminal.  

Is there a graphical way to do this?
Yeah, but the command line is easiest.

Let's say you want to back up everything in /home/shakujou to /media/external.

Do this:
```

tar -vcf /media/external/shakujou-backup.tar  /home/shakujou/

```
That should work.

---

### Post by Troll_the_Great on 2008-07-14
It is an easier way.Install ntfs-config from synaptic and it will auto-mount them at startup.
```
sudo apt-get install ntfs-config
```
If it keeps complain about ownership, open nautilus as "root" by hitting Alt+F2 and typing "gksu nautilus"), navigate to your hard drive and you're done :)
Have a look at this links:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Hope this helps.
Cheers!

---

### Post by shakujou on 2008-07-14
After installing ntfs-config and rebooting, it wont even detect the external HDD.  

Also, when I say I have the inability to use the terminal, I mean it's a white block incapable of text input.  I basically just want to get pictures off of here and that's about it.

---

### Post by Troll_the_Great on 2008-07-14
You mean you can't see your hard drive after installing ntfs-config?If you click in Applications-System Tools-NTFS configuration tools you can't see it?Before you installed it detected it?If yes, remove ntfs-config
```
sudo apt-get remove ntds-config
```
and then try what I suggested in the second part: open nautilus as root and move what you want where you want.Post back the results.
Cheers!

---

### Post by ChameleonDave on 2008-07-14
> **shakujou said:**
> After installing ntfs-config and rebooting, it wont even detect the external HDD.  

Also, when I say I have the inability to use the terminal, I mean it's a white block incapable of text input.  I basically just want to get pictures off of here and that's about it.
I don't get how you can be using a variety of graphical applications, but not a simple one like a terminal.  Even if gnome-terminal is not properly installed, you can always get to the real TTY terminals by hitting Ctrl + Alt + F1-F6.

---

### Post by shakujou on 2008-07-14
I love how the fact that I can't use the gnome-terminal goes completely unnoticed...

Anyway, found out my problem.  Turns out that I need to safetly unmount the drive from when I last used it in Windows.  Odd problem, but only saw the error message telling me this after using the links in your posts Troll.  

Thanks guys!

Also, I actually had no clue I could do the ctrl + alt + F1/F6...

Second edit: That also fixed all the other problems I've had since the thunderstorm... wtf.  I can even use the graphic terminal now.

---

### Post by Troll_the_Great on 2008-07-14
Glad we could help.Please mark your thread as "solved" if you don't need further assistance.
Cheers!

---

