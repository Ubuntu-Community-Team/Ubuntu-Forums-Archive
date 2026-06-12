---
title: "Upgraded to Hardy and now more problems"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-04-27
OK, so I was trying to fix a blunder that I made with my video driver and was being helped by a couple people but didn't fully understand.  One recommendation was to upgrade 7.10 to 8.04.  I thought this would resolve my problem so I did it.  When the upgrade was finished it restarted itself and the screen was showing something  like the following:
[####:######]ata2.00: exception Emask0X0 SAct 0X0 serr 0X0 action 0X2 frozen
[####:######]ata2.00:cmd a 0/00:00:24:00/00:00:00:00:00/a0 tag 0 plo 36in
[####:######]ata2.00: status:{DRDY}

please note the [####:######] is represent of real #'s counting up, the first set of 4 is moving slower than the second set of 6.  It just keeps doing it.  After watching this for half an hour I figured something was wrong so I powered down and powered back up.  It did it again.  Then I powered back down and when restarted I noticed that I had choices:

Ubuntu 8.04 Kernel 2.6.24-16-generic
Ubuntu 8.04 Kernel 2.6.24-16-generic(safe mode) 
Ubuntu 8.04 Kernel 2.6.22-14-generic
Ubuntu 8.04 Kernel 2.6.22-14-generic(safe mode)

Windows XP 

Yes I have a partition.  I then tried to start in the 2.6.22-14 generic
It does start, but with the same graphics problem I had with 7.10.  It also started a crash launch pad.  So I tried to register to see if they would email me an answer.  This did nothing and I didn't get an email they said for me to send error report.  

I think I need help with everything.  If you send me code should I type it in terminal or someplace else?  Could someone log into my computer and help me out?  I am excellent in M$ windows but looking forward to forgetting it.

PLEASE HELP!!!!!!!!

---

### Post by drrwhistle3 on 2008-04-28
PLease Help.  Sorry I had to push perhaps someone can help!?!

---

### Post by comsparks on 2008-04-28
I know this might not help you at the present but I had problems in the past with dual booting various Linux distributions with Windows XP. What I did was buy another computer (cheap one) and a KVM switch. I then began loading various Linux distros on it to test. The other computer had Windows XP which I reformated and put XP back on. Using the KVM switch I could switch back and forth between computers using only one keyboard, mouse and monitor. This way I have Linux on one computer and Windows XP on the other never the two shall meet. If an error or problem occurs you don't have to worry about it effecting the hard drive where other OS' are residing. This way you can experiment with other Linux distros until you find the right one you like and still keep Windows XP seperate to use until you feel confident to drop it all together.

---

### Post by drrwhistle3 on 2008-04-28
I really want to drop XP! But I can't until I resolve the issue or my wife will kill me.  Does anyone have any options?  I will let you log into my computer if possible and needed.

---

### Post by billgoldberg on 2008-04-28
The guy gave the wrong advice.

Just do a clean install (install ubuntu from cd, back up data)  and everything will be fine. Doing a clean install will take 20-30 min.

---

### Post by alienexplorers on 2008-04-28
Exactally what graphic card are you running and what graphic driver are you using?  Sounds like a miss match between the video card and the graphic driver.

Why not just install Hardy 8.04 from scratch and see if you still have the problem.

---

### Post by Zralou on 2008-04-28
As to the muliple instances of kernel entries, that is because grub adds a new kernel to the list without removing the old one.

I would suggest the same as the previous post and do a full re-install, upgrades (based on the threads on the forum) seem to be troublesome.

Sara Lou

---

### Post by kolisikepu on 2008-04-28
> **drrwhistle3 said:**
> I really want to drop XP! But I can't until I resolve the issue or my wife will kill me.  Does anyone have any options?  I will let you log into my computer if possible and needed.
LOL @ Wife killing this bloke.

I know what you're feeling.  I had installed Ubuntu with XP in a VM, but she didn't like that either.  I'm still dual booting with XP and Ubuntu.

Oh yeah... my 6yr old son has a Laptop running Vista and Ubuntu, but she won't use that either, LOL.

For your problem, fresh install and use Envy to install your drivers, but I don't remember you mentioning your Video card though... that would help.

---

### Post by drrwhistle3 on 2008-04-28
The screen resolution is 800x600 and is now using vesa - generic.
The video card is as follows:
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
Someone suggewsted that I use The Linux driver that is in hardy or the i810.  I tried both but is defaulting to the vesa - generic in what I call safe mode.  
I think part of the problem is that I am not sure how to do it or if code needs to be put in how do I do that.  Once someone explains it I will never forget.  
Anyway, in 7.10 there was something called display settings (or something like that so that is were I tried to change it.  I would restart and it would go back to vesa- generic.  
On the lighter side my 6 year old like Ubuntu better than windows xp and thinks my wife is being a baby.  He has to show her how to do things.  I am sarting to believe that he should show me too.

---

### Post by drrwhistle3 on 2008-04-28
Another question:  Can I reinstall Hardy 8.04 by just inserting the disk I downloaded with a torrent into the drive while working in Ubuntu or do I have to boot it from the disk and how do I do that?

---

### Post by Zaneyard on 2008-04-28
If I were you, I would boot into the live cd, remove the partitions with ubuntu on it, and just click install.
First backup all of your important data of course.
I, too, have upgraded to Hardy and everything was fubar.
After deciding I was bored enough, a fresh install made everything good.
The fact that XP is on the same hard drive as your Linux install doesn't mean crap. The only conflicts there might be that you have to work with GRUB.

---

### Post by Zaneyard on 2008-04-28
> **drrwhistle3 said:**
> Another question:  Can I reinstall Hardy 8.04 by just inserting the disk I downloaded with a torrent into the drive while working in Ubuntu or do I have to boot it from the disk and how do I do that?

You need to boot into the CD
Restart your computer with the disk in. Most likely it will do it automatically, if you see the GRUB screen you are too far. If you do see GRUB, go into your BIOS settings and allow boot from a CD. Or depending on your specific BIOS, hit F12 or something like that (you should see labeled, 'boot selection, or the like'  on the screen as soon as you turn on your computer) and select CD Drive from the list.

---

### Post by drrwhistle3 on 2008-04-28
How do I remove the partition with Ubuntu on it?
Oh yeah, and what is GRUB?

---

### Post by Zralou on 2008-04-28
Grub is the boot manager that pops up with the option to select Ubuntu or Windows.

Sara Lou

---

### Post by drrwhistle3 on 2008-04-28
> **Zaneyard said:**
> You need to boot into the CD
Restart your computer with the disk in. Most likely it will do it automatically, if you see the GRUB screen you are too far. If you do see GRUB, go into your BIOS settings and allow boot from a CD. Or depending on your specific BIOS, hit F12 or something like that (you should see labeled, 'boot selection, or the like'  on the screen as soon as you turn on your computer) and select CD Drive from the list.

Ok I tried this. I first downloaded 8.04 hardy from the Ubuntu site.  Extract it in Windows xp with power ISO. Then burn 1 bootable disk in nero and 1 with just the files copied.  Brought them both home from work and set my computer's bios to start from CD.  The bootable disk started up DOS and stopped there and froze.  The non bootable disk just said not recognised.  

Is there a way to format the Ubuntu partition and leave windows xp alone then reinsatll the Ubuntu on the formmatted area?  I really have nothing to lose in my Ubuntu side because all important files are on external.  If this is possible is there a way to repartition so my Ubuntu side is larger?

Desperatly waiting instructions!!!!

---

### Post by Zaneyard on 2008-04-29
> **drrwhistle3 said:**
> Ok I tried this. I first downloaded 8.04 hardy from the Ubuntu site.  Extract it in Windows xp with power ISO. Then burn 1 bootable disk in nero and 1 with just the files copied.  Brought them both home from work and set my computer's bios to start from CD.  The bootable disk started up DOS and stopped there and froze.  The non bootable disk just said not recognised.  

Is there a way to format the Ubuntu partition and leave windows xp alone then reinsatll the Ubuntu on the formmatted area?  I really have nothing to lose in my Ubuntu side because all important files are on external.  If this is possible is there a way to repartition so my Ubuntu side is larger?

Desperatly waiting instructions!!!!

I'm not sure if burning it like that will work well.
I would recommend using burnatonce from [http://www.burnatonce.net]("http://www.burnatonce.net")
what you would do is just load the ISO file and burn it.
Someone correct me if the end result is the exact same but this is my tried and true method.

Yes you can use gparted to resize your partitions
Yes, when working with partitions generally you don't hurt your Windows partition, 'less you delete it.
Just remember to never delete a FAT32 or NTFS labeled partition.
if you wanted your ubuntu partition to be larger you would have to shrink other partitions on your Hard Disk such as your windows partition

Try burning the iso to the disk using burnatonce and post your "boot results" here. you should be able to browse the web using the live CD.

---

### Post by Zaneyard on 2008-04-29
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

This guide is probably what you wanna look at once you can get into the live cd. Just make sure you don't use "guided: use the entire hard drive" when you get that far in the install

---

### Post by victor.zamanian on 2008-04-29
> **drrwhistle3 said:**
> I had choices:

Ubuntu 8.04 Kernel 2.6.24-16-generic
Ubuntu 8.04 Kernel 2.6.24-16-generic(safe mode) 
Ubuntu 8.04 Kernel 2.6.22-14-generic
Ubuntu 8.04 Kernel 2.6.22-14-generic(safe mode)

Windows XP 

Yes I have a partition.  I then tried to start in the 2.6.22-14 generic
It does start, but with the same graphics problem I had with 7.10.

Well, what happens if you start Ubuntu 8.04 Kernel 2.6.24-16-generic?
If that works, you can use the Synaptic Package Manager to remove the older kernel versions (using the search function).

Good luck!

---

