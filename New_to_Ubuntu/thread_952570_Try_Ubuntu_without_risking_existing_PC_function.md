---
title: "Try Ubuntu without risking existing PC function"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by tymorg on 2008-10-19
HI-
      Not to jump in on a thread like this, but I thought this was the correct forum to ask in;

I am totally new to ubuntu, just heard of it a week ago and tried for 20 mins on a friends system.  I am NOT an IT guy, so need a real hand hold if possible.

 I downloaded Ubu from the official site, and now it is sitting on my desktop as a zip file.  I have not tried to load/run it.  I understand the best thing to do is partition my HD and work it with windows, trading back as needed.

 I have windows XP home, SP 3, with a celeron (R) 3.46 gig, and 960 MB RAM.  pretty simple system so I understand, and lots of disk space. I keep an external HD for backup.

 I have read some forums here saying use a partitioning program (G something) and put Ubu on after running that.

 I DO NOT want to foul things up, as I must use my system 24/7.

 Any educated response and advise would be greatly appreciated. A walk through even more so.

 Can I do this 'safely' without jeopardizing system use while I am loading/learning?

Thanks to any and all----

---

### Post by laurielegit on 2008-10-19
If you need your computer 24/7 then it is probably best to install it inside windows so you can get a feel for it.. just burn the iso file onto a blank cd and then insert it into your computer. Then choose the option to install inside windows. Ubuntu will be slower but not to dramatically, and you should be able to get a feel for it.

In future please post unrelated questions in a new thread.

EDIT: the G something is probably Gparted which lets you partition you HD.The ubuntu installer has a partitioner build in which is quite good enough if you are planning on installing ubuntu.

---

### Post by Idefix82 on 2008-10-19
> **tymorg said:**
> HI-
      Not to jump in on a thread like this, but I thought this was the correct forum to ask in;

I am totally new to ubuntu, just heard of it a week ago and tried for 20 mins on a friends system.  I am NOT an IT guy, so need a real hand hold if possible.

 I downloaded Ubu from the official site, and now it is sitting on my desktop as a zip file.  I have not tried to load/run it.  I understand the best thing to do is partition my HD and work it with windows, trading back as needed.

 I have windows XP home, SP 3, with a celeron (R) 3.46 gig, and 960 MB RAM.  pretty simple system so I understand, and lots of disk space. I keep an external HD for backup.

 I have read some forums here saying use a partitioning program (G something) and put Ubu on after running that.

 I DO NOT want to foul things up, as I must use my system 24/7.

 Any educated response and advise would be greatly appreciated. A walk through even more so.

 Can I do this 'safely' without jeopardizing system use while I am loading/learning?

Thanks to any and all----

Your questions are easily answered, but I suggest you open a separate thread if you want a real hand hold. Otherwise we will be cluttering someone else's thread before his problems are solved.

---

### Post by ugm6hr on 2008-10-19
> **Idefix82 said:**
> Your questions are easily answered, but I suggest you open a separate thread if you want a real hand hold. Otherwise we will be cluttering someone else's thread before his problems are solved.

New thread created.

Advice to OP:

Ubuntu is not a zip file - it is an ISO file.

Burn it to a CD (LiveCD).

Then you can boot directly from the CD (bypassing Windows), to try it out without making any changes on your HD.

GParted (Partition Editor) will do what you want it to, but repartitioning always carries a small risk of data corruption. Hence, there is no way for you to install Ubuntu onto your existing HD without a small amount of risk.

This is why everyone recommends backups.

> **laurielegit said:**
> If you need your computer 24/7 then it is probably best to install it inside windows so you can get a feel for it.. just burn the iso file onto a blank cd and then insert it into your computer. Then choose the option to install inside windows. Ubuntu will be slower but not to dramatically, and you should be able to get a feel for it.
I have never used Wubi to install Ubuntu within Windows, but they do boast their "Uninstall" feature, which is supposed to allow installation without risk.  However, Wubi installs can behave in an unusual fashion (judging by some people's experiences on here), which can prove difficult to resolve.

---

### Post by expatCM on 2008-10-19
This might get you going
[http://blog.protonic.com/blog/?p=295](http://blog.protonic.com/blog/?p=295)

---

### Post by ellalan on 2008-10-19
Hi
Burn the image and insert the disk and run within Windows(wubi).
This is what I am doing in my laptop,I have no issues,its fast,works like a dual boot. You do not need to change any Partitions and it won't hurt your set up. Try it and if you don't like it you can un- install it from Windows.

---

### Post by bodhi.zazen on 2008-10-19
First, you should not test anything on a mission critical system.

Second you can try Ubuntu by burning the iso to a CD and re-booting your computer to the CD drive. You may need to set your BIOS to boot from the CD before the hard drive.

Third wubi installs Ubuntu within windows, but it is not virtualization. To run Ubuntu after a wubi installation you still need to reboot your computer (and select Ubuntu from teh boot screen).

If you wish to run Ubuntu within Windows you need to look at something like VMWare or Virtualbox.

I suggest you back up your data look at (read) a few tings before you proceed with an installation , wubi or otherwise.

    [uhelp]community/Installation[/uhelp]

[http://wubi-installer.org/](http://wubi-installer.org/)

Although windows suggests the iso is a "zip file", it is not. You burn it to CD not extract it. You may need to download CD bruning software.

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by sethvath on 2008-10-19
Given a choice I would suggest you try out [http://wubi-installer.org/](http://wubi-installer.org/) rather than muck it out with partitions and installing ubuntu manually. Too much room for error even for an experienced linux user. 

Once you get the hang of linux in general, go ahead and repartition your hdd for a windows and ubuntu dual boot. Stick with Hardy Heron 8.04 for now and wait a few weeks for most of the bugs in 8.10 to be resolved.

---

### Post by aysiu on 2008-10-19
I would try installing it inside Windows as a virtual machine. 1 GB of RAM is plenty for this without seeing a huge performance hit:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

If you want an actual dual-boot without risking a repartition and possible (however small a possibility) data loss, first burn the .iso as a disk image (it is not a zip file or a rar file):
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Then follow the install-inside-Windows prompts:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by tymorg on 2008-10-20
Wow.  Thanks very much to all who replied.  And thanks for starting the new thread in the right way. 
  I am going to review what you all supplied and try to get a feel.  Then get back to you when I start the process.

Thanks again--

---

