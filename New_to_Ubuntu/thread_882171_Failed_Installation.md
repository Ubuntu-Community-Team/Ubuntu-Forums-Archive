---
title: "Failed Installation"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by 98bluewave on 2008-08-06
I attempted to install Ubuntu 8.04.1 and couldn't complete the installation because of error message GRUB loading Error 21.

Now I can't open Windows Vista! Please help and thanks!

---

### Post by Ryadt on 2008-08-06
Try to change the slave hard drive controller from "off" to "auto" in bios set up.

---

### Post by hermes0710 on 2008-08-06
Try the following:

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html]("http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html")

---

### Post by Gone fishing on 2008-08-06
grub error 21 means that grub is looking for the grub configuration file on a disk that does not exist.

Which is odd.

I think I'd boot up on the live cd and then on system > administration > partition editor see if you have your Windows ntfs and linux partitions are still there.

If everything is still OK you could get Vista booting by booting on the Vist install cd clicking repair your computer then command prompt and using the BootRec.exe /fixmbr command (apparently it replaces the fixmbr command in XP).

I think I'd then remove the Linux partitions and reinstall Ubuntu again. Personally I install grub onto the Linux partition rather than the MBR and then use a boot manager called GAG, but I seem to be in a minority!

---

### Post by 98bluewave on 2008-08-06
THANK YOU! I was able to open Vista with your instructions and that was a huge relief. I have not attempted to install Ubuntu again. Thanks!

---

### Post by jdossey on 2008-08-06
I have had the same problem with GRUB Error 21. But the odd thing is, sometimes it WORKS? But USUALLY it doesnt. About 1 in 20 times of trying to reboot, it will work.

I want to remove GRUB from my internal hard drive, and reload UBUNTU. I dont know how GRUB landed on my systgem drive anyway.
I have Vista on there, so I rarely can boot either one.

I have downloaded a lot fo FIX-IT programs, none worked.
I have tried a LOT of suggestions to redo the GRUB setup. Nothing worked...

I wanteed to give LINUX a fair trial, but this is really discouraging me.
I need HELP!!

---

### Post by hermes0710 on 2008-08-07
> **98bluewave said:**
> THANK YOU! I was able to open Vista with your instructions and that was a huge relief.

really? :lolflag:

---

### Post by dileepm on 2008-08-07
Well you can put the live CD and check for your partitions with any linux partitions left out and delete them.You may then install Ubuntu if you wish...

---

### Post by Brandel Valico on 2008-08-07
Just as a Question do you have one Sata and one IDE Hard Drive?

I've noticed that if you do have a combination of both Hard Drives. Even if you install Linux on the Sata Drive Partitions Grub ends up on the IDE Drive by defualt for some reason. Then you get boot load errors.

If this is the case the fix is simple. Unhook the IDE Drive while you install Linux this ensures the GRUB gets placed on the correct drive. Then just hook it back up and mount it via Fstab or as a storage device. 

Now this solution is of course only something that applies if you answered yes to the question asked. But Since I have had a very similar issue and this was how it happened and how I fixed it I thought I would share. (There are no doubt much more elegant and better ways to do this of course. But it's a quick and guaranteed method I know works for me. So I use it.)

---

### Post by Gone fishing on 2008-08-07
hermes0710 when the stress levels have normalized :lolflag: I'd try Ubuntu again with a little tweaking I'm sure you'll find it nicer than Vista. :-&

I'm sure that other members are right and grub got confused about which was the primary drive and playing with BIOS settings will sort the problem. 

I think I'll just do one more plug for using GAG and putting grub on the root partition. It just makes things easier, I usually have XP and Ubuntu (as my main OS) and another OS to play with and that changes (although I have a space on my HD ready for Haiku) GAG is just easier than playing with grub.

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by jdossey on 2008-08-07
I bailed out! After spending a WEEK, and trying dozens of "fixes" I never ever could get the GRUB bootloader fixed.

I had to purchase a RECOVERY DVD and totally RELOAD my system.

There is a poor support system out here, I expected to find a lot of "experts" and I found lots of "Suggestions" that did NOT work.

I was not impressed with Linux if it takes this much effort to
solve such a simple problem WHY wouldnt UBUNTU provide some fix for this, it was a UBUNTU distribution that caused it.

I learned one thing about LINUX, I am now a Microsoft guy forever. I think LINUX is just DOS for the dark ages.

---

### Post by Brandel Valico on 2008-08-08
Your probably better off sticking with Microsoft.

Still just because I'm a curious guy. Did you ever try calling Microsoft's trained and paid (None of which the people here are) Tech's and asking them for help in getting both OS's to play nice together. I bet I can tell you what their answer would be. Yes you may not have encountered "experts" here (There are some but most are just users like you and me) But at least we try to help everyone who comes here no matter what OS they are using.

Incidently if the problem was so "simple" then why did you need help with it anyway?

---

