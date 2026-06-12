---
title: "First time install--problem with linux-generic kernel"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by kirby-u on 2008-11-17
Hi, All, 

I asked for help in the Installation section, but haven't gotten any responses. Since I am new to all things ubuntu and computer re-formatting, perhaps my question belongs here. 

I am trying this on an old Dell Inspiron computer:
old OS: Win XP Pro
30 GB hard-drive
256MB

I've tried to install both ubuntu 8.04 and 8.10 from the i386 alternate installer boot CD (I burned it myself). Both versions stop with an error loading the 'linux-generic' kernel during the base install section. The error doesn't really give me more information than that, other than the address of a log file that I don't know how to access. 

I have read several threads here but am not following them, really. I have seen a lot about command line possibilities but I don't know how to get to the command line to try anything. 

Can anyone help, or point me in the right direction? 

My previous posts: [http://ubuntuforums.org/showthread.php?t=984010](http://ubuntuforums.org/showthread.php?t=984010)

Thank you in advance.

---

### Post by mjwhitfield on 2008-11-17
when it pukes out the error and the log file location, hit ALT+CTRL+F3 and it'll take you to a new terminal.  I have no idea what the username and password will be, perhaps someone else here can fill in that blank.

However, once you are in, get the log file to output its contents with the following:
```
cat /path/to/file
```

Then write it down and come tell us what it says :)

---

### Post by philinux on 2008-11-17
Did you burn at 4x. And did you choose the option to check cd for defects.

---

### Post by kirby-u on 2008-11-17
@philinux No, I didn't burn at 4x. I will burn it again at that rate. I will also check the CD for defects before running the install as well. 

@mjwhitfield I will work on the philinux ideas and see what happens. If it turns out the same, I will try your idea. 

I will try both of these and report back the results later this evening. 

Thanks to you both.

---

### Post by oilchangeguy on 2008-11-17
if nothing else, your computer would greatly benefit from adding more ram. bump it up to at least 512mb. that may help with your current problem. if not when you do get it going, it will run much better.

---

### Post by LowSky on 2008-11-17
> **philinux said:**
> Did you burn at 4x. And did you choose the option to check cd for defects.

Slower is better when burning an ISO.

I have a similar laptop running 8.04, so I know its possible and shouldnt give you any issues.

---

### Post by kirby-u on 2008-11-17
> **philinux said:**
> Did you burn at 4x. And did you choose the option to check cd for defects.

So what do you do if your CD fails this check? 

Here is the message:

> The ./pool/main/g/gstreamer0.10/gstreamer0.10-tools_0.10.21-4_i386.deb file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted.

I did re-burn the image at the 4x rate before attempting this. 

Thanks.

---

### Post by kirby-u on 2008-11-17
Ok. I've had no luck here. 

Both of my 4x burned boot CD's (one for 8.04 and 8.10) have not passed the CD check for defects. 

I tried to install again in spite of this. The hang-up is again the 'linux-generic' load during the base system install. 

I tried the ALT+CTL+F3 at this part and a command like interface came up. I admit, I didn't really know what I was doing. 

I tried: usr=name ; nothing happened. 

When I just typed the "cat /path/to/file", it returned that there was no file in the directory. I tried both "file" just as I typed it one sentence before as well as trying the path that was on the error page. 

I have not gotten any more information. --How do I eliminate a hardware problem? I have never noticed the CD-ROM ever having a problem before, but it would be nice to know for sure this isn't the root of all these problems. 

Thank you again.

---

### Post by louieb on 2008-11-17
> **kirby-u said:**
> Both of my 4x burned boot CD's (one for 8.04 and 8.10) have not passed the CD check for defects.

