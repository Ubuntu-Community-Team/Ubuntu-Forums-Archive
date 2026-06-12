---
title: "Display shows as laptop on a desktop"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by Shadius on 2012-07-07
Hey everybody! :)

I've a fresh install of Ubuntu 12.04 LTS on my system with an ASUS P5P800 motherboard, 80 GB HDD, NVIDIA graphics card, and SoundBlaster Audigy sound card. My issue is that the display shows the monitor as a laptop. I've provided a screenshot. 

Here's some additional information:
```
shadius@shadius-asus:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)
shadius@shadius-asus:~$ 

```

How do I proceed to solve this?

---

### Post by codingman on 2012-07-07
I doubt this will affect you. 
It may offend you.

Anyways, it's probably just the drivers, no biggy.

---

### Post by Shadius on 2012-07-07
I figured it was something with the drivers, so how do I check what drivers the NVIDIA card is using and if I need to update it, how? It didn't offend me. :)

---

### Post by codingman on 2012-07-07
I'm not sure how to check, but in order to update the drivers, go to the NVIDIA website and then click on the drivers menu, and you can it from there, it's pretty self-explanatory.:p

---

### Post by Shadius on 2012-07-07
Yeah, I've tried the NVIDIA website, the autoscan fails. Having a difficult time finding the drivers for Linux. My CPU is a Pentium 4 64-bit but I've installed the Ubuntu 12.04 32-bit, so I should install the 32-bit drivers?

---

### Post by Shadius on 2012-07-10
Can anyone offer some help on getting this right?

---

### Post by bogan on 2012-07-11
Hi!, **Shadiu**s,

To check what nvidia driver, if any, is installed:```
lspci | grep -iA2 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```The System Details showing a Desktop Monitor as 'Laptop.', and failing to correctly identify the graphics card and driver, is a well known bug in 12.04 LTS. - Ignore it.

Chao!, **bogan**.

---

### Post by DingusFett on 2012-07-11
Seems pretty normal, I also have an ASUS motherboard and NVIDIA graphics card, and mine shows as a Laptop display. 

The easiest way to install NVIDIA graphics is to open up Additional Drivers and choose the option there, then to find out version just open dash and look for NVIDIA X Server Settings. The front page (X Server Information) should tell you the version of your drivers.

---

### Post by mastablasta on 2012-07-11
> **Shadius said:**
>  I've installed the Ubuntu 12.04 32-bit, so I should install the 32-bit drivers?
 
yes, the 32 bit drivers are the one you are after.

---

### Post by DingusFett on 2012-07-11
Going through Additional Drivers will get you the right version

---

### Post by UrFriendlyVirus on 2012-07-11
I was looking around and saw this. Might it be the answer you were looking for?
[COLOR=Red]_**[http://askubuntu.com/questions/129056/desktop-distorted-after-installing-nvidia-drivers](http://askubuntu.com/questions/129056/desktop-distorted-after-installing-nvidia-drivers)**_[/COLOR]

Hope it helps!
-UrFriendlyVirus

---

### Post by jmore9 on 2012-07-11
If everything is working fine as above poster said just ignore it.  I have a envision 17" crt that is identified as a 17" flat screen but everything works as expected so i just forget about it.

---

### Post by Shadius on 2012-07-12
> **bogan said:**
> Hi!, **Shadiu**s,

To check what nvidia driver, if any, is installed:```
lspci | grep -iA2 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```The System Details showing a Desktop Monitor as 'Laptop.', and failing to correctly identify the graphics card and driver, is a well known bug in 12.04 LTS. - Ignore it.

Chao!, **bogan**.

Here's my output:
```
shadius@shadius-asus:~$ lspci | grep -iA2 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
shadius@shadius-asus:~$ sudo apt-cache policy nvidia-current
[sudo] password for shadius: 
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
        100 /var/lib/dpkg/status
shadius@shadius-asus:~$ cat /sys/module/nvidia/version
295.40
shadius@shadius-asus:~$ 

```
I've included some additional screenshots to give you as much information as possible. I've been noticing some peculiar things happening on my display. If this current driver is going to bring about problems later, I want to install the right driver. Also, could you tell me the difference between the two drivers shown in the **Additional Drivers** window. Thank you.

---

### Post by bogan on 2012-07-12
Hi!, [B]Shadius,
[/B]
A quick search of the Nvidia site recommends the 295.59 driver for your 6200 card.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html)

