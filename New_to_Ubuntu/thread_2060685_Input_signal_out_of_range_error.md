---
title: "Input signal out of range error"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by jamesva3 on 2012-09-20
Context: ubuntu 12.04 had just installed about 100 packages and needed to restart however i also wanted to update my graphics drivers as i have been experiencing ocasional and extreme stutter in videos specificly youtube videos. I also reset my hp2009m to factory default as i was getting ready to calibtate the monitor which is also why i was interested in finding the nvidia control panel to ensure output was in 24-bit mode. 

I also wanted to look at my nvidia control panel settings but couldnt find it ( or least something that was similar to what i had in windows) 

So i downloaded new nvidia drivers as i recall version 304.xx and installed them via the concole command line (copy/paste from a website) it installed and so i exited the command line and went to restart the computer, but when it turned back on i got a "input signal out of range" error. This was typical for my machine, i alwalys get this message for a few seconds after a restart but i goes away and i am then presented with the log in screen, this has not hqppened this time qround and i dont know how to fix this. I ahe tried blindly logging in as i thought this would fix the problem but nothing happened. So i restarted and tried to use the ctr + alt + num +\- to change screen settings via keyboad this did not help.(i waited on averag. 4  seconds between each press and did so a few times using both + and - keys). I am using a stock hp slimline w/geforce 6150 (endig in either se or le) integrated on mobo. 

While i am at it i will also pose another question 

I have my hardrive split into 3 partitions one for windows, then hp's factory default image and then ubuntu portion however i cannot figure out how to access windows anymore as i am not presented with a dual boot screen (the one that  askes which OS to boot into) thanks guys

---

### Post by pissedoffdude on 2012-09-20
Do you get a console screen if you try to boot into recovery mode?  Also, please post the instructions you used to install the drivers

---

### Post by jamesva3 on 2012-09-20
[http://www.techlw.com/2012/03/install-nvidia-drivers-on-ubuntu-1204.html](http://www.techlw.com/2012/03/install-nvidia-drivers-on-ubuntu-1204.html)

i never seen the grub loader menu i keep reading about it but have never seen it pop up when i turn on my computer(from what i have read it is what gets me into recovery mode right?), first i see the bios screen starting then  black then the error message, but that usually disappears and then the log in shows up. i tried to hit esc anyway during the black screen which is right after the bios menu and during the error message but nothing happened.

---

### Post by jamesva3 on 2012-09-20
bump

---

### Post by pissedoffdude on 2012-09-20
Before you installed Ubuntu, did you ever see anything before you got to the desktop on Windows?  I'm wondering if this is strictly a grub issue, or if it's got something to do with your integrated graphics card and the bios settings.

For now, boot off the cd or usb that you used to install Ubuntu. Once booted, type this command: ```
sudo fdisk -l
```  Look for a large partition that says linux.  That will be your Ubuntu install. Find out which partition it is (/dev/sdaX).  If you're unsure, post the output here and we'll let you know

Then type:
```
sudo mkdir /media/ubuntu
sudo mount /dev/sdaX /media/ubuntu (where X is your partition number)
sudo chroot /media/ubuntu
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak (if you get an error here about the file not existing, don't worry)
sudo rm /etc/X11/xorg.conf (again, don't worry if it doesn't exist)
sudo nvidia-xconfig
exit
```

Reboot, and let us know if that works

---

### Post by jamesva3 on 2012-09-22
yes id did, on windows i would see the bios menu then the windows os would start up. 

i successfully booted from usb on the 32-bit 12.04 desktop Ubuntu i386 version

 [B]here is what i typed in terminal and the output (copy/paste)
[/B]
**1) sudo fdisk -l   **                                                                            relevant partition: /dev/sda5       430860288   594659327    81899520   83  Linux

**2) sudo mkdir /media/ubuntu                                                   output:**  nothing

**3)  sudo mount /dev/sda5 /media/ubuntu                           output:**  nothing but i noticed my harddrive linux partition  icon is now in the GUI sidebar

**4) sudo chroot /media/ubuntu                                                 output:**  nothing, but the user changed from   ubuntu@ubuntu:~$   to   root@ubuntu:/#