Then try 2x. Got to have a good burn. All it takes is a few twisted bits in the wrong place to give strange results. 
[HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM") 
[BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by heroes_on_a_half_shell on 2008-11-17
Hey Kirby,

I've got an inspiron 8100 (which is basically the same laptop) and it took absolutely no effort to install ubuntu.  However, at 256 mb of ram, I might suggest that you use Xubuntu (typically, less pretty = lot faster). Once you get your installation media correct, then you'll be fine.  (Let me know if you need any help setting up i8kutils - it's important for fan control and temperature readings)

Couple extra questions/suggestions:

1 Did you use the ftp server or the torrents to obtain your iso's?  Personally, I'd trust a torrented file more.  Make sure to use louieb's link to learn how to check the md5sum.

2 Also, how much do you trust that your cd burning device is working properly?  You might try to burn a debian live cd and see if it loads.  I actually installed ubuntu on my 8100 from a live cd, but I had 512 mb of ram and no hurry to get it done.

Anyways, hope all goes well.  Don't hesitate to ask any more questions (as long as you search the forums first and can't find the answer).

---

### Post by kirby-u on 2008-11-18
@louieb thank you. that was helpful.

@heroes_on_a_half_shell a couple of things:

the hashes for both of my iso files match. I did use torrents for the initial downloads. 

I have never had a problem with my CD-ROM drive. My 8200 has been a work horse. I was still using it regularly when I decided to do this. So, there is no reason I would doubt it. Unless there are known incompatibilities with certain models. I did search for that, but did not find anything conclusive. --When I first got this laptop, I un-locked my drive. Would un-locking it have done this?

@louieb I use Nero 7, and it doesn't have a 2x setting that I can find to mount the iso file even slower to ensure accuracy. 

@heroes_on_a_half_shell I will find this debian live CD and give it a go. :)

Thank you both. I will let you know what happens.

---

### Post by the.phantom on 2008-11-18
worse case
1. try and have a buddy d/l and burn a ISO
2. you can order and ubuntu will mail you a good cd ( but takes a few weeks)
3. try not using torrent and just download from a mirror site

---

### Post by PierreDeKat on 2008-11-18
Is there any chance you're using cheap, generic CDs? If so, you might pick up a few reputable ones to burn your Ubuntu alternate CD.

Also, make sure to stick with the alternate CD, rather than the live CD, which will hang about 3/4 of the way into the installation on a computer with less than 512 mb of RAM.

Otherwise, I'm running 8.04 on an old Dell laptop with 256 mb of RAM with no problems, whatsoever. And it runs way better than it does running Windows with antivirus on top.

---

### Post by kirby-u on 2008-11-18
@PierreDeKat I think my media are fine. Verbatim. 

So, since last night, I have burned new boot CD's on my work computer. This was the first time I used it to burn anything, so I am hoping that it burned them right. 

I did download the files again using torrents and made sure the hashes matched (they did every time). I burned at 4x, which was the lowest rate on this drive. 

@heroes_on_a_half_shell I did try the Debian Live CD last night and it detected one corrupt file as well-- on the newly burned CD. So, I didn't attempt an install from that CD. 

Fingers crossed that my issue is just an old burner trying to burn a perfect install disk.... I will try again tonight with the CD's I burned today. I will let you know what happens. 

Thanks everyone.

---

### Post by kirby-u on 2008-11-19
:(:( 

At what point do we say, 'yes, it might be my CD-ROM drive'? I burned 3 images yesterday using a drive that has never been used it is so new. All 3 returned defects when I ran them in my laptop. One of those disks was Xubuntu.  

Are there other ways to install an OS if the CD-ROM drive isn't up to the task? 

Thank you all.

---

### Post by PierreDeKat on 2008-11-20
> **kirby-u said:**
> :(:( 

At what point do we say, 'yes, it might be my CD-ROM drive'? I burned 3 images yesterday using a drive that has never been used it is so new. All 3 returned defects when I ran them in my laptop. One of those disks was Xubuntu.  

Are there other ways to install an OS if the CD-ROM drive isn't up to the task? 

Thank you all.
I'm sure there are, but I don't know them off the top of my head. 

However, I picked up a good used CD-ROM drive for my old Dell laptop off of Ebay for around $15, and that included shipping.

Sooner or later, you're going to need CD-ROM, so might go ahead and consider taking the plunge.

---

### Post by heroes_on_a_half_shell on 2008-12-02
hey kirby,

sorry it's been so long.  i kinda forgot that i had posted.  anyways, if you don't have a friend that would be so kind as to let you burn a cd from their computer, and you don't want to buy a cd drive (i really don't blame you), then you have only a couple options left (that i know of).

1) your 8200 doesn't support booting from usb.  the bios for some reason doesn't have the drivers for the usb interface.  however, you may be able to make a boot disk (floppy) using grub or something similar (which would load usb drivers), thereby allowing you to use these instructions to install from usb:  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

2)  i really don't know how old/trustworthy/reliable/easy this is, but this fella says you can install without any external media from windows:  [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

hope you haven't given up.  once you get into linux, it's worth the occasional extra bit of effort.

---

