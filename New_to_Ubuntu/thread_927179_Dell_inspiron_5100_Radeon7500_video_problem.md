---
title: "Dell inspiron 5100 Radeon7500 video problem?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by orygunpenguin on 2008-09-22
Hi, 

I have a Dell Inspriron 5100 with a Radeon 7500 video card. 
When I use the command: lshw -class video
I get: 
*-display UNCLAIMED
          Product: Radeon Mobility M7 LW [radeon Mobility 7500]
          Vendor: ATI Technologies Inc
          Physical ID: 0
          Bus info: PCI@0000:01:00.1
          Version: 00
          Width: 32 bits
          Clock 66MHz
          Capabilities: vga controler bus_master cap_list
          configuration: latency=66 mingnt=8

There is no mention of the driver, nor is there one in the xorg.conf file.
Is there any other way to confirm that this card is or isn't installed correctly?

---

### Post by orygunpenguin on 2008-09-22
Is there noone who can answer this?

---

### Post by willca on 2008-09-23
Just suggestion, you can try using envyng for this.

$ sudo apt-cache search envyng
which will give you this if you are running Hardy.

envyng-gtk - install the ATI or the NVIDIA driver
envyng-qt - install the ATI or the NVIDIA driver
envyng-core - install the ATI or the NVIDIA driver

Once you installed any one of them then run it like this
$ envyng

If you going to reconfigure your X, I would normally do this by running envyng when I dont have X desktop running at all. So hit ctrl-alt-backspace and if it gives a shell session then use it. Otherwise if it starts X again, then hit Alt-F1 or ctrl-alt-F1 or F2 or whichever gives you a new terminal session and do it from there.

Good luck.

---

### Post by orygunpenguin on 2008-09-23
unfortunately envyng doesn't support this card. I tried that when I saw it in a previous ATI card thread. From what  I see I have to use the open source ATI drivers? but they didn't seem to install when I loaded and I don't know how to do so manually......

Thanks though

---

