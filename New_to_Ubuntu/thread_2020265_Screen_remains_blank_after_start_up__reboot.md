---
title: "Screen remains blank after start up / reboot"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by pauloz on 2012-07-08
Greetings!

I recently installed Ubuntu 12.04 on an Acer Aspire 3500 and after experiencing problems with the wireless connection (now resolved thanks to chili555 and wildmanne39), I find the screen remains blank after I either start up or reboot the laptop. 

I find the problem is resolved after pressing CTRL ALT F1 and then CTRL ALT F7. Obviously I don't want to keep doing this, so can anybody help?

Thanks!

---

### Post by AlbertJB on 2012-07-08
Just found this: [http://askubuntu.com/questions/10384/blank-screen-after-switch-user-or-resume](http://askubuntu.com/questions/10384/blank-screen-after-switch-user-or-resume) 

It seems it's an old problem maybe related to xgamma... Anyone else?

---

### Post by NikTh on 2012-07-08
When you hit Ctrl+alt+F1 , login with username & password . Then give these commands 
```
sudo service lightdm stop 
sudo apt-get install -f 
sudo dpkg --configure -a 
sudo dpkg-reconfigure lightdm xserver-xorg xserver-xorg-core xsever-common xorg
sudo service lightdm start
``` 
Write down these commands to no mistake .
Reboot to check the result..

---

### Post by pauloz on 2012-07-08
Hello 

Unfortunately no change - any other suggestions? Thanks

---

### Post by NikTh on 2012-07-08
hmmm , strange problem. Try to reinstall ```
sudo apt-get install --reinstall lightdm
```Also check out  your graphics driver.. what it is ? open source or additional ? If you have additional driver enabled , do you want to procedure with an UN-installation (disable) ? 

There is also something else.. try
```
sudo update-grub 
sudo update-initramfs -u -k all
```

---

### Post by pauloz on 2012-07-09
Hello again NikTh 

Here's the output of the commands you asked me to check:


graham@graham-Aspire-3500:~$ sudo apt-get install --reinstall lightdm
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-plugins-main python-compizconfig python-central
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 96.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main lightdm i386 1.2.1-0ubuntu1 [96.3 kB]
Fetched 96.3 kB in 1s (89.7 kB/s)
Preconfiguring packages ...
(Reading database ... 200507 files and directories currently installed.)
Preparing to replace lightdm 1.2.1-0ubuntu1 (using .../lightdm_1.2.1-0ubuntu1_i386.deb) ...
Unpacking replacement lightdm ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up lightdm (1.2.1-0ubuntu1) ...
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
graham@graham-Aspire-3500:~$ 

Can you show me how to check the graphics driver and what I should do next? This time the screen came on when I started up but again went blank after about 10 minutes and the only way I could turn it on was to type CTRL ALT F1 then CTRL ALT F7.

Thanks

---

### Post by NikTh on 2012-07-09
> **pauloz said:**
> 
Can you show me how to check the graphics driver and what I should do next? This time the screen came on when I started up but again went blank after about 10 minutes and the only way I could turn it on was to type CTRL ALT F1 then CTRL ALT F7.

You can give this command and see what driver you use.. for graphics .. 
```
lspci -nnk | grep -iA2 vga
``` 

Depends on graphics driver , you can install or uninstall an see how goes. 
Also you have packages that no longer required so run this command to get rid of them (they are useless) 
```
sudo apt-get autoremove
```

---

### Post by PhilTroy on 2012-07-10
Hi!

When installing Lubuntu 12.04 with Cedarview drivers (for Atom N2800 on DN2800MT motherboard), I had a similar problem.  Please see my several entries on blog at [http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/](http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/)

The upshot is that I removed lightdm and installed gdm and Lubuntu booted right away, with the desired drivers.  I think that lightdm has some dependencies or bugs that need to taken care of.

Phil Troy

---

### Post by pauloz on 2012-07-10
> **NikTh said:**
> You can give this command and see what driver you use.. for graphics .. 
```
lspci -nnk | grep -iA2 vga
``` 

Depends on graphics driver , you can install or uninstall an see how goes. 
Also you have packages that no longer required so run this command to get rid of them (they are useless) 
```
sudo apt-get autoremove
```

Hello NikTh - here is the output of what you mentioned:


graham@graham-Aspire-3500:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
	Subsystem: Acer Incorporated [ALI] Device [1025:0082]
	Kernel modules: sisfb
graham@graham-Aspire-3500:~$ sudo apt-get autoremove
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  compiz-plugins compiz-plugins-main python-central python-compizconfig
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
After this operation, 5,959 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 200506 files and directories currently installed.)
Removing compiz-plugins ...
Removing compiz-plugins-main ...
Removing python-central ...
Removing python-compizconfig ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
graham@graham-Aspire-3500:~$ 

@ Phil - sorry I made a mistake when I selected the options. I'm running Ubuntu 12.04 not Lubuntu 12.04. Thanks anyway for your post.

Cheers
pauloz

---

### Post by NikTh on 2012-07-10
> **pauloz said:**
> 

graham@graham-Aspire-3500:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
    Subsystem: Acer Incorporated [ALI] Device [1025:0082]
    Kernel modules: sisfb

Hmmm... you have SIS. Sorry i cannot help you with SIS. I don't know those cards , but i know that have strange behaviour with Linux.

---

### Post by pauloz on 2012-07-11
> **NikTh said:**
> Hmmm... you have SIS. Sorry i cannot help you with SIS. I don't know those cards , but i know that have strange behaviour with Linux.

OK - thanks NikTh for your help. Can anybody else offer assistance?

---

### Post by chenhs05 on 2012-11-17
> **NikTh said:**
> When you hit Ctrl+alt+F1 , login with username & password . Then give these commands 
```
sudo service lightdm stop 
sudo apt-get install -f 
sudo dpkg --configure -a 
sudo dpkg-reconfigure lightdm xserver-xorg xserver-xorg-core xsever-common xorg
sudo service lightdm start
``` 
Write down these commands to no mistake .
Reboot to check the result..
Thank you NikTh!
It works for me.
I was able to login before I changed in the /etc/X11/default-display-manager file from "/usr/sbin/lightdm" to "/usr/sbin/gdm". 
Even though I changed back, it consistently gives me a black screen when I boot the system. I have to use "sudo service lightdm start" to go to the gui.
For me it's mainly because of the configuration...

---

