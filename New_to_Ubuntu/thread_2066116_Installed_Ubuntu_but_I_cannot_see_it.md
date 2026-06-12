---
title: "Installed Ubuntu but I cannot see it??????????"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by gertcher on 2012-10-03
I have just installed Ubuntu, at least I though I had.

I installed it along side Win 7, the whole process went very smoothly, it finished without a hitch. I took the ISO disc out 

Restarted. There was a message about checking the hard drive for something and it would take some time.  Lots of messages and progress reports and numbers roll past.

That finished.  Booted to Win 7.

That's it. No Ubuntu. Cannot see any sign of Ubuntu in Win 7. Cannot boot to Ubuntu from cold.  Reinserted ISO disc and it started the install again, canceled that and it reverted to running Ubuntu from the disc.

Any idea what's up?

Greg

---

### Post by oldfred on 2012-10-03
Do you have more than one drive?

This will give us details of what is where. Post link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by gertcher on 2012-10-03
> **oldfred said:**
> Do you have more than one drive? Just the single hard disc drive. This is a new laptop with Win 7 32 bit.  The hard drive has only the original setup programs.

Could the report about hard drive checking after the Ubuntu install have anything to do with it? Could it have wiped the install. The check looked very much like a hard drive formatting  procedure, although the Win 7 install remains exactly as it was before the Ubuntu install.

I will do the check you suggest, but cannot do it for another 17 hours or more

Thanks  Greg

---

### Post by AndyOpie150 on 2012-10-03
What method did you use to install? What type of .iso did you use, the standard or live .iso? Are you sure you didn't use the live .iso and then not really install it (the live .iso allows you to test drive it without really installing it if you don't want to).

Download a Disk partitioning tool like Mini Tool Partitioning Wizard. When you open it up it will list all the partitions on your hard drive. If you don't see the Ubuntu partition and the small swap partition, then you didn't actually install it.

Note: The boot repair that is linked to in oldfred's signature should be standard issue to any one that changes the partitions on the hard drive, especially new linux user's like us (saved my bacon, it surely did). All it took was a CD to burn the .iso to.

---

### Post by gertcher on 2012-10-03
> **AndyOpie150 said:**
> What method did you use to install? What type of .iso did you use, the standard or live .iso?I was using Google so had to download the file and burn it to a CD, which is what I did. Turned off the comp, inserted the ISO CD, turn on and it loaded and went through the install along side the Win 7, must have taken 20 minutes to complete.  I had no reason to think it had not installed, it even offered me to resize the partition.

The only thing I thought was out of the ordinary was the hard disc check at the end, I cannot remember exactly what it was for just assumed it was part of the install

---

### Post by tackyjan on 2012-10-03
> **gertcher said:**
> I was using Google so had to download the file and burn it to a CD, which is what I did. Turned off the comp, inserted the ISO CD, turn on and it loaded and went through the install along side the Win 7, must have taken 20 minutes to complete.  I had no reason to think it had not installed, it even offered me to resize the partition.

The only thing I thought was out of the ordinary was the hard disc check at the end, I cannot remember exactly what it was for just assumed it was part of the install

In my opinion the easiest and the best way to install Ubuntu on a pre-existing Windows 7 box is to use the official installer. All you have to do is startup Windows 7, run the installer (which looks and acts like any other application installer), then reboot. When you reboot you will get a menu option to select either Windows or Ubuntu. Here is a link to the installer:

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

If you are going to try re-installing using the official installer I suggest you wipe out the partition you had made for your first attempt, then let the installer do the rest. (Be careful when you delete a partition though!)

Jan

---

### Post by gertcher on 2012-10-03
I have attached a pic of the Win 7 computer manager. You can see there was an attempt to install. The 10GB and 512GB are the Win 7 partitions. The other partitions I assume are failed Ubuntu partitions.

Before I go any further I will need to merge the partition bits in to one of the other partitions, then I will try a different install.

Thanks to all the participants so far

Greg

---

### Post by oldfred on 2012-10-03
Only use Windows partition tools to shrink NTFS Windows partition. Do not create partitions as it may convert to dynamic and that does not work with Linux nor with some Windows repair tools.

Better to post info from Ubuntu liveCD, BootInfo report, screenshots from gparted etc.

---

### Post by Wim Sturkenboom on 2012-10-04
> 
Before I go any further I will need to merge the partition bits in to one of the other partitions ...

You don't have to merge them.

I guess you have an UEFI bios as the symptoms look like what I experienced a little while ago; there are a couple of threads that will give solutions, and it's my understanding that the boot-repair utility mentioned in post #2 can solve the issue.

---

### Post by NikTh on 2012-10-04
Hi , 

just give the results of boot-info script. Run boot-repair as suggested and give the link with the results here. This will help us to see what the problem is and hopefully solved.

Thanks

---

### Post by gertcher on 2012-10-04
I have just been reading someone else's thread about very similar problems to my self, see [here]("http://ubuntuforums.org/showthread.php?p=12277348&posted=1#post12277348"). It is worth reading my input there because it explains why I am not perusing any corrections to my failed install at this time.  

I am a supporter of Ubuntu and everything Linux, but I am not an enthusiast.  At my current understanding of the OS I just want it to work without having to learn why it goes wrong, sorry just don't have the time

Thanks to everyone for all your help.  I will be back but it will have to wait until the current beta is a full distro 

By for now

Greg

---

### Post by gertcher on 2012-10-12
Hi everyone

Thought I would give you an update

I started this thread with a problem sharing Ubuntu after loading with Win 7. I could not get Ubuntu to show. After much fluffing about with partitions; that eventually screwed up Win 7 so it too would not load, not even the recovery.  I took the plunge and installed Ubuntu as the only OS.

With only the minimum of user interaction the whole install process went very smoothly; I managed to carry on with the kitchen tiling without a 2nd glance.  I even installed the drivers for 2 wireless Lazar printers without the need of the discs .

This is my 3rd install of Ubuntu, one running and sharing with Win XP, one on its own, the other on a defunct laptop. I have never had a problem installing when not shared. When sharing there had been some hitches, this recent one was the worst.

IMO Ubuntu needs a bit of fine tuning to load in share mode without causing agro.

I cannot see anything Microsoft is offering to keep me from going fully Linux on other computers. Unfortunately there is still one Windows app I need to use for website design - Serif WebPlus. I have not found any reliable method of running any Serif product on Linux, anyone know different?

Thanks to everyone for your help.

At least there is a happy ending to this thread

Greg

---

