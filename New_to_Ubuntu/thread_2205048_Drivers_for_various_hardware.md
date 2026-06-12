---
title: "Drivers for various hardware"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by greg35 on 2014-02-11
I recently purchased $700 of computer parts with the intention of running games, Windows, Linux Ubuntu, doing work, watching movies, browsing, and similar tasks. Now, I have successfully built it, downloaded all Windows drivers, and run a few games, but I still have yet to find drivers for the MB, and quite possibly the GPU. My list of parts is: 
MB: Gigabyte GA-990FXA-UD3 (rev. 4.0)CPU: AMD FX-8320
RAM: 2x4GB Crucial Ballistix Sport
HDD: Hitachi travelstar 5400 RPM 320 GB and Seagate 7200 RPM 80 GB
GPU: Gigabyte GV-R927OC-2GD
PSU: 750 Watt Corsair
CASE: Zalman Z12 plus
Can someone please give me a link for the drivers, as well as detailed instructions? Also, I am a beginner, this is my first build, and hopefully, this will be my first time running Linux.
Thanks, I will greatly appreciate help.

---

### Post by wildmanne39 on 2014-02-11
Hi, almost all drivers needed will be included in ubuntu, just make a livecd or liveusb disk of ubuntu and then boot ubuntu livecd or liveusb and click try instead of install to see if everything works then you can install it.

Get ubuntu from here:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by bc.haynes on 2014-02-11
Hey, ****,
How to get your questions answered more quickly -->>  [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by G_Ajith_Kumar on 2014-02-12
Welcome Greg.

Since you have purchased the components recently, there is a very good the possibility that  they would all be compatible...a very broad  statement with a positive look at things :). As suggested earlier , may be you could download Ubuntu, say the 12.04 stable version, (with support till 2017) and make a CD/DVD. While you reboot with it (reset the BIOS to boot from CDRom, if need be), you will get an option to "Try it or Install it". Trying would mean getting in to Ubuntu environment from the CD/DVD with out any installation on the hard disc. If all goes well, then you know that all your hardware is compatible with Ubuntu. Any minor issues that come up could be solved with help from the forum too. Good Luck!!!!!

link for downloading Ubuntu 12.04 [http://releases.ubuntu.com/precise/ubuntu-12.04.4-desktop-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.4-desktop-amd64.iso)
link for making a DVD?CD  [http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
link for running Ubuntu from a CD [http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)
link for configuring BIOS [http://www.wikihow.com/Set-Bios-to-Boot-from-a-CD-ROM](http://www.wikihow.com/Set-Bios-to-Boot-from-a-CD-ROM)

Happy Ubunting :) :)

---

### Post by mastablasta on 2014-02-12
seems to be some old disks... :-O

anyway about the GPU what chip does it have AMD or nvidia?? Gigabyte just puts it all together and sticks a brand on it. you might need proprietary drivers (this is installed via an aplication).

otherwsie drivers in linux are built into kernel. so newer kernel=newer drivers. only a few drivers are outside these are closed source proprietary drivers (usually for GPU and wi-fi) which can't be inlcuded in kernel. for these there is additional drivers applciaiton to help you with finding them and installing them.

---

### Post by Mark Phelps on 2014-02-12
According to Google, Your Gigabyte card is an AMD Radeon R9 270.  That might pose some serious problems.

I recently acquired a Radeon R7 240 -- and, unlike with my previous AMD HD 4290, the open-source drivers are garbage.  They won't give me full resolution or multiple desktops and any attempt to install them through the repositories crashes my system.

Good Luck

---