The 295.40 driver you are using is the bugged one that caused all the varied and unpredictable  trouble starting in April; especially with 5xxx and 6xxx series cards.

However, if it works for you, and the only problem you have is the silly bug in 12.04 System Details which shows the screen as a 'Laptop', then why change it?.

Chao!, **bogan.**

---

### Post by Shadius on 2012-07-12
> **bogan said:**
> Hi!, [B]Shadius,
[/B]
A quick search of the Nvidia site recommends the 295.59 driver for your 6200 card.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html)

The 295.40 driver you are using is the bugged one that caused all the varied and unpredictable  trouble starting in April; especially with 5xxx and 6xxx series cards.

However, if it works for you, and the only problem you have is the silly bug in 12.04 System Details which shows the screen as a 'Laptop', then why change it?.

Chao!, **bogan.**

Thank you! How did you find this so quickly? I've been searching since I started this thread! Could you instruct me on how to install this new driver?

---

### Post by bogan on 2012-07-13
Hi!,** Shadius**,

You Posted:> Thank you! How  did you find this so quickly? I've been searching since I started this  thread! Could you instruct me on how to install this new driver?           I found it by entering your video card details in the Nvidia site search panels.

The quick and dirty way to install the driver is as follows: [ If it does not work, Post again and I will give you the full version.]

This depends on your having access to a text terminal [ tty], a working internet connection, and an already installed nvidia driver.

