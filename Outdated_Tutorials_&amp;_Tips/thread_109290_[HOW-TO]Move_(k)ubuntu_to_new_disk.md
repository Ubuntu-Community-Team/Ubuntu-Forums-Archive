---
title: "[HOW-TO]Move (k)ubuntu to new disk"
date: 2005-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Sir_Yaro on 2005-12-28
assumption:
old disk with kubuntu --> /dev/hda1 (primaty master)
**new** disk where we want to move data --> /dev/hdc1 (secondary master)

1. Unmount all disc . The best idea is to leave only  /
U can do it like that::
> sudo umount /some/mounted/place 

2. Create partition on new disc. It's no important how big it'll be. But it can't be smaler (it's logical, isn't it?)

U can do it using cfdisk
> sudo cfdisk /dev/hdc 

As a type of partition leave *Linux*
Don't forget to set partition as an active! (option *Bootable*)

3. Format ur partion and create file system. I'm using reiserFS so that's a proper command:
> sudo mkfs.reiserfs /dev/hdc1 


4. Mount new disc.
> 
sudo mount /dev/hdc1 /media/test/
 

5. If you're still in X turn it OFF!!
The best idea is to switch to single user mode:
> sudo telinit 1 
or just to console using:
> sudo telinit 3 

6. Start copying:
> cp -ax / /media/test 
Now you may go for a walk or sth beacase it'll take a lot of time...

If you can switch to other console (u used telinit 3) you ay check what is going on, ex.:
> watch df  
> watch ls -l /media/test 

After end of all proces you can check if data has been copied properly. > find / -path /proc -prune -o -path /media/test -prune -o -xtype f -exec cmp {} /media/test{} \; 
But i think it's a waste of time....

7. Modyfy */etc/fstab* to tally with content of new disc. Remember, even though disc is still /dev/hdc you need to think about it as a /dev/hda!! I can't discribe this part in detail beacause I don't have clue how your disc looks like.  My situation was clear. Every thing was almost in the same way but partition s was 2-4 times bigger. 
Only swap partition has been changed. From /dev/hda5 to /dev/hda2 what couse modification:
> /dev/hda5 none swap sw 0 0  to> /dev/hda2 none swap sw 0 0  

8. Install boot loader. In practise we don't need nothing more than put something in the MBR what can read files and start system.

* GRUB
As a matter of fact everything reduce to command:
> grub-install --root-directory=/media/test/ hd2 
but because of some strange reasons it gave me some errors and at last command:
> grub-install --root-directory=/media/test/boot hd2 
was accepted without any problems. It create aditional, useless directory stucture in /boot which u can sefety remove. 

*LILO
Edit /media/test/etc/lilo.conf : 

```
disk=/dev/hdc bios=0x80       # It tells lilo to treat 3rd disc as if it be 1st one 
                              # (BIOS ID 0x80).
boot=/dev/hdc                 # install lilo on 3rd disc
map=/media/test/boot/map        # localisation of "map" file.
install=/media/test/boot/boot.b # file choosed to copy on boot sector
prompt                        # show prompt?
timeout=50                    # after what time start system
                              # values in 1/10 sec
image=/media/test/boot/vmlinuz  # Localisation of kernel
                              # its possible that you need to change this line and input proper name of yur kernel ex:
                              # "vmlinuz-2.0.35".
    label=linux               # Name
    root=/dev/hda1            # Localisation of / partition on new disc
    read-only                 # First mount partition in read-only mode to check it

```

install lilo using command:
> sudo lilo -C /media/test/etc/lilo.conf 

9. Turn off computer. Connect new disc in place of old one. That's it! After turning on should be ony errors, your system should work in exacly the same way like before. 


Have a nice fun. :) :P

---

