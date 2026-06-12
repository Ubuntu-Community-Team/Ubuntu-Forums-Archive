---
title: "A truly unique Ubuntu/Vista/GRUB problem..."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by RCtennis3811 on 2008-05-20
OK, I have been searching the web through Google since midnight looking for a solution to my problem.  Sadly, I haven't found one yet so I've decided to post here.

I have a Sony VAIO VGN-N110G laptop that had Windows XP Media Center pre-installed, but now has Windows Vista Home Premium thanks to the "VAIO Vista Express Upgrade Program" where Sony sent me an upgrade disk when Vista was released.

Despite having Vista, I recently experimented with Ubuntu 8.04 Hardy.  While cool, I have decided to uninstall Ubuntu since it doesn't work with my school's wireless network.  So I had been reading about how to uninstall GRUB and wrote everything down.  However despite having a Windows Vista disk, I cannot access the "fixmbr" stuff.  Rather when I turn on my computer, it recognizes the CD and begins whirring while the screen pauses, then the whirring stops and GRUB starts.  I even tried entering BIOS settings and put CD to load first and HD to load last, but still the same happens.  So here's question #1:

**Is there a way to force my laptop to launch from the Vista CD before GRUB starts, or is there a way to use the command line in GRUB to read the Vista CD?**

Well after that happened, my friend tried to see if he could fix things.  Let's just say he made it worse... :(

On my GRUB menu, I have the option of loading Ubuntu 8.04, Ubuntu memtest; under "other operating systems" I have Windows 2000/XP, and then Windows Vista/Longhorn (loader), the latter of which loads my Vista perfectly.  However, my friend tried the Windows 2000/XP option and accidentally began to clear my C: drive to reinstall XP.  Apparently, there is a partition on my hard drive that came with the VAIO that has XP in case I needed to roll back to it.  Well, my laptop was "restoring back to C" for about 10 seconds before he unplugged the battery to prevent further loss of personal data such as documents and pictures.  However, everytime I try to select Windows Vista/Longhorn in GRUB, I get an ERROR 17.  Here's question #2:

**Can I still recover my documents and photos from Vista, and is there a way to do that through Ubuntu?**

Now I've heard of a FixMBR program that works through Vista, but now I CAN'T ENTER VISTA!!  Is there another way to FixMBR through Ubuntu other than the ms-sys program, which my terminal doesn't recognize...???

PLEASE PLEASE PLEASE HELP!!!

---

### Post by tamoneya on 2008-05-20
at this point i dont really think it worth it to continue messing with MBR and bootloaders since it seems messed up beyond comprehension.  Instead I would just go about recovering stuff and preparing to reinstall vista.

For file recovery programs the best thing is called test disk.  One of the first things that probably happened when the C:/ drive was being erased was that the partition headers and the Master file table got messed with.  Test disk doesnt look at these like normal programs.  Instead it just looks through the disk for anything that looks like a file.  Then once it finds your files I would copy them onto an external drive of some sort and then install vista from scratch.  

Test disk can be found on the Recovery is Possible LiveCD: [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

---

### Post by RCtennis3811 on 2008-05-20
> **tamoneya said:**
> at this point i dont really think it worth it to continue messing with MBR and bootloaders since it seems messed up beyond comprehension.  Instead I would just go about recovering stuff and preparing to reinstall vista.

For file recovery programs the best thing is called test disk.  One of the first things that probably happened when the C:/ drive was being erased was that the partition headers and the Master file table got messed with.  Test disk doesnt look at these like normal programs.  Instead it just looks through the disk for anything that looks like a file.  Then once it finds your files I would copy them onto an external drive of some sort and then install vista from scratch.  

Test disk can be found on the Recovery is Possible LiveCD: [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

I'm perfectly fine with doing a clean install to Vista or XP...I just want my files back! :)

Anyways, I clicked on that link you provided and I'm completely lost.  Which file should I download, and how does it work?? :confused:  Sorry, but I'm way too new at this.

---

### Post by HotShotDJ on 2008-05-20
> **tamoneya said:**
> Instead I would just go about recovering stuff and preparing to reinstall vista.Back in the day, after walking up hill both ways to school in the snow, we used to pop in the Windows install CD, select the DOS option, and then type something like fdisk /mbr 

Of course, I only used Windows for a few years, and the last version I used other than incidentally was Windows 2000. Is this not possible with the Vista cd?

---

### Post by phoenix_abhi on 2008-05-20
BOoT 2 UR RECOVERY CD OR PARTITIN DRIVE. AFTER BOOTING (CD INSERTED) GO TO RECOVERY CONSOLE TYPE
bootrec /fixmbr
bootrec /fixboot

how to retore grub

boot pc with live cd(ubuntu) inserted
in the terminal sudo grub
find /boot/grub/stage1
this will show which is the linux partition
now follow this comand
grub> root (hd0,1)    here hd0 is ur no of hard disk where ubuntu installed. if u have only one hd then it is 0 and the fig 1 is the linux partition of ur pc
grub> setup (hd0)
grub> quit

reboot. select the OS from Grub. Backup the data frm vista. Reinstall vista. After installing vista through manage>diskmanagement>delete the linux partition. forget about grub after that

---

### Post by tamoneya on 2008-05-20
> **RCtennis3811 said:**
> I'm perfectly fine with doing a clean install to Vista or XP...I just want my files back! :)

Anyways, I clicked on that link you provided and I'm completely lost.  Which file should I download, and how does it work?? :confused:  Sorry, but I'm way too new at this.

download the first one: [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/RIPLinuX-5.5.iso](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/RIPLinuX-5.5.iso)
Then just burn the ISO file like you did with the ubuntu CD.

---

### Post by RCtennis3811 on 2008-05-20
> **tamoneya said:**
> download the first one: [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/RIPLinuX-5.5.iso](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/RIPLinuX-5.5.iso)
Then just burn the ISO file like you did with the ubuntu CD.


LOL yeah I did that.  After I restarted, the program started...but I have no idea where to go from there.  I tried the HELP menu, but nothing popped up...

---

### Post by tamoneya on 2008-05-21
if you look through the menus on the lower left there should be a program called test disc install.  You need to tell test disk to scan drives for lost partitions / files.  I dont know the exact location or wording since I luckily havent used it recently.

---

