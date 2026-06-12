---
title: "Nvidia GTX 550 ti not working"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by david476 on 2011-11-22
I recently bought a GTX 550 ti graphics card. the user manual said to install drivers after putting the card in my computer. when I try to boot, it opens ubuntu as if it were in terminal. should I install the drivers before using the card?

I have tyed everything so far on this URL

[http://ubuntuforums.org/showthread.php?p=11486582#post11486582](http://ubuntuforums.org/showthread.php?p=11486582#post11486582)

---

### Post by oldsoundguy on 2011-11-22
> **david476 said:**
> I recently bought a GTX 550 ti graphics card. the user manual said to install drivers after putting the card in my computer. when I try to boot, it opens ubuntu as if it were in terminal. should I install the drivers before using the card?

The drivers that came on your install disk are for WINDOWS ONLY.

Have had a lot of luck just shutting down, put the card in, and turn it on in Linux.  Sometimes you have to install the restricted driver, but your system will let you know that. It SHOULD work with the default driver system.

---

### Post by david476 on 2011-11-22
I have already tried restarting, the drivers I was talking about were the ones provided for download on nvidia's website

---

### Post by papibe on 2011-11-22
Hi david476.

I would advice you to uninstall the driver that you got from the Nvidia site, remove your Xorg config file and restart.

Then install the Nvidia driver that has been tested for your version of Ubuntu in 'Additional Drivers'.

Tell us if you need more help with that.
Regards.

---

### Post by rectec794613 on 2011-11-22
> Hi david476.

I would advice you to uninstall the driver that you got from the Nvidia site, remove your Xorg config file and restart.

Then install the Nvidia driver that has been tested for your version of Ubuntu in 'Additional Drivers'.

Tell us if you need more help with that.
Regards.

To uninstall the Nvidia site-provided driver, rerun the installer and follow the prompts. To remove the config file, open a terminal and enter:```
sudo rm /etc/X11/xorg.conf
```
Restart

Then, you could try installing *nvidia-current*, the standard driver for GeForce cards series 6 and up. (Although sometimes newer cards can have bad support.
> GPUs such as GeForce series 6 or newer are supported.
Start a terminal and enter:
```
sudo apt-get install nvidia-current
```
Enter your password and let it install. I would restart afterwards, so you can use the driver.

---

### Post by Dblkickflip720 on 2011-11-22
> **rectec794613 said:**
> To uninstall the Nvidia site-provided driver, rerun the installer and follow the prompts. To remove the config file, open a terminal and enter:```
sudo rm /etc/X11/xorg.conf
```Restart

Then, you could try installing *nvidia-current*, the standard driver for GeForce cards series 6 and up. (Although sometimes newer cards can have bad support.

Start a terminal and enter:
```
sudo apt-get install nvidia-current
```Enter your password and let it install. I would restart afterwards, so you can use the driver.

Im having the same problem, and I tried to install nvidia-current and got this
```
sudo apt-get install nvidia-current
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 247 not upgraded.
Need to get 0 B/55.2 MB of archives.
After this operation, 170 MB of additional disk space will be used.
(Reading database ... 143108 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_280.13-0ubuntu6_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@david-A770E3:~$ 

```
Any idea what could be wrong? I am trying to install the driver for my nvidia gtx 560 ti

---

### Post by rectec794613 on 2011-11-22
> **Dblkickflip720 said:**
> Im having the same problem, and I tried to install nvidia-current and got this
```
sudo apt-get install nvidia-current
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 247 not upgraded.
Need to get 0 B/55.2 MB of archives.
After this operation, 170 MB of additional disk space will be used.
(Reading database ... 143108 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_280.13-0ubuntu6_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@david-A770E3:~$ 

```
Any idea what could be wrong? I am trying to install the driver for my nvidia gtx 560 ti

Looks like the package is corrupted. Try again and see if it works. If not, you can go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), scroll down to search, select your Ubuntu version from the menu and download nvidia-current from the site. If *that* doesn't work, it could be a bad internet connection, resulting in lost packets. Or it could be on their side.

---

### Post by david476 on 2011-11-24
I tried this two times and got the same result. It cannot find xorg.conf or download nvidia-current. I cannot easily post the code because as I stated earlier Ubuntu opens like a giant terminal window in black and white

---

### Post by david476 on 2011-11-26
I'm making a new post for this issue.

---

### Post by searchfgold6789 on 2011-11-28
Hrm. You should try:```
sudo apt-get clean
```then try```
sudo apt-get install nvidia-current
```again.

---

### Post by david476 on 2011-11-30
same thing, it says it cannot find some of the archives after it doesn't do anything for your first command (after I type my password).

---

### Post by MrSpike16 on 2011-12-01
What release of Ubuntu are you using (sorry if I missed it)?.
Ubuntu 10.04 (and also 10.10 I believe) doesn't have Nvidia drivers for our cards (I have the GTX 560 Ti).

To install the driver, I used the X-swat repository:

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

```

If you have Ubuntu 11.04 or 11.10, you can still use the above too.

---

### Post by MrSpike16 on 2011-12-01
Couldn't put another code box in my message above without losing the first one so created a 2nd message.

If you are using Ubuntu 11.04 or 11.10 you could try:

```

sudo apt-get update
sudo apt-get install nvidia-current


```

The first command will re-sync your package lists to the repositories
if this is the problem.

---

### Post by bvt on 2012-01-04
Finally got my GTX 550 TI working using Mr. Spike's repository ppa:ubuntu-x-swat/x information.  It was pretty easy on my Ubuntu 11.10 machine (using Gnome shell thank you) with AMD Athlon(tm) II X4 640 Processor.  But on my machine using AMD X2 Dual Core, I had to use the 10.04LTS package.  Never could get it to work with 11.10.

---

### Post by ataybuntu on 2012-03-06
It is working very well with my ubuntu. I found this solution after trying many methodes:
A. IF INSTALLING from a Live-CD:
1- After seeing the first screen press F2, choose language, press F6 than edit the command line you will see  .. replace th words (quiet) and (splash) by nomodeset
2- Choose with the arrow-Tabs (TRY UBUNTU)
3- the system will boot and you will get a desktop with low graphic resuliotion
4- install ubuntu from the GUI
5- when the install process is finished you will be asked if you want to reboot or continue trying ubuntu, choose to continue trying
6. You must now edit the installed system ... open the file manager and click on the harddisk symbol you think it is the root partion
7. open a terminal and give the command  ls /media
8. you will see some numbers (the now given name of the partions you had mounted by clicking on the harddisk symbols)
9. search for the partion with the boot folder   (ls /media/xyz*  ls /media/123*)
10. for exampel: ls /media/222??* givs (boot) than try: sudo gedit /media/222*/boot/grub/grub.cfg in order to be able to edit the boot config file
11. If you get errors than try it with:    sudo nano /media/222*/boot/grub/grub.cfg
12 search the menuentery :
menuentry 'Ubuntu,  Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root 48f5ba9f-9acf-4fa5-be34-ba3e38c5ec49
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=48f5ba9f-9acf-4fa5-be34-ba3e38c5ec49 ro   **quiet splash** vt.handoff=7

13 replace    quiet and splash     with   nomodeset
12 save the file (if using nano ctl-Tab and O)
14 reboot - (still having low reolution)
15 update your system  (in terminal: sudo apt-get upgrade)
16 be sure that the kernel is updated (3.0.0.16)
17 sudo apt-get install build-essential kernel-headers
18 download the driver package from nvidia.com
19 reboot
20 open a terminal and cd to the folder where the *run-file has bin downloaded
21     chmod a+x *run
22     sudo service lightdm stop
23    login in the text consol
24   cd to the folder of the *run file
25  sudo ./*run     answer always with "yes"
26 It is done, just type sudo reboot and you will have very smooth graphics with minimal CPU-load (under 3%)

there is no need to blacklist "nouveau", and it is not recommended. the drivers nvidia and nouveau seems to work fine together on this graphic card. Blacklisting "nouveau" caused another firmwaremodules not to load. I noticed higher CPU-Load (7%) and longer boot time if "nouveau" is blacklisted

---

