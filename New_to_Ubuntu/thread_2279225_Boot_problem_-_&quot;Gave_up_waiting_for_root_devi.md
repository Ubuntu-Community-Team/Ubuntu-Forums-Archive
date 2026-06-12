---
title: "Boot problem - &quot;Gave up waiting for root device.&quot;"
date: 2015-05-22
forum: New to Ubuntu
---

### Post by ashish-sharma-mw on 2015-05-22
[FONT=book antiqua]Hi all,

I am using Ubuntu 14.04, alongwith Windows 7 for an year now. Suddenly yesterday I encountered with the mentioned problem. However, by typing "exit" at initramfs, I was able to be redirected to normal boot process. But I wish to resolve this as the issue keeps coming up every time i reboot. I tried the measures suggested by @drs305  [http://ubuntuforums.org/showthread.php?t=1399810](http://ubuntuforums.org/showthread.php?t=1399810) and removed the search lines completely from the grub configuration file at the boot time (using "e" in the menu list) and also referred to my root as /dev/sda6 (I gotr to know that its sda6 through bootinfoscript) instead of UUID based reference. It booted my OS normally.
Next I followed [https://help.ubuntu.com/community/Grub2/Troubleshooting#Selected_Problems_and_Bugs](https://help.ubuntu.com/community/Grub2/Troubleshooting#Selected_Problems_and_Bugs) to make the changes made while boot process permanent by typing in commands:
[/FONT]
sudo update-grub
sudo grub-install /dev/sda
[FONT=book antiqua]
and ensured existence of all the contents mentioned therein, but the problem is, the changes that I intended to be permanent can not be seen at the next boot time and the problem persists/

Can anyone please let me know where I am getting wrong.
Thanks in advance.
[/FONT]

---

### Post by Vladlenin5000 on 2015-05-22
Hi and welcome.

You got the order of the commands wrong. First you (re-)install Grub (grug-install) then you update it to make changes permanent (update-grub).

---

### Post by ashish-sharma-mw on 2015-05-22
Hi Vladlenin5000,

Thanks for answering. I repeated in the order you suggested, but nothing changed. 
Please locate grub file which I edited at boot time:
[URL="http://postimg.org/image/lyvtg0u4v/"]http://postimg.org/image/lyvtg0u4v/
[/URL]
In the above picture, I removed all the if-else-fi lines alongwith search lines.
then I replaced 
root=UUID=<my device ID> with root=/dev/sda6

then Ctrl+x leads me to normal booting up.

Then on terminal, I did re-installation of grub and then updated it as well.
As per instructions it must be permanently changed now. In addition to this I also made change in /etc/fstab as:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
#UUID=883af998-6fdc-4cf9-a982-e16c14382c88 /               ext4    errors=remount-ro 0       1
**UUID=/dev/sda6 /               ext4    errors=remount-ro 0       1**
# swap was on /dev/sda5 during installation
UUID=bcfe2538-d8e0-46bc-a1fa-8b564ac4480b none            swap    sw              0       0

change is in the **BOLD**.

Can you now spot any problem. Please let me know if something else needs to be known here like grub.cfg etc.

Thanks again.

---

### Post by oldfred on 2015-05-22
UUID is the preferred method.

But the search requires grub to parse all your partitions to find the correct one. 
Do you perhaps have corruption on another partition that needs either fsck or chkdsk, so partition can be seen correctly by grub. 
Or is Windows hibernated so grub cannot parse it?

Post the link a new update to the Summary report from Boot-Repair gives you.

---

