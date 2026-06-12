---
title: "Restoring Windows without ruining Ubuntu"
date: 2020-07-02
forum: New to Ubuntu
---

### Post by jazz.fog on 2020-07-02
Hi!

During last update to Ubuntu 19.10 I've had some issues with nVidia driver that was included in the release, as a result my Ubuntu would not boot and I had to re-install it.
Not sure how that happened but along the way I ruined my Windows also installed on the same machine.
I did not need Windows on that machine so I did not care much back then but now I need again to do some tasks using Windows.

So what I am trying to do is to re-install Windows but without ruining my current Ubuntu that I use as my primary OS.
I know that reinstalling windows is easy but not ruining Ubuntu is the part that worries me the most.

Need an advice or some guidance how I can go about it!

This is what my disk currently looks like:

[[img]https://i.ibb.co/WWNWSsx/laptop-disks.png[/img]](https://ibb.co/5WXWq2M)


[ATTACH=CONFIG]286380[/ATTACH]

---

### Post by mastablasta on 2020-07-02
nvidia drivers are not part of Ubuntu and are not included. you should remove them before doing the upgrade.

Install windows, then you need to reinstall grub. probably UEFI install, right? [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

windows are not affected by Ubuntu upgrades /installs. What can get affected is grub that points to windows master boot record. 
on the other hand upgrading windows can ruin Ubuntu, but again i think only grub is then overwritten.

also not sure what you need to do in windows, but using virtualbox for limited tasks is a more elegant solution (if you have the RAM for it). for more serious prolonged work, you do need dual boot.

---

### Post by jazz.fog on 2020-07-02
> **mastablasta said:**
> nvidia drivers are not part of Ubuntu and are not included. you should remove them before doing the upgrade.

Install windows, then you need to reinstall grub. probably UEFI install, right? [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

windows are not affected by Ubuntu upgrades /installs. What can get affected is grub that points to windows master boot record. 


I believe nVidia driver is included starting 19.10 and, I believe, this is what caused me the issue. After the upgrade I've got error message, saying something about nvidia.
[https://www.omgubuntu.co.uk/2019/05/ubuntu-19-10-nvidia-drivers-iso](https://www.omgubuntu.co.uk/2019/05/ubuntu-19-10-nvidia-drivers-iso)
Since it was new release and new error related to this change - I could not even find error message like this on the internet by googling it.
I was not able to figure out how to fix it quickly and since it is my work machine and I needed to have it running without researching the problems for days I just decided to re-install Ubuntu.
I do not remember exactly what I did to ruin Windows, something on SSD partitioning step, I did not care much back then.



> **mastablasta said:**
> on the other hand upgrading windows can ruin Ubuntu

This is why I am here :)

> **mastablasta said:**
> 
also not sure what you need to do in windows, but using virtualbox for limited tasks is a more elegant solution (if you have the RAM for it). for more serious prolonged work, you do need dual boot.
 

I need to work with some graphics applications, performance in VB/VMWare is not great.

> **mastablasta said:**
> but again i think only grub is then overwritten.

I am afraid that I might screw it up on the partitioning stage

I might need at least some help identifying the particions I can safely delete so I could maximize the available space.

Does it look like only the last 3 partitions are belong to Linux and
Can I safely delete all the partitions in the front in order to install windows there?

---

### Post by kurt18947 on 2020-07-02
My primary PC is a desktop. I have a 512 GB. NVMe drive and 128 GB. SATA SSD. I have Windows on the SSD. It stays unplugged the vast majority of the time so when I plug it in there are all sorts of updates. I haven't had GRUB broken since keeping Windows on a separate drive. When I did have Windows and Ubuntu on the NVMe drive, Windows update did break GRUB but boot-repair fixed it.

---

### Post by Impavidus on 2020-07-03
> **jazz.fog said:**
> I believe nVidia driver is included starting 19.10 and, I believe, this is what caused me the issue. After the upgrade I've got error message, saying something about nvidia.
Starting 19.10 (or 18.04.4), the AMD drivers are included on a fresh install, not the nvidia drivers. Those can be installed from the official repositories, section "restricted", what you probably did. That's all for license reasons. They may get occasional upgrades. I don't think you have to remove them before a release upgrade, but I've no nvidia graphics here, so I can't say for sure.

---

### Post by mastablasta on 2020-07-03
> **jazz.fog said:**
> I believe nVidia driver is included starting 19.10 and, I believe, this is what caused me the issue. After the upgrade I've got error message, saying something about nvidia.
[https://www.omgubuntu.co.uk/2019/05/ubuntu-19-10-nvidia-drivers-iso](https://www.omgubuntu.co.uk/2019/05/ubuntu-19-10-nvidia-drivers-iso)
Since it was new release and new error related to this change - I could not even find error message like this on the internet by googling it.
I was not able to figure out how to fix it quickly and since it is my work machine and I needed to have it running without researching the problems for days I just decided to re-install Ubuntu.
I do not remember exactly what I did to ruin Windows, something on SSD partitioning step, I did not care much back then.



that's kind of like adding exe file to windows install disk. it's there but nothing happens unless you run it. 


otherwise hard to see from your photo. 2,3 and 4 are osme kind of windows partition, parittion 1 is boot partition. leave 6, 7 and 8 alone - they are ubuntu partitions.

you can also do backup and full reinstall and rearrange partitions. but careful with the one using bitlocker - it's locked and you will need key or unlock it and backup the data.

---

### Post by jazz.fog on 2020-07-03
> **kurt18947 said:**
> My primary PC is a desktop. I have a 512 GB. NVMe drive and 128 GB. SATA SSD. I have Windows on the SSD. It stays unplugged the vast majority of the time so when I plug it in there are all sorts of updates. I haven't had GRUB broken since keeping Windows on a separate drive. When I did have Windows and Ubuntu on the NVMe drive, Windows update did break GRUB but boot-repair fixed it.

Yeah, I've had issues with erased grub after windows update and I've fixed it multiple times, this is not what bothers me.
What I am trying to do is to delete unneeded partitions and re-install windows from scratch using maximum available space but not to ruing Ubuntu doing that. 

> **Impavidus said:**
> Starting 19.10 (or 18.04.4), the AMD drivers are included on a fresh install, not the nvidia drivers. Those can be installed from the official repositories, section "restricted", what you probably did. That's all for license reasons. They may get occasional upgrades. I don't think you have to remove them before a release upgrade, but I've no nvidia graphics here, so I can't say for sure.

Hard to tell, but I did not do anything special during the upgrade.

And yes, after the upgrade failed and I re-installed Ubuntu I've got newer nVidia driver that I had before.

---

### Post by jazz.fog on 2020-07-03
> **mastablasta said:**
> that's kind of like adding exe file to windows install disk. it's there but nothing happens unless you run it. 

Gotcha, maybe just a coincidence then that I've got nVidia driver-related issue during the upgrade.

> **mastablasta said:**
> otherwise hard to see from your photo. 2,3 and 4 are osme kind of windows partition, parittion 1 is boot partition. leave 6, 7 and 8 alone - they are ubuntu partitions.

Here is the screenshot of 1st partition details
[[IMG]https://i.ibb.co/DVBBVWt/laptop-disk-2.png[/IMG]]("https://ibb.co/8KyyKs0")

It looks like Windows related since it says FAT. Would you suggest to leave it alone or delete?
To be clear, I do not care about that old Windows installation and I am OK with loosing everything related to it since I am going to re-install it.

**UPD:** According to this
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and the icon indicators it looks like it is in use and I need it, so I will leave it alone.



> **mastablasta said:**
> you can also do backup and full reinstall and rearrange partitions. but careful with the one using bitlocker - it's locked and you will need key or unlock it and backup the data.
Yea, I do not worry about the data though backing up the entire disk with partitions sounds like a good idea,
would you suggest any free software that help with that?

---

### Post by jazz.fog on 2020-07-03
Screenshots of all partitions (Click to see bigger image)

[[IMG]https://i.ibb.co/S5TDn1w/1.png[/IMG]]("https://ibb.co/2W20tL3")
[[IMG]https://i.ibb.co/FnTdWRK/2.png[/IMG]]("https://ibb.co/HX8925V")
[[IMG]https://i.ibb.co/Smpf0xJ/3.png[/IMG]]("https://ibb.co/NNzTp37")
[[IMG]https://i.ibb.co/V27tFfj/4.png[/IMG]]("https://ibb.co/Qr2fWyb")
[[IMG]https://i.ibb.co/CtyHdtM/5.png[/IMG]]("https://ibb.co/W3X293P")

---

### Post by jazz.fog on 2020-07-03
[[img]https://i.ibb.co/QMJJkq1/6.png[/img]](https://ibb.co/YhNNXKq)
[[img]https://i.ibb.co/wwhkvNr/7.png[/img]](https://ibb.co/X3xQwZk)
[[img]https://i.ibb.co/K6v8Y0M/8.png[/img]](https://ibb.co/R2wJ1vx)
[[img]https://i.ibb.co/37BqJQ7/9.png[/img]](https://ibb.co/pxJ8m5x)

---

### Post by mastablasta on 2020-07-06
fat partition is boot/efi this one can stay. it's a boot partition (yes it's FAT so that windows and UEFI can also ready it). but someone with more knowledge about UEFI would know more.

free space means there is nothing there.

i am still not sure where is windows installed. we are saving windows now, right? windows disk manager (disk management) should show that. more on disk in windows here: 
[https://docs.microsoft.com/en-us/windows-server/storage/disk-management/overview-of-disk-management#:~:text=Disk%20Management%20is%20a%20system,see%20Extend%20a%20basic%20volume.](https://docs.microsoft.com/en-us/windows-server/storage/disk-management/overview-of-disk-management#:~:text=Disk%20Management%20is%20a%20system,see%20Extend%20a%20basic%20volume.)

is bitlocker encrypted partition system partition?

---

### Post by jazz.fog on 2020-07-15
No, I was not going to save Windows, I was going to re-install it.

Anyway, it is done now! Thank you Mastablasta for the help, I've kept the fist one and the rest partitions with stars and deleted the rest collapsing them into "free space", then I installed Windows onto that free-space, then fixed the grub.

Now everything is as desired.
Thanks again!

---

