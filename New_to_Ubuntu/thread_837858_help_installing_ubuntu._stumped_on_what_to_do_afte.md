---
title: "help installing ubuntu. stumped on what to do after selecting install"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by wattsburns on 2008-06-22
i put the ubuntu cd in and rebooted my computer. i select install and it goes through the whole ubuntu loading bar thing. then shows this:: Loading, please wait... Linux ubuntu 2.6.24-16-generic #1 SMP T Apr 10 13:23:42 UTC 2008 i686 The programs included wth the Ubuntu system are free software: the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright. Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law. To access official Ubuntu documentation, please visit: [http://help.ubuntu.com/](http://help.ubuntu.com/) To run a command as adminstrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details.
ubuntu@ubuntu:~$ _ what do i do from here?

---

### Post by 449 on 2008-06-22
Try burning the iso onto a new cd at a slower speed.

---

### Post by Ripfox on 2008-06-22
Sounds like you got dropped to a command line interface. Your graphics did not configure correctly, I guess. Is this AFTER installing Ubuntu or are you trying to use the live cd?

---

### Post by Ripfox on 2008-06-22
Try > sudo dpkg-reconfigure xserver-xorg

---

### Post by wattsburns on 2008-06-22
i put in the cd that i burned ubuntu to. so i guess the live cd. it loaded all the way thru the orange progress bar you know? then it went to the cmd screen and showed that. i dont see what reburning it at a slower speed would do. i scanned it for defects and it said its fine. ::::::::: ok ill five that a try hold on

---

### Post by wattsburns on 2008-06-22
alright typed that in and pushed enter and it took me thru a bunch of stuff with my keyboard. after i did that(i did it all correct i know it) it said this in the cmd thing::: xserver-xorg postinst warning: overwriting possibly-customising configuration file; backup in /etc/x11/xorg.con.20050622202554 under that it says: ubuntu@ubuntu:~$_

---

### Post by Ripfox on 2008-06-22
try typing > startx

---

### Post by Ripfox on 2008-06-22
if that doesnt work, download the "alternate install" cd and try that. Be aware when you do a full install of Ubuntu it will erase any info on the computer unless you pay attention to where and how you install it. But if you don't care or don't have anything important on the computer just install it to the entire disk and erase the whole computer hard drive.

---

### Post by wattsburns on 2008-06-22
ok the screen flickers then theres an error. maybe my video card isnt compatible with this version??

---

### Post by Ripfox on 2008-06-23
Download the "alternate install" cd and try that.

---

### Post by wattsburns on 2008-06-24
alright i thought before i tryed the alernative cd, id try installing it in safe graphics mode and it said it was unable to display video input. so i tryed it normal again and it said it failed the graphics thing but the other 2 got ok. i think the graphics thing was gfk or something? idk it went fast.

---

