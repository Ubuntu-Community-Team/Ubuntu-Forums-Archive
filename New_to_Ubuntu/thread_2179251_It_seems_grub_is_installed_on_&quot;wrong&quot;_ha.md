---
title: "It seems grub is installed on &quot;wrong&quot; harddrive"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by aleksandar5 on 2013-10-07
Dear friends,
I tried latest daily build of x86 Ubuntu and installed it along my Win8 install. After a reboot I got to a black screen and "grub rescue:" prompt. After fooling around I tried booting different HDs from BIOS and it seems grub is installed on my 4th Disc (same as Ubuntu is installed on) as I got the grub screen and could boot into Win8 no problems. 

Now should I be worried about this? I mean should grub be on a "first" disck? Should I try and move grub to first disc somehow or something? 

Thank you for your time!

---

### Post by Bucky Ball on 2013-10-07
Welcome. Not really an issue. Just set the BIOS to boot from this disk at startup and should be fine. If it ain't broke, don't fix it. Easy to put grub on sda if you really want, but don't see much point in your situation. ;)

---

### Post by fantab on 2013-10-07
> **aleksandar5 said:**
> Now should I be worried about this? I mean should grub be on a "first" disck? Should I try and move grub to first disc somehow or something? 

GRUB can be on **any** Hard Disk. It is recommended that you must install GRUB to the HDD where you have Ubuntu installed if you have more than one HDD. Looks like by mistake you got it right. ;)
Like Bucky says just change the HDD boot order in BIOS to boot your HDD with Grub first.

---

### Post by oldfred on 2013-10-07
With multiple drives & multiple installs it is always a good idea to understand what is where. 
I regularly run BootInfo report or the part of it that is the bootinfoscript as part of my rsync backup. Then I have documentation on what is installed where and details of partitions and drives.

       [URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info
[/URL]
 [http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by Bucky Ball on 2013-10-07
> **oldfred said:**
> 
I regularly run BootInfo report or the part of it that is the bootinfoscript as part of my rsync backup. Then I have documentation on what is installed where and details of partitions and drives.

 

Nice tip. Thanks. ;)

---

