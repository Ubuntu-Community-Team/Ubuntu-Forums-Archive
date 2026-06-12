---
title: "how to run a program"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Agent26 on 2011-11-15
Hi there all, 
I was wondering some more noob stuff....
 
how can i run a intillation CD of lubunto from a running xubunto please.
 
(I have tried severall times with the normal bios change ,bot from cd ect)
For some reason it just goes to some busy screen so i'm trying to get around that.
Also is there a task manger because xubuntu is on an underpowered machine and keeps freezing.
 
So my plan is run the discfrom xubunto.
 
p.s....I dont understand how to use terminal atall.
Please help, thanks.

---

### Post by Elfy on 2011-11-15
Did you manage to install the xubuntu properly? 

Assuming you did - I would first check the md5sum of the lubuntu iso you have burnt. 

Do you still have the iso to burn the disc from?

If you have - where is it located - is it in the Download folder, on the Desktop?

---

### Post by WasMeHere on 2011-11-15
Hi Agent26,

What computer is it? Is there an internal CD/DVD drive?

It would be possible to run Lubuntu in a virtual machine from Xubuntu, but if the machine is 'underpowered' it is not a good idea.

Instead keep trying to get the installation disk run a live system 'test Lubuntu without installation' by rebooting your machine with the CD inserted. Is there a function key F9 or F10 ... that can be pressed shortly after reboot to get a menu to select 'boot from ...'?

Have fun finding out :-)
Olle

---

### Post by Agent26 on 2011-11-15
Hi there guys,
Yes I still have the iso but it's on another computer, ive been downloading and burning on my laptop and then poping the disk in to the desk top.
I saved the files though so if i will need them, I still got them.
 
Olie, the machine is a desk top that is a bit old, got it in 2000 with millenium edition on and cant get rid of it(a bit sentimental). I want linux to make it fast again.
it has amd duron 900 mhz processor and 256mb ram.
 
Xubunto installed of the disk easy and it runs nice untill, crunch, it freezes up and doesn't try to come back even after 10 mins, one freeze andit's thepower button.
 
Lubunto seems more likley but dam I just cant get a disc to run.
 
I can change my first boot to the disc drive but soon during insatll it drops me of at a busy box screen.
Be nice if i could just typr run like the old speccy days.

---

### Post by snowpine on 2011-11-15
If you already have Xubuntu working, then you don't need to reinstall. Simply open the Software Center and install Lubuntu Desktop, or if you prefer the terminal:

```
sudo apt-get update
sudo apt-get install lubuntu-desktop
```

Then, log out, and from the login screen, you can select Sessions, LXDE to switch to Lubuntu.

I doubt Lubuntu will magically make your slow computer into a fast computer, but perhaps it will give you a small performance boost over Xubuntu. Good luck! :)

ps If you decide to get rid of Xfce (Xubuntu) entirely and go with "pure" LXDE (Lubuntu) this guide will help you: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by Elfy on 2011-11-15
I would check the md5sum of the iso and check the integrity of the cd before looking further, 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

The hashes to check can be found here 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If those are ok then we can try some other things.

---

### Post by mike555 on 2011-11-15
The "live " cds take about 512 memory to run ...... but you can install from the Alt .iso ...... I recommend you buy another 256 RAM for that old computer .....

---

### Post by Agent26 on 2011-11-15
Thanks for the help guys, I just tried another time but with a different disc from another place but the same.
I suspect it's my aged machine.
 
I shall try and check the disk with those instructions and also try install with that terminal code. Got to get used to it at some point.
 
Thanks again guys, Im off now to get this up and running.
 
P.s it's a real shame about xubutu as that was fast and looked great but it is just to much for my aging system.
 
Certenly would like to buy a bit of ram.

---

### Post by snowpine on 2011-11-15
> **Agent26 said:**
> Thanks for the help guys, I just tried another time but with a different disc from another place but the same.
I suspect it's my aged machine.
 
I shall try and check the disk with those instructions and also try install with that terminal code. Got to get used to it at some point.
 
Thanks again guys, Im off now to get this up and running.
 
P.s it's a real shame about xubutu as that was fast and looked great but it is just to much for my aging system.
 
Certenly would like to buy a bit of ram.

See my post #5. You do not need  to download a new .iso, you do not need to burn a CD, you do not need to reboot, you do not need to reinstall.

Lubuntu is simply Ubuntu plus the LXDE desktop, which you can install with a few clicks in the Software Center.

---

### Post by Agent26 on 2011-11-15
Thankyou Snow pine, I just went in got it installed and presto.
It was that easy but thanks to all else as too forall info's good info as i'm just over from windows.
 
This terminal seems a bit complex at the moment.
Can some one tell me a simple program to enter in(in step by step lamens terms) and a link to the threads here about it would be brill, thankyou. 
 
Thanks again people

---

### Post by Rex Bouwense on 2011-11-15
Welcome.  Here is a site for you to start:
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
This will answer any questions that you have or point you in the right direction for all things Lubuntu.  Amjjawad and the others that monitor that site are the greatest.

 A Site for information on the terminal:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Agent26 on 2011-11-19
Thankyou Rex, I will be giving this a good read.
Starting to get there now and thankyou.

---

