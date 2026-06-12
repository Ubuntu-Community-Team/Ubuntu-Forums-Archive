---
title: "Ubuntu 12.04 does not boot from live disk"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Subcomfreak on 2012-07-02
[COLOR=Red]CURRENTLY NOT SOLVED. I think it is a CD drive issue at this point. Read post #5[/COLOR]


1) I have verified the checksum
2) I meat the recommended system requirements. 1ghz processor, 1024 mb of ram, a 128mb graphics card
3) my computer is currently booting windows 2000. I wish to dual boot.
4) My computer is at least 13 years old.
5) for all of these I used a 32 i386 iso (the one that was auto recommended to me by official unbuntu download page)
6) I can't boot from a USB stick. No dice from this old bios.
7) Yes, almost forgot, I have made back-ups.

Okay... first I tried Wubi (the windows installer) and everything seemed to be going well. After the first reboot everything seemed okay. It started checking all of the install stuff. Then, for a very brief second, a white box (that looked like the slide show) flashed on and off in the middle of the screen. Once it flashed off I got a black screen. I'm pretty sure that I need to remove the slide show via the "sudo apt-get remove ubiquity-slideshow-ubuntu" command in the terminal. However, I can't get there with wubi because it auto starts an install. 

I'm not completely stupid, so I said "hell, why not boot from a live cd. Once booted in, sense it booted up find with wubi, I can take care of that slide show and be on my way to dual booting glory!"

Good plan of action I thought... I burned off a live CD (not dvd oddly enough, even though I do have that capability) and rebooted. the bios found that it had an OS on the cd and proceeded to boot from it. I got a very nice splash of Ubuntu booting up and was happy.

My problem starts now:
After a while of the splash with the little dots that change from white to pink (or purple, what ever that weird lavender color is) I got shipped to the, you guessed it, BUSY BOX! with an error saying it couldn't find any live medium on the disk (or marital, something like that).

So, for some reason it doesn't like the LIVE cd... I could boot up find from the hard drive with wubi, but I couldn't change the slide show.  I can't boot from the live cd, but I could change the slide show.

As you can see, I need to be able to do one of two things:

either
1) be able to remove the slide show before wubi goes through its install gyrations in linux

-or-

2) boot from a live cd that all ways puts me to busy box on boot (note I have burned multiple copies of the live disc. Same problem)

-or-

3) something else that I am not aware of.

Thank you in advance!

---

### Post by JanuaryJones on 2012-07-02
Hi! 

