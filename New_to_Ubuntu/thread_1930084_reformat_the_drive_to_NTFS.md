---
title: "reformat the drive to NTFS"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by jilli on 2012-02-23
Hello all!

I suspect you are going to hate this, perhaps even a lot, so forgive me.

My son has inherited a beautiful old system running Ubuntu from my house mate.

BUT. . . he wants to play Samarost, and use Photoshop and 123D, and design game levels. . . etc.

Since I am possibly the least programmy person in the world, I fear the solution is to install Windows.

I'm sorry!

My problem is that when I try to do so, my lovely system says no, your partitions are not NTFS.

So, my question to you, is how does the least programmy person in the world reformat the drive to NTFS in Ubuntu.

The box is not on the internet.

I have downloaded an iso image for Gnome Partition Editor, burned a disc of it, but apparently autorun is not installed / working on this box. So I extracted the files to the desktop, and here is sit.

Stuck.

Help? The young'un and I would really appreciate it.

Jilli

---

### Post by MG&amp;TL on 2012-02-23
No hate here. :)

There is two potential options (that I can see):

-Install Windows. You might be better off on a windows forum, and bear in mind it willl probably cost...a reasonable amount, shall we say. 

-Use Wine. Wine is a program that simulates the window environment, so some Windows programs will run in Ubuntu. However, it's not perfect, and you would do well to check the wine appdb here: [http://appdb.winehq.org/](http://appdb.winehq.org/) before investing in an expensive program like photoshop. Wine is in the Ubuntu repositories. 

If you mean by "designing game levels" programming, you can definitely do that on Ubuntu. 

Have a nice day!

PS Perhaps you can keep your son interested in Ubuntu for us? ;)

---

### Post by Gone fishing on 2012-02-23
If you want to delete Ubuntu you can simply remove the Linux partitions and then install Windows. Load up on the Ubuntu installation disk open gparted and then remove the partitions (you will loose all you’re your data). Then install Windows as normal.

You could consider installing Windows on part of the drive and Ubuntu on the rest this will allow you to duel boot the system.

---

### Post by Grenage on 2012-02-23
> **jilli said:**
> I'm sorry!

Unforgivable!

> **jilli said:**
> So, my question to you, is how does the least programmy person in the world reformat the drive to NTFS in Ubuntu.

I thought that there was an option to delete existing partitions during Windows installation.  I guess not!

> **jilli said:**
> I have downloaded an iso image for Gnome Partition Editor, burned a disc of it, but apparently autorun is not installed / working on this box. So I extracted the files to the desktop, and here is sit.

When you burned the disc, did you burn the the ISO as an image, or did you just burn the file onto a disc?  If the PC came with an Ubuntu CD, a copy of Gparted is on it when you boot it.

---

### Post by wyliecoyoteuk on 2012-02-23
A word of warning:
don't go spending lotds of money on software before you check it out.
If it is an old system, Windows may well disappoint him, especially if it is short on memory.
Just because it is nice and usable in Ubuntu does not mean that it will be in Windows.

---

### Post by jilli on 2012-02-23
I'm feeling the distinct lack of hate, guys, thank you all!

MG&TL: Thank you for the tip on Wine. I had considered it, but the "how to" frightened me into a corner (least programmy, remember). Thank you though.

Gone fishing: this sounds succinct and promising! We don't have the Ubuntu installation discs, but I'm looking up how to create some right now.

Grenage: you're quite right, I burned the iso like a file, not like an image. Looking into correcting that too. Would that program (Gnome Partition Editor) be the go for reformatting the hard drive if I can get it to work?

wyliecoyoteuk: Very good point, I hadn't thought of that. I do have the software already (graphics professional) but hadn't considered the RAM required by the young'un : RAM in the box ratio. He's asleep now, but I'll check in the morning.

Thank you all! I'm not out of the woods, but I do have a trail of crumbs to follow (actually two trails of crumbs, and some nice advice about crumbology). You rule!

Jilli

---

### Post by Grenage on 2012-02-23
> **jilli said:**
> Grenage: you're quite right, I burned the iso like a file, not like an image. Looking into correcting that too. Would that program (Gnome Partition Editor) be the go for reformatting the hard drive if I can get it to work?

Indeed, it should work fine.  I believe you can right-click on the ISO and burn as an image from that menu.

---

### Post by jilli on 2012-02-23
Fabulous! I'll try it tomorrow with the properly-created magic disc.

I send you all Samarost by way of thanks:

[http://amanita-design.net/games/samorost-1.html](http://amanita-design.net/games/samorost-1.html)

Good night!

---

### Post by Grenage on 2012-02-23
Lol, much obliged.  Rest assured I've already got it; a very good game!

---

### Post by nothingspecial on 2012-02-23
Hi, unprogrammy instructions to follow.

Download the latest Ubuntu cd from here

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

You will need to burn it to a cd or usb, the instructions on how to do this with Ubuntu, Windows or a Mac are in the previous link.

Then you need to boot the cd/usb. Restart the computer. Before it boots you should see something saying to press Esc or F12/F2 etc in order to enter your bios.

When you get there, find the boot menu or boot order or whatever it is called in your particular computer. Set it so that the first boot device is cd or usb depending which you chose earlier.

Then exit the bios. After a few minutes the live cd/usb should boot. Choose to "Try Ubuntu".

In the menu find the partition editor. Open it and from the drop down box at the top right, choose the internal hard drive of the computer.

Right click all the partitions and choose to delete them (there may only be one). Then select all the free space and choose to make a new ntfs partition.

[SIZE="2"]**[COLOR="Red"]THIS WILL COMPLETELY WIPE THE ENTIRE COMPUTER OF EVERYTHING[/COLOR]**[/SIZE]

Click the tick on the top bar to apply the changes then go and make a coffee and watch some tv.

When it's done you can shut down the computer and restart it with a windows installation disc. There shouldn't be any further problems installing windows.

You may want to think about this for a while if you have a perfectly good working Ubuntu. Once Windows is installed then you are going to have to mess about finding drivers and what not. It can be a long frustrating process.

Any way, good luck :)

---

### Post by Mark Phelps on 2012-02-23
If you simply can't get the reformatting to work with Linux apps, then download and burn the Partition Wizard Boot CD -- it's FREE, and is a Windows partitioning app.

---

### Post by jilli on 2012-03-01
Thank you all, your guidance worked like a charm and got me under the hood. 

You rule! Thank you so much!

Best,

Jilli

---

### Post by alfu on 2012-05-14
Photoshop?  Your son should try Gimp in Ubuntu first.  It is quite a respectable workalike.

I also tried installing Autodesk 123D under Wine, and it failed.  But I have Ubuntu 9.04, and upgrading to the latest version, which I plan to do, may fix that.

---

### Post by TheMTtakeover on 2012-05-14
I've only ever gone from Ubuntu to Win 8. My Win 8 installation told me the same thing but there was an advanced option setting during installation that gave me the option to erase all data on disk. I did that and it worked like a charm. Im not sure if other edition on Win give the same option or not

---

