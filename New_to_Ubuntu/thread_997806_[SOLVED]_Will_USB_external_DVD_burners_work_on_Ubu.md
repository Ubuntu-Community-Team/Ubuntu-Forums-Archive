---
title: "[SOLVED] Will USB external DVD burners work on Ubuntu 8.10?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by resander on 2008-11-30
Got a Compaq D310 that has two optical drives, a CD drive and a CD writer/burner. The CD burner drive is working, the other is not but stops the dust getting in. Here is the output from lsusb:

ken@ken-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I guess this output indicates most ports are USB version 1.1.

I have looked at [www.amazon.co.uk](www.amazon.co.uk) and found Freecom DVD RW External DVD writer USB2 (model 29510) for 40 pounds that is getting an average of 4 stars out of 5 from 15 reviewers (the Roxio software that came with it let it down, otherwise it would have received a nearly perfect all 5 star score). Most/all reviewers seemed to be on PCs with Windows. Have not ordered it yet.

Will/should this burner work with Ubuntu 8.10?

If yes, I assume I just plug it into a USB port. It uses USB 2.0, but how can I find out which port/ports are USB 2.0?

---

### Post by razy60 on 2008-11-30
Have you checked the specs on your pc on google just did a quick check and it indicates that your pc has usb 2.0 on all 6 slots.
If it is possible it would be better to get a drive that runs on the internal connections (replace the drive that is not working) as a direct connected drive will always give better results, less disk failures etc. plus they are normally cheaper.
No reason why it shouldn't work though.

---

### Post by fr.theo on 2008-11-30
go into terminal and type "dmesg" to see where you device is located, as for Ubuntu 8.10 supporting external drive's it should, I had a DVD burner external drive in 8.04 LTS so I don't see why intrepid shouldn't support it.


but I could be wrong.

---

### Post by mips on 2008-11-30
I would rather replace the faulty internal drive, much better option.

---

### Post by resander on 2008-11-30
Thank you all.

So, maybe I should get an internal burner instead. Have never been under the hood and installed hardware before, so don't have any knowledge. Also I am well aware of 'If it works don't touch it'.

Are there any gotchas to be aware of and watch out for when replacing and installing optical drives?

Don't know if I am talking nonsense, but I would start by disconnecting the connecting cable from the faulty CD drive and connecting it to the new internal DVD burner while the latter is still outside the computer. Then what do I do? Turn off and restart the computer? Will Ubuntu then detect the new drive? Will I be able to check the new drive is working (while outside), e.g. by requesting K3B or Brassero to burn something?
Well, you can see I am total hardware newbie.

---

### Post by binbash on 2008-11-30
I am using 2 external dvd burners atm at intrepid.

---

### Post by mips on 2008-11-30
> **resander said:**
> Thank you all.

So, maybe I should get an internal burner instead. Have never been under the hood and installed hardware before, so don't have any knowledge. Also I am well aware of 'If it works don't touch it'.

Are there any gotchas to be aware of and watch out for when replacing and installing optical drives?

Don't know if I am talking nonsense, but I would start by disconnecting the connecting cable from the faulty CD drive and connecting it to the new internal DVD burner while the latter is still outside the computer. Then what do I do? Turn off and restart the computer? Will Ubuntu then detect the new drive? Will I be able to check the new drive is working (while outside), e.g. by requesting K3B or Brassero to burn something?
Well, you can see I am total hardware newbie.

1. First check whether you have SATA or PATA interfaces for drives.

2. DISCONNECT ALL POWER, switch of MAINS & unplug power cable.

3. Open case and disconnect power cable & sata or pata cable on faulty drive.

4. Undo clips or 4 screws and slide drive out the front.

5. Install new drive and follow the previous steps in reverse.

---

### Post by resander on 2008-12-01
An external USB burner would probably work, but I will go out and buy a Philips screwdriver and have a go at installing an internal burner.

Solved - many thanks.

---

