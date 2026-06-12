---
title: "ubuntu will not start"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by jryprt on 2008-05-08
I have grub it will start XP but will not start 7.10 hardy .
Here is what I have done I had 7.10 running good then upgraded to 
8.04 thur update manager was having some problems so I wiped the linux partition did a clean install of 8.04. I had a backup of 7.10 & 8.04 using [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
so I restore the 8.04 , after it I did not have grub anymore no xp or  8.04 so I wiped the linux partition & installed 7.10 & it started from grub so did xp , did a restore of 7.10 , after words I got grub I can start xp but when I try to start 7.10 I get a ubuntu screen with the bar but it sets there for 2 or 3 min. then I get this  ```
BusyBox V1.1.3(Debia 1.1.1.3-5ubuntu7)Built-in shell(ash) Enter 'help' for a list of Built-in commands (initramfs)
```I have other problems but need to get to ubuntu first . I am using xp for this so will I need to use the live cd to fix it .
Thank you Jerry

---

### Post by TeoBigusGeekus on 2008-05-08
Type 
```
startx
```
and post us the output (error messages etc.)

---

### Post by jryprt on 2008-05-08
> **TeoBigusGeekus said:**
> Type 
```
startx
```
and post us the output (error messages etc.)
Do I use the live cd or after I get the busybox thing ?

---

### Post by TeoBigusGeekus on 2008-05-08
After the busybox thing.

---

### Post by Eccentrus on 2008-05-08
BTW, I am experiencing a similar problem. My Ubuntu won't start after I updated it... I was going to upgrade it to Hardy through internet when the updater said that it recommended me to get the latest update for my gutsy, then after it finished and requested to restart, the problem began, is it because the gutsy's notorious updating problems?

---

### Post by jryprt on 2008-05-08
> **TeoBigusGeekus said:**
> Type 
```
startx
```
and post us the output (error messages etc.)

Got this ```
/bin/sh:startx: not found
```

---

### Post by TeoBigusGeekus on 2008-05-08
Perhaps this thread can help you...
[http://ubuntuforums.org/showthread.php?t=785891]("http://ubuntuforums.org/showthread.php?t=785891")

---

### Post by phoenix_abhi on 2008-05-08
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your hard disk + boot partition numbers are 
5. Type "setup (hd0)", or whatever your hard disk number is.
6. Quit grub by typing "quit".
7. Reboot

if this helped reply

---

### Post by jryprt on 2008-05-08
Thanks to all that tried to help .
I did a clean install & did not use the backup I had .

---

