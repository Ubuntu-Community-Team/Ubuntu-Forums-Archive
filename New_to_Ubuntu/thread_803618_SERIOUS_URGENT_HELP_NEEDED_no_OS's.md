---
title: "SERIOUS URGENT HELP NEEDED no OS's"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by tethys on 2008-05-22
First of all, just want to say, please read it all, because all of it is important.

What I did:

Last night, I was trying to install a new splash screen. So I go and install startup manager, then select the splash screen. The guy that has it up on gnome-look says do a sudo edit menu.lst to find the right line for resolution, so I do and don't find it... whatever. He then says to run sudo --hminfo (I think) to find the code for the resolution... I ran that like a bunch of times and the screen never stayed long enough for me to read it. He also says to edit another file that has your selected resolution... so I change the bottom value to 800, cause the top one was fine at 1280...

I go to restart the compy and get a chain of commands that say failed, but I used to randomly getting these, and they usually go away in a day or so. My compy restarts, and when the splash screen shows up, I get this list of stuff saying [OK] at the end of every line. It goes in to my login screen, which I have also changed correctly, and I login. Now I cannot see my top or bottom bar, and cannot launch any programs. I figured crap, I'll have to reinstall, but no big deal. What saved me a little was that I had a Nautilus launcher on the Desktop, so I moved the stuff I wanted saved back onto my Vista partition.

I reboot, and this time choose Vista, and get into it nicely. I go into my Disk Manager and delete the two partitions for ubuntu, cause I want to start of clean and with a bit more space this time. I change the partitions to unallocated and push 'em back into the Vista partition. I then go and uninstall Nero from the Windows side and some other crap to free up somme more space for when I go to reinstall Ubuntu.

Nero asks me restart, so I do... Here's the hook... GRUB tries to load... WTF... there is no GRUB anymore, why in God's name would it even KNOW if it WAS trying to load... GRUB doesn't even exist anymore. It says error22, which I take to mean GRUB doesn't exist... shocking. So I shut down the computer and restart it and look in the bios and boot screens to see if I can take the GRUB boot line out of it... Didn't find anything... shocking.

Thank God I still have the live CD around, so I pop that in and go to reinstall ubuntu, but now it gives me an "unknown error writing files" when I try to use the guided and manual partitioner. I figure, fine, I'll just do a live boot from CD and get on here and type this post out. No dice, gives me IO Buffer errors and will not start.

I'm at a loss for what to do, as I know have a 600 dollar paperweight that I cannot afford to lose information from. So I really really really really hope someone here at the very least knows how to get ubuntu reinstalled.

Thanks for reading my tales of woe this far everyone.

---

### Post by neurostu on 2008-05-22
When you installed Ubuntu it replaced the windows boot loader with Grub. Grub was installed onto one of your ubuntu partitions, so when you deleted the data on the partition it deleted grub as well.  What you need to do is re-install ubuntu on the partition where it used to be installed. This will re-install grub and you will be able to boot into windows.

About your partitions.... open the live CD, under System-->Adminstration you will find the Partition Editor. Open that and reformat your ubuntu partitions to EXT3 and set the mount point as '/' then reinstall ubuntu.

---

### Post by tethys on 2008-05-22
thanks for the info but...

> I go into my Disk Manager and delete the two partitions for ubuntu

and for the Live OS boot

> I figure, fine, I'll just do a live boot from CD and get on here and type this post out. No dice, gives me IO Buffer errors and will not start.

---

### Post by sam_delta on 2008-05-22
to get your data on windows.
download a copy of supergrub disk @ [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) , and restore the bootloader, then boot into your windows partition and backup your data

then you can try to boot again into your live cd ,free up space and try to install again and see what happens, you can also try the alternate install cd

just my 2 cents

tell us how it goes
sam

---

### Post by neurostu on 2008-05-22
also you might consider removing the HDDs from your computer then booting into the live cd. then reboot but reconnect the hdd's one by one to see if it is a hdd that is causing the problem.

---

### Post by tethys on 2008-05-22
and just know that I'm typing this from a seperate computer, as the other one only recognises boot discs, also the Live CD seems to be freezing up on loading linux kernal now, even though it shows at 100%

im getting kinda scared now...

I'll try the grub thing if I can

oh, and it is a laptop, HDD is gonna be a no go

---

### Post by sam_delta on 2008-05-22
is it a laptop or a desktop? try to remove all kind of power for a while, battery, AC, etc. for some 5 mins or something before booting into the live cd

sam

---

### Post by tethys on 2008-05-22
its a laptop... I have had it shut down for about 10 minutes, and am trying to reinstall ubuntu with the linux irqpoll line that i had to use the ffirst time, but it is hanging on loading linux kernal at 100%

---

### Post by tethys on 2008-05-22
sweet, so the super grub disc does....... nothing... it tries to load grub

---

### Post by tethys on 2008-05-22
no more help? i know it hasnt been long at all, but I'm freaking out here

