---
title: "Ubuntu or Windows 8"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by sagemaster210v2 on 2013-12-07
Im currently using Ubuntu 13.10 on an external drive to test it, and im loving it! I am also thinking about installkng Ubuntu to my actually laptop to i can update everything and have full use of it, but im running Windows 8 on my laptop, and I was wondering if i should replace w8 woth ubuntu, and if so which version (12.04 lts or 13.10) and reasons why i should.

---

### Post by Dreamer Fithp Apprentice on 2013-12-07
> **sagemaster210v2 said:**
> Im currently using Ubuntu 13.10 on an external drive . . . and . . . am also thinking about installkng Ubuntu to my actually laptop to i can update everything and have full use of it If you mean an external hard drive you CAN update it and get full use of it as it is. The only difference should be speed as typically internal drives are faster since they don't have to go through the usb interface. Or at least that's my understanding.> **sagemaster210v2 said:**
> I was wondering if i should replace w8 woth ubuntuNo "should" involved really. Purely a matter of preference. If it were me, if I had the drive space, I'd shrink some partition on the drive with gparted or something similar, create a new partition large enough for ubuntu (say at least 5 gb, you can look it up for a more exact figure; 20 if you have scads of drive space), partition it ext3, and install ubuntu to it and dual boot.> **sagemaster210v2 said:**
> which version (12.04 lts or 13.10) and  reasons why i should.Good question, but the choice isn't  crucial. In principle the LTS should require less frequent and less  extensive updates once it's updated the first time (because they've  already had plenty of time to fix it up) so the updating won't take as  much of your time or bandwidth. So it should be, in an overused word,  more stable. Saucy will have some applications that have had bugs fixed  upstream that aren't readily available to the LTS and may break it if  you trick it into installing them anyway. I'm dual booting both atm and  tinkering with both, optimising them for different things. If and when  I'm satisfied with my tweaking of the Precise system I"ll probably back  it up as is and try upgrading it to the latest version. Thunar and  Pcmanfm both work appreciably better in the later versions available to  Saucy than in the earlier versions that are the newest in the Precise  repos. Offhand I can't think of any other differences I've noticed.

---

### Post by oldfred on 2013-12-07
I would not un-install Windows 8, but use Windows 8 disk tools to shrink it. To keep it functional you do need at least 30% free space inside the NTFS partition. When it gets too full it gets very slow. Also with Windows 8 you must turn fast boot or the always on hibernation off.
Since it is Windows 8, you will have UEFI with secure boot. Often best to turn off secure boot.
Ubuntu will have two entries in UEFI menu, one BIOS/CSM/Legacy & the other UEFI. 
If secure boot is on, it should only show the secure boot UEFI entry.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

UEFI is relatively new, secure boot is very new and Microsoft, vendors & Ubuntu are regularly updating. I might suggest 13.10 and then upgrade to 14.04 when it comes out. The current 12.04.3 is not as current on UEFI but will be updated with the 12.04.4 update in Jan. If very new Haswell system you may have to use 13.10 as Intel added updates to kernel, video and other support systems to support Haswell or 4th gen chips.

Also check that you have vendor's latest UEFI/BIOS version.
Lots of info in link in my signature.

---

### Post by sagemaster210v2 on 2013-12-07
Okay, thanks for the reply. Oh and i apologize for my misspellings. Anyway, what I meant by replace, is if i should just disregard windows 8, and use the entire drive to install ubuntu?

---

### Post by sagemaster210v2 on 2013-12-07
Thanks oldfred, but I recently acquired my laptop from my Uncle, and he did not include the windows 8 disc, so I can't change the size of the partition, which is why i asked if i should just install Ubuntu to my laptop and disregard the fact that windows 8 exsists on my laptop.

---

### Post by sagemaster210v2 on 2013-12-07
Oh, and when I said i don't have full use, i meant like accessing my video drivers, and so on. For some odd reason, since i'm running off of an external usb harddrive, i can't update my video card from it, and when i try to on windows 8, which i have forgotten the admin password for (don't question it), it asks for the admin pass in order to update it. Also applications like steam, that have built in video card updaters (not sure if thats a word) can't read/search for an update since its not actually on my laptop. Another thing is that i can't use flash drives (usb) because Ubuntu is not actually on my laptop.

---

### Post by Mark Phelps on 2013-12-07
> so I can't change the size of the partition,Of course, you can!  Simply use the Disk Management utility already built into Windows to shrink down the size of the OS partition.

---

