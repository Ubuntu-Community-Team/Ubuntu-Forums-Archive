---
title: "[SOLVED] first time installer coming from xp"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-13
hello,

i am going to install ubuntu for the first time. i currently have two partitions on my laptop hard drive, they are the c and d drives. The D drive is 9.52 gigs and the c drive is 64.9 gigs. I have a Dell XPS M1210 with the T7600 2.33ghz and 4 gigs of ram. 3.25GB of ram is available, i think the rest is used by my GeForce Go 7400 Nvidia card.

I plan to install it from the install file and not by burning it to a cd. I noticed that ubuntu asked me with drive i want to install the OS to, but it also asked me how large ubuntu should be? IT gave me larger options for the 65gig drive than it did for the 10gig drive. Can anyone offer any help here? Thank you.

p.s. Will ubuntu work with my GeForce Go 7400 Nvidia card? 

thank you.

---

### Post by Elfy on 2008-10-13
> I plan to install it from the install file and not by burning it to a cd. I noticed that ubuntu asked me with drive i want to install the OS to, but it also asked me how large ubuntu should be? IT gave me larger options for the 65gig drive than it did for the 10gig drive. Can anyone offer any help here? Thank you.

It will give a bigger size for the 65Gb drive as there is more room for it to fit into. It has to make a virtual drive to install onto if you are installing inside windows - from the file and not a disc.

There is a wiki for what you are doing, there is also a specfic forum for it - you're installing wubi

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

Yes your video should work ok, but I'm not completely sure about wubi.

---

### Post by Orange_and_Green on 2008-10-13
Hi :) Welcome to the forums and to the Ubuntu world :)

> **GumpTron said:**
> I plan to install it from the install file and not by burning it to a cd.

I presume you mean you want to install from within Windows by using Wubi...

Since you already have two partitions, I would however suggest you move the data from D to C (if you have any) and use the Ubuntu CD to install ubuntu on a partition of its own as it's much cleaner and more error-proof that way. The CD is also great because you can boot from it without installing anything to test Ubuntu live (mind you, it will run a bit slower than when it's installed because it runs entirely from RAM in live mode).

Have fun with Ubuntu!

---

### Post by howefield on 2008-10-13
I know you don't want to burn a cd, but the benefit would be in booting up the Live CD, and making sure everything works before you commit.

I don't think your graphics card is responsible for using your ram, I believe that card comes with 64meg but can also use 192 of system memory for a total of 256. Sounds more like you have 4 gig of memory and running a 32 bit operating system which can only see approx 3.2 gig of your 4 gig.

---

### Post by GumpTron on 2008-10-13
I have a 700mb blank cd, is that all i need to burn it to, just one cd?

If you guys say its best to burn to cd i will do it then, where can i learn how to burn it to the cd and install it from the cd.

thank you all very much.

ps. does this mean i can install ubuntu to my 10gig drive and still use windows xp on my c drive? that would be great. I assume i would be asked to boot from either drive on start up?

---

### Post by alwez_loner_TZ on 2008-10-13
I think you should allocate more space for Ubuntu like 20GB to 30GB, they advice you on the minimum required.

The you install Ubuntu on the Live CD, where you can boot easily form the CD. Create the partitions and install, then enjoy ubuntu.

---

### Post by Orange_and_Green on 2008-10-13
Dear GumpTron,

you can download the CD image from here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and burn it with your favourite burning utility in Windows (if you don't have one, I recommend [deepburner]("http://www.deepburner.com"), it's powerful and free :))

