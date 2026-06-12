---
title: "help!!! a Ubuntu beginner!!!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by nickyc on 2008-04-29
hi there Ubuntu community!!!

Basically Shipit takes to damn long! I have waited 7 weeks and still nothing! I was wondering if anyone has a spare Ubuntu 7.10 (or 8.04) disk anywhere??? Please help me here!!! I know the response will be "why don't u download it?" Well for some reason I can't get them to work once I've gone through all the stages!! So please help a new user out!!!

---

### Post by muteXe on 2008-04-29
What happens when you "try to get them work"?  How do you go about installation once you've dl'd it?

---

### Post by Michael.Godawski on 2008-04-29
So you say you have downloaded an iso but it does not work?

What was the problem? Have your burned the cd correctly? Did you encounter booting issues, installation errors?

---

### Post by ad_267 on 2008-04-29
I can't send you a CD sorry but I may be able to help you with getting the downloaded CD to work. What exactly are you doing to get the CD to work and what isn't working?

---

### Post by Nevyn on 2008-04-29
Without question, the download option is the quickest and easiest way to get Ubuntu. Why doesn't downloading work? Please post what you did when you tried it and the error messages that you may have gotten.

---

### Post by Boyohazard on 2008-04-29
My suggestion would be to burn the CD at 4x rather than "maximum"

---

### Post by muteXe on 2008-04-29
and make sure you "burn image", rather than any burn data options.

---

### Post by infinitejones on 2008-04-29
> **nickyc said:**
> 
...for some reason I can't get them to work once I've gone through all the stages!! So please help a new user out!!!

Why don't you give us a bit more information about the problems you're having getting your downloaded Ubuntu to work? Chances are the Ubuntu community that you're happy to be part of can help you fix it so you won't have to worry about other people sending you disks. 

Tell us what stages you're going through and where it's going wrong.

---

### Post by Boyohazard on 2008-04-29
> **muteXe said:**
> and make sure you "burn image", rather than any burn data options.

Good call, I forgot to mention that :D

---

### Post by nickyc on 2008-04-29
ok basically im burning it at x2 and using imgBurn to put the iso onto disk and YES I am choosing the "burn the image to disk". I get to the installation ubuntu screen and then press enter and the ubuntu loading screen stalls on me! help!

---

### Post by lorienjohnson on 2008-04-29
I used DVD Decrypter and burnt the ISO in Write mode to DVD. That worked for me.

Meanwhile, you say that you get through "the stages". Does that mean that you can actually see the Ubuntu install process? Which stage stops working?

---

### Post by eldragon on 2008-04-29
this is not going to help but will forecast the future.

if you get to that stage, im sure once you get the stamped version of the cd you will suffer in the same manner. the downloaded ISO and the stamped cd are the same and only.

unless your cdrom drive is to blame.... :D

---

### Post by nickyc on 2008-04-29
basically i get to the below screen (see link).