### Post by oldfred on 2013-12-07
XP was the last version that vendors offered disks for reinstall. 
Now you get an image, which is not a full Windows installer like you would purchase, but an image of the installed version you have. You also can make a backup of the image to DVDs which is a good idea. 
But you should also make full back ups of Windows.
We have users who want to fully install Ubuntu, but then have that one application or game that only runs in Windows. So they want Windows back. It took me years to totally wean my self off that one application.

---

### Post by Sef on 2013-12-07
Is your computer under warranty?  If so, by installing Ubuntu, you could void the warranty.  Have you thought about installing it virtually?

---

### Post by DuckHook on 2013-12-07
> **oldfred said:**
> ...It took me years to totally wean my self off that one application.I'm still not weaned. Sid Meier's Alpha Centauri will only run properly from Windows. Have never been able to get it running well using WINE. That is the main reason I've still got Windows on my machine.

You reach an age where you don't *want* to wean yourself off the things that give you pleasure. Regression, I suppose.

@OP It's always good to have choices and a fallback strategy. W8 may end up being completely disposable. But it's nice to be in the position where *you* are in control and get to choose when you can ditch it to reclaim the disk space.

---

### Post by sammiev on 2013-12-07
Keep W8 and install Ubuntu along side. You can make a set of W8 DVDs from within Windows. You may want to do a system backup before making any changes first.

---

### Post by Dreamer Fithp Apprentice on 2013-12-08
> **sagemaster210v2 said:**
> Oh, and when I said i don't have full use, i meant like accessing my video drivers, and so on. For some odd reason, since i'm running off of an external usb harddrive, i can't update my video card from it, and when i try to on windows 8, which i have forgotten the admin password for (don't question it), it asks for the admin pass in order to update it. Also applications like steam, that have built in video card updaters (not sure if thats a word) can't read/search for an update since its not actually on my laptop. Another thing is that i can't use flash drives (usb) because Ubuntu is not actually on my laptop.Possibly you are confusing drivers with firmware? Booting from a usb connected hard drive shouldn't affect your being able to install drivers. Drivers are software and their physical location is on the hard drive platter, not in the video card. Installing new FIRMWARE to your video card is something most of us never do but it IS possible, at least in principle, if the card supports it and someone, usually the manufacturer, makes it available.  It is concievable that your video card manufacturer might have a firmware updater tool that only run under windows. But installing Ubuntu to the hd isn't going to change that if that's the case. Basically, as far as I know, and I've been booting from a usb drive for more than a year, internal or external drive doesn't affect what you can do with a system. External is typically a little slower, that's all.

---

### Post by jdeca57 on 2013-12-08
For me. there are two good reasons to keep W8: first there is the compatibility issue, also for programs you don't use (yet) but can be of interest in the future. After all you paid for the license why not keep the option of using it? Second is a first-hand experience with the OS that actually stays the market leader: Windows is not dead, and W8 is here to stay. Actually a new user interface is nothing to surprise Ubuntu users... ;-)

---

### Post by monkeybrain20122 on 2013-12-08
> **sagemaster210v2 said:**
> Oh, and when I said i don't have full use, i meant like accessing my video drivers, and so on. For some odd reason, since i'm running off of an external usb harddrive, i can't update my video card from it, and when i try to on windows 8, which i have forgotten the admin password for (don't question it), it asks for the admin pass in order to update it. Also applications like steam, that have built in video card updaters (not sure if thats a word) can't read/search for an update since its not actually on my laptop. Another thing is that i can't use flash drives (usb) because Ubuntu is not actually on my laptop.

What do you mean by running off an external usb harddrive? It sounds like you have a live usb. On the other hand if you actually install Ubuntu in an external hard drive (with the proper linux file system) you can do all these things and if it is a hard drive (not a flash drive) you can get the same speed and performance as an internal install. I am typing from Ubuntu 13.10 installed on an 500 G external hard drive now (using maybe only 20 g now) Usually I set up the next OS in my external drive, do all the testing and customization and run it for may be a month to make sure everything works, then clone it to my internal hard drive (currently on Ubuntu 13.04) that way there will be no unpleasant surprises from upgrading. This (a real install in an external hard drive) is a really good way to test hardware compatibility before you do anything to your internal hard drive.

Well ask yourself if you would need Windows, if the answer is yes, then keep it. If no, get rid of it. I don't get all the advise to keep Windows 'just in case'. No Windows user would waste their hard drive space to keep Linux 'just in case'. Are we not having confidence in our OS? :) Personally I got rid of XP after dualbooting for a few months, never used it, never boot into it except for updating antivirus.

---

