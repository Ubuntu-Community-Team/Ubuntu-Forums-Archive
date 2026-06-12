---
title: "Installing Grub After Windows 7"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Vorsaykal on 2011-10-08
Hello, I've been using Ubuntu for about three days now, and I really like it, so I want to dual boot Natty and Windows 7. I had Natty on first, and nothing else, then installed Windows 7 afterwards. I now can only boot into Windows 7.

I read that I have to reinstall Grub (or Grub2 or something, I'm confused) and that will allow me to select which OS to launch. I tried "sudo grub" and it gave me this error: "sudo: grub: command not found" I've been looking for a fix for about 4 hours and it's driving me nuts. I even tried to reinstall Ubuntu but it wouldn't even let me do that!I'm currently in the LiveCD of Natty.

How do I get Grub on so I can dual boot? I don't want only Windows 7:(

---

### Post by drs305 on 2011-10-08
Vorsaykal

Welcome to the Ubuntu Forums ! :-)

Boot an Ubuntu LiveCD/Installation CD. Mount your Ubuntu partition and then install Grub 2. While it's installed, if Ubuntu is on the same drive as Windows, it will override the MBR to point to Grub 2. Both Ubuntu and Windows will be available in the Grub 2 menu.

If Windows and Ubuntu are on separate drives, mount the Ubuntu drive/partition but make sure you install it only to the Ubuntu drive.

[COLOR="Red"]X[/COLOR] is the drive Ubuntu is on (a, b, c, etc)
[COLOR="Red"]Y[/COLOR] is the partition number (1,2,3,5, etc).
Do not use the partition number in the second command.
```
sudo mount /dev/sd[COLOR="Red"]XY[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]X[/COLOR]

```
Example if your Ubuntu partition is on sda5:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If you don't understand these instructions, click the BIS link in my signature line. Download and run the boot info script and post the contents of RESULTS.txt and we can tell you the values to use in the above commands.

---

### Post by Vorsaykal on 2011-10-08
> **drs305 said:**
> Vorsaykal

Welcome to the Ubuntu Forums ! :-)

Boot an Ubuntu LiveCD/Installation CD. Mount your Ubuntu partition and then install Grub 2. While it's installed, if Ubuntu is on the same drive as Windows, it will override the MBR to point to Grub 2. Both Ubuntu and Windows will be available in the Grub 2 menu.

If Windows and Ubuntu are on separate drives, mount the Ubuntu drive/partition but make sure you install it only to the Ubuntu drive.

[COLOR=Red]X[/COLOR] is the drive Ubuntu is on (a, b, c, etc)
[COLOR=Red]Y[/COLOR] is the partition number (1,2,3,5, etc).
Do not use the partition number in the second command.
```
sudo mount /dev/sd[COLOR=Red]XY[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sd[COLOR=Red]X[/COLOR]

```Example if your Ubuntu partition is on sda5:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If you don't understand these instructions, click the BIS link in my signature line. Download and run the boot info script and post the contents of RESULTS.txt and we can tell you the values to use in the above commands.

I typed: "sudo grub-install --root-directory=/mnt /dev/sda1" and got  this error: "/usr/sbin/grub-probe: error: cannot stat `aufs'"

I have one hard drive, so I chose A, and it's on my 99GB partition which  is listed first in Disk Utility, so I figured it would be sda1, did I  figure that out wrong?

And thanks for the speedy reply!

---

### Post by drs305 on 2011-10-08
> **Vorsaykal said:**
> I typed: "sudo grub-install --root-directory=/mnt /dev/sda1" and got  this error: "/usr/sbin/grub-probe: error: cannot stat `aufs'"

I have one hard drive, so I chose A, and it's on my 99GB partition which  is listed first in Disk Utility, so I figured it would be sda1, did I  figure that out wrong?

And thanks for the speedy reply!

sda1 is most likely one of your Windows partitions. sda5 is most likely your Ubuntu partition. Run the first command as "sudo mount /dev/sda5 /mnt" and then run this command:
```
ls /mnt
```
You should see a lot of Ubuntu files and folders such as boot, bin, dev, etc. If that is what you see, then run this:```

sudo grub-install --root-directory=/mnt /dev/sda
```
If you get no errors, reboot and you should see the Grub menu (or it may boot directly into Ubuntu). If you don't see the menu, let us know.

If you mount sda5 and don't see the folders I mentioned, it would be best to run the boot info script and post RESULTS.txt

---

### Post by Vorsaykal on 2011-10-08
When I try to mount sda5 it says it looks like a swap space.

When I go into my Home Folder and click File System it shows the same files as my 99GB Partition (sda1)

When I type "sudo bash ./boot_info_script.sh result.txt" it says "bash: ./boot_info_script.sh: No such file or directory"

EDIT: Nevermind, had to "cd Desktop"

---

### Post by drs305 on 2011-10-08
> **Vorsaykal said:**
> 
When I type "sudo bash ./boot_info_script.sh result.txt" it says "bash: ./boot_info_script.sh: No such file or directory"

You will have to change into the same folder as the script was extracted to. It may be in ~/Downloads or on your Desktop (~/Desktop) or in your /home folder. In a terminal, try changing to one of those folders and look for the script:
```
cd ~/Downloads
ls *.sh
# If not there:
cd ~/Desktop
ls *.sh
cd ~/
ls *.sh

```

Added: don't include "results.txt" in the command, just *sudo bash ./boot_info_script.sh*

---

### Post by Vorsaykal on 2011-10-08
Results in attachment.

---

### Post by drs305 on 2011-10-08
Ok, your Ubuntu installation is on sda1. You may have gotten the original 'aufs' error message if you hadn't mounted the partition first. 

Here are the commands that should install Grub2. First we will unmount all the partitions to start fresh. If it says it's not mounted, don't worry about it:

```
sudo umount /dev/sda5
sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This should install Grub 2 and point the MBR to your Grub folder. Looking at your RESULTS.txt, Grub hasn't yet found your Windows installation, so the first time you boot you probably won't see the Grub menu.

After booting into Ubuntu (without the CD), run the following command and look for a message that it found Windows. If it does, Windows will be included in the menu the next time you boot and you should see the Grub menu and have a choice of OS's to boot.
```
sudo update-grub
```

---

### Post by Vorsaykal on 2011-10-08
"Installation finished. No error reported." I assume this means that this means it's all ready to go, thanks for the help, I'll post here again if I run into any troubles.:guitar:

---

