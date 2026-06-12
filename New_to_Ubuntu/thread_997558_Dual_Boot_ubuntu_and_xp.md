---
title: "Dual Boot ubuntu and xp"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by rizzle on 2008-11-29
I know this has been posted somewhere and I have searched my butt off trying to solve this myself. It all starts with me installing 8.10 and finding out that full support for audio and video is not quite there. I decided to install 8.04 so I could install my audio and video drivers and use wine to play my games. I am trying to kick  windows and Microsoft to the curb.
I am trying to dual boot and I have a raid 0. 8.10 had no problem recognizing my array and installing. With 8.04 the partitions need to be set up manually. I have used info from forms to get my partitions set up and install the system all the way until grub install and then it says it can not install grub. This of coarse totally throws my xp install out so I have to install that again as well. I am looking for advice here. Should I install 8.04 in a different manner, or should I wait until my drivers are fully supported. Should I install Ubuntu on a separate drive so that my install does not destroy my xp install. I am lost here!
I did see some post that said I should install grub to a different partition but nothing step by step that I felt comfortable with.

I have 
a8n32sli premium
2gb ram
2 7900gs video card
2 75 gb 10000rpm raptors

I know I am leaving out some important info here so let me know what you need to know to help me out and Thanks in advance

---

### Post by Vaidok on 2008-11-29
If you have a live-cd you can load it in Windows and then install Ubuntu using wubi, which is on the cd.  This will use the windows boot loader instead of Grub.

---

### Post by rizzle on 2008-11-29
Thats an idea. I have been using the alternate cdup until now as I thought it was the only way to configure the raid array. Can you confirm that I can install to the raid array with wabi. Thanks!

---

### Post by Vaidok on 2008-11-29
Yes, I had to do this with my friend's computer.

---

### Post by caljohnsmith on 2008-11-30
If you can install Ubuntu to a non-RAID drive, and also set that drive to boot on start up, then that is probably the easiest solution. If you want to install Grub to your Windows RAID array doing a full install (not using Wubi), then this link might help you:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Or if non of the above options are workable, then as all ready mentioned, Wubi is definitely a good alternative.

---

