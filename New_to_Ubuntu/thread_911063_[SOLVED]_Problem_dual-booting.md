---
title: "[SOLVED] Problem dual-booting"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by amelie on 2008-09-05
Hi there!
Trying to double boot Ubuntu with some XP, but when starting the Ubuntu and pressing Enter when the message "boot from CD appears" nothing happens and I can;t start Windows installation... 
What am I supposed to do?
Thanks in advance

---

### Post by Crafty Kisses on 2008-09-05
What are your system specs? You may need to use the alternate CD installer.

---

### Post by Peter09 on 2008-09-05
If you have installed Ubuntu then make sure you have removed the CD from the drive.

---

### Post by amelie on 2008-09-05
No, I've installed Ubuntu long time ago, now I just want to add Windows as well (for my unhappiness) 
Where can I see my System specifications :confused: I've got a Desktop PC with DVD-RW and DVD-ROM...

---

### Post by Peter09 on 2008-09-05
I believe it is difficult to add windows after Linux because Windows will over write your grub menu. 

However having never done this I will have to leave others to comment.

---

### Post by Peter09 on 2008-09-05
Why don't you use virtualbox to run windows?

---

### Post by amelie on 2008-09-05
well I have a tutorial so I'll recover Grub after installing Windows :) Hope everything is okay
Meanwhile I found my specs: Ubuntu 8.04 hardy kernel Linux 2.6.24-17 generic
Gnome 2.22.1
processor AMD Sempron(tm) 3200+

---

### Post by Crafty Kisses on 2008-09-05
You can definiatley run the LiveCD, did you download the right architecture?

---

### Post by Peter09 on 2008-09-05
If you have somewhere around 1GB memory or more in that it will be easier to use virtualbox, it is really simple and good.

---

### Post by amelie on 2008-09-05
Codename: What do you mean by "the right architecture" and isn't the LiveCD for Ubuntu...

Will I be able to run windows-orientated programs by virtualbox - I just didn't have the possibility to undestrand why is it worthy the 5 minutes I read about it...i;ve got 950miB memory..

---

### Post by Crafty Kisses on 2008-09-05
> **amelie said:**
> Codename: What do you mean by "the right architecture" and isn't the LiveCD for Ubuntu...

Will I be able to run windows-orientated programs by virtualbox - I just didn't have the possibility to undestrand why is it worthy the 5 minutes I read about it...i;ve got 950miB memory..

You have enough memory and use you be able to run Windows-orientated programs in Virtualbox.

---

### Post by Peter09 on 2008-09-05
I think Codename may have assumed that you are trying to run the Ubuuntu live CD to install Ubuntu onto windows.

Yes you can run windows on Virtualbox, as long as it does not need heavy graphics. You can run other operating systems as well. 

The reason to go this way is that VirtualBox will contain windows within its own structure. You do not risk losing Ubuntu, and you can remove windows, or re-install it whenever you like with no problems.

---

### Post by amelie on 2008-09-05
Thank you both!!! So now no need to install windows, just the virtualbox :) this is really cool :) Thanks a lot really!!!

---

### Post by Peter09 on 2008-09-05
Yes, virtualbox is in the repositories, you can use synaptic to install it.

---

