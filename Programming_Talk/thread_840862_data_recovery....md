---
title: "data recovery..."
date: 2008-06-25
forum: Programming Talk
---

### Post by hockey97 on 2008-06-25
hi, I was on my windows os while windows prompted me that 2 hard drives are not formatted so it formatted it.  Is their a way where I can recover that data.

I have been told that even if you delete the data it's not really deleted until it gets rewritten.

is their a program that could recover the files that are missing???

---

### Post by LaRoza on 2008-06-25
testdisk. See the link in my sig.

(It is on the gparted live cd)

---

### Post by hockey97 on 2008-06-25
ok, so I will be able to recover my data back right??

it looks like my windows os reformatted my ubuntu drive but the drive is where the home file is.

I downloaded that program before coming back becuse I done a google search and found a post of a guy that by mistake reformatted his windows drive.

now I ran the software and looks like it's not finding anything.

is their any instructions on how I can find the lost files and recover it?

---

### Post by hockey97 on 2008-06-25
ok I ran testdisk and guess what?? now my windowsxp is now change to linux file system, when I boot now I get like 1,000 words saying grub.

What should I do next??

is testdesk bootable from cd??

I am in a big mess. I have website files that I worked on for 1 year and was close to finishing.

---

### Post by LaRoza on 2008-06-25
> **hockey97 said:**
> ok I ran testdisk and guess what?? now my windowsxp is now change to linux file system, when I boot now I get like 1,000 words saying grub.

What should I do next??

is testdesk bootable from cd??

I am in a big mess. I have website files that I worked on for 1 year and was close to finishing.

I am not up on your situation. I am not sure what you did.

Data recovery is a meticulous activity which requires a lot of preparation and careful control (ideally, starting with a write protector and a byte copier).

I am not an expert in this area (although I have great success in data recovery, even when "experts" failed), so I can't give advise on this without offering it with a grain of salt.

I too am a web developer, and I have backups of all sites (including my wiki, which is a remote service). If you don't have backups, I am sure you will in the future.

Could you explain what you did better? I had originally recommended running testdisk from a live disk (and didn't think you'd use it otherwise) when I said Gparted had it.

---

### Post by Wybiral on 2008-06-25
I've never had any luck recovering data, which is why I've learned to upload everything I write somewhere on the internet. Think of it as a lesson, from now on you will be very careful to make sure your code exists somewhere safe (especially after bursts of hard work).

---

### Post by CptPicard on 2008-06-26
Reminds me of when my laptop's hard drive failed with my Master's Thesis on it. I had to shake the laptop to make the drive read while scp was copying the data over the net through all the kernel DMA failure messages... :) (I succeeded though)

---

### Post by hockey97 on 2008-06-26
ok let me fill you guys in.

first I will tell you how my hard drives are setup.

ok I have windows xp and ubuntu os a dual boot. 

I have a 300gb hard drive and a 80gb hard drive.

the 300gb had xp on it and the 80gb had ubunutu on it at a dual boot.

the 300gb was slip 120gb for windowsxp becuse windows didn't let me install the whole 300gb so I could only make a 120gb part. So the rest of the freespace I made it as a second partician for ubuntu this is where the home folder was and also had my websites and some programs.

Well today I was on my windows xp os and a window pops up and says drive  R: is not formatted, then it had a progressbar showing on this window and then another popup message said the  R: DRIVE Has been reformated. the H: drive was where ubuntu was installed the R drive is where the home folder was this was the hard drive that had a windows xp partician.

so I check the drive and saw it in a ntfs partician.
So got on here, and then downloaded testdrive and ran it, it showed a cruppeted file system , which was that partician that had that home folder in ubuntu it's the one with my website files ect.

well it showed it was in a ntfs filesystem, so I saw the options which had T meaning type, which I typed that and selected that partician that was bad the home folder one and so I selected ext2 the linux filesystem thinking this will change back the partician. Now to me looks like it changed the whole hard drive to a linux file system and now when I boot I can't even get into windows when it boots after the bios does the on off test and checks all cd roms and floppydrives it then loads the words grub and it's like alot of them then at some point stops and then that's it.

I just now tried booting in dos which I did and so far no luck.

I am trying to use testdisk but how can I use it without having to use windows since right now it I can't get into any os.

any suggestions??

