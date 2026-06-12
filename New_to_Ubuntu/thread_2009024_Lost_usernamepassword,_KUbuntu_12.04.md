---
title: "Lost username/password, KUbuntu 12.04"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by bob1866 on 2012-06-23
Hi, I have used older versions of Ubuntu previously with no problems, but recently installed Kubuntu 12.04 onto my netbook, and set the option to login without username/password prompt.  I was trying to use another version of linux from live usb, which didn't work, but when I went back to the installed O/S, it started to prompt for, what I think, is username and password.

I typed in what I thought was correct, but it doesn't do anything apart from put you back to the login screen.  I have tried rebooting several time, but this doesn't make any difference.  At one point, I did get the GNU GRUB VERSION 1.99 Menu, and followed a blog by naveen I found.  It said I had successfully changed my Unix password, but I still can't log in to the Netbook via the login screen.  it does however allow me to log into the console?

Can anyone advise?

Regards,
Bob

---

### Post by Ms. Daisy on 2012-06-24
See if this works:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bob1866 on 2012-06-24
Hi, tried that, it allowed me to change the password but still can't log in on the login screen. I believe I might have run out of space on my hd, as the pc is a netbook with 4Gb SSD.:(

---

### Post by bob1866 on 2012-06-24
Hi, tried that, it allowed me to change the password but still can't log in on the login screen. I believe I might have run out of space on my hd, as the pc is a netbook with 4Gb SSD.:(

---

### Post by mastablasta on 2012-06-24
4gb is too low for the Kubutnu OS. ok you might install it but most of it will be taken by OS. 

it might be worth considering a lighter distro on it (in term of neede hard disk space)

---

### Post by robtygart on 2012-06-24
You might be interested in Puppylinux its really small, puppylinux.org it is made from Ubuntu packages.

It is also great for older PCs with low RAM.

---

### Post by bob1866 on 2012-06-24
this is the same conclusion I had reached, but wasnt sure which version to go for. had thought of using ChromeOS, but have had a problem with my USB stick. I've managed to set up one to bootand install from before, but at the moment when I try to create one the creating machine says it was sucessful, but the problem machine won't recognise it as a boot device :( will give puppylux a try if I can get it loaded.

---

### Post by robtygart on 2012-06-24
> **bob1866 said:**
> this is the same conclusion I had reached, but wasnt sure which version to go for. had thought of using ChromeOS, but have had a problem with my USB stick. I've managed to set up one to bootand install from before, but at the moment when I try to create one the creating machine says it was sucessful, but the problem machine won't recognise it as a boot device :( will give puppylux a try if I can get it loaded.

Have you looked in your bios to see if the USB (Removeable Meda) is set to boot before the HDD? 

Start with "Lucid Puppy (Ubuntu-Compatible Build)" if your making a USB make sure to open the USB find the file "syslinux.cfg" 

it will look like this ```
default puppy
display boot.msg
prompt 1
timeout 50

F1 boot.msg
F2 help.msg
F3 help2.msg

label puppy
kernel vmlinuz
append initrd=initrd.gz pmedia=cd
```

Change pmedia=cd to pmedia=usbflash 

You could also try using "unetbootin" and there is a drop down menus with versions of linux and puppy, it will download right onto your USB. 

If you are stil having trouble try asking on their forum or IRC. They have a few tricks to get it to boot. I haven't had any trouble but I understand some computers can be tricky.

---

### Post by bob1866 on 2012-06-25
Thx robtygart, problem solved :)

---

