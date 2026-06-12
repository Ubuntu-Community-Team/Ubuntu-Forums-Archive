---
title: "[SOLVED] need to revert permissions of my drive to normal"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by macvr on 2008-09-09
i had used this to change my universal permissions
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda5 ***/mnt/linux
find /mnt/linux -type d -exec chmod 755 '{}' \;
find /mnt/linux -type f -exec chmod 644 '{}' \;
umount /mnt/linux
exit

```
as per the posts in this thread, for a GDM problem
[http://ubuntuforums.org/showthread.php?t=862263&page=2]("http://ubuntuforums.org/showthread.php?t=862263&page=2")

 but it has landed me into more trouble!!!now i get this>>>

```

BusyBox v1.1.3(Debian 1:1.1.3-5Ubuntu12) Built-in shell (ash)
Enter Help for listing of commands

(initramfs)_

```

so i want to revert to my original permissions, how do i do it?

---

### Post by Calabresi on 2008-09-09
Try in terminal

```
chmod 755 /
```

This will restore the root original permission.

Edit: Now I read your original post and understood your problem is worst than normal, when you get the grub (the first and inicial boot window) get the restore option, ask for prompt and do the job above.

good luck

---

### Post by macvr on 2008-09-09
> **Calabresi said:**
> Try in terminal

```
sudo chmod 755 /
```

This will restore the root original permission.

Edit: Now I read your original post and understood your problem is worst than normal, when you get the grub (the first and inicial boot window) get the restore option, ask for prompt and do the job above.

good luck
i'm not able to get into the recovery mode!!! before that itself i get stuck at the BusyBox


what if i try the opposite of what i did above?
would that work?
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda5 ***/mnt/linux
find /mnt/linux -type d -exec chmod 644 '{}' \;
find /mnt/linux -type f -exec chmod 755 '{}' \;
umount /mnt/linux
exit

```

---

### Post by Calabresi on 2008-09-09
Well, if you are able to use the command's you are asking (I don't know what will happen if you try what you ask) you should be able to reset your root permission with the code I suggested.

---

### Post by macvr on 2008-09-09
> **Calabresi said:**
> Well, if you are able to use the command's you are asking (I don't know what will happen if you try what you ask) you should be able to reset your root permission with the code I suggested.

now i'm using my system from a Live CD...

the third post command is just reverse of what i did to mess up my system....

---

### Post by macvr on 2008-09-10
ok got a solution from the irc chats...

1) Bootup with Ubuntu LiveCD.
2) Open a terminal.  Type the command:
```
sudo fdisk -lu
```

3) In the output, find the line (there should be only 1, if you have a default/generic install) with "Linux" at the end (not "Linux swap", that's something else), e.g. for example
```
   Device Boot      Start         End      Blocks   Id  System
***/dev/sda5***   *          63   613056464   306528201   83  Linux

```
and then note down the bit at the start, e.g. ***/dev/sda5***

4) Type the following commands, replacing ***/dev/sda5*** with what you noted above:
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda5 ***/mnt/linux
find / -xdev -exec chmod /mnt/linux/'{}' --reference '{}' \;
```
after u run the last command it keeps giving errors>eg: "chmod: cannot access `/mnt/linux//usr/share/gtk-doc/html/evolution-exchange/ximian-connnector-booking.html': No such file or directory" 
this command is looking at the permissions of the live CD's files and then trying to adjust the relevant files on the install .. and off course, the install isn't going to have all the same files***[2 guys(unop,soundry) in the irc chat came up with that command, to match and reset the file permissions, on the spot! that was pretty cool]***

 after the errors , u'd get back to prompt, then
```
umount /mnt/linux
exit
```

after this was done

5]Reboot
 i returned to my original Gdm error and was not sure if i was getting connected to the web.

6]so Again from the liveCD itself, reinstalled the grub
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda5 ***/mnt/linux
mount --bind /dev/  /mnt/linux/dev
mount --bind /proc/ /mnt/linux/proc
mount --bind /sys/  /mnt/linux/sys

chroot /mnt/linux
```

# then in the chroot run this command,

```
aptitude reinstall gdm; [[ -d /var/lib/gdm ]] || mkdir -p /var/lib/gdm
```

7]to check if the gdm was installed
```
ls -dl /var/lib/gdm
```
u should receive something like this:> drwxr-x--- 2 gdm gdm 4096 2008-07-18 00:44 /var/lib/gdm

8] reboot

now i kept getting errors like this> failed to launch child process"thunderbird"(permission denied)
this is because i had messed up the permissions!

9] to correct it:
```
while read -d : dir; do sudo chmod +x "$dir"/*; done <<< "$PATH"

```

u might get errors like this:
> chmod: cannot access `/usr/local/sbin/*': No such file or directory
chmod: cannot access `/usr/local/bin/*': No such file or directory

that's fine .. those directories are usually empty

10]after that command, reboot .. and  most of it is sorted.
i might need to reinstall a few packages , still keep getting these errors for a few other packages

finally my system was rescued without needing a reinstall,

[B]i'm planning to select all packages in the synaptic and reinstall, hope that does the final resets...
[/B]



[I][U] thanks to help from the irc chat: #ubuntu... especially with help from>unop, soundry<
[/U][/I]so if anyone is going to check the irc for help,look out for those guys, they are really good, there are several others there too

---

