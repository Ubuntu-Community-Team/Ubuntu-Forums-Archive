---
title: "Complete newby looking for advice"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by daitheboot on 2008-11-18
I am a total newby to Ubuntu or Linux in any form.I have downloaded and created a CD of vers 8.10 and I am ready to make a move. As I use my existing pcs for many important purposes I want to set up Ubuntu on a spare laptop in the first instance. The laptop I am going to use has XP Pro already installed but I would like to remove that and only have Ubuntu on this machine. Is that possible and where can I get instructions or direction on how to do this. Second question will I be able to network the new machine with my existing MS based network? I am sorry if I am in the wrong forum and will move if I am told where it should be placed.
Thanks

---

### Post by rampageoberon on 2008-11-18
Not in the wrong place at all.

To install Ubuntu you want to boot off your CD drive with the Ubuntu CD in there and the installation is very straight forward from there. You can choose to use the full partition/all available space and that will overwrite the windows install.

Regarding networking with the MS netwrok, it is indeed possible with the use of Samba.

Hope that helps, do ask if you have any other queries or issues.

---

### Post by tarps87 on 2008-11-18
To remove XP and have just Ubuntu installed, select "guided - use entire disk" on the partitioning section of the install.
A couple of things to check if you haven't already, run the cd check on the cd, to do this boot using the cd and select the check menu option.
Did you download the live cd or alternative and was it the server or desktop version? I think the one your looking for is the live cd desktop version which is the default install. If you have problems using it you may want to use the alternative cd.
You can network the machine using a thing called samba. This is available through the Ubuntu repository.
Here is a link about samba on Ubuntu:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Hope this helps

---

### Post by hashimoto on 2008-11-18
Look here for information about partitionong possibillities (and a lot else, too):
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I would recommen that you make a separate /home . Makes the upgrading a lot easier later.

---

### Post by bennachie on 2008-11-18
I'd support the advice given above. However, since you are apparently completely new to the OS, why not try it out first and make sure that everything works the way you want it to work. It's actually very easy to install Ubuntu "inside" Windows. Just boot the old laptop in XP, then mount the LiveCD. You'll be offered the chance to install Ubuntu in just that way (a programme called Wubi does the magic).

You can subsequently choose to boot the laptop into either XP or Ubuntu. If you boot into XP, you can "uninstall" Ubuntu just as if the OS itself was a normal Windows programme.

It really is very convenient, laptop performance is only slightly reduced, and when you are quite satisfied, you can proceed to replace XP as the other forum members have recommended.

---

### Post by hyper_ch on 2008-11-18
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by mapes12 on 2008-11-18
Yep, all good advice here. Particularly, setting up the partitions correctly via the Psychocats link.

If you decide to wipe XP completely my personal preference would be to run a low level format application from a floppy or CD to completely erase everything on the HDD.

Then use a Live CD or a GParted Live CD to setup the partitions per the Psychocats link. Then when you run the installation you will get to section called "Paritioning". The default is "Guided - User entire disk". If you want to make the most of the partitions you would have created you would need to move down the list and select the option "Manual". It's the last one. Then the installer will ask you what you want each partition to do i.e. /(root), /home & Swap. Just set the variables and the installer will go on and do the rest for you.

If you wipe the HDD completely clean then it doesn't matter if you make a hash of it the first time round. If it's wrong or not what you want then simply reinstall. Believe me, you will get familiar with the install options once you have done this quite a few times, as I have done.

Welcome to Ubuntu.

---

### Post by handydan918 on 2008-11-18
> **bennachie said:**
> I'd support the advice given above. However, since you are apparently completely new to the OS, why not try it out first and make sure that everything works the way you want it to work. It's actually very easy to install Ubuntu "inside" Windows. Just boot the old laptop in XP, then mount the LiveCD. You'll be offered the chance to install Ubuntu in just that way (a programme called Wubi does the magic).

You can subsequently choose to boot the laptop into either XP or Ubuntu. If you boot into XP, you can "uninstall" Ubuntu just as if the OS itself was a normal Windows programme.

It really is very convenient, laptop performance is only slightly reduced, and when you are quite satisfied, you can proceed to replace XP as the other forum members have recommended.

Just to provide a counterpoint, before following this suggestion, go to the section of the forums [here]("http://ubuntuforums.org/forumdisplay.php?f=234")and make ksure that the problems listed are the kind you want. Wubi is an abortion, IMHO. 
Ubuntu (and Linux in genereal) is best used either standalone or as a dual-boot. The installer will do all the heavy lifting for you, dual booting is not that difficult.

---