---

### Post by AmericanYellow on 2008-06-26
I don't see how the Windows partition could have been changed to Linux file system by itself, but your next best option would be to connect your hard drive to another computer running either Windows and Mac OS X and install a simpler recovery software that can scan and recover files from your hard drive. If you have time, I believe testdisk can reset the Window's partition to be recognized as NTFS but you'd have to read a manual or something to learn to do this properly because testdisk is quite complex. I haven't used test disk in a while but if I find or remember how to do this exactly, I will post it here.

Good luck.

I will post good and easy recovery software that you can use on Windows or MAC OS X.

---

### Post by pmasiar on 2008-06-26
> **LaRoza said:**
> If you don't have backups, I am sure you will in the future.

:lolflag:

---

### Post by nvteighen on 2008-06-26
> **cptpicard said:**
> reminds Me Of When My Laptop's Hard Drive Failed With My Master's Thesis On It. I Had To Shake The Laptop To Make The Drive Read While Scp Was Copying The Data Over The Net Through All The Kernel Dma Failure Messages... :) (i Succeeded Though)

:cool:

---

### Post by CptPicard on 2008-06-26
> **nvteighen said:**
> :cool:

Seriously that was my life's "oh ****" moment... and to think that I was a CS student. I must really have hated my thesis to not have backups.. ;)

---

### Post by hockey97 on 2008-06-26
ok thanks.

I plan to buy an external hard drive to store backups.

I never made backups before becuse it would cost to store it.

so far I able able to boot up in dos and run testdisk

so far it finds an ntfs partician. but On that 300gb drive I had 2 particians one for windows xp and the other for ubuntu for my websites ect. The ubuntu partician on that hard drive got reformatted to ntfs.
So I ran testdisk on windows to try and recover it, it then I selected that partician to get recovered and then it ask to restart which I done so then at boot up it would then only boot the words Grub like about 1,000 of them and then it just hangs.

I ran testdisk right now and shows only one ntfs partician.

I don't want to use testdisk on my other computer which is what I am using to make this post, the reason I can't afford to screw up this computer since I have online college classes and this is the only computer that I use when my main computer gets messed up.

---

### Post by LaRoza on 2008-06-26
> **hockey97 said:**
> I ran testdisk right now and shows only one ntfs partician.

I don't want to use testdisk on my other computer which is what I am using to make this post, the reason I can't afford to screw up this computer since I have online college classes and this is the only computer that I use when my main computer gets messed up.

My recommendation to look into testdisk wasn't an invintation to run it without carefully considering what it does...

Data recovery is a specialty and often very difficult. Ideally, you would have made a byte copy of the original disk.

---

### Post by hockey97 on 2008-06-26
[IMG]http://img167.imageshack.us/img167/9617/helpky3.png[/IMG]

ok this image shows the file system map selection.

I used the gpt one to recover the that one partician which now when I boot I get the word grub 1,000 times and then stalls/sits their.

the I tried the intel one and I can only find 1 partician.

---

### Post by LaRoza on 2008-06-26
> **hockey97 said:**
> 
the I tried the intel one and I can only find 1 partician.

You are running this on mounted disks!

From what I see, whatever you have lost is gone for all purposes and recovery attempts will be futile.

---

### Post by hockey97 on 2008-06-26
well now I am able to boot in windows xp but at the end of where it shows the windows loading at the end it says can't find autock then a blue screen pops up and then the computer restarts.

I have the windows xp cd is it possible I just just install missing system files??

---

### Post by hockey97 on 2008-06-27
ok I looked on the internet. I found this [drive-repair-mechanic]("http://www.sharewareconnection.com/drive-repair-mechanic.htm") Do you think that should work???

for right now I just want to be able to get in my windows part.

---

### Post by hockey97 on 2008-06-27
ok, my partician of windows is ok, the problem, when I try booting in windows, the windows xo loading comes up but at the end it fails saying can't find auto somthing

do you think I can repair this with windows xo cd??

does anyone got any more ideas what I could try??

I know from my eletronic class that the files are still on the hard drive even when you reformat the drive. when you reformat the drive it does nothing but take the files and put them in the front most sectors to get overwritten so this is where my ubuntu partician is at.

---

