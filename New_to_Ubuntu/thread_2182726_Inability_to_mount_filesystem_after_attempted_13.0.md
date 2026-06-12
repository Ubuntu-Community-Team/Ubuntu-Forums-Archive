---
title: "Inability to mount filesystem after attempted 13.04 upgrade"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by sev1 on 2013-10-22
About 20 minutes into 13.04 upgrade my system locked up completely. I waited for close to an hour to ensure that no progress was being made then had to do a hard reset causing the upgrade to abort before completion. When I booted up I got the following message:

General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
bash:groups: command not found
root@mycomputer:~#

CNTRL-D brought me to GRUB, which was not installed prior to the upgrade attempt as there was no OS beside 12.10 on my HDD.
Attempting to boot to all three Ubuntu options resulted in a loop back to the same error message. I did some research and found this
[thread]("http://askubuntu.com/questions/288842/general-error-mounting-filesystems-after-upgrade-to-13-04") describing the same problem. 

I used UnetBootin to make a [boot repair]("https://help.ubuntu.com/community/Boot-Repair") USB knowing that I wouldn't be able to boot to 13.04 but hoping I could somehow recover 
12.10. Using the recommended repair only gave the option of repairing 13.04 on dev/sda1 - 12.10 appears to have been purged and I
obviously already know 13.04 is a broken (incomplete) install.

To further complicate matters, my HDD has /home(sda2), /usr(sda5), and /var(sda3) partitions. Running the 'mount' command from the
maintenance shell gets: /dev/sda1 on / type ext4 (rw, errors=remount-ro). Not sure how to interpret this? No error messages for
sda2, 3, or 5. 

Is there any way I can revert back to 12.10 using boot repair or any other utility? The only solution I've found that appears
to work is to complete the 13.04 install using LiveUSB/CD. Any alternate solutions/suggestions would be appreciated.

---