**5) sudo cp /etc/x11/xorg.conf /ect/x11/xorg.conf.bak   output: **sudo: unable to resolve host ubuntu, then next line down   cp: cannot stat `/etc/x11/xorg.conf': No such file or directory

**6) sudo rm /ect/x11/xorg.conf                                                 output:** sudo: unable to resolve host ubuntu, then next line down   rm: cannot remove `/ect/x11/xorg.conf': No such file or directory

[B]7) sudo nvidia-xconfig                                                                 
             output: [/B]

sudo: unable to resolve host ubuntu

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Cannot find /proc/version - is /proc mounted?
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

**and for good measure im going paste the entire terminal session here, **

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   430859437   215429687+   7  HPFS/NTFS/exFAT
/dev/sda2       430860286   600684543    84912129    5  Extended
/dev/sda3       600686415   625137344    12225465    7  HPFS/NTFS/exFAT
/dev/sda5       430860288   594659327    81899520   83  Linux
/dev/sda6       594661376   600684543     3011584   82  Linux swap / Solaris

Disk /dev/sdb: 15.8 GB, 15812526080 bytes
255 heads, 63 sectors/track, 1922 cylinders, total 30883840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128    30883839    15441856    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/ubuntu
ubuntu@ubuntu:~$ sudo chroot /media/ubuntu
root@ubuntu:/# sudo cp /etc/x11/xorg.conf /ect/x11/xorg.conf.bak
sudo: unable to resolve host ubuntu
cp: cannot stat `/etc/x11/xorg.conf': No such file or directory
root@ubuntu:/# sudo rm /ect/x11/xorg.conf
sudo: unable to resolve host ubuntu
rm: cannot remove `/ect/x11/xorg.conf': No such file or directory
root@ubuntu:/# sudo nvidia-xconfig
sudo: unable to resolve host ubuntu

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Cannot find /proc/version - is /proc mounted?
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

root@ubuntu:/# exit
ubuntu@ubuntu:~$ 

this post is before the computer restart, will be switching the boot device back to my internal hdd and start machine will post results afterwards

---

### Post by jamesva3 on 2012-09-23
so i just rebooted from internal hdd and same error as before, also no grub loader menu

---

### Post by pissedoffdude on 2012-09-29
Sorry for the late reply.  Do the first two steps from my last post, then:

```

sudo mount --bind /dev /media/ubuntu/dev
sudo mount --bind /proc /media/ubuntu/proc
sudo mount --bind /sys /media/ubuntu/sys
sudo rm /etc/resolv.conf
sudo touch /etc/resolv.conf
sudo echo 8.8.8.8 > /etc/resolv.conf
sudo echo 8.8.4.4 >> /etc/resolv.conf
sudo cp /etc/resolv.conf /media/ubuntu/etc/resolv.conf
sudo chroot /media/ubuntu
rm /etc/X11/xorg.conf
nvidia-xconfig
exit

```

Reboot, and see if you can boot into Ubuntu.  If you're still having issues, then we'll just uninstall the Nvidia drivers.  You will do the same steps as above, but instead of ```

nvidia-xconfig
exit
```

Do ```
apt-get purge nvidia-current
exit
```

Let me know if that works, then we can focus on the grub issue.

---

### Post by Sunfist on 2012-09-29
I had the same problem and while I think I could have fixed it, I ended up just removing the Nvida driver and that solved the problem. Someday when I am feeling energetic and have some time on my hands I may go in and try to fix it but it works fine with the regular default Ubuntu driver.

---

### Post by jamesva3 on 2012-10-08
sudo: unable to resolve host ubuntu, i get this error every time i try these commands. should i just do a fresh ubuntu install? if i do is there a way to keep the installed programs, settings documents ect..

---

### Post by pissedoffdude on 2012-10-12
That "unable to resolve host error" should be a problem only AFTER you've run the chroot command.  I didn't put sudo in the commands after that.  Try again and let me know if it's still a problem.  And you could reinstall if it's a headache (but learning to fix it always helps us out.  In any case, a lot of us here have reinstalled after borking our system, haha)

If you choose to reinstall, there are 2 ways of keeping your files:

1) Boot a liveced, access your files via  the file manager, then copy them to your Windows drive

2) Or, create a new Ext4 partition (or choose any filesystem you'd like), then copy the files you'd like to back up to that newly created partition, call it X.  Then create ANOTHER partition, call it Y, and install Ubuntu on it.  Then copy the files from X on to Y.  Delete X, then extend Y so that it includes X's space (using a livecd)

---