### Post by hockey97 on 2008-06-28
ok, I talked to someone, they said that All I need is a ubuntu installer cd, this will install the grub load, since I am using a dual boot, i need it to be ubuntu becuse the ubuntu would hold the master boot record.

They suggested me to download and burn to a cd and run the ubuntu installer which will detect a wrong master boot record. and then will install teh grub boot master loader.

Do you guys think this may work??
 Should I try this??

---

### Post by LaRoza on 2008-06-28
> **hockey97 said:**
> ok, I talked to someone, they said that All I need is a ubuntu installer cd, this will install the grub load, since I am using a dual boot, i need it to be ubuntu becuse the ubuntu would hold the master boot record.

They suggested me to download and burn to a cd and run the ubuntu installer which will detect a wrong master boot record. and then will install teh grub boot master loader.

Do you guys think this may work??
 Should I try this??

If that will solve it, then I think you haven't described the problem very well to us. If that won't solve it, you didn't describe the problem well to whoever gave that advise.

Installing grub is easy, I actually did it recently when I was reconfiguring my partitions. However, all partitions need to be intact.

If your Windows and Ubuntu partitions are intact, it will fix the MBR (get the Super Grub Disk in case you want the pure Windows bootloader)

---

### Post by hockey97 on 2008-06-28
ok, I havent tried it yet, because I think I have version 7.10 ubuntu.

would that matter?

I think this is the problem, becuse when I reboot my computer right after I used testdisk program I had the words Grub like 1,000 of them and it then sits their .

the first problem was that xp reformatted my s2nd partician, I have 2 hard drives one has 300gb and the other is 80gb the 80 gb has ubuntu on it which has the root stuff all the guts of the os is on that.

on the 300gb xp only allowed me to use 125gb for a partician, so 125gb partician is windows xp and the rest is a second extended partician for ubuntu, this is where then home folder stores the files, which is where my website is at.On xp I had a program that would read the ubuntu filesystem, so xp promted me saying an unknown filesystem was detected which has a loading bar in the window, and then another window poped up saying drive R: was reformatted to ntfs filesystem, this is the drive where that home folder is for ubuntu, the 2nd exteneded partician which was on the 300gb hard drive.

So I tried testdisk program to try and recover that ubuntu extened partician becuse it was now empty and is now a ntfs filesystem, so after I ran testdisk it said to reboot in order to see the new settings to take effect. So I rebooted my computer then after checking the cd-rom and floppy drive for a boot it usally then starts the window where you select either windows xp or ubuntu, but when I rebooted and got to that point I got only words saying grub repeatly until 1,000 grubs where on my screen it then stopped and stat at 1,000 grub words.

Do you think this might work??

---

### Post by LaRoza on 2008-06-28
> **hockey97 said:**
> ok, I havent tried it yet, because I think I have version 7.10 ubuntu.

would that matter?

No, but that isn't the problem.

> 
I think this is the problem, becuse when I reboot my computer right after I used testdisk program I had the words Grub like 1,000 of them and it then sits their .

Do you think this might work??

"used testdisk" really isn't that descriptive. testdisk does a lot of things, and it is supposed to be used on a byte copy, not the original.

---

### Post by hockey97 on 2008-06-28
ok, well I used the grub thing, and now I am able to get that screen where it shows all my partitions.

when I tried my windows xp to load windows xp, I get an error.

