---
title: "New ubuntu user 14.04 install questions"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by Ken_H on 2015-11-07
Semi-experienced Windows user. Decided to try Ubuntu on an older Windows laptop.

Windows laptop specs: 
Gateway MX6426
AMD Turion Mobile ML40 2.2 GHZ Single Core CPU
ATI Radeon XPRESS 200M integrated GPU
80GB HD
Broadcom 802.11n WiFi adapter (upgraded from original WiFi g adapter)
1 GB RAM PC2700
Windows XP, SP3, which still runs fine. 

I loaded Ubuntu 14.04 on a USB drive from this website and then installed it while in Windows XP using the GUI that came with the program.

The first time I tried booting I got nothing but a black screen. After a few more attempts with the same result I searched online and found the 'nomodeset' temp fix using the "e" command in GRUB. That at least allowed video. Then the program went to a text page that says "BusyBox v1.21.1....." There is also a help command with many options.

I searched more online and changed "ro" to "rw" on the linux line in GRUB, which then allowed the program to load and got to the desktop. 

Did the updates a few times. Ethernet works but the WiFi does not and the hardware driver is not found in software updates. Ran Firefox and it works. Slowly, as does everything else I try running.

Each time I boot I have to make the nomodeset and rw changes. 

Questions:
Based on my very limited knowledge, I expected Ubuntu to run relatively fast on this machine; it does not. Is this primarily due to the 1GB memory? 

The 80GB HD is in two parts. C: is 70GB formatted NTFS and has 10GB free. D: is 6GB formatted FAT32 and has 4GB free. If I were to completely erase the HD and install Ubuntu from scratch would that allow it to run significantly faster?


If adding more memory and starting with a blank HD would make a major difference, I would gladly do that, and then ask for suggestions on how to permanently fix the nomodeset, rw, WiFi issues.

Any other comments or suggestions on how to improve performance are welcome.

Thanks in advance.

---

### Post by sandyd on 2015-11-07
You are currently using Ubuntu 14.04 through Wubi, which has various bugs that may impact performance and functionality.

Please try booting the computer from the USB Drive or burn the ISO to DVD and boot from there.

Also ensure that the ISO you have downloaded is not corrupted, it can cause odd issues if it is. See [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows) for directions on how to verify the ISO under Windows. You will not need to do this if you have downloaded it using a torrent as the torrent client checks this for you.

1G of ram is probably too small to run Ubuntu fully as well. You should probably look at using a light flavor of Ubuntu such as Xubuntu or Lubuntu if you want to run under 1GB of RAM.

---

### Post by grahammechanical on 2015-11-07
> expected Ubuntu to run relatively fast on this machine; it does not. Is this primarily due to the 1GB memory?

I am running Ubuntu 15.10 on a machine with 1 GB of RAM and it runs as fast as it should. But I do have a discrete graphic adapter with 1 GB of its own memory and a dual core CPU. And that makes the difference between your experience and mine.

You have an integrated video adapter which can use up to 256 MB of memory taken from main memory. That reduces the amount of memory for the OS. It is highly likely that the video adapter cannot do 3D rendering which Ubuntu's user interface requires. So, the video rendering is being done by the CPU, which is single core. 

[http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html](http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html)

Regards.

---

### Post by Ken_H on 2015-11-07
Ok, I definitely need more RAM. Will 2GB do the job? I've already looked into upgrading the processor but as far as I can tell there is not much I can do and a dual core is not possible with the motherboard. And the integrated graphics are also not upgradeable.

I tried to boot from the USB drive but the message 'Missing operating system' comes up. The only .exe file in the ISO is Wubu. Is there a way to boot Ubuntu otherwise?

---

### Post by tea for one on 2015-11-08
> **Ken_H said:**
> Ok, I definitely need more RAM. Will 2GB do the job? I've already looked into upgrading the processor but as far as I can tell there is not much I can do and a dual core is not possible with the motherboard. And the integrated graphics are also not upgradeable.

I tried to boot from the USB drive but the message 'Missing operating system' comes up. The only .exe file in the ISO is Wubu. Is there a way to boot Ubuntu otherwise?

Have you created your USB device correctly?

Here is a guide when using a Windows PC.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Good luck

---

### Post by Sweet_Baby_Jamie on 2015-11-08
2 GB might not do if it is *shared* memory. Graphics cards take alot of it.  But 1 GB is more than plenty for the "light weight flavors" of Ubuntu which are wonderful!  Both _X_ubuntu and _L_ubuntu have easy to use interfaces that will be kinda familiar to people who are used to Windows XP.  Don't spend any money yet, try them both out for free and see how they do.  I'm running a Lubuntu 12.04 "re-spin" in a computer that's actually older than me, and with only 512 MB of RAM!  And according to my parents it runs better than when it was brand new running Windows XP!

---

### Post by hakuna_matata on 2015-11-08
> **Ken_H said:**
> how to permanently fix the nomodeset,

 rw, WiFi issues.

[LIST]
[*]nomodeset -> [NOMODESET - making it permanent]("http://ubuntuforums.org/showthread.php?t=1675337") 
[*]rw -> should not necessary, if you don't use Wubi. If you use it, see [Ubuntu 14.04 not booting after error message. /tmp could not be mounted]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted")
If I use Wubi for testing purpose, I always use a script which is a workaround similar to [this solution.]("http://askubuntu.com/a/552041") 
 ```
sudo wget http://bazaar.launchpad.net/~hakuna-matata/wubi/lp1317437/download/head:/loopremount-20150403212347-dqcyn1kotehtxqfj-2/loop-remount -O /etc/initramfs-tools/hooks/loop-remount # download
sudo chmod +x /etc/initramfs-tools/hooks/loop-remount # set mode to executable
sudo /etc/initramfs-tools/hooks/loop-remount # run script
sudo update-initramfs -u # update initramfs
``` 
[/LIST]
 
[LIST]
[*]Wifi -> depends on your hardware. [More details]("http://www.linuxwireless.org/en/users/Drivers/b43/") about your hardware are necessary. IMHO it is better to create a new thread for your Wifi issue. 
[/LIST]

---

### Post by mastablasta on 2015-11-09
> **Ken_H said:**
> 
I loaded Ubuntu 14.04 on a USB drive from this website and then installed it while in Windows XP using the GUI that came with the program.

Bad idea as this method is no longer supported. also it is using a virtual disk which may slow it all down a bit.

> 
Based on my very limited knowledge, I expected Ubuntu to run relatively fast on this machine; it does not. Is this primarily due to the 1GB memory? 

no, winXP uses 2D desktop, Ubuntu uses 3D acceleration. so if the GPU is not good or if it ha spoor support it will work slow as all desktop drawing is transfered to CPU.  Xubuntu and Lubuntu have 2D desktops. As well as Mate and a few other desktops arround.

you GPU has only opensource drivers available and hopefully with proper install you won't need nomodeset. because if you do then you are stuck with software acceleration. or in other workd - internet browsing & office work should work with light 2D desktop. but gaming won't.
It says here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) that X200 has full 3D support so I really hope that with proper install you will be able to enable the 3D on he chip. it might be missing some features, but ok.


> 
The 80GB HD is in two parts. C: is 70GB formatted NTFS and has 10GB free. D: is 6GB formatted FAT32 and has 4GB free. If I were to completely erase the HD and install Ubuntu from scratch would that allow it to run significantly faster?


that or a separate Linux partition (just make some free unformated space on the disk and let the installer do the rest). is D actually a disk or is it a partition?

---

