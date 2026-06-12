---
title: "AMD 7670m: Cannot boot into gui"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by venkatramsam on 2014-05-23
My xorg.conf file is corrupted and I don't have access to the GUI. I can only run commands from the other ttys. Please do help me with this one. Also, is it possible to repair the OS with a bootable disk keeping my home folder and installed packages intact?

---

### Post by coldcritter64 on 2014-05-23
If you can boot to a tty screen and can connect to the network from the cli any graphics are relatively easy to fix. Not necessary to go to a bootable disc for such as yet, but yes a bootable disc can do as you are asking. 

Do you know your graphics card details like nvidia intel or amd etc ?  Do you use the open source or proprietary drivers from the card manufacturer ? These details will help work out what commands to use in a tty or possibly a recovery boot console etc. More serious problems with broken installs can be fixed with chrooting into the broken install from a live cd, but at this stage I don't think you will need that.

If you are having nvidia problems just purging all the nvidia packages from the command line and clearing xorg.conf and a reboot will get you to a Nouveau (open source driver) desktop from where you can reinstall the broken proprietary drivers (if that is what is causing the problem).

---

### Post by cwmoser on 2014-05-23
sudo apt-get remove nvidia*
sudo apt-get install nvidia-current

---

### Post by venkatramsam on 2014-05-23
My graphic card is amd 7670m.

---

### Post by squakie on 2014-05-23
> **cwmoser said:**
> sudo apt-get remove nvidia*
sudo apt-get install nvidia-current

You should've waited - the card isn't nvidia! ;)

---

### Post by squakie on 2014-05-23
That adapter seems to belong to the same group as my old Radeon 6000 series adapter.  For best results, install the flgrx-updates driver and support package:

sudo apt-get install fglrx-updates

That should get both, as I *think* the support package is a dependency (if it isn't, you can download it seperately).

Of course, you can't do this until you follow the above advice for getting online from a terminal session.

---

### Post by dannyboy79 on 2014-05-24
when at the tty console, can you install pastebinit, this will allow you to upload text files and provide you a link to paste here so we can view some log files of yours. here's the commands to run
```
sudo apt-get install pastebinit
```
```
pastebinit /var/log/Xorg.0.log
```
that should return a web link, tell us what that link is so we can view your Xorg log file to see what's failing.

---

