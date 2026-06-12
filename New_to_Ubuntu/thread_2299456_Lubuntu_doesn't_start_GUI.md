---
title: "Lubuntu doesn't start GUI"
date: 2015-10-18
forum: New to Ubuntu
---

### Post by saul10 on 2015-10-18
Hello good afternoon

I install lubuntu 14 on a old pc (celeron, intel chipset graphics).

All was good, but lubuntu was updated adn after that the GUI doesn't start. 

Using terminal (as a root) I tried to run "startx" but it give me an error:

Error setting MTTR (base=0x44000000, size=0x03000000, type=1) Invalid argument (22)
xinit:  unexpected signal 2

I run command dmesg |grep -i agp
82810E DC-133 (CGC) Chipset Graphics Controller
Intel Corporation
32 bits
66 MHz

intel i810 Chipset

Can someone help me to fix this problem? Thanks

---

### Post by sandyd on 2015-10-18
Hi, have you tried an earlier kernel?
You can access the grub menu by pressing SHIFT during boot.

If it does not show up, you can do the following.

Go to a terminal, and run
```

sudo nano /etc/default/grub

```
Remove the pound sign from in front of GRUB_HIDDEN_TIMEOUT (if any), and set the value to 10. This will be your grub menu timeout.

Save by pressing control+x, and run
```

sudo update-grub
```

You should now have a grub menu during boot. Choose Advanced Options for Ubuntu, and choose an earlier kernel whose name does not end in "recovery".

---

### Post by saul10 on 2015-10-20
Yes, I try to use an earlier kernel with the same result. I use recovery mode to access to the terminal mode. In all cases (new and old kernel), the result was the same: startx command send me an error. I checked similar problems but those problems were with a specific graph (nvidia), no one with intel controller. 


Next weekend, I'll check another distribution (puppy linux), the PC is a really "museum piece". In my usual laptop I use ubuntu without hard problems.

---

### Post by tgalati4 on 2015-10-21
Boot into BIOS and increase the shared video RAM.  Increase from 64 MB to 128 MB or greater.  Look in /var/log/Xorg.0.log for errors.

---

### Post by Bashing-om on 2015-10-21
saul10; Hello;

Be also aware;  the command to start the GUI from terminal in lubuntu is :
```

sudo service lightdm start

```
for 14.04 (-)  upstart; in 15.04 + the initiate system is systemd, and the startup is different.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

