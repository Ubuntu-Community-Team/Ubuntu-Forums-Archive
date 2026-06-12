---
title: "Massive lag when installing to computer!"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Xm3buX on 2008-08-12
I used Wubie or what ever it's called to install ubuntu, and when I run it, it's fine, but when I click the "install" thing on ubuntu's desktop, there is a massive amount of lag. Eventually when the install thing pops up asking what language, there are no options, and I can't press "next". I'm guessing that the languages appear on the left, because there is a white panel type thing that is blank.

Oh, and there is also lag with my cursor, it moves from the bottom to the top of my screen when I tried moving it 30 seconds before.

Please help, I really want to start using Ubuntu, but I'm going to have to go back to Windows if it lags this much when it's installed properly.

Thanks, all help is appreciated.

---

### Post by hyper_ch on 2008-08-12
if you really want to start using ubuntu why don't you do a real install instead of using wubi?

---

### Post by Dill on 2008-08-12
You may want to pose your question to those at the Wubi forum:

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

They may be able to help you more. However, I would suggest trying to re-install Wubi as a start, following the guide here: [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation) . That way, you can make sure you've installed it correctly and are ready to rock and roll.

Cheers, 
Dylan

---

### Post by Xm3buX on 2008-08-12
> **hyper_ch said:**
> if you really want to start using ubuntu why don't you do a real install instead of using wubi?

What's the difference?

---

### Post by lisati on 2008-08-12
> **Xm3buX said:**
> What's the difference?

It is possible to obtain a CD where you don't have to run Windows (or another OS) in order to install Ubuntu. The "Live CD" lets you try it out first before actually installing.

---

### Post by nicedude on 2008-08-12
Listen to hyper_ch's advice and either do a clean "real" install of Ubuntu ( as in wipe drive and then install ) or research and read one of the many guides on setting up a dual-boot machine ( not very hard especially if Windows is installed first ) so that you can boot to either Windows or Ubuntu, but regardless it will be at full speed and give you the best results. From your enthusiasm you show to learn Ubuntu and get away from windows I have a feeling it won't be long before you will forget that windows is on your GRUB boot list :-) 


Good luck with learning Ubuntu and everyone here will help you with anything you can't figure out.


nicedude

---

### Post by rabatitat on 2008-08-12
A lot...

I suggest you try it out with a different hard drive (avoid install headaches with windows)... Get the desktop install, take out your windows hard drives and install on that spare/test hard drive...

The reason why you're experiencing slowdown is because wubi is emulated on windows... It eats up a lot of resources (considering windows already ate up a lot of your PCs resources).

---

### Post by hyper_ch on 2008-08-12
with wubi it always runs within ntfs and hence it's slower... and there are other problems associated with wubi. If you wanna give it a real try - as you sound like, remove the wubi installation, make about 10 GB free on your harddisk and then install it there. You can also use less than 10 GB but 10 GB should be enough to install additional stuff also.

---

### Post by Xm3buX on 2008-08-12
Right, I have a CD for it, it's just that wasn't working out very well either. If someone could post a link to a VERY detailed guide, I would be grateful.

EDIT: Never mind, I found a good one.

---

### Post by Dill on 2008-08-12
The installation itself is fairly detailed and offers helpful tips, but try this:

[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

This is assuming you have an i386 processor, which you likely do, unless you're running Windows under Boot Camp, or unless you have an AMD 64 processor, or something like that...

---

### Post by hyper_ch on 2008-08-12
(0) MAKE BACKUPS

Before you start, make sure you have backups. You're changing your whole setup and things can go wrong. Either there's an some kind of problem or you could manually just delete all the data... it happened to me... I was used to do partitioning and stuff and at one occasion I didn't pay enough attention and deleted the wrong partition. So, be sure to MAKE A BACKUP FIRST!

(1) before you repartition your drive, run 2-3 times the Windows Defragementation on your c-drive. Very likely you have only one driv.

(2) then start with the actual installation ;) in the partitioner then first make your windows partition smaller (there might be already a hidden partition that contains the data for a reinstallation of the default windows). Make sure you get about 10 Gb diskspace. If you can afforder more giving to Linux, then do so.

---

### Post by Xm3buX on 2008-08-12
Ok, thanks for all the help so far, but now I'm really stuck with the partioning bit. By default it, the slider thing was set as:

/dev/sda3[COLOR="White"]...........................[/COLOR]Ubuntu 8.04.1
2% (654.4 MB)[COLOR="White"]....................[/COLOR]98% (34.9 GB)

[COLOR="DarkOrange"]This part was orange[/COLOR][COLOR="White"].......[/COLOR]   [COLOR="DimGray"]This part was grey[/COLOR]

But when I click Foward or next or what ever, it says "Too small size."

Can anyone tell me what to set this to?
Thanks.

---

### Post by hyper_ch on 2008-08-12
can you make a screenshot or pic with a digicam?

---

### Post by Xm3buX on 2008-08-12
I'll use a digital camera, I'm using another computer.
Just hold on 1 minute.

---

### Post by hyper_ch on 2008-08-12
I haven't used the graphical installer for ages and never used it to resize the windows partition anyway ;)

---

### Post by Xm3buX on 2008-08-12
Well, here is a picture, if anyone can tell me what to set the slider to, thanks alot ;)
[http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu3.jpg](http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu3.jpg)

---

### Post by hyper_ch on 2008-08-12
I think /dev/sda3 is too small. I think you need to make it bigger.

Btw, you run VISTA? If so, use the VISTA partitioner to create some free space.

---

### Post by Xm3buX on 2008-08-12
No, I used XP.
I tried making that one bigger (I put it to 10GB), but it just loaded for about 40 seconds and went back to the default partitioning screen. (How it is in the picture, but without the pop-up).

---

### Post by hyper_ch on 2008-08-12
hmmm, as said, haven't used a gui partitioner for ages... maybe you want to try with a windows based one. I used to use PartitionMagic when I was still using windows. Maybe you have more luck with that one.

---

### Post by Xm3buX on 2008-08-12
> **hyper_ch said:**
> hmmm, as said, haven't used a gui partitioner for ages... maybe you want to try with a windows based one. I used to use PartitionMagic when I was still using windows. Maybe you have more luck with that one.
OK, I have no idea what that is, as you may have guessed, I'm completely useless with computers.

---

### Post by hyper_ch on 2008-08-12
go back to manual partitioning and then make a screenshot with the cam from there, so that all partitions are shown.

---

### Post by Xm3buX on 2008-08-12
I think this is what you mean:
[http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu4.jpg](http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu4.jpg)
[http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu5.jpg](http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu5.jpg)

Sorry for taking so long to respond, the computer I'm on is being really slow :(

---

### Post by hyper_ch on 2008-08-12
what OS do you ahve installed there and why is everything fat32?

---

### Post by hyper_ch on 2008-08-12
and do you have anything important on sda3 (probably drive e: in Windows)? 750 MB are used there, 38 GB are unused. If you could move those data onto sda2 (probably drive d:) then you could select in the installer to delete sda3 completely and use it for installation of Ubuntu.

---

