---
title: "Accidenstupidly set account type to Standard"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by clovisdecruz on 2012-05-29
Hi,

I have accidentally and moronically set my only valid user account to Standard type from Administrator. So I can't revert it and now I can't  do any changes. The only other account I have is the guest account. I've been trying all sorts of **** in the terminal and recovery console like :

1) usermod -a -G admin [B]username
[/B]
2) usermod -a -G admin,sudo **username**

3) sudo adduser **username** admin

Is there a way to fix this so I can feel like a less moron or do I have to reinstall the OS?

---

### Post by matt_symes on 2012-05-29
Hi

From the grub menu select recovery mode and boot into a root console.

If you are using 12.04 type

```
usermod -aG sudo <your_user_name>
```

else

```
usermod -aG admin <your_user_name>
```

Then type 

```
reboot
```

**EDIT:** I missed that bit about you have tried the recovery console. Did that not work ? Try then again.

Can you post the output of 

```
groups
```

Kind regards

---

### Post by kc1di on 2012-05-29
try this one in terminal
```
sudo usermod -aG sudo <username>
```
without the <>

---

### Post by clovisdecruz on 2012-05-29
First I get this:

usermod -aG sudo clovis
usermod: cannot lock /etc/passwd; try again later.


Then I get this:
sudo usermod -a -G sudo clovis
[sudo] password for clovis: 
clovis is not in the sudoers file.  This incident will be reported.


It appears in both terminal and recovery console.

---

### Post by matt_symes on 2012-05-29
Hi

Is the drive mounted read only ?

In the root console type

```
mount | grep ^/dev
```

Your looking for a line like this

```
matthew@matthew-Aspire-7540 ~ % mount | grep ^/dev
/dev/sda1 on / type ext4 ([COLOR="Red"]**ro**[/COLOR],errors=remount-ro)
matthew@matthew-Aspire-7540 ~ % 
```

If you see a "ro" like i have, highlighted above, on / then type

```
mount -n -o remount,rw /
```

an then try the usermod command again.

You need to be in the root console to do this though. It should just be a text interface.

If it still gives you problems then you can also do it from a LiveCD/USB (assuming you have one).

Kind regards

---

### Post by Irihapeti on 2012-05-29
Here's a step-by-step set of instructions with screenshots:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Disclaimer: I've not actually tried it myself, but it looks like it should work.

---

### Post by clovisdecruz on 2012-05-30
No dudes. Looks like the drive is already read / write and I still get the "cannot lock /etc/passwd; try again later" error.

---

### Post by zombifier25 on 2012-05-30
Is there any file named passwd.lock or anything.lock in /etc? If so, remove them.

---

### Post by wilee-nilee on 2012-05-30
I would chroot to the install and do the fix from there, run a visudo and add the user to all. The first X the HD the second X is the partition your trying to access, this is done from a live cd.
                                  [FONT=Verdana, sans-serif][SIZE=1]```
sudo mount /dev/sdXX /mnt
``` [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``` [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]```
sudo chroot /mnt
``` [/SIZE][/FONT] 
                                     
Run the visudo here.

[http://www.pendrivelinux.com/how-to-add-a-user-to-the-sudoers-list/](http://www.pendrivelinux.com/how-to-add-a-user-to-the-sudoers-list/)
[FONT=Verdana, sans-serif][SIZE=1]
```
Exit chroot: CTRL-D on keyboard
``` [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]```
sudo reboot
``` [/SIZE][/FONT] 
     
  I would think this would work, it does on a debian set up to give sudo to a limited account.

---

### Post by clovisdecruz on 2012-05-30
no man, there's no file called passwd.lock or .lock

---

### Post by clovisdecruz on 2012-05-30
think i'll just reinstall it

---

### Post by matt_symes on 2012-05-30
Hi

> **zombifier25 said:**
> Is there any file named passwd.lock or anything.lock in /etc? If so, remove them.

I think the lock file is named .pwd.lock in Ubuntu now and is a hidden file in /etc. 

```
 % ls /etc/.pwd.lock 
/etc/.pwd.lock

```

That is what is would have looked at next though; the lock file.

Kind regards

---

### Post by clovisdecruz on 2012-05-30
Wondering about the Xs... does linux have a c: or d: naming scheme for the partitions... I don't think so. So do I just use the full name of the hard disk and partition.

Anyways, I am downloading the 12.04 ver as I currently use the 11.10 version. Hopefully I'll be able to recreate an admin ID. Or should I delete the linux partition from windows and try again.

---

### Post by matt_symes on 2012-05-30
Hi

> **clovisdecruz said:**
> Wondering about the Xs... does linux have a c: or d: naming scheme for the partitions... I don't think so. So do I just use the full name of the hard disk and partition.

Linux names hard drive partitions as sda1, sda2... sdb1, sdb2... depending on the number of hard drive and the number of partitions.

I.E

sdXY, where X is the drive and Y is the partition number on that drive.

> 
Anyways, I am downloading the 12.04 ver as I currently use the 11.10 version. Hopefully I'll be able to recreate an admin ID. Or should I delete the linux partition from windows and try again.

You should be able to fix the admin problem from a LiveCD. Use the link that was supplied by Irihapeti.

I have used both the LiveCD method and the root console method in that past. This is why i was surprised you were having problems with the root console method.

Personally, i would back up my data and install 12.04 as i think it is better than 11.10. 

If you want to go down this route then might i suggest using 12.04 as a liveCD/USB for a couple of hours just to make sure there are no problems.

Kind regards

---