### Post by Mopar1973Man on 2013-12-08
Like myself I ditched Windows products all together for the security aspect of it no longer have to worry about cross contamination from sharing things back in forth between Linux and Windows. 99% of all the software I use Linux has a answer for. There is only a few programs that I use in a VirtualBox and cure that problem. So as for keeping Win8 I say for a noobie kept as a dual boot for now till you get your feet wet then once your comfortable I say yank Win8 out and never turn back. I got a good friend in Riggins, ID that I taught Ubuntu operations and basics. He had his first sample of Win8 from another friend and it was OMG! he was totally lost and was all thumbs operating Win8. He wasn't impressed at all so net result he grabbed his little Lubuntu and smiled...

---

### Post by mkmanifesto on 2013-12-08
Dual booting is up to you. I personally would ditch Windows and move over to Ubuntu or some Linux distro. I haven't had any problems completing tasks or finding equivalent software. Prior to switching 100% I was no stranger to Ubuntu and other flavors of Linux. Its just a matter of doing it and not looking back.

At the end of the day you have to look at your needs and what you want. If you feel like Ubuntu is going to do the job then I don't see the point in keeping the Windows install on your hard drive.

---

### Post by cmcanulty on 2013-12-08
I would only keep the win 8 if you might need it for school or work. Do burn the restore and repair DVDs though either way as it gives you a fallback option and do backup everything important! I always use Ubuntu classic but keep a win machine as I have to give tech support to windozers quite often at our library, never without the free speech on why linux rocks before I fix the annoying win issues

---

### Post by monkeybrain20122 on 2013-12-08
> **Sef said:**
> Is your computer under warranty?  If so, by installing Ubuntu, you could void the warranty.  Have you thought about installing it virtually?

I buy a machine to run my software and OS. It doesn't make sense to have to use the machine in ways which are suboptimal for my purpose just because of the warranty. It is like using a crippled machine voluntarily. Speaking for myself, I wouldn't run my OS of choice, crippled and suboptimally in a vbox inside an OS that I can't stand, on my own machine just because of the warranty, sooner or later it will expire anyway.

---

### Post by sagemaster210v2 on 2013-12-08
Because i got it preinstalled from my uncle. My laptop is kinda old, and my uncle decided to install windows 8 on it (he works for dell so yeah)

---

### Post by DuckHook on 2013-12-08
Although it is indeed heartwarming to see that so many people have found the Linux-sphere has progressed to the point that they no longer need Windows, we must remember that our own needs do not reflect the needs of others. I side with those who advise the OP to keep Windows. Aside from eating up a few GB of disk space, it does not hurt and can only help to keep it kicking around. The only drawback to W8 is that an OEM install is almost impossible to convert into a VM, so W8 must either be kept as a dual boot or Ubuntu must actually be run as the VM inside the W8 host. I agree with *monkeybrain20122* that confining Ubuntu within a VM would stick in my craw, but setting up a dual-boot is not that difficult.

@OP

Ultimately, it's up to you. You are getting lots of good comments here, each bringing a different facet to your attention. But only you know your own situation. I do agree with the observation that Ubuntu has reached the point where the general user can find good equivalents to almost anything the Windows world has to offer.

---

### Post by Dreamer Fithp Apprentice on 2013-12-08
If you have enough drive space, installing a dual boot system is no more trouble than overwriting the windows system. And, again, IF YOU HAVE ENOUGH DRIVE SPACE, there is NO downside. You may derive no benefit from it, but it can not hurt. You don't HAVE to use it. It's not going to magically attract malware while it is sitting inert on the drive. You will not get more bragging rights by ditching it.  It won't even control the boot process anymore. It leaves you an option you may never use. So what? Think of it as a long shot bet that costs nothing to cover. But if you need the space, that's a different matter. In that case, back it up and ditch it. That is if you need the space NOW. If you are just thinking you might need the space at some future time, that's irrelevant. When that happens, just reformat the Windows partition. Also, there is much to be said for having 2 or more bootable systems on a machine, regardless of what kind of systems they are. If you bork one you might can fix it from the other.

---

### Post by monkeybrain20122 on 2013-12-09
> **DuckHook said:**
> Aside from eating up a few GB of disk space, it does not hurt and can only help to keep it kicking around. The only drawback to W8 is that an OEM install is almost impossible to convert into a VM, so W8 must either be kept as a dual boot or Ubuntu must actually be run as the VM inside the W8 host. 

Op just said it is an old computer and his uncle installed W8, so in particular the uncle would have a disk.

---

### Post by Jake Sweeney on 2013-12-09
I would dual boot Ubuntu alongside Windows 8, giving you the best of both worlds. You can always resize partitions in Ubuntu's install wizard

---

### Post by Jake Sweeney on 2013-12-09
I would dual boot Ubuntu alongside Windows 8, giving you the best of both worlds. You can always resize partitions in Ubuntu's installation wizard

---

