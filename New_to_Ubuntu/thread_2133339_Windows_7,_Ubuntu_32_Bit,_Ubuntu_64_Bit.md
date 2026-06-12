---
title: "Windows 7, Ubuntu 32 Bit, Ubuntu 64 Bit"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Glkanter on 2013-04-07
Just got this refurbuished machine. 64 bit, 1 TB HD. Pre-loaded with Windows 7.

I installed 32 bit Ubuntu 12.04 using the recommended disk partioning, for a dual boot setup.

Then it *finally* dawns on me I just bought a 64 bit machine.

When I tried to install 64 bit Ubuntu 12.04, it did *not* offer to repartion the drive for me. Just "erase all" and "configure the darn thing yourself" more-or-less.

Well, I have *no* idea what's what with all that stuff.

Any ideas?

Thanks!

---

### Post by hayden92 on 2013-04-07
Hi Glkanter,

Have you tried using (not installing) Ubuntu from the liveCD and partitioning the hard drive with Gparted? You should then be able to select that partition for installation during the 64 bit install process.

---

### Post by Glkanter on 2013-04-07
I have not tried that.

Will Gparted prompt me with a viable partition arrangement?

---

### Post by Bashing-om on 2013-04-07
Glkanter;
My memory may be a bit hazy, but does not the installer advise you of what is installed and give you the option to install over one of them ?? Like over the 32 bit install; I can not imagine a reason to keep the 32 bit install.

GParted: Yes there is both a graphical display of the partitioning scheme as well as in the editor it's self,  a textural list. GParted is available from the liveCD, One may look at the disk(s),read the documentation, delete the ubuntu 32 bit install partition(s), re-write the partition table and exit GParted back to the desktop and then click the install icon to install the 64 bit system.
[INDENT=3]
hope this helps

[/INDENT]

---

### Post by Glkanter on 2013-04-07
The cd installer only offered to erarse the whole thing, or let me configure it. It did not propose any solutions.

I goofed. I can live with it. I just don't have the experience to monkey around with Linux partions via either the installer or Gparted.

Thanks guys!

---

### Post by Bashing-om on 2013-04-07
Glkanter;
Long as things look bright.
we are here to help, just a question away --and await a response.[INDENT=3]
happy ubuntu'n

[/INDENT]

---

### Post by UltimateCat on 2013-04-08
Hi:

> It did not propose any solutions.

That's odd--

You could shrink the Win's 7 parition first before the Ubuntu install-
Make sure you write those partitions down so that when the Ubuntu partition manager shows you all of the partitions you know which partitions not to bother. 

If it were me I would download the ISO Image of Ubuntu for X86_64bit architecture.
Put in the new Ubuntu install and when it comes time to partition choose 'manual'
Delete the 32bit Ubuntu install partition (journaling file system)  that you already created.
Delete the 32bit Ubuntu install swap that you made.

