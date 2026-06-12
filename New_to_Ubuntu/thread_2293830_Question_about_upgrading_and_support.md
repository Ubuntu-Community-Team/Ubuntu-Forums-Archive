---
title: "Question about upgrading and support"
date: 2015-09-07
forum: New to Ubuntu
---

### Post by greentea2 on 2015-09-07
Hello all, 

I have an absolute beginner questions regarding the updating the Ubuntu Versions ;). 

If I install 15.04 can i update to 15.10 and later to version 16 or should I do each time clean installs? 

I ask this questions because I want to install Ubuntu on my parents laptop, but as I don´t see them that often maybe I cannot maintain their Ubuntu, neither they know how to do it. 

Therefore not sure if it is better to install the newest version or still go with v.14 which has long time support. 

I really would appreciate your help! 
Green Tea

---

### Post by grahammechanical on 2015-09-07
If you install Ubuntu 15.04 then your parents or you or someone will have to upgrade to 15.10 within 3 months of 15.10 being released. It is a simple operation. The OS will notify the user when an upgrade available and then it is a one click operation. But some of us think it is best to wait a few weeks before accepting the offer of an upgrade.

If you install 14.04 then the OS will notify the user when 16.04 is released. Again it is a simple one click operation. I would suggest 14.04. Do not underrate your parents ability to learn new things. Keep the OS simple.

Regards.

---

### Post by greentea2 on 2015-09-07
Hi @grahammechanical

thanks for your help. I would try to support them with updates using TeamViewer and login into their device. 

However, I still have one question. My parents have an older Acer Aspire 5536 with AMD Athlon 64 X2 Processor and ATI RadeonHD 3200 graphics card. 

I understand that_ ubuntu v.15 offers better support for ATI_, not??

---

### Post by Bucky Ball on 2015-09-08
Probably no, unless their machine is two or three minutes old and a brand new model. But then possibly no. Go for 14.04 and see what happens. If it is an older machine you should not have any problems (and may not need the ATI proprietary drivers anyway as the open-source one in the kernel may work fine for their purposes). 

Really best to stick with the LTS (long-term support) releases for this. As you are not physically present upgrading once every two years rather than every six months is best. Also, the LTS releases become extremely stable. That's the idea. You may well spend half your life helping them with bugs and upgrades using interim releases. I wouldn't go there.

---

### Post by mastablasta on 2015-09-08
> **greentea2 said:**
> Hi @grahammechanical

thanks for your help. I would try to support them with updates using TeamViewer and login into their device. 

However, I still have one question. My parents have an older Acer Aspire 5536 with AMD Athlon 64 X2 Processor and ATI RadeonHD 3200 graphics card. 

I understand that_ ubuntu v.15 offers better support for ATI_, not??

yes and no. 14.04 has hardware enablement stack - you can upgrade kernel only if needed. kernel has the drivers for your card since proprietary ones are no longer available. make sure to test it live first before installing. see if drivers and such work ok. you can also upgrade only drivers via PPA.

I am not sure how much work if any is being done on Radeon 3xxx series, but I think this one still get's some updates since AMD helped the opensource driver developers quite a bit as they abandoned the chip with their proprietary drivers.

regarding updates - you might want to set up automatic updates for them (at least security patches) - [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

also if you plan to help them at distance then think about installing and configuring SSH server for secure remote connections. : [https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

when (yes, when, not if) things get messy you will need CLI anyway.

---

### Post by MartyBuntu on 2015-09-08
TeamViewer and LTS versions of Ubuntu *only*.

Don't complicate this.

---

### Post by mörgæs on 2015-09-08
The open source drivers are improving a lot for both old and new ATI cards, among other things the new drivers are less power consuming. Because of this and lots of other improvements I generally recommend the latest stable release, that is 15.04 as of now.

However, I don't trust an online upgrade so if you don't have the option to reinstall the system every half year then an LTS version is the best choice in this case.

---

### Post by ian-weisser on 2015-09-08
> **greentea2 said:**
> I ask this questions because I want to install Ubuntu on my parents laptop, but as I don´t see them that often maybe I cannot maintain their Ubuntu,

My laptop tuns 15.04. My parents' laptop runs 12.04 LTS. 
I want newer applications and improvements. They don't.
I use many features in 15.04. They don't.
I do complex tasks on mine. They don't. They merely do e-mail and web browsing and stream the occasional movie.

Their laptop is set to install security updates in the background only. No update nags or confusion for them.
Once or twice each year, when I see them, I update everything else (sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove && sudo apt-get autoclean), backup their /home to my server (with their permission), and ask them if they have any problems. They never do. 

I considered setting up a VNC server (pre-TeamViewer era) and SSH server on their laptop so I could help them remotely...but didn't. They have never needed remote help anyway.

---

### Post by mörgæs on 2015-09-09
By the way, for a computer like this I recommend X/Lubuntu over Ubuntu.

---

