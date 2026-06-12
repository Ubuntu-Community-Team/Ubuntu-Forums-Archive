---
title: "Curious problem with setting up Ubuntu"
date: 2019-06-07
forum: New to Ubuntu
---

### Post by david1903 on 2019-06-07
I am new to Linux, and want to try it out.  I have read many articles on how to do this, and have dutifully downloaded the iso and loaded into Virtual Box.  My VB works well with another OS (XP) but not with Linux, since I cannot get out of terminal and start any GUI.

"sudo apt-get install Ubuntu-desktop" gives me hundreds of text lines at speed and always comes back to the text prompt.  Most of the 'solutions' that I have looked at and tried give the same result - always back to the prompt.  I have tried using install with a USB but there is no difference.  If I look at software that can installed or updated, I am offered over 2 GB of updates, which, when run, still fail to move my system off the prompt.

What, guys, should I be doing next?

---

### Post by cruzer001 on 2019-06-07
What is your host system?  XP?

---

### Post by david1903 on 2019-06-07
I am running Windows 10.

---

### Post by cruzer001 on 2019-06-07
I have win10 running vBox and ubuntu guest, works fine.  I did install the extension pack, but it can be done later.

If you did a mini install then your posted ubuntu-desktop command (with small u) will download about 1200/1500 packages.  I use a different desktop and its about a 1G download.  If you are not seeing any errors then let it process.  Try
```
sudo apt -f install
```
if you can

There are lighter desktops.

---

### Post by ajgreeny on 2019-06-07
How did you install the Ubuntu you have used, and which version was it?

The easiest way is to set up a new VM in Vbox, name it in first screen, give it as much memory as you can afford but not more than half of the host machine's amount. choose to create a new disk (vdi) of the recommended size or larger.

Once created choose to start it, and in the first screen there will be an option to point to the downloaded ubuntu.iso image file you have somewhere downloaded on disk.  If your .iso file was a server or minimum install version there will be no GUI and you will need to add that along with all the other applications you need.

See [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by TheFu on 2019-06-07
Everything in every OS, except MS-Windows, is case-sensitive.
```
sudo apt-get install Ubuntu-desktop
```
is incorrect. Wrong case.  Every Unix-based OS works this way - so OSX, iOS, Android, and all versions of Linux are case sensitive.

You shouldn't have to see a prompt on a fresh install of any Ubuntu desktop version.  There should be some point-n-clicking, but that's about it.  The only way a 2GB download would be offered would be if you installed the wrong base packages in the wrong distro release.

Would be best NOT to install the default "Ubuntu"  version. Inside a virtual machine, you want a lighter desktop - so Mate, XFCE or LXDE are better.

Also, you should install an 18.04 variant, not 19.xx.  All 19.xx releases only have 6 months of support.  18.04 is an LTS - Long Term Support with 5 yrs of support - so 2023.  For someone new, that is extremely important.  [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/) is probably what you need/want.  

Give the virtual machine 1 vCPU and 3-4GB of RAM.  The storage should be VDI and 20-25G of total space.  On the Display page, the video RAM should be 128MB (the max).  You can change everything easily later except the total storage, so don't worry too much.  If you put the VDI file on an SSD, performance will be pretty good, except for the GPU stuff. That always has to be rendered using the CPU regardless of what $900 GPU is inside the computer. In the virtualization world, the real hardware isn't seen by any guests without complex, difficult, effort.

And just to get your head wrapped about the most important things about Linux from a Windows standpoint, read this: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

---

### Post by david1903 on 2019-06-08
Thank you for your helpful reply.

---

