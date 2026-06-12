---
title: "Regular freezes with HP ENVY x360 (Ryzen 3300U)"
date: 2021-03-02
forum: New to Ubuntu
---

### Post by zueryyz on 2021-03-02
I've been trying out Ubuntu 20.04 on an HP ENVY x360 and while I like the OS a lot more than Windows, I have been experiencing regular freezes, sometimes multiple times per day where a hard reboot is required to get the PC working again. Suspend has never worked - it always goes to a black screen and hangs. I've found posts which say that Ryzen processors and linux don't always work well together, but I haven't found much on Ryzen 3 procesors specifically. Until now, I've tried the standard suggested solution of adding processor.max_cstate=1 to /etc/default/grub, but it's unclear if the issue has improved.

The PC: 
-Ryzen 3 3300U with radeon vega mobile gfx × 4 
-vers F22 BIOS 
-Ubuntu 20.04.2
-Kernel 5.4.0 (it seems that the 5.8 kernel doesn't support the computer's hardware)

I'm not sure anyone can actually help solve the issue here, but I would be interested to know if other users of similar hardware have been experiencing similar issues?

---

### Post by mrdc76 on 2021-03-02
I am pretty sure they have not dropped the support for 3000 series Ryzens in the 5.8, so it is your best bet.

---

### Post by mIk3_08 on 2021-03-02
Did you try HW probe for more information about your hardware? This web system collects hardware details of Linux-powered computers over the world and help people to collaboratively debug hardware related issues, check for Linux-compatibility and find drivers. Best if you will try. this will help you a lot as it helps me a lot. Best regards and Good luck.

---

### Post by zueryyz on 2021-03-02
I forgot to mention in the original post that I tried kernel 5.8 but the trackpad wasn't supported, so I rolled back to 5.4. Does anyone know if 5.8 will be supported for this PC at some time in the future?

---

### Post by zueryyz on 2021-03-02
Thanks, I ran hw-probe as and uploaded the results to the database. The first thing I saw was that the AMD Picasso graphics card is not supported, but would this be related to random freezes? (My knowledge of linux is prety limited unfortunately.) ;-)

---

### Post by blackbird34 on 2021-03-03
> **zueryyz said:**
> I've been trying out Ubuntu 20.04 on an HP ENVY x360 and while I like the OS a lot more than Windows, I have been experiencing regular freezes, sometimes multiple times per day where a hard reboot is required to get the PC working again. Suspend has never worked - it always goes to a black screen and hangs. I've found posts which say that Ryzen processors and linux don't always work well together, but I haven't found much on Ryzen 3 procesors specifically. Until now, I've tried the standard suggested solution of adding processor.max_cstate=1 to /etc/default/grub, but it's unclear if the issue has improved.


I have an MSI with a Ryzen 5 4500U in it. I think suspend doesn't work because Microsoft has been pushing a new "Modern Standby" mode, which Linux doesn't support out of the box yet. My solution was to enable hibernation, and that works fine (although you'll need as much swap as you have RAM).

See [https://askubuntu.com/questions/768136/how-can-i-hibernate-on-ubuntu-16-04](https://askubuntu.com/questions/768136/how-can-i-hibernate-on-ubuntu-16-04) (the instructions worked for me on Ubuntu 20.10)

Edit: I just updated my BIOS and now suspend AND my trackpad work perfectly. No more workarounds. Yay. 

As for the graphics card, I strongly suggest you upgrade to the 5.8 kernel (it should be available in the Synaptic package manager) because you're likely to get better results from your card. I doubt it's fully unsupported, my more recent Ryzen graphics are fine. Well, they can play the odd 1080p Supertuxkart game without missing a beat.

---

### Post by mastablasta on 2021-03-04
5.4 kernel might need iommu=soft kernel switch. my kids laptop (Ryzen 5 3500U) doesn't work propperly on battery without this switch. no issues so far with this switch turned on at boot.

upgrade to 5.8. if you can. what touchpad is it? if synaptics, you could patch kernel with current driver, although it should be included.

Ryzen CPU & Vega GPU  are well supported by linux kernel out of the box. my kid plays various games on this laptop. ok no new GPU intensive ones, but still. Last one he bought was Subnautica, but he also plays CS:GOvarious other source games, minecraft, some older games with no issues.

---

