---
title: "[SOLVED] Really Need Help Installing o.0"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by toasterr on 2008-07-22
I was recently asked by my cousin to help fix his laptop, its an acer with decent hardware
the problem with it is that his little sister got on it and a virus ate Windows Vista to shreds 

either way to make a long story short his computer is basically locked out, i managed to get to a recovery utility page but nothing there is of any use since the virus broke system restore and my cousin made no back up discs

i figured a possibly solution to fix this would be to get rid of vista and install a different operating system (i.e. linux) 
i downloaded it from this site to an SD card but it wont read the card, then i put it on a dvd and tried thats but when i put it in nothing happens,
i just wanna know what i need to do to get rid of vista and put ubuntu on 
-------------------------------------------------------------

also i have an older laptop (very old, like 128mb Ram intel celeron, a weird version of windows 95 made to run a nerve conduction test and apparently nothing else)
and i dont even know if ubuntu would work on it but if you think it would tell me
( i have no idea how to get it on there because it cant read dvds and isnt compatible with my thumb-drive

---

### Post by WRDN on 2008-07-22
Boot the laptop, and when prompted, enter a specific key (it may be Del) to enter the BIOS. In the BIOS, find the relevant page with the option to change the order of the boot devices. Set the first boot device as the CD/ DVD Drive, and the second as the HDD (not mandatory). Now, reboot and it should boot from the CD/DVD.
If you want to completely remove Vista, during the installation process for Ubuntu, just select to "Use entire Drive" and it will format it, automatically create the partitions, and leave you with only Ubuntu. On the LiveCD, you can also use GParted to resize, delete or create new partitions. I would recommend creating 3 partitions during the installation (Manual partitioning):

- 1 for root (/)
- 1 swap
- 1 home (/home)

This way, it is possible to reinstall Ubuntu, while saving your settings/ files.

As for your other question, Ubuntu may work, but it would be slow. You could use [Xubuntu]("http://www.xubuntu.org/") or [Puppy Linux]("http://www.puppylinux.org/") though (among others).

---

### Post by toasterr on 2008-07-22
i tried this and it skipped the dvd like it wasnt even there

---

### Post by Thingymebob on 2008-07-22
did your burn the iso image to dvd or just copy the iso to the dvd?

---

### Post by toasterr on 2008-07-22
i copied it

---

### Post by Sneaky07 on 2008-07-22
Are you sure you burned the ISO right?  How did you burn/create the DVD?

---

### Post by avtolle on 2008-07-22
> **toasterr said:**
> i copied it
It needs to be burned as an image, not copied. If you need assistance, post back and someone will give you a link.

EDIT: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) may help you.

---

### Post by Troll_the_Great on 2008-07-22
First, how did you put it on a DVD?You just copied the file.ISO on the DVD?And why did you use a DVD, the file is around 700 MB so you could put it on a CD.You should burn the image to disc, not just copy it.Nero is a popular Windows CD creator.Use the option "burn image to disc".
Also, you have to configure your computer to boot from a CD.When you boot, hit F2 (or Delete, is different for different systems, but you should have a key that says "Enter setup").In there configure your computer to boot from a CD and install Ubuntu.
As for your second question, I would recommend PuppyLinux, or Damn Small Linux rather then any Ubuntu version.
Tell me if you need further assistance.
Cheers!

---

### Post by echo314 on 2008-07-22
ImgBurn is a decent program, you can google that and download it, free to use.

---

### Post by WRDN on 2008-07-22
> **avtolle said:**
> It needs to be burned as an image, not copied. If you need assistance, post back and someone will give you a link.

EDIT: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) may help you.

After reading the original post, burning the iso on the mentioned computer may be easier said than done, as he can't access Vista currently.
So, find a working PC, and if it is running Windows, I would recommend using [DeepBurner]("http://www.deepburner.com/index.php?r=products&pr=deepburner&prr=features") (free) to burn the iso.

---

### Post by cpetercarter on 2008-07-22
Have a look at [https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation"). It contains or links to complete instructions about how to make the ISO and check it for integrity and how to boot into Ubuntu from it. 

You may not be aware that you can boot into Ubuntu from the CD without installing Ubuntu onto your hard disc. It is always worth doing this, and taking plenty of time to play around with Ubuntu before commiting to a permanent install on the hard disc. In particular, check that printers, cameras etc work.

For your old computer, I suggest Xubuntu, which is designed for machines with limited memory resources.

---

### Post by Victormd on 2008-07-22
> **toasterr said:**
> also i have an older laptop (very old, like 128mb Ram intel celeron, a weird version of windows 95 made to run a nerve conduction test and apparently nothing else)
and i dont even know if ubuntu would work on it but if you think it would tell me
( i have no idea how to get it on there because it cant read dvds and isnt compatible with my thumb-drive

You can get another version (i.e., Xubuntu) to run on it, no problem but you'll need to use the Alternative CD, not the Live CD. Also, use CDs, not DVDs... more compatible and cheaper... :)

---

### Post by toasterr on 2008-07-22
well atm im on my beast laptop, i have access to a burner

---

### Post by toasterr on 2008-07-22
also i tried putting it on a standard cd but i had to format it and afterwards i only had like 560mb free, it kept doing this to all my disks >.<

---

### Post by WRDN on 2008-07-22
> **toasterr said:**
> also i tried putting it on a standard cd but i had to format it and afterwards i only had like 560mb free, it kept doing this to all my disks >.<

How did you format a CD? (As far as I know, its not possible and you wouldn't lose that much space if you did manage to format it anyway)
Also, what are you referring to when you say "it kept doing this"?

---

### Post by Troll_the_Great on 2008-07-22
> **toasterr said:**
> well atm im on my beast laptop, i have access to a burner

So burn the image to disk, see previous posts if you don't know how to do it, and try Ubuntu.Is best to use the Live CD first, and if you like it go for a full installation.Just keep in mind that the computer will be much slower when booting from the live CD.

EDIT: Lol, how in the world did you format a CD?! What burner did you use?

---

### Post by toasterr on 2008-07-22
seriously i dont know, i put the CD in and it told me that it had to be formatted, i took that disc out and put a different one it and it did the same thing

---

### Post by WRDN on 2008-07-22
> **toasterr said:**
> seriously i dont know, i put the CD in and it told me that it had to be formatted, i took that disc out and put a different one it and it did the same thing

Were you forced to format it? If not, click Cancel if available, or close the Window that appears. Then open a burner such as Deep Burner, and try burning the ISO. The PC should NEVER prompt you to format a CD.

---

### Post by Troll_the_Great on 2008-07-22
> **toasterr said:**
> seriously i dont know, i put the CD in and it told me that it had to be formatted, i took that disc out and put a different one it and it did the same thing
What program did you use?Try Nero 6, is old but in my opinion is the best and easiest to use of all.

---

### Post by toasterr on 2008-07-22
it wasnt a program that was formatting my CDs it was windows, all i did was flag+ E to open windows explorer and see that it has read that a blank cd was inserted and windows prompted me to format it and it only left me with roughly 560mb of space

but i think ive gotten it to work, i have a program called roxio on here and i think its doing the job, i could be wrong though

---

### Post by toasterr on 2008-07-22
i got it to work, although whatever error or virus that ate up vista made the C:\ drive unacessable

---