Next, reboot your PC and choose to boot from CD (you will have to hit a key to enter Boot Menu or BIOS setup and change the boot config. Which key it is, well that depends on your BIOS. Usually it is one among F2, esc, del etc, in any case it's written on the very first screen you get after switching on the computer.)

When you boot from the CD, you can choose to "Try Ubuntu without any change to your computer" (that's what is called "live mode"). Try that one first, so you can see if it runs well and all devices get detected.

If you feel comfortable with Ubuntu and want to give it a serious try, click on the "Install" icon. It will ask you a few questions, and then (4th step) ask you how you want to partition your disk.

Before you go on, make sure all the data on the D drive is backed up, or moved to C in Windows. Next, select "manual partitioning" and:
1) select the 10 GB partition and erase it (this will destroy all data, hence the need to back up or move the files);
2)in the empty space, create:
  2.1) a partition about 4-5 GB, file system "ext3", mount point "/". This is the minimum requirement and is plenty enough I think, because you can see your windows driver from Ubuntu and use the space from it, I'll show you how (that's what I've dd with my wife's PC, for instance).
  2.2) a partition about 1GB, file system "swap"
  2.3) a partition with the remaining space, file system "ext3", mount point "/home". /home is where all your personal documents and settings are, so having it on a separate space is very handy, because even if you reinstall the "core" OS (the root), all your settings are preserved.
3) Highlight the first, 65GB disk, click "edit", use it as "ntfs" and specify a mount point the likes of /media/Windows.
4) Hit continue and proceed with the install.

Once install has completed, reboot. You will enter your freshly-baked Ubuntu system (be sure to update it soon) and on the desktop you will have an icon with your old C partition, read-write. You can even set up your Desktop/Documents/Music etc. folders to point to the old ones from your windows account, import browser settings, import mail, etc. Be sure to ask more help if you are interested in any of these topics.

Have lots and lots of fun,

---

### Post by GumpTron on 2008-10-13
i have downloaded the file and I have a rar folder. Should I unzip it and burn that folder to a cd or should i burn the unzipped folder to cd? 

thanks

---

### Post by alwez_loner_TZ on 2008-10-13
Hey check out this thread maybe you would know how to manage you 10GB 
*[http://ubuntuforums.org/archive/index.php/t-360151.html*](http://ubuntuforums.org/archive/index.php/t-360151.html*)

---

### Post by hyper_ch on 2008-10-13
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by Orange_and_Green on 2008-10-13
> **GumpTron said:**
> i have downloaded the file and I have a rar folder. Should I unzip it and burn that folder to a cd or should i burn the unzipped folder to cd?thanks

You should actually have an .iso file (possibly, you have an association for iso files to be opened with winrar). iso files are CD image files, so open that file with your CD burning program and it will know what to do with it :). I suggest you burn it at the slowest speed possible so as to make sure you don't get write errors.

Have fun :KS

---

### Post by howefield on 2008-10-13
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

I beg to differ, the OP has given enough of a clue as to the content of the question about to be asked, there is enough in the title for you to decide whether you can help or not, although that opinion is always subjective.

This isn't a "noob here" or "need help" title and consistently berating new users with a cut and paste admonishment doesn't help too much. Just my 2 pennies worth. 

Gumptron, what is the name of your download, I expected an iso file :)

---

### Post by Elfy on 2008-10-13
> **GumpTron said:**
> i have downloaded the file and I have a rar folder. Should I unzip it and burn that folder to a cd or should i burn the unzipped folder to cd? 

thanks

No - you must burn it as an iso or image - details [here]("https://help.ubuntu.com/community/BurningIsoHowto") 

Make sure to check the md5sum before you burn it - details on the same page

Psychocats is a good resource for how to go about it [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

One thing that could be of importance to you concerns the size of your swap - if you intend to use hibernate then your swap must equal or be greater than your RAM, otherwise you will be fine with a small swap of ~512MB or even less.

---

### Post by stephanvaningen on 2008-10-13
If you don't know how to write an .iso to a CD you can always just ask on the website to send you a CD. Choose Ubuntu Desktop 32-bit - I would guess that since it's now 2 to 3 weeks before the next release that sending a CD would go rather quick at this point: a lot of people will only start requesting a CD for the new Intrepid-version.
--
On the other hand, if you really want to burn .now. you can use a free iso-burning program like [http://cdburnerxp.se](http://cdburnerxp.se)

---