If I understand you right, you have problems with the graphical installer? Maybe you should try the alternative installer instead? [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

### Post by Subcomfreak on 2012-07-02
I have been asking my self for ever why they have to have stupid graphics to install an OS. WILL TRY THE TEXT install!!! Thanks! Results coming soon.

2 hours and 33 mins, plus burn time of the cd until I can test it.

---

### Post by JanuaryJones on 2012-07-02
> **Subcomfreak said:**
> I have been asking my self for ever why they have to have stupid graphics to install an OS. WILL TRY THE TEXT install!!! Thanks! Results coming soon.

2 hours and 33 mins, plus burn time of the cd until I can test it.

You're welcome! That has often worked for me when installing Ubuntu on an older computer :) Good luck!

---

### Post by Subcomfreak on 2012-07-02
I am 100% sure that you pointed me in the right direction, however, it still failed. Here is a break down of what happened:
Plopped in the disk a rebooted.  different Ubuntu instillation system started that I must say is absolutely superb. Now it went fine until it got to the point of mounting the disk. It failed at that point.

Now, something that I forgot to mention was the fact that I have two cd/dvd drives.

My main drive is a super combo dvd/cd reader and burner. BIOS says that this is my cdrom 0

The second one is a cd reader and burner that is on the fritz. It randomly disconnects from the computer, meaning that windows, nor the bios can detect it some times. I hardly ever use it and it must be 10-6 years old. It can go disconnected for a long time (days sometimes), and rebooting does nothing. BIOS reads as cd rom 1.

So back to the install process. I got a message saying that it couldn't mount the live disc, and this was probably caused by the disk not being in the trey. I pressed retry a few times to no avail. BUT, then it struck me: Why not just toss the disk in the lower tray and see what happens? Guess what? It worked. It wen through the mount step and started "copying files" or something like that. Remember how this drive sometimes randomly disconnects?  well apparently that is what happened sometime during this instillation. Nothing happened to my system that I can tell from this abort (booted into windows fine and all disk sizes are the same). But guess what the trick didn't work again because the CD wasn't there. 

Well, the obvious next step, that I took, was to go into the good old bios and disable the disc 1 (the cd only drive). No luck here. The instillation persists that the disc is not in the drive. EVEN WHEN THERE IS NO SECOND DRIVE IN THE BIOS.

Well, the obvious solution that I know you guys will tell me is to try a USB live disk. Well, my bios won't support that. I really really don't want to risk editing the bios or messing around in there. Is there a way to trigger a boot from a USB device in windows 2000? Or some other way? Maybe booting from the cd and then plugging in the USB flash drive? I'm sure that if I could achieve a USB boot I would probably be well on my way.

The second route is what I'm probably going to have to end up doing. I'm probably going to go into the guts of the computer and "pull the plug" on the old cd drive. That could fix the problem of linux being confused over which cd drive is which... how knows?


I hope it works![-o<

---

### Post by JanuaryJones on 2012-07-02
> **Subcomfreak said:**
> I am 100% sure that you pointed me in the right direction, however, it still failed. Here is a break down of what happened:
Plopped in the disk a rebooted.  different Ubuntu instillation system started that I must say is absolutely superb. Now it went fine until it got to the point of mounting the disk. It failed at that point.

Now, something that I forgot to mention was the fact that I have two cd/dvd drives.

My main drive is a super combo dvd/cd reader and burner. BIOS says that this is my cdrom 0

The second one is a cd reader and burner that is on the fritz. It randomly disconnects from the computer, meaning that windows, nor the bios can detect it some times. I hardly ever use it and it must be 10-6 years old. It can go disconnected for a long time (days sometimes), and rebooting does nothing. BIOS reads as cd rom 1.

So back to the install process. I got a message saying that it couldn't mount the live disc, and this was probably caused by the disk not being in the trey. I pressed retry a few times to no avail. BUT, then it struck me: Why not just toss the disk in the lower tray and see what happens? Guess what? It worked. It wen through the mount step and started "copying files" or something like that. Remember how this drive sometimes randomly disconnects?  well apparently that is what happened sometime during this instillation. Nothing happened to my system that I can tell from this abort (booted into windows fine and all disk sizes are the same). But guess what the trick didn't work again because the CD wasn't there. 

Well, the obvious next step, that I took, was to go into the good old bios and disable the disc 1 (the cd only drive). No luck here. The instillation persists that the disc is not in the drive. EVEN WHEN THERE IS NO SECOND DRIVE IN THE BIOS.

Well, the obvious solution that I know you guys will tell me is to try a USB live disk. Well, my bios won't support that. I really really don't want to risk editing the bios or messing around in there. Is there a way to trigger a boot from a USB device in windows 2000? Or some other way? Maybe booting from the cd and then plugging in the USB flash drive? I'm sure that if I could achieve a USB boot I would probably be well on my way.

The second route is what I'm probably going to have to end up doing. I'm probably going to go into the guts of the computer and "pull the plug" on the old cd drive. That could fix the problem of linux being confused over which cd drive is which... how knows?


I hope it works![-o<


Oh, it's THAT complicated? I am not an expert so I can unfortunately not help you with that. Although, I don't think that booting from the CD and then plug in the USB will work..I am not sure and you can of course try, but I have my doubts. 

Maybe someone else know what will work?

Good luck again! :)

---

### Post by oldfred on 2012-07-02
I have never used it, but some have posted that this works for those old BIOS that will not boot a USB.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

It should not be difficult to disconnect CD drive in case. My problem always was (is) that whenever I open case I manage to bump something and have another loose connection.

---

### Post by Subcomfreak on 2012-07-02
Plop looks like a viable option. I don't want to over wright my boot sector with anything but grub if possible. So I might try burning off a grub CD as the plop manual suggests. Will that work to boot the alternate edition of ubuntu from a USB key?

---

### Post by mkstallings1 on 2012-07-02
I use Plop Boot Manager on my ancient laptop.  It's an .iso you download and burn to a cd and you boot it up and it shows a menu that will allow you to  boot from usb.

---

### Post by Subcomfreak on 2012-07-02
will try!

---

### Post by Subcomfreak on 2012-07-02
Update: Didn't work. Going to try adding cdrom-detect/try-usb=true to boot options. 

This may be something to do with the alternate edition. I used linuxlive usb creator in order to create a usb live disc (I guess that's what they are called) and it said that the alternate version is not supported. If all else fails I could try the standard version except before install use the "sudo apt-get remove ubiquity-slideshow-ubuntu" terminal command.

EDIT: Did not work with the detect cd rom command. Am trying vanilla umbuntu...

---

### Post by Subcomfreak on 2012-07-02
When he so ubuntu loading off of his LiveUSB drive he said, "It was glorious" (I'm actually posting from firefox in Ubuntu right now!!!!!!!!!!!!!!!)

Now... we aren't out of the woods yet. I still have to try to install this thing. :p

applying the remove slideshow command and so forth.

---

### Post by Subcomfreak on 2012-07-02
okay, my situation is vastly improved. It seems like that unbuntu installed correctly. I had to do a manual partitioning...

My drives are as follows:
sda1/2 is my 360gb E;/ F:/ drive that holds my windows stuff that I have been cacking on my hard drive for 10 years
sdb is where I put linux partitioned as follows (in the order that I partitioned)
25gb /
2gb swap
rest of the 360gb as /home
Don't worry, I used ext4 for the OS and /home, and swap for swap...
sdc USB
sdd my windows os C:/

I didn't know where to put the boot loader... so I just left it in sdb. Now I can only boot to windows. It doesn't give me a choice. Probably should have done sdb1 (/) right?

How can I fix this problem? Probably a google will help...

---

### Post by Subcomfreak on 2012-07-02
Sense linux is installed correctly, and it did boot from the live format correctly, this is actually solved. I'll create a new thread for this boot loader problem.

The solution was:
1) burn off a plop disc from the .iso file found in plop's zip file
2) make a USB of ubuntu 12.04 STANDARD (not ALTERNATE)
3) plug in USB and insert disc
4) reboot and select USB when the boot menu comes up
5) install

---

### Post by oldfred on 2012-07-02
Default install is usually to sda, but it may be in sdb, if you had that set in BIOS. Did you try booting from the other drive(s)? If not we need boot info script or Boot_repairs BootInfo.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Subcomfreak on 2012-07-02
My bios is old so I can not select what drive to boot from.

Downloading the repair disk now. However, I did make a separate thread for this issue sense I was able to boot into the live format.

---

### Post by mkstallings1 on 2012-07-02
Boot Repair should easily solve your problem.

---