[http://www.futuredesktop.com/images/gutsy/picture_4a.jpg](http://www.futuredesktop.com/images/gutsy/picture_4a.jpg)

and then choose the Start or Install Option. 

Then the below screen comes on and within 5 seconds stalls!!

[http://img136.imageshack.us/img136/5552/boot3fa9.jpg](http://img136.imageshack.us/img136/5552/boot3fa9.jpg)

---

### Post by nickyc on 2008-04-29
stages i've taken:

1. downloaded iso from ubuntu site.

2. used ImgBurn to put the iso onto disk using x2 option.

3. gone into Boot setup and changed to cd drive so that it boots from the cd.

4. then i choose the first option as shown in my last post and then goes wrong!

---

### Post by tacutu on 2008-04-29
man, did you try the alternate cd install?

---

### Post by nickyc on 2008-04-29
I think so yes didnt work

---

### Post by Boyohazard on 2008-04-29
> **eldragon said:**
> ...once you get the stamped version of the cd you will suffer in the same manner. the downloaded ISO and the stamped cd are the same and only.

unless your cdrom drive is to blame.... :D

I agree. It seems like a hardware problem, likely the CD drive, do you have another you can try?

---

### Post by nickyc on 2008-04-29
I could try my other laptop! I will try tonight!!

---

### Post by Boyohazard on 2008-04-29
> **tacutu said:**
> man, did you try the alternate cd install?

By this we mean:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Underneath the Start Download button tick the box which asks if you want the alternate cd

---

### Post by nickyc on 2008-04-29
what is alternate about this cd???

---

### Post by martyssweb07 on 2008-04-29
I've had a similar problem and it was the cdrom.  In fact the worst thing you can do (from my experince ) is get it to work.  By that I mean eventually after trying several times I did get it to install, but it was (of course) a bad install, and you will walk away frustrated.  Do your self a favor replace the cdrom.

---

### Post by tacutu on 2008-04-29
> **nickyc said:**
> what is alternate about this cd???

AFAIK, it's a text-based installer which can be used if the "normal" cd doesn't work.
anyway, did you check that the CD is OK? I mean, after booting select "check CD for defects" and see what happens.

---

### Post by Boyohazard on 2008-04-29
It essentially is just an installation disk; i.e. it's not a LiveCD. It's generally useful for those with older spec machines especially when there isn't much RAM

It's worth a try if your machine is having trouble loading the LiveCD into RAM

---

### Post by nickyc on 2008-04-29
ok well I will firstly try to use it on my other laptop therefore checking whether it's my cd drive and then I will download the alternative cd version without the live cd thingy!!! Nice one for the quick responses here lads! Oh and yes i tried to select the option for cd errors but it just stalled on me!!

---

### Post by conehead77 on 2008-04-29
You could check the md5sum of your ISO to see if its corrupt.
md5sums for hardy can be found here: [http://lug.mtu.edu/ubuntu-releases/8.04/MD5SUMS-metalink](http://lug.mtu.edu/ubuntu-releases/8.04/MD5SUMS-metalink)

just run
```
md5sum nameofisofile
```

and compare with the number on the link.

---

### Post by nickyc on 2008-04-29
done the md5 check! looked fine.

---

### Post by ghostdog2402 on 2008-04-29
Hey!
What about installing from a USB memory stick. Maybe you can boot from USB. Depends on your Bios. Try this [tutorial]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by clairegrrl on 2008-04-29
> **lorienjohnson said:**
> I used DVD Decrypter and burnt the ISO in Write mode to DVD. That worked for me.

I used DVD Decrypter also and had no probs.  I have to say I've only been a Ubuntu user for three weeks, and so far (crossed fingers) I havent had any problems.  Sometimes it's scarey  doing things cause I'm afraid I might mess something up.

---

### Post by Boyohazard on 2008-04-29
Go on mess it up, it's what we're here for anyway :D

Besides your signature makes me think you want to!

---

### Post by clairegrrl on 2008-04-29
Hehehe...you dont seem to understand.  I have no idea what Im doing.  I read this stuff like 100 times before I do anything and so far Ive been lucky that everything has gone ok.  Last night I upgraded to Hardy and was afraid I would get in trouble, but it actually fixed a screen resolution prob Ive been having.  After only three weeks with Ubuntu, Im very happy.

---

### Post by Boyohazard on 2008-04-29
Heh I have no idea what I am doing either. I've broken my Ubuntu install 3 times so far :)

---

### Post by clairegrrl on 2008-04-29
> **Boyohazard said:**
> Heh I have no idea what I am doing either. I've broken my Ubuntu install 3 times so far :)
Boys will be boys.  I like to get things the way I like and dont want anything changed.  Maybe I need to learn how to backup.

---

### Post by Boyohazard on 2008-04-29
Hehe.
To make it easy on yourself, create a separate home directory and just back that up:
[_Psychocats-separate home directory_]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Victormd on 2008-04-29
> **nickyc said:**
> basically i get to the below screen (see link).

[http://www.futuredesktop.com/images/gutsy/picture_4a.jpg](http://www.futuredesktop.com/images/gutsy/picture_4a.jpg)

and then choose the Start or Install Option. 

Then the below screen comes on and within 5 seconds stalls!!

[http://img136.imageshack.us/img136/5552/boot3fa9.jpg](http://img136.imageshack.us/img136/5552/boot3fa9.jpg)

From the flickers in your second image, it seems as if you're going to have video problems. What graphics card do you have? Have you tried the "safe graphics mode"? I don't think this is a problem with your CD/CD-ROM or any thing like that, but just to check, you can use the "check CD for defects" option.
If there is nothing wrong with the CD and the "safe graphics mode" fails, try downloading the Alternate CD. Also, seems like you're installing Gutsy. Try downloading Hardy (8.04) because it provides better support for newer graphics cards. Just a thought, is this a desktop or a laptop? Please provide your hardware info so we can help you better.

---

### Post by clairegrrl on 2008-04-29
If I wanted to make a backup, wouldnt I want it to like a thumb drive rather than a partition on the same HD?  What if the HD crashes?

When I installed 7.1, i wiped the drive so there is only one big patrition.  Isnt that ok?

---

### Post by Victormd on 2008-04-29
> **clairegrrl said:**
> If I wanted to make a backup, wouldnt I want it to like a thumb drive rather than a partition on the same HD?  What if the HD crashes?

When I installed 7.1, i wiped the drive so there is only one big patrition.  Isnt that ok?

I think what boyohazard means is that if you have "home" in a separate partition, then it's easier to backup because you can simply copy that partition (to a DVD or something)and it will backup everything (including program settings/desktop settings/etc). This has its pros and cons. The best way that I've found is to simply be "organized" so you know what you want to back up and just copy it to a flash drive/external HD/CD/DVD.

Also, it might be a good idea to have a separate partition (even if you don't move "home" to it) to keep all your important stuff because if you need to format/re-install your OS (because of a crash or something), you still keep all your personal files intact and don't have to worry about doing a last minute backup risking losing important files.

---

### Post by kansasnoob on 2008-04-29
I started looking at Linux just out of curiosity. There'd been a lot of publicity regarding gOS 1.0.1, and I was also curious about Freespire having tried Lindows many years ago.

After a bit of research I just ordered my first CD's here:

[http://www.linuxcdshop.com/](http://www.linuxcdshop.com/)

It took about one week to receive them and get started. In the mean while I'd pulled out an old PII Micron puter, a bunch of spare parts, ordered a few goodies from ClubIT, especially a Via P2500E mobo w/a gb of Kingston Valueram.

The first problem I encountered was a bad CD Rom ........... in fact I went thru 3 old ones before I found a good one.

But that's been a couple of months ago and after playing the discovery game I settled on Ubuntu for my own computers (dual boots all), my daughter loves Kubuntu, and my oldest son prefers Xubuntu.

But, the odds that you'll "break it" at some point are almost inevitable, but each and every time you learn more and more ............. and you never have to worry about "activation" or any COLA BS.

Now I burn all my own ISO images because Ubuntu seems to love doing it!

But one disc I'd recommend for anyone ordering any flavor of Ubuntu is GParted (yes, it's in the Ubuntu live CD, but it's quicker and less "fiddly" to use the GParted CD). The SystemRescueCD is also an excellent addition to the old toolkit, but I'm still discovering all the great things it can do.

Freespire has a list of places you can order CD's for all flavors of Linux:

[http://wiki.freespire.org/index.php/Download_Freespire](http://wiki.freespire.org/index.php/Download_Freespire)

---

### Post by Boyohazard on 2008-04-29
> **Victormd said:**
> I think what boyohazard means is that if you have "home" in a separate partition, then it's easier to backup because you can simply copy that partition (to a DVD or something)and it will backup everything (including program settings/desktop settings/etc).

Yup that's what I was trying to say, thanks :)

If you did a standard installation you probably have two partitions already, one for the core files and one for swap.

There are certainly advantages to having more than one partition, making backups is just one. You can learn more here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by WorldTripping on 2008-04-29
> **nickyc said:**
> basically i get to the below screen (see link).

[http://www.futuredesktop.com/images/gutsy/picture_4a.jpg](http://www.futuredesktop.com/images/gutsy/picture_4a.jpg)

and then choose the Start or Install Option. 

Then the below screen comes on and within 5 seconds stalls!!

[http://img136.imageshack.us/img136/5552/boot3fa9.jpg](http://img136.imageshack.us/img136/5552/boot3fa9.jpg)


I got exactly the same on my old Toshiba laptop with an nVidia graphics card.

Using the alternate CD fixed it for me.

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Remember to tick the box just below the 'Download' button to get the alternate one.

It's a text based installer, and not a 'Live CD'.

But if you still want a disk posting pm me, and I can get one in the post tomorrow. Just say what version you want.

---

### Post by kansasnoob on 2008-04-29
Victormd said,

"Also, it might be a good idea to have a separate partition (even if you don't move "home" to it) to keep all your important stuff because if you need to format/re-install your OS (because of a crash or something), you still keep all your personal files intact and don't have to worry about doing a last minute backup risking losing important files."

That's an excellent suggestion! My primary computer now has a dual boot of 8.04 and Win XP with a third FAT32 partition so I share virtually any and all files between either OS, and I can copy any or all of the files to a pen drive and transfer them to even old windows puters that can't handle NTFS.

If I tear up either OS beyond practical repair I can easily toss in the GPArted CD and just wipe out that partition without disturbing any personal data or the other OS.

---

### Post by Victormd on 2008-04-29
> **kansasnoob said:**
> That's an excellent suggestion! My primary computer now has a dual boot of 8.04 and Win XP with a third FAT32 partition so I share virtually any and all files between either OS, and I can copy any or all of the files to a pen drive and transfer them to even old windows puters that can't handle NTFS.

Why do you use FAT32? Though NTFS is not as good as ext3, it's better/faster/safer than FAT32 and ubuntu will recognize it without any problems... just a thought...

---

### Post by clairegrrl on 2008-04-29
> **Victormd said:**
> I think what boyohazard means is that if you have "home" in a separate partition, then it's easier to backup because you can simply copy that partition (to a DVD or something)and it will backup everything (including program settings/desktop settings/etc). This has its pros and cons. The best way that I've found is to simply be "organized" so you know what you want to back up and just copy it to a flash drive/external HD/CD/DVD.

Also, it might be a good idea to have a separate partition (even if you don't move "home" to it) to keep all your important stuff because if you need to format/re-install your OS (because of a crash or something), you still keep all your personal files intact and don't have to worry about doing a last minute backup risking losing important files.


Thanks :(  You've now given me more hours of reading to figure out how to do all this.  Hehehe

---

### Post by Victormd on 2008-04-29
That's easy. Let me know if you need any help...
tip: download the gparted live CD and that will make your life a whole lot easier. Furthermore, don't worry about moving your home folder as this might cause you some headache (i.e., crashes)... simply create a separate partition to store your personal files...

---

### Post by kansasnoob on 2008-04-29
"Why do you use FAT32? Though NTFS is not as good as ext3, it's better/faster/safer than FAT32 and ubuntu will recognize it without any problems... just a thought..."

One of my dual boots is set up with an old win 98SE OS because it works perfectly with some old software that doesn't work well in Wine, and doesn't work at all in XP. FAT32 works with everything I have.

I expect to be able to ditch windows altogether within a year anyway.

---

### Post by VraiChevalier on 2008-04-29
I have had several instances when the Live CD would stall during an attempted install. I then tried the Alternate CD and was able to install with no problems. This was on older hardware. I believe the Alternate CD requires much less in system resources in order to install. Try the Alternate CD.

What are the specs of the system you are trying to install on?

---

