---
title: "Black Screen after boot-up"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by gazzadtfan on 2008-11-19
Hi All

Just received the 8.10 disc from Canonical today and did a clean install. It seemed fine until I updated all the software and tried to reboot. A black screen comes up with a prompt, as though I was in the terminal. I noticed before it arrived at the prompt the following messages:

kinit: name_to_dev_t(long list of numbers) = dev(8,17)
kinit trying to resume from /dev/disk/by-uuid/(another long list of numbers)
kinit no resume image, doing normal boot

it then boots and I login at the following:

Ubuntu 8.10 Gary_Desktop tty1

and finally goes to my normal prompt as though I was at the terminal

gary@gary-desktop:~$

I've tried looking at the forum and although others are having problems with the black screen I haven't seen anything which I think is the same as mine.

Can anyone help or show me the right direction to go down?

Cheers

gazzadtfan

---

### Post by Crafty Kisses on 2008-11-19
Try a couple of things, try running the following command:
```
startx
```
You should probably getting an error message seeing as how X didn't start in the first place, post the error back here. Then I want you to run these commands:```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now
```
Once it's rebooted and you are able to log in again, look in **System --> Administration --> Hardware Drivers** to see if your graphics card is on the list. Click the proper driver for the proper card. Don't forget to go into the BIOS to turn off the onboard video card controller first before you boot into recovery mode.

---

### Post by gazzadtfan on 2008-11-19
Codename

I did as you suggested but unfortunately I can't get as far as getting into Ubuntu yet. I did the sudo commands and then rebooted. When I do startx at the prompt I get the following errors:

xinit: Connection Refused (Err 111) unable to connect to x server
xinit: No such process (Err 3) Server Error

I don't know what the above means. Don't know if it is serious or not. Hope you can help.

gazza

---

### Post by gazzadtfan on 2008-11-28
Hello Folks

Unfortunately I'm still having problems with getting into 8.10. Can anyone please advise which way to turn as I'm going to have to resort to an earlier version of Ubuntu if I can't get this sorted which I don't want to have to do but I have no option.

gazza

---

### Post by philinux on 2008-11-28
It would help if you posted your pc specs and graphics card make and model.
Before you installed did the live cd work ok and give you a desktop environment.?

However. Boot up and when grub menu appears press escape. use the down arrow key to hight the second boot option labeled recover mode. when the menu appears choose xfix then when it's finished choose resume normal boot.

---

### Post by vgrisham on 2008-11-28
> **gazzadtfan said:**
> Hello Folks

Unfortunately I'm still having problems with getting into 8.10. Can anyone please advise which way to turn as I'm going to have to resort to an earlier version of Ubuntu if I can't get this sorted which I don't want to have to do but I have no option.

gazza

What kind of graphics card do you have?

---

### Post by gazzadtfan on 2008-11-28
Hello Folks

I'm currently using a Dell XPS 630 Quad Core machine (Q6600 @ 2.40hz) with 4gb Ram, acres of storage space with Ubuntu on a separate drive. I have dual graphics cards which are Nvidia GeForce 8800GT (500mb each).

I had this machine whilst using 8.04 and the only problem I had was with the Soundblaster X-Fi sound card which gave me no sound with Ubuntu. I know this is a long standing problem with this type of card and hopefully is somewhere nearly sorted.

As far as 8.10 is concerned I just can't get into it at all. I installed it and it seemed to work fine until I downloaded all the updates through the synaptic package manager and I've not been able to get into it since.

gazza

---

### Post by vgrisham on 2008-11-28
I'm not an expert at this stuff, but it sounds like your x-server is broken due to a bad driver for your nvidia card. I too have a gforce and it has given me fits since upgrading to Intrepid. 

If I were you, I would download the beta driver for your card from nvidia.com to a directory that you can access from Ubuntu (a thumb drive would work). I would then choose recovery mode from the grub menu, navigate to where you saved the file and code: sh (name-of-your-driver).run. Follow the onscreen instructions and say no when it wants to download files. Say yes to everything else and you should be good to reboot into Ubuntu.

EDIT: Here is the applicable NVIDIA [link]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

---

