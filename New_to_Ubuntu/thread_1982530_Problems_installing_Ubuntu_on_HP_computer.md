---
title: "Problems installing Ubuntu on HP computer"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-05-18
I have had trouble installing ubuntu on a HP computer for two years. I had 9.04 installed OK originally but tried to upgrade to 10.10. This failed for an undisclosed reason and locked up the computer requiring a hard reset. The installation of ubuntu has not worked since on this computer. Note this computer had a LAN connection as well as a wirless card.

Since then I have tried many times to install 10.4, 10.10,11.4, 11.10 without success. Each attempt ending in computer lockup. Note the demo mode worked from the boot disk each time.

I had another go this week at installing 12.04 inside windows. This also failed but I fiddled with the start up options and eventually found the installation was stalling because it could not find a driver for the wireless card (ASUS). I removed the card and used a LAN cable and restarted this time I got the installation to work in a kind of way with a default graphics. 

I had another wirless card that I installed and removed the installation and started all over. This time the installation completed flawlessly and I now have 12.04 working on this computer. I must add that I have Ubuntu 12.04 installed on three other computers witout problems.

My gripe is 
1. Why if the wireless card did not work for the new installation was the LAN connection not found?
2. If there was a problem with wireless cards Why was there not some indication of the reason

If I had known the wireless card was the problem I could hve changed it two years ago.

Barry

---

### Post by wilee-nilee on 2012-05-18
Can you post the wireless card?

Do you have enough ram and cpu, minimum for ubuntu to run good is one gig ram.

If you post more info on the HP, like details on the fails the errors, and the lspci readout we would probably be closer.

You probably had problems with the upgrade do to end of life on the 10.10, it helps to know when this was actually tried.

Details are the key here. :)

---

### Post by EB0V on 2012-05-18
Did you ttry a clean installation using a USB stick?

---

### Post by barrykgerdes on 2012-05-18
> **wilee-nilee said:**
> Can you post the wireless card?
Details are the key here. :)

The wireless card is a ASUS model WL-138G V2

Do you have enough ram and cpu, minimum for ubuntu to run good is one gig ram.

Memory no problem

If you post more info on the HP, like details on the fails the errors, and the lspci readout we would probably be closer.

The error I eventually got was to refer to a site
[http://wireless.kernel.org------](http://wireless.kernel.org------)  for driver info but I could not make anything out here. a catch 22 situation no internet!
After this the installation hung waiting for the solution.

You probably had problems with the upgrade do to end of life on the 10.10, it helps to know when this was actually tried.

No! at that time 10.10 was the current upgrade that was suggested. It started but eventuall the installation hung and no joy from then on.

As I said before a new wireless card fixed the problem.

Barry

---

### Post by barrykgerdes on 2012-05-18
> **EB0V said:**
> Did you ttry a clean installation using a USB stick?

No!
Did clean installations from Disk in both full mode and as a subset of Windows XP.

The problem was mainly no indication what was causing the installation to hang. If there had been a warning "no wireless card" or words to that effect I would have changed the card long ago. The wireless card had worked flawlessly in Windows so I did not suspect it til I got the message in 12.04 install.

Barry

PS I am not a prolific Linux user. I only keep it as an operating system to do test compiles of Stellarium when there are problems. So I am not fluent in its use even though I have been using it since version 6.04  B.G.

---

