---
title: "Grub 2 - karmic"
date: 2009-09-19
forum: Philippine Team
---

### Post by mewt518 on 2009-09-19
If this topic has been discussed before then please close this thread and just point me to the right direction otherwise I would appreciate some input. Ngayon lang po ako naging active sa forums eh. hehe

here's my problem..

nag install po ako kahapon lang ng karmic. I have 3 OS installed(actually 4 pero tinanggal ko lang yung backtrack4 tsaka win 7 and added sabayon). Currently I have XP, Sabayon and ubuntu in my system. Grub works fine before when I still use Jaunty but everything was messed up when I installed karmic. I didnt know that karmic uses grub 2! Grub detects XP but for some reason it does not detect sabayon. So, dati wala akong problema sa ganto i-edit ko lang yung menu.lst pero walang menu.lst sa grub 2. I guess my question is, pano po ba i-edit yung grub 2? 


Thanks!!!!!

---

### Post by frustphil on 2009-09-19
Update mo lang it will eventually pick the other OS. Pag ayaw parin i-add mo lang yung ibang OS sa list...

---

### Post by drs305 on 2009-09-19
Don't know what was said entirely, but have you tried running "sudo update-grub" after finishing the install? Although it should have been run automatically, some people are finding that they need to run it manually for Grub 2 to pick up all the OSs.

I've written an introduction to Grub 2 that explains the basics of how it has changed from Grub and how to make changes to it. There is also a comprehensive wiki. Here are the links:

GRUB 2 BASICS  / GRUB 2 WIKI
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by mewt518 on 2009-09-19
@frustphil oo chong.. na pickup ng grub yung sabayon pero ayaw mag display sa menu

@drs305 - I have tried both sudo update-grub and sudo update-grub2, it was able to detect XP and Sabayon although it refers to it as a gentoo based OS and not specifically Sabayon. For some reason, it does not display sabayon in the grub menu so yeah I had to manually add the entry in /etc/grub.d/ folder that is after some extensive reading in this guide [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2") Thanks for providing the link. It helped me a lot although I have to say that grub 2 is definitely not for beginners. At least not yet. 

Now I enjoy both sabayon 4.2 and ubuntu karmic w00t!

Thanks again!

---

### Post by foxy123 on 2009-10-31
> **mewt518 said:**
> <snap> For some reason, it does not display sabayon in the grub menu so yeah I had to manually add the entry in /etc/grub.d/ folder that is after some extensive reading in this guide [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2") <snap>

Could you please share how you edited /etc/grub.d/ folder to have Sabayon added to the grub menu...

---

### Post by karlo on 2009-10-31
> **foxy123 said:**
> Could you please share how you edited /etc/grub.d/ folder to have Sabayon added to the grub menu...
ano yung sabayon?

---

### Post by killer_d76 on 2009-10-31
Sabayon is another Linux Distro.. [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

---

### Post by karlo on 2009-10-31
> **killer_d76 said:**
> Sabayon is another Linux Distro.. [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)
ah .. eh ano na nangyari sa bayanihan linux?

ang pagasa kaya ... linux ang gamit talaga? ano kaya program gamit nila pang generate ng satellite images.

---

### Post by killer_d76 on 2009-11-01
would you believe.. Kris Aquino uses Linux?!.. I don't know what distro she uses but she mentioned once on her noontime show that she prefer to use Linux over MS!.

---

### Post by loell on 2009-11-01
> **killer_d76 said:**
> would you believe.. Kris Aquino uses Linux?!.. I don't know what distro she uses but she mentioned once on her noontime show that she prefer to use Linux over MS!.

Yeah, and there's even a good chance that our next president will be pushing Linux more for government use.  :biggrin:

maganda talaga vibes ko on 2010 and beyond.. :twisted:

---

### Post by bluegene on 2009-11-02
I would agree since the CICT (Commission on Information and Communication Technology) spearheaded the adoption of FOSS particularly in implementing computerization program in the country's public high schools in which our school (an SUC) is a partner implementor of the iSchools project.

Ubuntu rocks! :)

---