Now take advantage of that free space from the old partitions that you just deleted and create new partitions.
-Highlight the free space
-Create a new partition (make your (/) ext 3 journaling file system 20GB
-Create another new partition (make your swap space ....2GB
Done, finish and write to disk--

As an example here is what I recently did for a dual boot with Win's 7 and Fedora:
```
dev/sda1* Windows 7 Home premium NTFS
dev/sda1 Windows 7 Recovery  NTFS
dev/sda/ 5 / boot ext 3 20GB for Fedora
dev/sda 6 swap ext3 2GB
dev/sda 7 home  ext3 2GB
dev/sda 8 root ext4 2GB

```
The only reason I made 2 additional partitions is because the Fedora documentation recommends it-

Hope this helps-:KS

---

### Post by Glkanter on 2013-04-08
**If it were me I would download the ISO Image of Ubuntu for X86_64bit architecture.**[INDENT]Done.
[/INDENT]
 **Put in the new Ubuntu install and when it comes time to partition choose 'manual'**[INDENT]Yes.
[/INDENT]
 **Delete the 32bit Ubuntu install partition (journaling file system)  that you already created.**[INDENT]I'll copy any of my files onto a usb drive, first.
[/INDENT]
 **Delete the 32bit Ubuntu install swap that you made.**[INDENT]Yes.
[/INDENT]
 
Now take advantage of that free space from the old partitions that you just deleted and create new partitions.
-Highlight the free space
**-Create a new partition (make your (/) ext 3 journaling file system 20GB**[INDENT]I have a 1 TB HD. About 500 GB belongs to Ubuntu, the other 500 GB belongs to Windows.
[/INDENT]
 **-Create another new partition (make your swap space ....2GB**[INDENT]This will only account for 22 GB of the 500 GB available. Is there an implied step, that I am missing?
[/INDENT]
 **Done, finish and write to disk--**[INDENT]That would be great...
[/INDENT]

I will wait to hear back from you before proceeding. Thanks!

---

### Post by fantab on 2013-04-08
> **UltimateCat said:**
> If it were me I would download the ISO Image of Ubuntu for X86_64bit architecture.
Put in the new Ubuntu install and when it comes time to partition choose 'manual'
Delete the 32bit Ubuntu install partition (journaling file system)  that you already created.
Delete the 32bit Ubuntu install swap that you made.

AFAIK SWAP is not architecture dependent (correct me if I am wrong). Earlier SWAP size used to depend on the architecture but not any more. No need to delete it. If in doubt you can re-format it.

In fact no need to delete anyting. Just boot you Ubuntu_64 LiveDVD/USB and Install. When you reach the screen where you are offered install on HDD options choose "**Something Else**" to point the installation to the partition where you installed Ubuntu_32 and just format it using ext4 filesystem. Then continue.

Make sure Grub is being installed to /dev/sda ONLY and not on partition like, /dev/sda1 or /dev/sda2 and so on.

---

### Post by 3rdalbum on 2013-04-08
As Fantab said: Choose the "Something Else" option in the Ubuntu installer and select your existing Ubuntu partition. Click Edit (I think... or Properties or something like that) and set the mount point to /

Then click Ok and then Install. It's that easy!

I'm assuming you didn't set up a separate /home when you first installed Ubuntu - doesn't sound like you did as that would have required using the Something Else option too.

---

### Post by Glkanter on 2013-04-08
This new advice is much more in line with my skill set.

Here's what Gparted reports:


[IMG]http://img254.imageshack.us/img254/4140/cam00012f.jpg[/IMG]

Am I OK with the sda vs sda1 issue?

Thanks, as always, for everything guys!

Garry

---

### Post by fantab on 2013-04-08
/dev/sda means the HDD device, while /dev/sda1 means the first Partition on /dev/sda, like wise /dev/sda3 means third partition on /dev/sda and so on. Grub should be installed on /dev/sda (Device) Only. You will be formatting /dev/sda5 (fifth partition on /dev/sda) with ext4 filesystem and installing Ubuntu_64 on it with "/" mountpoint. That is all you need to do.

/dev/sdb means the Second HDD device and on it the partitions will be /dev/sdb1, /dev/sdb2 and so on. Since your /dev/sdb is USB drive, there aren't any partitions on it. It is a simple partition.

---

### Post by Glkanter on 2013-04-08
Wish me luck!!!!

---

### Post by Glkanter on 2013-04-08
Well, that's what I get.

So, when I began the 64-bit install the 2nd time, I *was* prompted by the installer with a proposed reformatting of about half of the Ubuntu partition.

And, since that was what I had wanted at the outset, I accepted it. I mean, it's a 1 TB drive. I'd have 250 GB available, and I'd have all three boots (Windows, 32, 64) to choose from, right?

Well, the install appeared to go flawlessly.

But the boot-up menu program only offers one Ubuntu choice, plus "older versions".

And both choices brought up the 32 bit version.

Which isn't the end of the world.

Should I start a new thread with my new problem? Or should I just go away? LOL, I hope.

Thanks!

Garry

---

### Post by oldfred on 2013-04-08
You may have installed new version but new versions grub did not get correctly installed?

Best to see all the details now. You can just  add this to your existing installer, then run the BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Glkanter on 2013-04-08
.

---

### Post by Glkanter on 2013-04-08
Yes, you may described what may have happened correctly.

Beyond that, I am unable to understand what it is you are suggesting.

I'm just not that familiar with any of the terms or concepts you posted.

Thank you,

Garry

---

### Post by oldfred on 2013-04-08
You just need to follow the directions on installing & running Boot-Repair to get a BootInfo report. See first link in previous post for details. Has screen shots so you should easily be able to follow it.

In any working Linux or Live installer you install Boot-Repair using the terminal, copy & paste is easiest way to run these commands:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```
Depending on which Desktop you have launch Boot-Repair.
And run the BootInfo report. It scans system and creates a large report.
Post link it gives you so we can see report.

---

### Post by fantab on 2013-04-08
> **Glkanter said:**
> ... I *was* prompted by the installer with a proposed reformatting of about half of the Ubuntu partition.

And, since that was what I had wanted at the outset, I accepted it. I mean, it's a 1 TB drive. I'd have 250 GB available, and I'd have all three boots (Windows, 32, 64) to choose from, right?

Well, the install appeared to go flawlessly.

Do you mean to say that you have both Ubuntu-32 and Ubuntu-64? And that you are booting into Ubuntu32?

If YES, then boot into 32bit Ubuntu and run [copy/paste + enter] from Terminal:

```
sudo update-grub
```

Restart and see if Ubuntu64 is shown in the Grub Menu.

I suspect that the Installer did not intstall GRUB... so it could be that you still have GRUB from your 32bit install. Just try the above and see if it helps. If it doesn't then BOOTINFO SCRIPT, as adviced earlier, is what we need.

Good Luck.

---

### Post by TheMTtakeover on 2013-04-08
> **Glkanter said:**
> Just got this refurbuished machine. 64 bit, 1 TB HD. Pre-loaded with Windows 7.

I installed 32 bit Ubuntu 12.04 using the recommended disk partioning, for a dual boot setup.

Then it *finally* dawns on me I just bought a 64 bit machine.

When I tried to install 64 bit Ubuntu 12.04, it did *not* offer to repartion the drive for me. Just "erase all" and "configure the darn thing yourself" more-or-less.

Well, I have *no* idea what's what with all that stuff.

Any ideas?

Thanks!

Can you choose to set it up manually and then just write over your 32-bit partition?

---

### Post by Glkanter on 2013-04-08
Updating Grub did the trick!

As *always*, you guys are the best!!

I can't thank everybody enough.

Garry

---

### Post by UltimateCat on 2013-04-09
> This will only account for 22 GB of the 500 GB available. Is there an implied step, that I am missing?

No, your not missing any step-
Ubuntu doesn't need much more room than that -

As I said you can make more partitions if you want but that's entirely up to you.
Some folks make a additional partition for Home but I don't think it's a requirement.
Check in the Ubuntu Documentation to be sure if it is suggested.;)

Unless you want Ubuntu to take up the entire drive:-

---

### Post by gnugen on 2013-04-10
If it does not give you the boot alongside option, do not go ahead with the install. Something could have happened to your hard disk when you dual-booted Ubuntu 32-bit and Windows 7. However, this may not necessarily be the issue.

---

### Post by Glkanter on 2013-04-10
I'll mark this as "Closed", if someone can help me find that button.

I've looked for it three times.

---

### Post by mansonfan78 on 2013-04-10
At the top of the page, just below the page number selections, there are three drop down menus:  the first one "thread tools" should have an option to mark as solved (this should only appear to the person who started the thread).

---

### Post by Bashing-om on 2013-04-10
Glkanter; Hey again.
Due to the recent upgrade to the forum there are a few things yet to work out, and the "solved" button is one of those issues.
The interim method to mark as "solved":
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=2]
read you later 
[/INDENT]

---

### Post by Glkanter on 2013-04-10
Thanks!

It's so intuitive! LOL

---

