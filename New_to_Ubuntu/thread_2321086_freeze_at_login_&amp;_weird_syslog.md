---
title: "freeze at login &amp; weird syslog"
date: 2016-04-20
forum: New to Ubuntu
---

### Post by ZannaStar on 2016-04-20
I'm using Ubuntu 16.04
Since successfully fixing my wifi using this page
[https://wiki.debian.org/InstallingDebianOn/Asus/X205TA](https://wiki.debian.org/InstallingDebianOn/Asus/X205TA)
I have a new issue - the system freezes completely at the end of the boot process about 4/5 attempts. I get to the login screen, and then it happens. If I can get past that moment, I don't get any more freezes.
I checked out syslog & kern.log. The freezes look very very strange
in less (^@^@^@^@^@^@^@^)
[https://roseannastar.files.wordpress.com/2016/04/syslog1.jpg](https://roseannastar.files.wordpress.com/2016/04/syslog1.jpg)
in gedit (\00\00\00\00\00\00\00\) (not highlighted by me)
[https://roseannastar.files.wordpress.com/2016/04/screenshot-from-2016-04-17-08-54-55.jpg](https://roseannastar.files.wordpress.com/2016/04/screenshot-from-2016-04-17-08-54-55.jpg)
Does anyone know what this is, and what I should do about it?

---

### Post by DuckHook on 2016-04-21
It is difficult to help without proper data. I am guessing that your system is an Asus X205TA with a Broadcom 43341 WIFI chipset, but this is only a guess based on your link. Please confirm.

You mention 16.04, which is not yet released, so are you using the Beta version?

Your link is for a fix to Debian at kernel 4.1, whereas Ubuntu 16.04 will have the 4.4 kernel, so the driver you installed may not be compatible. Or it may work in Debian but not Ubuntu because the way Canonical configures the Ubuntu kernel is just slightly different than Debian.

Your attached```
perf interrupt took too long...
```warnings do not seem to be the cause of your freezes. Firstly, the message involves a performance analysis tool for the kernel. The message crops up on some systems but is usually innocuous (bad messages start with "WARNING" or "ERROR"). I am bothered by the string of repetitive 0s and \s, but cannot tell you why they are being generated.

The other and stronger reason to ignore this message is your time stamps. They show that this message is being generated hours after you have logged on, so are unrelated to a freeze at login.

You have the right idea looking through logs and including them in your post and should be commended for such forethought, but a screenshot of a small snippet is not the best way to do this. Attach the whole syslog itself so that members here can parse through all of it. Best to attach as a file. syslog and kern.log can be huge. Since you are attaching files, also do:```
sudo lshw -sanitize > ~/Desktop/lshw.txt
```...and attach the resulting file too. It should show up on your desktop as "lshw.txt". This will give us a complete picture of your system HW.

---

### Post by ZannaStar on 2016-04-22
Thank you so much for the detailed & helpful reply. I will reply as completely as possible although the freezes seem to have mysteriously stopped without me doing anything (& no updates)
[QUOTE=DuckHook]I am guessing that your system is an Asus X205TA with a Broadcom 43341  WIFI chipset, but this is only a guess based on your link.[/QUOTE]
Correct!
[QUOTE=DuckHook]You mention 16.04, which is not yet released, so are you using the Beta version?[/QUOTE]
Yes! which is a good reason for it to wobble. I think I will clean install the shiny official release when I've figured out how to tweak a few more things
[QUOTE=DuckHook]Your link is for a fix to Debian at kernel 4.1, whereas Ubuntu 16.04  will have the 4.4 kernel, so the driver you installed may not be  compatible...[/QUOTE]
Good point, and probably where the problem lies, but this fix seems to work for most folks with the same device. I am not sure there is any firmware other than the Android version that does work. (I am using locally compiled 4.4.6 with config & patches written by other folks with X205TA, but I got the same freezes booting the packaged kernel (4.4.0-16))

As you point out, the data preceding the nonsense from the freezes does not seem to show what triggers them. Looking at the kernlog I can see a panic on the first day, and again on the second day - the second time, the freeze junk \00\00\00\00 comes after that. (It's good to know that 'perf interrupt..' message is innocuous. I am still getting used to the glorious transparency of Linux after years of using Windows and never knowing what is going on.)

The kern.log and syslog files are toooo huge to attach, by far. I can't upload them to my wordpress account because of 'security'. So I don't know how to share them with you! But maybe I don't need help anymore... if the system carries on playing nice today I will mark as SOLVED (mysteriously)

---

### Post by DuckHook on 2016-04-22
I'm happy things are working for you, even if we can't figure out why! If it changes and breaks down again, change thread status back to unsolved and post again. You can also whittle a massive log file down to manageable size using *grep*, but I won't get into that for now. You will have plenty of time exploring the uses of grep if you want, now that you have a stable system.

Regards,
DuckHook

---

### Post by ZannaStar on 2016-04-23
Indeed! Many thanks :D

---

### Post by ZannaStar on 2016-05-06
So, it turns out I am a fool, and what actually fixed it was blacklisting the btsdio module, which I did for a completely different reason. I installed the officially released 16.04, fixed the wi-fi, the freezes returned, I waited for them to go away and started thinking maybe they left because of the blacklist. I did the blacklist again - voila! I tested it really thoroughly, and now I'm 100% sure that was the fix. Fortunately Bluetooth doesn't work anyway so I'm not losing anything by blacklisting that module for now

---

