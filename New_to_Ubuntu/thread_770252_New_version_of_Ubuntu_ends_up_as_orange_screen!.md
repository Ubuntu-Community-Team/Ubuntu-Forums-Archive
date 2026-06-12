---
title: "New version of Ubuntu ends up as orange screen!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by andrew_jmdata on 2008-04-27
Hi - I downloaded and installed the new release of Ubuntu on Thurs/Fri.  

When I tried to re-start the PC (Dell 600mhz with 256Mb Ram) I got some error messages:

vm.mmap_min_addr error

Also, 

etc/rcs.d/S10vdev:105: /bin/udevmonitor: notfound

Then when it trundles on I get a message saying do I want to configure my graphics card manually/contine/cancel.  If I click continue/manually I end up with a blank orange screen with nothing on it excepet the mouse pointer.

I can't get beyond this point.

It all worked reasonably well before this though I could never get a screeen to be 1024. It either was stuck on 800 (couldn't change it) or on the odd occasion when I changed to 1024 it would change back to 800 on next reboot.

Apart from my 1st job 20 years ago, where I did loads of Unix shell programming... I know little about Linux!!

Any ideas?

Thanks


Andrew

---

### Post by TeoBigusGeekus on 2008-04-27
Boot up in recovery mode with grub and type

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the vesa driver and see what happens...

When you exit the reconfiguration program just type

```
reboot
```

---

### Post by Joeb454 on 2008-04-27
Hi there,

With that Processor & RAM I would recommend using Xubuntu, it's less resource intensive than the standard Ubuntu, therefore better suited to older systems :)

---

### Post by andrew_jmdata on 2008-04-27
Hi - booted in recovery mode and did all the sudo dpkg... and got "xserver-xorg is broken or not fully installed"

Andrew

---

### Post by Joeb454 on 2008-04-27
Ok, try something very similar, if you are in recovery mode you should see ```
root@<your pc name>:~#
``` if so then just type ```
dpkg-reconfigure -phigh xserver-xorg
``` This creates a new xorg.conf file.

Let me know if it brings back the same error

---

### Post by andrew_jmdata on 2008-04-27
Get same "xserver-org broken.."

---

### Post by mister_pink on 2008-04-27
try
```
apt-get install --reinstall xserver-xorg

```
in recovery mode

---

### Post by andrew_jmdata on 2008-04-27
Ok, typed what you suggested and it said same thing, tried a couple of variations (spaces/dashes) and it set do... (sorry can't rcall) and it spend about 10 mins installing, reconfiguring and whirring away... I thought... ah all solved now.

Reobboted and have exactly the same problem!

Am thinking to reinstall Ubuntu from disk was sent last year. There is nothing on the Linux box, it was an experiment to see if I could network with my Windows XP PC.

Unless anyone has any more ideas... I will re-install.

Thanks

Andrew

---

