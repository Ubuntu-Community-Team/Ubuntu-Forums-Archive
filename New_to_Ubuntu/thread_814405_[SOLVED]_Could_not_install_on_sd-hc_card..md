---
title: "[SOLVED] Could not install on sd-hc card."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by therock003 on 2008-05-31
Hi guys,so i'd like to install ubuntu on my sd-hc card in order to use it as a secondary OS on my asus eee umpc.

So i followed this guide up till the end,and still i didnt get it to work.

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

I did everything there,i got a working connection so it got to install the files from the wget command and such,so i dont know whats wrong.

I set the sd-hc as the primary hdd and primary boot device,but when i start the computer it doesn even get to boot,i got a flashing underscore and nothings happening.

What do you guess went wrong?

Also what is a persistent installation?

---

### Post by therock003 on 2008-06-01
So what could be wrong,how shall i handle this thing?

---

### Post by KenBW2 on 2008-06-01
When you first turn it on try pressing ESC, where a menu should show up listing all the media to boot from. Select your SD Card from there.

Let me know how it goes 'cos I want to do this on mine. 2GB just ain't enough :(

---

### Post by therock003 on 2008-06-01
Well i could not wait any longer so i tried the instal options from the ubuntu menu,and then did the install from cd procedure.Anyway either by changing boot priority,or by pressing escape and selecting the drive to boot,i get to a menu asking me what os to boot.

If i select any optio nat all i get a partition error.

Specifically i get an ero=ror 22 no partition defined.

Ok so how do i completely erase all contents and partitions from my sd card and then install properly the ubuntu distro?

PLZ i dont want any trouble,i just want to boot ubuntu!

---

### Post by KenBW2 on 2008-06-01
<out of interest>
Can I ask how you're running the CD? Are you using an external CD drive?
</out of interest.

It may not be too late to rescue your installation. Load up Ubuntu from LiveCD and look in System > Administration > Partition Editor
If there's a semi-full partition on there you're good, and the problem is with /boot/grub/menu.lst

Is this the case?

---

### Post by therock003 on 2008-06-01
Yes of course i'm running from external.The asus eee doesnt have any internal drives.

I will check the paritioning info you provided me and will report right back.

---

### Post by therock003 on 2008-06-01
Ok i did and some weird stuff are happening.

Theres an sdb1 partition type unknow and then an sdb2  "linux swap" and an sdb3 extended that expands to sd5 ext3 and an sdb6 linux swap!

---

### Post by KenBW2 on 2008-06-01
I was wondering about the CD drive since it might've been that you were using a bootable USB drive like I did.

Anyway

So your drive looks something like this?:

|     sdb1     | sdb2 ||    sdb5    | sdb6 ||
|     unknown  | swap ||    ext3    | swap ||


That IS weird. Are you bothered about wiping your installation?

---

### Post by therock003 on 2008-06-01
Well i'm new to linux,how can i remove all files and partitions and se it up as new again so i can try from scratch.

---

### Post by KenBW2 on 2008-06-01
Right, this is the way I've always done it, although it might not be the easiest way.

In GParted:
1) Delete every partition, click Apply
2) Create 1 ext3 partition, leaving:
|--a) If you want to keep data on its own partition, 4GB
|--b) If not, all except for 1GB
3) Create a 1GB linux-swap partition
4) [optional] If you wanted data on its own partition, make an ext3 partition filling the rest of the card
5) Click Apply

6) Install Ubuntu normally. At the partitioning stage select the manual option
7) Set:
|--the 1st partition as /
|--the swap as swap
|--if you created a data partition, set that as /home
8) Install


Let me know if that works :)

---

### Post by therock003 on 2008-06-01
Pk so i created a second with free space after 1024 mb (1 gb as you told me),applies all the changes and going for the install.Shall i do it from inside the live,or reset and select the option before it boots?

---

### Post by therock003 on 2008-06-01
Well i tried to install from within,and when the moment came i chose guided with resing and it gave me an error while writing the changes.

---

### Post by KenBW2 on 2008-06-02
What error does it give you? And what application gives you the error?

I think you might have misunderstood what I meant with the partitioning, so I've attached screenshots of the key parts. Please download the screenshots and apply to your eeepc what I've shown in them, using the following instructions. **All of the following instructions should be performed while running from the LiveCD**

**Image *1 - GParted.png***
Open System > Administration > Partition Editor and select your SD Card
Set up your SD Card like this
All but 1GB as ext3
The other 1GB as linux-swp

**Image *2 - Manual.png***
Run the installation.
At the Prepare disk space screen select Manual, **not** Guided and click Forward