I then tried my ubuntu and it loads but after I type in my username and password it has errors saying can't find home folder would you like to use root as your home folder, if I say no it then takes me back to the login screen and if I say yes it would then take me back to the login screen.
I used the testdisk, by selecting the Intel/PC partition menu it scanned for partitions, and only found one partition the windows xp one ntfs. so I then restarted testdisk and used the gtp one (look on page 2 of this thread for the menu I am talking about,it's the second selection from the top of the menu.) I used that and found one windows xp ntfs and the others were ex3 meaning Linux this was what was found on the hard drive GB so I selected the ext3 and changed type to ex3 and then write the filesystem on that and after it done so it asked to reboot in order to see the changes to take effect, when I done so, after the computer checked the floopy drive and cd-drive for bootable stuff it then booted the words grub on my screen their were 1,000 grub printed on my screen and it then stops their until I turn off my computer and turn it back on which would do it again, so I was not able to boot into windows xp.

---

### Post by hockey97 on 2008-06-28
Ok now I am able to see the windows xp booting screen but failed to load windows xp, I googled the problem of autodiskcheck not found when booting windows xp, I found websites that said that the windows xp partician is not active this is due to having a dual boot system which I have, so I have to use fdisk to make the partician active so far I am trying to google around on just how to go abouts doing that.

how can I set a partician active??

---

### Post by LaRoza on 2008-06-28
> **hockey97 said:**
> Ok now I am able to see the windows xp booting screen but failed to load windows xp, I googled the problem of autodiskcheck not found when booting windows xp, I found websites that said that the windows xp partician is not active this is due to having a dual boot system which I have, so I have to use fdisk to make the partician active so far I am trying to google around on just how to go abouts doing that.

how can I set a partician active??

You can use GParted to mark a partition as active, but I think you are just making things worse...

---

### Post by hockey97 on 2008-06-28
would I need to have it on a live cd?? how would I use it? I downloaded the live cd from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

would this boot by itself??

---

### Post by LaRoza on 2008-06-28
> **hockey97 said:**
> would I need to have it on a live cd?? how would I use it? I downloaded the live cd from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

would this boot by itself??

It is on the Ubuntu live disk, and it is on that live disk.

---

### Post by CptPicard on 2008-06-28
Look... from what I can gather from your confused explanations, the boot sector issues are your smallest problem here, and messing with GRUB is totally pointless and risks destroying even more of the data that may be there... although it doesn't look good, you have essentially formatted a partition from some Linux format to NTFS already, which is bad.

Now, what you *can* try is first of all *do nothing to the partition that you formatted*. Don't mount it etc. Best thing to do would be to transfer the whole drive to another computer and then take a byte by byte copy of the hard drive device using something like dd (see "man dd"). Then, run whatever salvage software you may have handy on that file.

Most probably there is nothing you can do though, I would just learn to live with the fact that the data is gone.

---

### Post by LaRoza on 2008-06-28
> **CptPicard said:**
> 
Now, what you *can* try is first of all *do nothing to the partition that you formatted*. Don't mount it etc. Best thing to do would be to transfer the whole drive to another computer and then take a byte by byte copy of the hard drive device using something like dd (see "man dd"). Then, run whatever salvage software you may have handy on that file.


I already mentioned the byte copy a while ago. It is way too late now.

Clonezilla is good at making copies like this, and would be less confusing than dd.

> 
Most probably there is nothing you can do though, I would just learn to live with the fact that the data is gone.

Yeah, spend the time to rebuild what was lost, instead of borking some more.

---

### Post by hockey97 on 2008-06-28
ok, I decided to just reformat everything and start all over while I am installing eveything again I will have a hammer right next to me so every  5 min I will hit myself lol. 

Well I decided since I am starting all over again gosh.. ugh!!.
I might as well prevent this from happening again.

So I decided to buy a external hard drive usb, to save important files  like my website onto it as a backup.

I have a question about ubuntu like apache, dns, all the server software, how can I make a backup of it so I don't have to re-install it every time these things happen?

I want to make a backup in a way where I can just easily transfer my website and server software over and no need to reinstall the server stuff.
 It was painful for me to install the dns and also mail server so I want to backup all the stuff so I don't have to install it ever again just copy the files over to make the servers work exactly how I installed it the first time.

Also if you got any tips on good ways to backup my files please tell me so.

Thanks for the help though. And hope you understand my frustration. lol.

Well off to reinstall everything. urgh!!!!!

---

### Post by LaRoza on 2008-06-28
> **hockey97 said:**
> 
I have a question about ubuntu like apache, dns, all the server software, how can I make a backup of it so I don't have to re-install it every time these things happen?


You can use clonezilla to copy a partition and restore it (you will need some space for this)

You can just copy the confige files for the programs and back them up (that is what I do on my local machine) in case you need to resinstall.

> 
I want to make a backup in a way where I can just easily transfer my website and server software over and no need to reinstall the server stuff.
 It was painful for me to install the dns and also mail server so I want to backup all the stuff so I don't have to install it ever again just copy the files over to make the servers work exactly how I installed it the first time.

Clonezilla is the way to do that.

---

### Post by hockey97 on 2008-06-29
ok thanks I will keep clonezilla in mind, just have to wait until I get my external hard drive.

---

