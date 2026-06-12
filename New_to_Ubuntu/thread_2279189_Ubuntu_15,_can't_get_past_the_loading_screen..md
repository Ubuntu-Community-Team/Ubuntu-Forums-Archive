---
title: "Ubuntu 15, can't get past the loading screen."
date: 2015-05-21
forum: New to Ubuntu
---

### Post by rah2 on 2015-05-21
Hello guys, 

I need your help, I can't seem to know what caused this to happen but I am unable to get to the login screen.  This happened after I upgraded from 14.10. 

I have a dual boot with windows 8.1.  My graphics card is intel.  Has any of you encounterd an issue like this?  

[IMG]http://i57.tinypic.com/bezdiw.jpg[/IMG]

I am not actually sure if my issue is similar to this;  [http://ubuntuforums.org/showthread.php?t=2268988&page=2&highlight=ubuntu+15.04+login](http://ubuntuforums.org/showthread.php?t=2268988&page=2&highlight=ubuntu+15.04+login)

If worse comes, I might just have to reinstall Ubuntu some time.  I jsut installed it to try learn Linux once again.

---

### Post by cariboo on 2015-05-21
It would be helpful, if you told us which version of 15 you are using, 15.04 was released in April, and 15.10 will be released in October. I'running Wily Werewolf (15.10) and I see the same screen when booting up. It has no affect on the way Wily runs.

Would you let us know what graphics adapter and driver you are using.

---

### Post by rah2 on 2015-05-22
Hello cariboo,

I am using 15.04, and my graphics is AMD Radeon HD 7520G.  Unfortunately, I am not quite sure which driver I used on Ubuntu. You mentioned you see the same screen when booting up as I posted, did it take a long time to get into the login screen too?  The longest time I waited just to see if I can get into the login screen before I give up was 30mins.

---

### Post by tristan16 on 2015-05-22
> **cariboo said:**
> It would be helpful, if you told us which version of 15 you are using, 15.04 was released in April, and 15.10 will be released in October. I'm running Wily Werewolf (15.10) and I see the same screen when booting up. It has no affect on the way Wily runs.

Would you let us know what graphics adapter and driver you are using.

If 15.10 will be released in October, isn't it a little obvious the general public would be using 15.04?

---

### Post by tristan16 on 2015-05-22
> **rah2 said:**
> Hello cariboo,

I am using 15.04, and my graphics is AMD Radeon HD 7520G.  Unfortunately, I am not quite sure which driver I used on Ubuntu...

Did you manually install a driver, or did you install it via Ubuntu Software Center?

---

### Post by rah2 on 2015-05-22
> **tristan16 said:**
> Did you manually install a driver, or did you install it via Ubuntu Software Center?

yeah i dead.  i updated the driver by selecting another one on **Additional Drivers.  **But I can't remember which one I selected though.

---

### Post by rah2 on 2015-05-22
hello guys!  good news!  i am now able to get in my Ubuntu.  the issue was indeed the graphics driver.  

i found this site:  [https://mwop.net/blog/2014-11-03-utopic-and-amd.html](https://mwop.net/blog/2014-11-03-utopic-and-amd.html)  and followed the cmd:

sudo mount -o remount, rw /

$ sudo apt-get purge 'fglrx*'
$ sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
$ sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx

and when i rebooted... i can now get into the login screen!!!

---

### Post by cariboo on 2015-05-22
> **tristan16 said:**
> If 15.10 will be released in October, isn't it a little obvious the general public would be using 15.04?

Not necessarily, some new users seem to think that the latest is always the greatest, and get themselves into trouble using the development version.

To the op, my system boots in just over 11 seconds, I haven't used an AMD graphics card since they were still ATI, and probably never will.

---