---

### Post by philinux on 2008-05-22
Grub is on the main boot record, mbr, you need to boot the windows disk in recovery mode and use fixmbr as I remember.

Or Download and burn supergrub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) if you have no windows bootable disk.

---

### Post by sam_delta on 2008-05-22
you could also try booting into your vista CD , then into a recovery console, and type "fixmbr" to install vista bootloader and get your data

sam

---

### Post by wigglydiggly on 2008-05-22
One thing you could try is to restore the original MBR that comes with windows.  The MBR is located at the beginning of the first boot HDD.  So deleting the Linux partions would not remove or change the MBR.  There are utilities to do this for windows.  Just google for "MBR recovery windows".  Once you have that you should be able to boot into windows and repartition your drives.

Good luck

---

### Post by tethys on 2008-05-22
wellllll... game over gents, I booted up my recovery disc gateway gave me.. looked in the file browser window and it shows my c drive as 102 GB free of 102 GB

---

### Post by sam_delta on 2008-05-22
try to go into the recovery console and type "fixmbr"
there might be a slight possibility that windows partition is still there
try wont hurt

sam

---

### Post by tethys on 2008-05-22
i cannot get to a recovery console, nothing is accessable, there are no backups present it says, and there is no restore to an earlier time present, and it is not able to fix it automatically it said... all i can do is go to a command prompt... I'll type it in, but i dun  think it'll do any good now

---

### Post by tethys on 2008-05-22
it says "fixmbr is not recognised as an internal or external command, operable program or batch file."

---

### Post by philinux on 2008-05-22
Get supergrub and restore your windows mbr. Thats why the recovery cd wont work it thinks the windows install has gone as the mbr has grub on it.

Super grub can restore your the mbr to windows.

---

### Post by tethys on 2008-05-22
ok well i tired to boot supergrub and just tried again, all it does is try to boot grub and fail... then nothing happens... thats all

---

### Post by ugm6hr on 2008-05-22
Sounds awful.

I would recommend you stop trying to write to the HD while you resolve this.

Did you have data on the HD that isn't backed up?

If so - try an alternative LiveCD to see if you can retrieve it.

Did the LiveCD work the first time, or did you install with Wubi (inside Windows)?

If the Windows partition is still there, you might be able to access it with GAG: [http://www.users.bigpond.net.au/hermanzon/p18.htm#GAG_Boot_Manager](http://www.users.bigpond.net.au/hermanzon/p18.htm#GAG_Boot_Manager)

PS: Your problems stem from
1. Deleting Ubuntu / Linux partition without restoring a usable bootloader first.
2. Resizing partitions without backing up first (resizing / moving / deleting partitions is a known risk factor for data corruption)

---

### Post by calraith on 2008-05-22
Wow, what a series of unfortunate events!  I'm betting that the chances for data recovery on your partition-confused drive is very high.  The bad news is that in order to do so, you will probably either have to attach the drive to a working computer, or get some professional help.  A quick Google search turned up [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), which is described as follows:

> **TestDisk** is a *powerful* free data recovery software! It was primarily designed to help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or *human error* (such as *accidentally* deleting a Partition Table). Partition table recovery using TestDisk is really easy.

Hmm.  Now that I think about it, it seems like I've seen some sort of recovery CD somewhere that includes TestDisk.  UBCD4Win, maybe?  I can't remember, but it probably exists....

---

### Post by tethys on 2008-05-22
yes i have a lot of data that isnt backed up... I can find it online, but that would take ages... though I did have a lot of billing info

the live cd worked after a few tries... I always hung on the partitioning part, then i put in linux irqpoll at the end of the options and it installed

also your page does not work

---

### Post by tethys on 2008-05-22
> PS: Your problems stem from
1. Deleting Ubuntu / Linux partition without restoring a usable bootloader first.
2. Resizing partitions without backing up first (resizing / moving / deleting partitions is a known risk factor for data corruption)

= damn noobish ways

so i have a few questions... if i install ubuntu on my hard drive as the only OS, will ibe able too install vista afterwards, or is it a install vista now or forever hold your peace deal?

---

### Post by forestpixie on 2008-05-22
> **tethys said:**
> ok well i tired to boot supergrub and just tried again, all it does is try to boot grub and fail... then nothing happens... thats all

Are you saying that supergrub is not booting - if your setup to boot from cd first then you shouldn't see grub.

When you got supergrub did you burn it as an iso or data disc - it needs to be as an iso so you can boot with it.

---

### Post by ugm6hr on 2008-05-22
> **tethys said:**
> the live cd worked after a few tries... I always hung on the partitioning part, then i put in linux irqpoll at the end of the options and it installed

also your page does not work

DO NOT try to reinstall or move partitions again.

You are merely risking your data further.

If a LiveCD will boot, you should take the opportunity to back up your data BEFORE doing anything else.

Sorry - that link: [http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager](http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager)

---

### Post by tethys on 2008-05-22
to forestpixie: i burnt as an iso... i am very familiar with burning things... dreamcast... lol... and no it does nothing... shows grub error22, thats all

to ugm6hr: the restore disc says there is no data to back up...

---

### Post by lswest on 2008-05-22
If you have vista the command to restore the MBR is ```
bootrec /fixmbr
bootrec /fixboot
``` (run both) and there's a link to restoring bootloaders in my sig (which is what you're trying to do), see the third line.

