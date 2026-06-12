---
title: "Trying to boot to USB from GNU Grub"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by Justin_Gardner on 2014-10-13
Hey guys, 

I'm having trouble with Kali linux and I wanted to remove it and download Ubuntu. However, I cannot boot to the flash drive I created from the Rescue Grub that was provided. Its grub version 1.99. Whenever I try to "ls (hd2)" which is my flash drive it gives me "Device hd2: Not a known filesystem - total size 60532992 sectors."

Any ideas on how I could boot?


Thanks
Justin

---

### Post by yancek on 2014-10-13
What Rescue Grub and provided by ??  Common methods of creating a bootable flash drive are using the dd command in Linux, unetbootin software or universal usb installer.  Have you tried those?

---

### Post by sudodus on 2014-10-14
Welcome to the Ubuntu Forums :-)

Maybe this link (and links from it) will give you the information you need.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Otherwise, please come back with more questions! A detailed description of your computer and your problem will make it easier to give relevant advice.

---

### Post by oldfred on 2014-10-14
When you boot from BIOS, BIOS tells grub that drive is hd0.

If you boot from another drive then drives become in BIOS or Ubuntu order. On my system drive order matches SATA port numbers, but I skipped one port. If I plug in a flash drive it is sde, but if I reboot grub sees it as hd0. And when rebooted with flash drive plugged in but not used for boot it is sdb and all my other drives add a letter.

---

### Post by Justin_Gardner on 2014-10-14
I used the unetbootin software to create the Ubuntu boot USB.

---

### Post by sudodus on 2014-10-14
Unetbootin is a good tool. Please tell us more details about your computer and your problem :-)

---

### Post by Justin_Gardner on 2014-10-14
If only it was that easy... I know how to make the USB, I just don't know how to make it boot.

---

### Post by Justin_Gardner on 2014-10-14
The problem I'm having is that I can't boot to the usb because my computer boots into the Grub each time.

I can't access the bios because the grub auto boots...

---

### Post by sudodus on 2014-10-14
The methods to get into the BIOS/UEFI menus are different so please specify your computer

- Brand name and model  <--- (right now this item, later we may need the other information too)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Justin_Gardner on 2014-10-14
I figured it out *Facepalm* I wasn't booting into the bios because I had to press the fn+f2 key to access f2. Super dumb of me, sorry for wasting your time!

---

### Post by sudodus on 2014-10-14
Not super dumb, actually these very basic things are often the most difficult to find. I remember when I had to make a hard reboot on a laptop. I was used to pull the plug, but the battery was there. So I had to remove the battery until a helpful guy told me to push the power button for several seconds :-P

[COLOR=#696969]***Edit***: That was long ago. Now I have learned about

(alt) SysRq  R E I S U B

[/COLOR][[COLOR=#800080]https://en.wikipedia.org/wiki/Magic_SysRq_key[/COLOR]]("https://en.wikipedia.org/wiki/Magic_SysRq_key")[COLOR=#696969]

in linux and can avoid hard reboots.[/COLOR]

---