**Image *3 - Partitions.png***
The partitions should be set up as shown on the screenshot:
Only deal with /dev/sdb (sda will take care of itself)
The ext3 partition should be set to: "Use as: ext3; Mountpoint: /"
The linux-swap partition should be set to: "Use as: swap; {No mountpoint}"
Make sure to set the ext3 partition to be formatted

Proceed with installation

NB: This is a standard installation method, but on the SD Card instead of the built-in hard drive. It **might** cause problems with the boot menu (grub) as to where the OS is located, but I don't know.
If Grub doesn't function properly, you can try pressing ESC as soon as you turn your eeepc on and selecting your SD Card.

Let me know if you need any more help, or if you succeed :)

---

### Post by therock003 on 2008-06-03
Thanx a lot for your help,my friend,i was finally able to install ubuntu.

Now that i can boot though i cant see the partition editor.Is it a live only option?

---

### Post by KenBW2 on 2008-06-03
Yes, Partition Editor is uninstalled as, theoretically, you don't need it once it's installed. You can easily reinstall it by:

GUI:
Applications > Add/Remove... > Partition Editor
Or in Terminal:
sudo aptitude install gparted

I was thinking of doing the same on my eeepc as well. Can I benefit from your experience by asking:
- Did you follow the instructions exactly or were there adaptations you needed to make?
- Do Hibernate and Suspend work?
- Do you have to press ESC every time you boot?
-- If so, amybe that can be changed in the BIOS settings
- Anything else you think is worth mentioning?

I'm glad I could help. I'm by no means an expert on Ubuntu, but I've been using it for about 7 months, and I'm just dispensing what I do know :)
If you could let me know how it works with those points I'd be very appreciative :)

---

### Post by therock003 on 2008-06-04
Actually i messed the partition management the first time,cause i forgot to switch to the sd and i mistakenly deleted and created partitions for the internal disk.

So i decided to install on the disk instead of the sd...

Other than that.
-Suspend works,hibernate does not.

Recover from suspension occurs by pressing the power button.At least on my eee pressing keyboard keys and mouse controls didnt wake it up.Not on ubuntu and not on Xandros either.

Hibernate gave me a couple of error messages and seems like it shut the computer down.

If you decide to install on a card,then i advise you to go into the bios and the hdd tab set the card as primar hdd,instead ssd and there will be no need to press esc.

Other than that i like the ubuntu envirinment so far,but it takes too long to boot!

I get all the unix like commands loading before the gui loads up,and it takes way more than a minute,maybe even more than 2,and so far this is what i dont like.

---

### Post by KenBW2 on 2008-06-04
Oh, so you didn't do it on SD card. Oh well.

Yea, Xandros has a rediculously fast boot time; I don't know how. But in the end you get used to it and it's well worth it.

Could you mark the thread as Solved (Thread Tools > Mark thread as solved), and if you're feeling generous, could you put Thanks on the post you found helpful :D It's the little badge with a star on it on the bottom-right corner of the post

Thanks, and glad I could help

---

### Post by therock003 on 2008-06-04
Well i wanted to install on sd,so i can have xandros as my primary fast booting OS and ubuntu as my OS of  choice,but since i erased partitions on the ssd,i thought what they hey,lets install on the disk.

Other than that,the SD card still is kind of corrupted.I get a **lost+found** folder when i brwse and i cannot delete this folder.How can i format the card as new,with no partitions?

Also what filesystem shall i format it into?Does it support ntfs?Or will i have to go fat32 necessarily?

---

### Post by KenBW2 on 2008-06-04
If I remember rightly you get the Xandros CD with the eee, so you *should* be able to install it again.

"the SD card still is kind of corrupted". In what way? Yea, I get that lost+found folder - dunno what it's for. *Googles*
> 
Every partition has a lost+found in its upper directory. Files that were saved during failures are here.
[http://www.faqs.org/docs/linux_intro/sect_03_01.html](http://www.faqs.org/docs/linux_intro/sect_03_01.html)

You can format the card using Partition Editor. Open it up, select your SD card and right-click > Delete all the partitions (remember to back it up). Click Apply.

As to what format it into:
FAT32: Universally accepted (Linux *and* Windows)
NTFS: Not really - that's a Windows format (although Ubuntu does support it), but I don't think it's for SD cards
Ext3: If you're going to install a Linux OS on it, although FAT32 can do this.

Anything else, just ask :)

**EDIT:** I've sent you a private message - it'll show up in User CP at the top of the page

---

