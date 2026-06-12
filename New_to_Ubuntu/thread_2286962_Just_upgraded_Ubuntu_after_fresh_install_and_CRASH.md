---
title: "Just upgraded Ubuntu after fresh install and CRASH"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by karnival8 on 2015-07-16
So first, I'm very new to Linux and I don't know much so keep that in mind.

I dual booted my MacBookPro (latest model) with Ubuntu. I'm using rEFInd to boot. 
I'm doing the best I can to migrate over to Linux full time. (not off to a good start :) )

It worked great, got everything all set up and configured correctly.

After I ran apt-get upgrade and restarted the machine, linux jams right after grub. I get a blinking cursor and no action. 

When I choose to start in recovery mode from grub, the jam occurs after CPU #1 _ and I get a blinking cursor there. 

I have a Live USB ready to go, but no idea what to do next.

Anyone know anything about this or how to go about troubleshooting it?

---

### Post by dino99 on 2015-07-16
probably a graphic driver issue; but which ubuntu have you installed ? which graphic card/chipset is used ? with which driver installed ? (you can get an easy packages overview with 'synaptic')

---

### Post by karnival8 on 2015-07-16
I installed 15.04
MacBook 12,1

Made no driver installations. 

With the blinking cursor, I can't access the command.

---

### Post by karnival8 on 2015-07-16
I installed 15.04
MacBook 12,1

Made no driver installations. 

With the blinking cursor, I can't access the command.

---

### Post by toxx on 2015-07-16
If you use ctrl+alt+F1 are you able to access the text-only tty? If so, can you run dmesg and check for error messages?

---

