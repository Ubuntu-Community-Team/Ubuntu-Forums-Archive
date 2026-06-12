---
title: "Desktop PC, RAID 0 and bootloader trouble"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Gilgeam on 2012-07-23
Hey everyone,

I guess I'm in way over my head here. I tried searching multiple forums and ran across a very, very wide array of sometimes contradictory tips, so now I turn to you and hope you can give me a hint or two.

I'm running a Windows 7 PC with a RAID 0 setup via mainbord (Hardware RAID, I s'pose). The raid has two primary partitions (the windows boot partition and the windows partition itself) and two logical ones after installing Ubuntu via the alternate CD (EXT4 and swap). 

I first tried the usual Ubuntu desktop CD (12.04) and got a "grub install dummy failed" message. I then tried the alternate CD. Here I got another grub install failure, but I could choose where to put the bootloader manually. I then chose the EXT4 partition and GRUB supposedly installed successfully. However, upon rebooting I only got the Windows 7 bootloader with only Windows as an entry.

I then tried adjusting the windows bootloader using EasyBCD as I have read in a few postings. However, even though I can add the boot entry to the Linux partition just fine, Ubuntu still does not show up on the boot screen.

I'm a little at the end of my wits here. What's going on?

Any help would be appreciated!

Thanks,
Gil

---

### Post by lukeiamyourfather on 2012-07-23
Unless you spend hundreds of dollars on a RAID controller its probably fake RAID.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Unless you have a good reason for RAID 0 you should steer clear. Especially when using fake RAID.

---

### Post by TheFu on 2012-07-23
Like [lukeiamyourfather]("http://ubuntuforums.org/member.php?u=774656") says, you probably have RAID driver issues and Ubuntu doesn't know how to access the RAID disks.

I'll also chime on on saying that using RAID0 for anything other than a scrap workspace is foolish. If either drive fails, you've lost your data -ALL of it, including the OS, apps, boot sectors ....

In the Linux world, booting off RAID is usually avoided, though running off RAID is a best practice.  Simply put, /boot should to be non-RAID.  Many servers will boot from USB or a CF card, load RAID drivers, then access the rest of the OS files from a RAID device or even a SAN.

To get any Linux working under a RAID card, you'll get to learn more about your RAID card.  I'd start by booting a LiveCD and using 'lshw' to learn about the specific RAID device you have. Next, I'd google to determine how supported that device is under Linux.

Generally, for home Linux needs, softwareRAID is best. It provides all sorts of flexibility and doesn't tie us to specific hardware. RAID cards fail all the time. In an enterprise, they will have excellent backups or a spare **identical** RAID card available. At home, you probably don't.  Often, switching RAID cards, even within the same vendor, will loss all your data.  SoftwareRAID will be a little slower than a good quality hardwareRAID card, but the added flexibility more than makes up for that.  I know of what I speak. [http://blog.jdpfu.com/2010/02/12/software-raid-migration](http://blog.jdpfu.com/2010/02/12/software-raid-migration)

---

### Post by Gilgeam on 2012-07-23
Thanks for your help and insight!

That at least solves one mystery for me. Now I still need to figure out how to get it right. As the page you linked says I guess Ubuntu recognizes my RAID setup - I can point it to /dev/mapper/something rather than /dev/sdX, at least.

Now, about my second question: given this, where should I install the bootloader? I tried installing it the partition containing / but that obviously didn't work out.

Edit: I'm pretty sure now that since I'm only using a mainboard-feature of my ASUS P8P67 Pro, I guess its just fake RAID. My problem with software RAID is that a) I simply don't have a way to backup the amount of data already on the disks and b) I'd like to dual boot windows and linux and read it's better to have a solution that's not OS-specific in that case.

---

