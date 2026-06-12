---
title: "Install - Can't continue or reconfigure"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by Yippee38 on 2014-08-09
Hi all.  I'm a long time OpenSUSE user.  I'm having a problem on OpenSUSE that I've been unable to resolve, so I decided to test Ubuntu.  I'm installing Ubuntu Desktop 14.04.1 LTS on a single hard drive that already has data on it, but it is junk.  When I run the installer, I select my language then I get to a screen that says, "For best results, please ensure that this computer:"  It has two boxes that have an "X" next to them.  One is "has at least 6.5Gb available disk space" and one is "is connected to the internet".

The problem is that the Continue button is greyed out.  My only options are to go Back or Quit.  I cannot click on either of the two entries.

As I said above, the drive has data on it, but it's junk. I want to reformat and thought that the installer would give me the option to do so.  I'm also using a wired network with a static IP, but I cannot find anything about how to change the installer to use a static IP address.

Can anybody tell me how to configure the installer to let me change these things and successfully install Ubuntu?

---

### Post by Jonathan Precise on 2014-08-09
Hello Yippee38. Welcome to the forums!

How many GB of HDD space does it have? In other words, how many GB of data do you have? If you have more than 7 GB, then hit the back button, and hit the next button to return to the same screen. This is an intermittent problem on some machines.

If it still is grayed out, post the results of:

```
parted -l
```

to give us more info about the HDD space ubuntu is detecting.

Hope it's of help! :)

---

### Post by Yippee38 on 2014-08-09
> **Jonathan Precise said:**
> Hello Yippee38. Welcome to the forums!

How many GB of HDD space does it have? In other words, how many GB of data do you have? If you have more than 7 GB, then hit the back button, and hit the next button to return to the same screen. This is an intermittent problem on some machines.

If it still is grayed out, post the results of:

```
parted -l
```

to give us more info about the HDD space ubuntu is detecting.

Hope it's of help! :)

I have no idea how much free space is on the drive.  I had previously installed Mageia linux on it, but decided not to use that.  I don't know how much space it took up.  I will find out, but......

....Does the installer NOT have any functionality for partitioning and formatting the hard drive before install?  Even Windows has that.

BTW, I found the Network Config options.

---

### Post by Jonathan Precise on 2014-08-09
Not free space, but how much drive **capacity** does it have.

Please press Ctrl. Alt. and T at the same time. Let go immediately, and you'll see a terminal. Copy this code and paste it into the terminal:

```
sudo -i parted -l
```

Copy the results from the terminal and paste them here under [NOPARSE]```
Code Tags
```[/NOPARSE] :
```
Code tags
```

---

### Post by Yippee38 on 2014-08-09
Thanks for the info on the Ctrl+Alt+T.  I didn't know that.  I ended up using the Mageia install disk to run parted because I couldn't figure out how to get to a terminal window in the Ubuntu installer.  Anyway, it wasn't giving me any info, so I tried fdisk.  That wasn't giving me any info either.

That's when I realized that I had made a stupid user mistake.  I had the wrong SATA cable plugged into the hard drive.  That's why Ubuntu was saying there wasn't enough disk space.  I connected the correct cable.  All is good now.

Thanks for telling me to do parted -l.  That was the brick upside the head I needed to figure it out.  ;)

---

### Post by Jonathan Precise on 2014-08-09
Sure, no problem!

Hey, can you do us all a favor and mark this thread as solved, so people can know that you problem was solved.

---

### Post by grahammechanical on 2014-08-09
> [COLOR=#000000]Does the installer NOT have any functionality for partitioning and formatting the hard drive before install? Even Windows has that.[/COLOR]

Yes it does but you are not getting that far. This is what you can expect to see but you have not got to the Installation Type page

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Does the live session load to a desktop? The live session has Gparted that will show you the partitions on the hard disk. You should not need to reformat or resize partitions. That should all be taken care of if we select Erase disk and install Ubuntu.

The Live session also has Disks, a utility that will also show you disk partitioning. It will format that disk for you. Select Ext4. If you wish to do that.

At the Installation Type page if we select Something Else we can select which specific partition we want Ubuntu to be installed in. Yes, I know you have to get to that page.

There are three ways we can start the Ubuntu installer.

1) Let the live session load until we arr offered the option to Try or Install. We can select Install to start the installer

2) We can select Try and load to the live session desktop and launch the installer by click the Install Ubuntu icon on the desktop.

3) At the first purple screen press Enter. Then select the language (Default English). Then select Install.

All these methods should work but sometimes one or two methods will work but the third will not.

Regards.

---

### Post by Jonathan Precise on 2014-08-09
@grahammechanical: The OP said that the problem was fixed because he plugged in the wrong SATA cable.

---

### Post by grahammechanical on 2014-08-09
I saw that after I sent some time typing my post and working out what to write and thinking about what was causing the problem. I do not know about you but I cannot read new posts at the same time as I am writing a post to put in the thread. Still it all notches up the bean count.

---

### Post by Yippee38 on 2014-08-09
Sorry to make you do all that typing for nothing grahammechanical.  :(

---

### Post by Jonathan Precise on 2014-08-09
grahammechanical: Oh. I thought skipped over the post. Sorry.

True though. It increases bean count.

---

### Post by coffeecat on 2014-08-09
@Yippee38, I don't think grahammechanical did do all that typing for nothing. He told you some useful things about the Ubuntu live session that perhaps you were not aware of. For example, that you can access gparted if you boot into the live desktop rather than straight into the installer.

Good luck!

---

