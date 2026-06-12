---
title: "Dell 8400 Won't Boot To Windows Now?"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by Akacheebe on 2013-01-28
OK so I've read on here where Grub isn't suppose to do anything to a Windows drive when Ubuntu is installed on a different drive in the same computer??  I've been running Ubuntu 12.04 and Windows XP Pro on this box for a few months now but today I wanted to try to partition the 150GB Windows XP drive and make a storage D drive on it so I opened up the box and disconnected the Ubuntu drive so as not to get the two confused while working on Windows.  Problem is, now this computer will not boot to the Windows drive??  I get an error of "Drive 0 not found  Serial ATA, SATA-0

Error: No such device: "then a long number letter combination"
Grub Rescue> _

So if Grub is NOT suppose to be installed on my Windows XP hard drive, WHY is it wanting to do a "Rescue"??

So I reconnected the Ubuntu drive and now I'm booted up on that but I need some help.  

So can someone tell me how to get my computer back to running on the Windows drive only?  That drive has the complete restore partition for the OS so I don't want to screw that up?

Thanks

---

### Post by Akacheebe on 2013-01-28
Don't know if this matters or not, but on my Windows XP C drive there is a folder there called "boot-sav" and it has several other folders inside, one of which has a reference to "etc_fstab_new" and "etc_fstab_old" and "grubenv"  These are inside a folder called sda1 and there are several other drive names in that "boot-sav" folder also??

Please note that I had to reload Windows XP back a couple of weeks ago and I kept getting an error at boot about the old version so I edited the Ubuntu "etc/fstab" to reflect the new software load.  Maybe this new folder is part of that but as I said before, it's written in many places on the internet that grub doesn't do anything to Windows when it's on a different drive??

Thanks

---

### Post by frank604 on 2013-01-28
Just to confirm you have two physical hard drives.  The first one has winxp installed and the second has ubuntu installed.  You want to reformat/partition the first hard drive that has winxp on it and convert it into a storage drive.

Why not just boot into the ubuntu system, run gparted to do this?  Also update grub so that it takes off windows from the grub menu.
```
sudo update-grub
```

---

### Post by Mark Phelps on 2013-01-28
> it's written in many places on the internet that grub doesn't do anything to Windows when it's on a different drive??

NOT true -- unfortunately.

GRUB installs, by default, to the "first" hard drive it sees in the PC -- unless you go out of your way to prevent that -- which most folks don't even know about.

For example, if you're booting from a Windows drive (and that is sda) and you just got finished installing to sdb -- guess which drive is the first? Right -- sda.

Yeah, when you change your boot order such that the Ubuntu drive is then "first", it will become sda -- but by then, the damage has already been done.

---

### Post by Akacheebe on 2013-01-29
So this means that if I loose the Ubuntu load on it's drive then I also will loose the ability to boot to the Windows XP drive??    THAT SUX A BIG ONE!

And just to clarify, the Windows drive is a 160 GB SATA drive of which Windows only uses about 30GB.  What I was going to do was use Partition Manager to create a D: drive partition on that HD for storage as I've got another computer that is setup that way and it works really well to store files and such on in case something goes wrong.  I even store ALL Ubuntu files on that Windows drive so that there's no hassle recovering data when Ubuntu goes south.  Been there, done that!

So is there any way to repair the Windows drive so it will again boot from Windows without having the Ubuntu drive connected?  I really don't want to have to install Windows again as I just did that about a month ago!

---

### Post by Mark Phelps on 2013-01-29
> **Akacheebe said:**
> So this means that if I loose the Ubuntu load on it's drive then I also will loose the ability to boot to the Windows XP drive??    THAT SUX A BIG ONE!
Not necessarily.  What it means is that, in a multi-drive system, GRUB will attempt to install on the first drive it finds -- and in some cases, this can break Windows booting.

> So is there any way to repair the Windows drive so it will again boot from Windows without having the Ubuntu drive connected?  I really don't want to have to install Windows again as I just did that about a month ago!
Do you have a Windows XP CD? If you do, you can boot from that and repair the MBR on the Windows drive so it will boot again.

---

### Post by Akacheebe on 2013-01-30
Mark thanks for the info.  

Just to clarify, Ubuntu is set to be the default boot device in BIOS and was installed and updated WITHOUT the Windows drive even connected.  I started doing that some time back to keep from overwriting another drive.......AGAIN!  I guess grub got installed on the Windows drive then during first boot with both drives connected.  

Do you happen to know what the command line is that works to repair the Windows boot problem?

I did a search on here and found a bunch of stuff and even found where someone has disabled grub's install on other drives by turning off the "OS Prober", which I take it fixed this problem for that person.  I may have to resort to that myself as I can choose the boot drive in BIOS.

---

### Post by Mark Phelps on 2013-01-30
> **Akacheebe said:**
> Mark thanks for the info.  

Just to clarify, Ubuntu is set to be the default boot device in BIOS and was installed and updated WITHOUT the Windows drive even connected.  I started doing that some time back to keep from overwriting another drive.......AGAIN!  I guess grub got installed on the Windows drive then during first boot with both drives connected.   I wouldn't think that would happen as I have multi-boot systems and have never encountered that.

> Do you happen to know what the command line is that works to repair the Windows boot problem?Using the Windows XP CD, you boot to a command window and enter "fixmbr" followed by "fixboot". But, don't remember how you do that from inside Ubuntu and can't find the thread link I once had.

> I did a search on here and found a bunch of stuff and even found where someone has disabled grub's install on other drives by turning off the "OS Prober", which I take it fixed this problem for that person.  I may have to resort to that myself as I can choose the boot drive in BIOS.From what I recall, os_prober only searches for OS files and updates the grub.cfg file with what it finds.  I'm not aware it does anything to other drives.

---

### Post by Akacheebe on 2013-02-02
Well, I did the "fixmbr" thingie and got a warning about a non standard boot sector and to proceed with caution as it "might" mess up the partition tables?  Went ahead and did it anyway as it wasn't working anyhow and then did the "fixboot" one and all is well now!   From now on though I'm going to disconnect that Windows drive whenever any grub updates come in!!

Thanks!! 

Then used Partition Magic to add a storage partition (D drive) and the second problem was taken care of too so both pieces of this puzzle are solved.

Now to try to learn to use PGP encryption on Linux but thats a topic for a new thread.

Thanks guys!!

---

### Post by Mark Phelps on 2013-02-02
You're welcome ... glad to see you got it working.

---

