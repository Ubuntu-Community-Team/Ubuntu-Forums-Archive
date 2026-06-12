---
title: "synaptic package manager &amp; hplip in ubuntu 20.04"
date: 2020-07-27
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2020-07-27
I'm using Ubuntu 20.4. I have a hp Deskjet all in one printer. When I went to print a file it didn't work. So if found out that I had to reinstall Hplip.  I installed Hplip 3.20.6 via source forge. It installed but there was a device communication failure error 5012.  Someone suggested that I update my IP address & so I did that via hp-setup. It worked. After that I turned off the computer. When I rebooted computer and went to print a file then the Hplip software failed to work. So I removed Hplip and all components. [SIZE=2]Someone suggested that I should use Synaptic package manager for Hplip software. So I did this and it installed and it was in my system. Then I discovered that I still have communication device error 5012. [/SIZE]So I removed Hplip and all components via synaptic package manager. From cups website I removed the printer. I tried to again install from Sourceforge but then I got message not install as root user. I don't know how to do that. It seems like I'm in a Kafkaesque situation. Can anyone shed some light on this problem so I can get the printer to work. Thx

---

### Post by ajgreeny on 2021-01-18
You haven't given any details of your method of installing hplip, nor your printer, and perhaps most importantly the method you are connecting, or trying to connect, with the printer.
Are you using USB or wireless connection, and if wireless, does the printer use a static IP address?
If the repo version works for your printer the easiest way to install hplip if from the Ubuntu repos as you already have.
However, if the problem is caused by a wireless connection problem you must solve that first, and I think a static IP is the first likely cause of your problem.

If necessary, because of a new printer model not yet supported by the hplip version in 20.04 I suggest you download the hplip-3.20.11.run file from [https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip) and then run that file in terminal as shown in the webpage at [https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)

Start that script as user and at step 5 you will be asked to enter your password in order to continue.
The installation takes a few minutes but is very easy and each step is spelled out in the terminal as it proceeds.

---

### Post by rbmorse on 2021-01-18
and keep the .run file handy because you might need to run it again the next time Ubuntu pushes a kernel upgrade.

---

### Post by Autodave on 2021-01-20
I am thinking that this may be another issue with the 5.8 kernel since I have a relative's machine doing the same thing.  I tried everything a couple days ago, but nothing really worked,  If I removed the printer and hp-lip and reinstalled everything, I could get it to print one page and then nothing.  I am heading over there in a few hours to try again and will roll back and use the 5.4 kernel and report back.

---

### Post by Autodave on 2021-01-20
So, not a 5.8 kernel issue since it was still running 5.4.  What I did today was to disconnect the printer USB cable, deleted the printer, completely removed HP-LIP.  Rebooted.  Plugged USB cable into printer.  Printer was recognized.  Tried printing and it worked.  Tried again and it worked. Rebooted and printer still worked.  I never did reinstall hp-lip.

---

### Post by ajgreeny on 2021-01-21
> **Autodave said:**
> So, not a 5.8 kernel issue since it was still running 5.4.  What I did today was to disconnect the printer USB cable, deleted the printer, completely removed HP-LIP.  Rebooted.  Plugged USB cable into printer.  Printer was recognized.  Tried printing and it worked.  Tried again and it worked. Rebooted and printer still worked.  I never did reinstall hp-lip.
That does not surprise me in many ways.
Many, or perhaps most HP printers, along with many other makes are now fully operational in Linux as driverless devices.
Use ***driverless*** command in terminal anmd you may well see an output something like this, which is what I see with my HP Envy 4527 all-in-one
***ipp://HP%20ENVY%204520%20series%20%5BDC214D%5D._ipp._tcp.local/***

---

### Post by Paddy Landau on 2021-01-21
> **tuesdaybarrett said:**
> … I installed Hplip 3.20.6 via source forge. …
Definitely use the standard repositories to install hplip as your first choice. I wouldn't install directly from sourceforge.

I have no problem hplip on my HP printer, and my installation was the default one.

You might have some leftover bits from the original sourceforge installation. If the advice from @ajgreeny doesn't work, try this.

[LIST=1]
[*]Remove all hplip-related packages that you've installed via sourceforge.
[*]Open Synaptic, and uninstall everything beginning with hplip (hplip, hplip-data, etc.).
[*]Open a terminal and enter these commands, in order.
```
sudo apt autoremove
sudo apt update
sudo apt upgrade
sudo apt install hplip hplip-data hplip-doc
```
[/LIST]
Restart your computer and retest.

If your printer is wireless, it needs a static IP address (as @ajgreeny said).

---