---

### Post by tethys on 2008-05-22
ok, so it didnt restore the bootloader, and going into startup repair didnt do anything either... it says bootmanager is missing or corrupt








fine.... how do you completely kill anything that could be on the disc, I'm gonna start from scratch

---

### Post by lswest on 2008-05-22
> **tethys said:**
> ok, so it didnt restore the bootloader, and going into startup repair didnt do anything either... it says bootmanager is missing or corrupt

looks to me like you've somehow deleted your vista partition then, or at least the bootloader files from that partition.  Or there is a problem with your hard drive.  Try removing it (it is possible in a laptop, google for your laptop and you should find instructions on how to do so) and booting to a liveCD, if it works, then it would probably be smart to invest in a new hdd.

---

### Post by ugm6hr on 2008-05-22
> **tethys said:**
> to ugm6hr: the restore disc says there is no data to back up...

If you are confident the data is gone.... Sorry.

If you want to maintain a dual-boot, try this: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

And plan partitions before installing.

---

### Post by phoenix_abhi on 2008-05-22
According to ur problem, there is no more Ubuntu or Grub exist. I also faced likewise problem earlier

If u want backup ur data from Vista to DVD, my way when everything failed is:

Put ur recovery cd in drive and make BIOS boot from CD
Go to recovery comsole
Type
bootrec /fixmbr
bootrec /fixboot

If this is not doing anything, if u have more than one partition then bring one XP cd and install XP into a less required partition

I think ur Live CD is corrupted
U can do all this only as last option

---

### Post by nicedude on 2008-05-22
To the guy with the problem I scanned over all the posts in this thread and felt I would let you know exactly why you are getting grub errors since no one has actually said how grub works.

Grub rewrites your hard disk MBR (master boot record) this previouly had a vista loader on this space, this is cool as grub can then boot vista and Ubuntu both, but the part you might not get is that grub is too large to fit fully into the MBR alone and as such writes the remainder of its needed data to /boot/grub/menu.lst on your Ubuntu partition ( Not your vista one ) so when you deleted your Ubuntu partition you destroyed this vital data that grub needs to work. At this point as messed up as it seems you would be able to use your Microsoft vista install disk to recover by fixing the MBR but alas you have a system restore disk that your PC maker has given you which isn't a true MS vista install disk so the utilities others have suggested are not there as this disk is designed for one purpose to put your PC back to the same way as when you opened the box it came in.

At this point your best bet to get your data back would be to use a live linux distro disk (any that will boot and there is nothing that you did that I see that would stop one from booting ) in conjunction with say a USB memory stick to copy the data to. You can use testdisk util as others here have suggested as I have seen others get good results with it. then just try to mount the partition and try to copy the data to another disk or USB stick.

Just my 2 cents and I thought maybe this would shed light on how grub and PC manufacturers do things.

Sorry to see your results of your adventure and I hope in future it works a little better for you and while you can install Ubuntu before Vista I think the easier method is Vista first Ubuntu second. And you wont really have a choice with a factory restore disk since if you install Ubuntu first the restore disk will just overwrite it when you try to install vista with it.

---

### Post by tethys on 2008-05-22
nope, I think I'll just nuke my HD and only have ubuntu

isnt there a command or something to erase everything

---

### Post by tethys on 2008-05-22
i also tried typing rstrui.exe/OFFLINE:D:\RECOVERY into the commad prompt and it told me there are no restore points on the drive, but the drive is there and it shows 4.75 GB free of 9.74 GB

---

### Post by ugm6hr on 2008-05-22
> **tethys said:**
> nope, I think I'll just nuke my HD and only have ubuntu

isnt there a command or something to erase everything

It isn't necessary.  If your Ubuntu CD doesn't have errors (you can check from the boot screen), and Ubuntu works, you can just tell the installer to reformat the HD.

If you want to do it manually, use Partition Editor from the LiveCD to plan your partitions.  A separate /home is useful for the future.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by tethys on 2008-05-22
well like was going on before and i jus put it in again...

it hangs on loading linux kernal, even though it is at 100%... maybe I'll try burning onto a different disc brand and at slower speeds... iunno, my dreamcast hates these magnavox cd's too

---

### Post by tethys on 2008-05-22
wow, just kinda died off dint it? ok, well im downloading the disc agan, since i obviously cannot get it off my compy, I'll burn it on a different brand disc and report back in prolly 6 hours

---

### Post by ugm6hr on 2008-05-22
Check md5 & burn at 2-4X: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

