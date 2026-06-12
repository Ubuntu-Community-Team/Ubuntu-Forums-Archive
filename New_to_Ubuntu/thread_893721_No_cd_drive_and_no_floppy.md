---
title: "No cd drive and no floppy"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by pritesh.123 on 2008-08-18
Hi everyone, got a fairly old laptop that im trying to install xubuntu on as the laptop is quite slow. Its only going to be used for browsing so xubuntu should be fine for what its going to be used for.

Now here's the problem, there is no floppy drive so I cant use sbm and there is no cd drive. Booting from a usb drive is also not possible.

Is there any other way I can get xubuntu on it? even if it means removing the hard drive and install from a desktop.

Thanks

---

### Post by philinux on 2008-08-18
Yep unetbootin 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by pritesh.123 on 2008-08-18
Hi, all ready thought of unetbootin but thought that was to install from a usb key.

Can I remove the hard drive from the laptop, connect it to my desktop from there run unetbootin and select the hard drive that I just installed (form the laptop)?

thanks

---

### Post by halitech on 2008-08-18
if you have any operating system currently on the hard drive you should be able to run unetbootin and just select the option to take over the entire drive. Thats what I did with my old compaq with no cdrom and it worked fine.

---

### Post by pritesh.123 on 2008-08-19
Hi at the moment there is no os installed.

---

### Post by halitech on 2008-08-19
ok, so no possible way to boot anything currently on the machine and no OS. Looks like your only option is to take the drive out and put it in a machine that has booting from one of the 3 and installing and putting back in the laptop

---

### Post by Sef on 2008-08-19
> ok, so no possible way to boot anything currently on the machine and no OS. Looks like your only option is to take the drive out and put it in a machine that has booting from one of the 3 and installing and putting back in the laptop

Not correct.  Do you have access the net?  If so, then check out [Server and network installations]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD").

---

### Post by halitech on 2008-08-19
not to disagree with someone who has been around longer then I have but if he has no cd rom, no floppy, can't boot from USB and nothing currently on the hard drive now, how is a server install going to work?

edit: forgot about the pxe boot but that will depend on him having a machine he can set up as a dhcp/pxe server. My apologies Sef.

---

### Post by pritesh.123 on 2008-08-21
Hi guys sorry for the late reply, I took the hard drive out of the laptop that I wanted xubuntu on and put it in another laptop that allowed me to boot from cd. I then put the hdd back in to the original laptop and it seems to be working fine.

Just having one slight problem which is that I cant browse the net. I have scanned for networks, found mine and selected it. Entered the wpa and selected dhcp but when i open firefox i get the message saying it cant find the server or something to that effect.

---

### Post by philinux on 2008-08-21
Start a new thread for that one.

---

### Post by LowSky on 2008-08-21
reboot the router, 99% of all issues when you can see and use your wireless card are cuased by a bad router connection, just turn it off then back on, and may, just maybe that will fix the internet issue.

---