Press 'Ctrl+Alt+F1', [ or F2-F6] login and enter password, [ it will not show] just type and press 'Enter'. [ 'Ctrl+Alt+F7' will return to the GUI,
Run: ```
sudo service lightdm stop
sudo nvidia-installer --latest
```This will confirm the Web connection and report the version installed and version that will be downloaded and installed instead, but will notchange anything.```
sudo nvidia-installer -f
```This will un-install the old version and replace it with the version it downloads.

You may get a warning that a script has failed - ignore it - accept the various options, navigating with 'Tab' and pressing 'Enter' to accept.

Reboot.

Post how you got on.

Chao!**, bogan**.

---

### Post by Shadius on 2012-07-13
Hey bogan! 

I followed your instructions, but I get a prompt that the *nvidia-installer* command was not found. I had to reboot to get back to my system because using *Ctrl+Alt+F7* didn't bring me back. Am I doing something wrong?

---

### Post by bogan on 2012-07-13
Hi!, **Shadius**,

I do not think you did anything wrong. if you had used: ```
sudo service lightdm stop 
```you would have needed to run:```
sudo service lightdm start 
```before 'Ctrl+Alt+F7', for it to work. [My bad ]

Check in /usr/bin/ to see if 'nvidia-installer' is there. If not, we will have to use a different route.

If it is there, then try again, but this time, after logging in on a tty, enter:```
sudo service lightdm stop 
cd /usr/bin # the prompt will change
sudo ./nvidia-installer --latest
```Then continue as previous instruction.

[The: './' means: 'look in the current directory, not in the normal path.']

Chao!,** bogan.**

---

### Post by Shadius on 2012-07-13
> **bogan said:**
> Hi!, **Shadius**,

I do not think you did anything wrong. if you had used: ```
sudo service lightdm stop 
```you would have needed to run:```
sudo service lightdm start 
```before 'Ctrl+Alt+F7', for it to work. [My bad ]

Check in /usr/bin/ to see if 'nvidia-installer' is there. If not, we will have to use a different route.

If it is there, then try again, but this time, after logging in on a tty, enter:```
sudo service lightdm stop 
cd /usr/bin # the prompt will change
sudo ./nvidia-installer --latest
```Then continue as previous instruction.

[The: './' means: 'look in the current directory, not in the normal path.']

Chao!,** bogan.**

No *nvidia-installer* in my */usr/bin*.

---

### Post by bogan on 2012-07-14
Hi!, **Shadiu**s,

Right so here is the full version.
*[This is based on Post #280 of MAFoElffen's Blank Screen magnum opus Sticky in Installations &Upgrades.]*

To Install the nvidia driver it is necessary to reboot to a Text Terminal, or shut down the Xsession from a GUI screen, as the nvidia driver must be installed when the Xserver and GUI screen is inactive. Then CD to the folder where you have downloaded the .run file, make it executable and run it.

However, the first time you do this there are some preparatory steps: first you should add some Blacklists to the /etc/modprobe.d folder; then ensure the necessary build procedures are installed, and it is also advisable to purge any previous nvidia installations.

1.: Add blacklists: In a terminal enter:```
 sudo gedit /etc/modprobe.d/blacklist.conf 
```If the file does not exis, gedit will show a blank screen with that name, add:```
 # Added for nvidia driver.
blacklist nouveau
blacklist lbm-nouveau
```Save and close gedit.

2.: Prep and make sure everything is there for any dependencies, and  Cleanup:
Ensure you have fully updated your installation.
```
sudo apt-get update
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
```Run 'uname -r' and insert the output in the following command: substituting it for 'uname -r', for example:
 "sudo apt-get install linux-headers-3.2.0-26-generic-pae"

```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo nvidia-installer --uninstall # if you do not have nvidia-installer this is not necessary
sudo apt-get remove --purge nvidia-*
```You may get some 'file not found' messages on the 4th or 5th command. That is okay. Continue. We just want to make sure that older modules are removed or not there so that they don't cause a conflict.

3.: Down load the appropriate driver from nvidia.com:
[http://www.nvidia.co.uk/object/linux...driver-uk.html](http://www.nvidia.co.uk/object/linux...driver-uk.html) That is for the 32.bit version, make sure you have the correct one.

4.  To install the downloaded driver, Xorg cannot be running. You need to shut down the X-Session. In a termina,l enter:```
sudo service lightdm stop # If using 10.10 or earlier use 'gdm' in place of 'lightdm'
```You will get a black screen; if it does not have a login prompt, to get one, press 'Ctrl+Alt+F1' [or F2-F6], login, enter your password.[ It will not show, just enter it and press 'Enter'. If you need to return to the GUI screen, first run:```
sudo service lightdm start
``` Then press: 'Ctrl+Alt+F7' ]

Alternatively, reboot into recovery and a TTY Text Console and login:

5.: Installing the driver. In the following substitute the correct file name:

Change directory [cd] to the directory where you saved your file.
eg.:```
 cd /home/username/Downloads
ls 
```Running 'ls' will confirm you are in the right place and you can be sure the spelling is correct - entering 'NV' and pressing 'Tab' will Auto-complete the file name.

 Mark the downloaded file as executable:```
sudo chmod a+x NVIDIA-Linux-x86-295.59.run
```*{ AT this point you can, if you wish, check that your Internet connection is OK by: *```
sudo sh NVIDIA-Linux-x86-295.59.run --latest
```*This will show the latest version available, and the version installed, if any, but will not change anything.}*

Run the file to Install drivers:```
sudo sh NVIDIA-Linux-x86-295.59.run
```You may get an error message about a failed script, continue, accept the options, navigating by using 'Tab' and pressing 'Enter'.

When complete, reboot,```
 sudo reboot.
```If necessary edit the grub boot menu script, by pressing 'e' with the boot option highlighted and entering 'nomodset' after 'splash ' in the Linux line where it shows "ro quiet splash ", and pressing 'Ctrl+x' to boot.

Chao!, **bogan**.

---

### Post by t_shawn on 2012-09-13
> **DingusFett said:**
> Seems pretty normal, I also have an ASUS motherboard and NVIDIA graphics card, and mine shows as a Laptop display. 

The easiest way to install NVIDIA graphics is to open up Additional Drivers and choose the option there, then to find out version just open dash and look for NVIDIA X Server Settings. The front page (X Server Information) should tell you the version of your drivers.

I could ignore the system reporting my display as a laptop, no big deal, but I have dual screens and since the system says 'laptop' I have no option to configure dual screens. 

I have the latest drivers installed
 out put from lspci | grep -iA2 VGA
VGA compatible controller: NVIDIA Corporation G86 [Quadro NVS 290] (rev a1)

---

### Post by bogan on 2012-09-13
Hi!,** t_shawn**,

By video driver standards, this is a pretty old, & inactive Thread. You would do better to start your own thread with a title that includes 'Nvidia Quadro' and 'Dual Screens. { *then maybe edit your Post here to give a link to the new one*.}

I do not use dual screen setups, but Laptops can certainly use them, and do; as many other threads show they also give a lot of trouble.

The full output from:```
lspci -nnk | grep -iA[COLOR=Blue][COLOR=Red]3[/COLOR] [/COLOR]vga
```Will show exactly which drivers & modules are in use.

Have you tried the suggestion you quote of using 'NVIDIA X Server Settings' to configure your setup.

Chao!, bogan.

---

