---
title: "ubuntu hangs on startup after update"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by elejele on 2012-04-27
Hey guys,

I updated to 12.04 yesterday and now Ubuntu hangs after  displaying the startup screen. Among other things that are displayed on  screen is, and I don't know if this is normal or not is

unhandled kernel version ('uname -r' = 3.0.0-17-generic)How do begin to fix the problem?

---

### Post by elejele on 2012-04-28
hmm, i tired tinkering with revovery mode but to no avail. I scanned the disk for errors, connected to the network but the dpkg fix packages didn't seem to work

i don't wanna go back to windows. how to I begin to diagnose the problem?

---

### Post by yrohinkumar on 2012-04-28
Hi Elejele,

I guess it is the same bug quoted here...I'm facing the same issue...I guess it is either due to grub not being updated or 3.2 (latest kernel version in ubuntu 12.04) is not in the old list where 3.0 is the highest version

[http://askubuntu.com/questions/74338/unhandled-kernel-version-error-when-trying-to-install-laptop-mode-tools]("http://askubuntu.com/questions/74338/unhandled-kernel-version-error-when-trying-to-install-laptop-mode-tools")

I'm going to install jupiter from root mode in recovery...if that doesn't work I'll see the other method & let u know...

---

### Post by yrohinkumar on 2012-04-28
Nope...making change in the script doesn't work...it gets me out of the loop but booting still hangs up with lot of irrelevant info...
Booted through ubuntu alternate cd and going through rescue procedure...will let u know if I find something working :)

---

### Post by elejele on 2012-04-29
Cool, thanks. Would disabling laptop tools from the live CD at least allow me too start ubuntu, or would something really bad happen. Also what do you mean by rescue procedure?

Edit:
I also tried modifying the usr/sbin/laptop_mode with the same results as you reported. i did notice that GRUB displays kernel 3.0 instead of 3.2. I ran update GRUB from recovery mode but that didn't change anything

---

