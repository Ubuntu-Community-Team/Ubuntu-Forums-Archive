---
title: "PPC, b43 wireless driver on Powerbook G4"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by Eudaimon on 2012-09-23
Hi all, 

I'm running a Powerbook G4 (powerpc, 512 MB ram), and I've already successfully installed Ubuntu 10.04.  I'm trying to upgrade to Lubuntu, and here are the successful steps thus far: 


[LIST=1]
[*]boot into open firmware
[*]type in "boot cd:,\\:tbxi" - (Lubuntu 12.04 iso live cd loaded on the CD)
[*]yaboot opens up
[*]type "live b43.blacklist=yes"
[*]live cd opens, click on Install Lubuntu 12.04
[*]"Completely erase Ubuntu 10.04, install Lubuntu 12.04"
[*]entire installation process runs smoothly, with ethernet cable attache
[/LIST]
That's where success ends.  When installation finishes, it asks to reboot to finish install, but the computer freezes before it fully shuts down.  After further research it seems like a problem with the b43 wireless driver again.  Grrrr.  

After trying ~$ sudo apt-get install b43-fwcutter firmware-b43-installer    again no luck.   
startup error says firmware file "b43-openucode5.fw" not found.  When I try to log in to Live, download it, and reboot, it crashes on reboot again.  Back to the beginning. 

Suggestions?

---

### Post by daslinkard on 2012-09-23
These following sudo commands should do the trick for you...```
sudo apt-get remove --purge bcmwl-kernel-source
``````
sudo apt-get install linux-firmware-nonfree
```

You may have to restart your PC....if that doesn't work....can you display the output of the following command:

```
lspci
```

---

### Post by Hadaka on 2012-09-23
hi, go into bios,disable the wireless pci card. then load 12.04 and let it ask you
to boot to complete the install. If if loads ok and you are able to access the internet
with the ethernet cable, then  make sure b43 is still blacklisted. boot back into bios
enable the wireless then boot back to 12.04 and run your b43 install commands. then
remove b43 from the blacklist, boot and it should activate your card.

---

### Post by Eudaimon on 2012-09-24
Thanks for helping! 

Hadaka, could you let me know the prompt to disable the wireless from open firmware?

Linkard, removing the bcmwl didn't work, it says "virtual packages like 'bcmwl-kernel-source' can't be removed."   lspsci says a lot, but the key parts are that its a bcm4318 wireless.  

still froze on reboot.  had to hard shut down when the screen goes broken-nintendo.  

could you help me with a few more possibilities?

---

### Post by daslinkard on 2012-09-24
Please try the following sudo command and once completed restart your machine....

```
sudo apt-get install b43-fwcutter
```

---

### Post by Hadaka on 2012-09-24
Hi, sorry for just now getting back to you, i'm not familiar with
appl machines, but, it would seem logical that when it first boots up
there should be some kind of ability to get into "setup" or..bios. The
wireless card needs to be disabled before it boots. I had the same
problem with many dell laptops with the same card 4318 when loading
12.04, yet 11.10 loads fine without interuption,but the b43 driver does need
to be loaded. Try going online and do a search for shutting off the wireless card
for your powerbook.

---

### Post by Hadaka on 2012-09-24
Hi, here is a link on how to turn off your airport card,if this doesnt work for
you, you might ask a mod to move this to the aapl forum.


[https://discussions.apple.com/thread/2735832?start=0&tstart=0](https://discussions.apple.com/thread/2735832?start=0&tstart=0)

---

### Post by Eudaimon on 2012-09-25
Hi guys, 

Linkard, I've done the  _sudo apt-get install b43-fwcutter _command many times and it doesn't solve the issue on my powerbook.  I've had to even go into the modprobe file and disable the wireless card there, which I get a successful shutdown, but upon restarting again the same problem occurs.  Grrr.  

Hadaka, unfortunately the wireless card is already turned off in the live session, but the driver is still there.  

Anyway, long story short, I'm reverting to Ubuntu 10.04.  I had to give up on Lubuntu, but I just don't have the patience to take this one any further.  Another time, another laptop, and maybe Lubuntu and I can be friends again then.  

Thanks so much everyone, for all your help! 

Signing off, Eudaimon

---

### Post by daslinkard on 2012-09-25
Please mark this as solved...good luck!

---

