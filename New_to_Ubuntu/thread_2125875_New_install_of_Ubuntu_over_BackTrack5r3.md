---
title: "New install of Ubuntu over BackTrack5r3"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by clayman1000x on 2013-03-15
My laptop is an HP Compaq 6715b with an AMD 64 dual core with 4g of ram, I am currently dual booting Win7 and Backtrack5r3 (BT), BT is installed on its own partition, not through win 7. I have a 100mb space as the first partition (win7 put it there), then Win7 is on the second 168g partition, then BT is on the third 39.06g partition and storage on the last 92g of this drive. Now, what I want to do is install Ubuntu 12.04 on this third partition instead of BT (I have BT in a VM if I want it), can I just overwrite this partition without screwing up the MBR.  

If I can, how can I change the start up list to put windows as the first OS instead of having to scroll to the win7 start up. I have installed several Ubuntu's in the past but never over the top of each other.
By start up, I mean when I turn the computer on I get a list of choices to boot into, the top 4 are BT, (I want Ubuntu instead), then the fifth choice is Win7, I want Win7 at the top, first start up choice.
Thanks

---

### Post by grahammechanical on 2013-03-15
You can install Ubuntu over earlier installs. I do it all the time. Just choose the Do Something Else option at the partitioner screen and tell the installer to put Ubuntu into the partition where Backtrack is. Do you know how to do that?

What you need to keep in mind is that Ubuntu will install its version of the Grub menu into the MBR of the disk and Ubuntu will be at the top of the list. All reference to Backtrack will be removed from the Grub boot menu. It is the Grub boot menu that you are talking about and not some Windows boot loader?

Regards.

---

### Post by clayman1000x on 2013-03-15
[[COLOR=#000000] [/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")
Thank you grahammechanical for your reply, I thought that was what I would need to do but wasn't completely sure, new to Linux in general. That answers the first part of my question, I'll get it installed then come back for the second question.
Thanks 			 				 					[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")

---

### Post by clayman1000x on 2013-03-15
Now for my second question, how can I change the start up list to put windows as the first OS  instead of having to scroll to the win7 start up.
By start up, I mean when I turn the computer on I get a list of choices  to boot into, the top 4 are Ubuntu, then the fifth  choice is Win7, I want Win7 at the top, first start up choice, how can I do this?

---

### Post by sandyd on 2013-03-15
You can use grub-customizer, avaliable [here]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer?field.series_filter=precise")

---

