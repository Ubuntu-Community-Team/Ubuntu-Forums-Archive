---
title: "grub boot password issues"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by hookitup on 2013-03-29
So i decided to put a grub boot password on my ubuntu 12.10 machine. BAD IDEA as i have done it wrong i think. i followed this link 

[http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/](http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/)

up to the point where it says [h=3]Password Protecting Boot Entries[/h]
i did not continue as i thought this did not apply for the general grub password protect.

but after reboot it ask for my username and password and i am entering what i have set it to and it will not let me in at all. i know for a fact that i am entering the username and password correctly. how do i fix this.

i tried booting to a live ubuntu usb and mounting the hard drive and editing the file i have changed but i do not get write access. i have tried the command ```
mount -o remount,rw /dev/sda1 /mnt
```
this was after it had mounted when i click on it in the Nautilus and got permission denied when trying to navigate to the file.
i tried various different commands to get this mounted with write access and no luck at all.


Does anybody have a solution ?

---

### Post by AndyOpie150 on 2013-03-29
If nobody else gives a clear answer on how to fix, you might try Hirens Boot CD.iso.
I had to use it to fix a bad boot sector on the Windows partition, and I think I remember seeing that it could fix grub/BIOS passwords. Not totally for sure. Check out there site for a listing of included programs and what they are capable of.

---

### Post by coldcritter64 on 2013-03-29
> **hookitup said:**
> So i decided to put a grub boot password on my ubuntu 12.10 machine. BAD IDEA as i have done it wrong i think. i followed this link 

[http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/](http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/)

up to the point where it says **Password Protecting Boot Entries**


i did not continue as i thought this did not apply for the general grub password protect.

but after reboot it ask for my username and password and i am entering what i have set it to and it will not let me in at all. i know for a fact that i am entering the username and password correctly. how do i fix this.

i tried booting to a live ubuntu usb and mounting the hard drive and editing the file i have changed but i do not get write access. i have tried the command ```
mount -o remount,rw /dev/sda1 /mnt
```
this was after it had mounted when i click on it in the Nautilus and got permission denied when trying to navigate to the file.
i tried various different commands to get this mounted with write access and no luck at all.


Does anybody have a solution ?


You may need to do a chroot into the "broken" install from a live cd, remove the alterations from /etc/grub.d/40_custom in the chroot environment, then from within the chroot run, ```
update-grub
```Note: chroot terminal is a root terminal, no sudo needed, see the edit below. By updating from within a chroot from a live cd, the grub files will be correctly set up before you try and reboot into the main install including removing the password request. 

[s]Unfortunately my notes on this aren't readily available, will get back with detailed instructions later if nobody has such notes/info handy[/s].

**Edit:** 

1. in a terminal from a live cd copy/paste the one line of code below


Note, this sets up a chroot environment in the terminal with /dev/sda1 being mounted to /mnt, the remaining command bind mounts necessary system folders and sets up networking available (not needed in these circumstances-for when downloading into a chroot is necessary)


```
sudo mount /dev/sda1 /mnt/ && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt/ /bin/bash
```


2. with the terminal open and chroot mounted, open a 2nd terminal and copy/paste the command
```
gksudo gedit /mnt/etc/grub.d/40_custom
```

3. Remove your alterations, read the header of the file carefully and make certain the exec line is not touched.

4. Save the file in gedit and exit.

5. Go back into the still open chroot terminal and issue the command.
```
update-grub
``` you may not need sudo, it is a root terminal in the chroot environment (working on your hard disk install).

6. Press, Ctrl+d on the keyboard to exit the chroot when the grub update completes, your prompt will return to ubuntu@ubuntu (user) from root@ubuntu (root) in the live cd terminal.

7. Unmount the chroot filesystem mounts and networking with the code,

```
sudo umount /mnt/etc/resolv.conf && sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

8. Close the terminal and reboot into your hard drive install (hopefully). Cheers.

---

### Post by hookitup on 2013-04-01
Cheers to [B][U][COLOR=#000000]coldcritter64


[/COLOR][/U][/B]_[COLOR=#000000][/COLOR]_[COLOR=#000000]This has resolved my issue and i am back in my computer with no problems.

Thanks for all the help[/COLOR]

---

### Post by coldcritter64 on 2013-04-01
Edit: to mark your thread as solved please see

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

> **hookitup said:**
> Cheers to [B][U][COLOR=#000000]coldcritter64


[/COLOR][/U][/B][COLOR=#000000]This has resolved my issue and i am back in my computer with no problems.

Thanks for all the help[/COLOR]
Actually thank you for letting us know, was wondering if that'd work ;) ... :lol: Cheers.

---

