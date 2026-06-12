---
title: "Partition deleted by mistake"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by iamrandy on 2012-04-24
i just deleted the partition unbuntu made with windows on a HD that i have and when it deleted it it deleted the permissions for it too can anyone help me figure this out please i'm just trying this out too and the os is ubuntu 11.10

---

### Post by papibe on 2012-04-24
Hi iamrandy. Welcome to the forums.

I'm afraid we are going to need a little more information.

How did you install Ubuntu (regular install or Wubi)? 
The partition you deleted was a Windows partition or a Ubuntu partition?
What do you mean with "the permissions were deleted"? What kind of problems are you having because of that?

Kind Regards.

---

### Post by iamrandy on 2012-04-24
installed regular and it was the windows partition and permissions for saving files it won't let me save anything to it


thank you

---

### Post by papibe on 2012-04-24
You can't save files to the Windows partitions from Ubuntu? Is that it?

How did you delete the partition?

Regards.

---

### Post by Kneegrowplease on 2012-04-24
Welcome


I know I've been in a similar situation, but you're going to have to be a little more descriptive. not even sure what you did at this point, but we'd love to help if you could just please provide a bit more info.

---

### Post by iamrandy on 2012-04-24
i had windows xp and my friend told me i might like ubuntu better.
he downloaded this free version. we created the partition to have it just incase we wanted to go back, which i never would by the way, it created a partition for ubuntu that was only 4 gigs we installed gparted partition editor and erased the partition along with windows and now the ubuntu is on it's own HD the other hd that was with it i lost ownership of


thank you

---

### Post by papibe on 2012-04-24
Could you post the result of these commands?
```
sudo fdisk -l

mount -l

df -h
```
Regards.

---

### Post by iamrandy on 2012-04-24
i don't even know what to do with that


thank you for helping though

---

### Post by iamrandy on 2012-04-24
no problem what do you need i am only a novice with this but i can stand on my own two feet

---

### Post by iamrandy on 2012-04-24
just found out on the forum how to get the terminal window up but it needs a password and my login password doesn't work

---

### Post by iamrandy on 2012-04-24
when i tried the commands sudo fdisk -1 it required a password unknown to me. with mount -1 it told me how to mount the hd in all sorts of configurations. with df -h it showed me the hard drive that ubuntu is on but not the one i lost ownership to

---

### Post by xtjacob on 2012-04-24
The password for sudo fdisk is the password you chose when you installed ubuntu. Please post the full output of the commands.

---

### Post by iamrandy on 2012-04-24
so you want me to copy the terminal and post it

---

### Post by xtjacob on 2012-04-24
Yes.

---

### Post by iamrandy on 2012-04-24
[attach][attach]216545[/attach][/attach]

---

### Post by xtjacob on 2012-04-25
That should be an l, not a 1. ```
mount -l
```

---

### Post by iamrandy on 2012-04-25
the code you have there is what i needed to put in?

---

### Post by xtjacob on 2012-04-25
Yes, you can copy it from the page and paste it into the terminal.

---

### Post by souravc83 on 2012-04-25
Your windows drive is probably not mounted. That's all.
[HTML]sudo fdisk -l[/HTML] 

would make everything clear for us.

Do you remember your password? the one you set when you were installing the system, or the one that you used in order to log in to the system? 
Please use this password when prompted after the command.

If you have forgotten this password, then that is another story altogether.You are going to need your password to work with Ubuntu, to log in, to install software etc.  I don't know how to retrieve forgotten password, but somebody else might be able to help you.

If you know the password, then use the command, and then show the screenshot, or copy paste the terminal output.

Also,you can click on the Home Folder, and the Window that pops up, on the left side, you might be able to see the Windows partition. Clicking on the partition will mount it. See if that works.

---

### Post by iamrandy on 2012-04-25
[attach]216546[/attach]

---

### Post by souravc83 on 2012-04-25
The option is the letter "l" (l as in love) not the number "1".

---

### Post by iamrandy on 2012-04-25
[attach]216547[/attach]

---

### Post by critin on 2012-04-25
Randy, go back to post #7 and copy the code with your mouse.  You know how to do that?  Highlight the code, right click the mouse and choose 'copy'.    At the terminal, right click again and choose 'paste'.
You are using the number 1 instead of the letter small l.  Copy the code and paste it into the terminal.

Your password in the terminal will not show up--you will not see it.  If you know you're entering it correctly, don't worry about not being able to see the characters.

You'll get there, just take a deep breath.  ):P

---

### Post by iamrandy on 2012-04-25
[attach]216556[/attach]

---

### Post by iamrandy on 2012-04-25
randolph@T-man:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/randolph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=randolph)

---

### Post by iamrandy on 2012-04-25
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c014

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    36497407    18247680   83  Linux
/dev/sda2        36499454    39100415     1300481    5  Extended
/dev/sda5        36499456    39100415     1300480   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x641e641e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            2048    39100415    19549184    5  Extended
/dev/sdb5        36499456    39100415     1300480   82  Linux swap / Solaris
/dev/sdb6            4096    36497407    18246656   83  Linux

Partition table entries are not in disk order

---

### Post by iamrandy on 2012-04-25
randolph@T-man:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   13G  3.4G  80% /
udev                  617M  4.0K  617M   1% /dev
tmpfs                 250M  792K  249M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  624M  608K  623M   1% /run/shm

---

### Post by iamrandy on 2012-04-25
ok i think i'm getting there

---

### Post by iamrandy on 2012-04-25
randolph@T-man:~$ /etc/fstab
bash: /etc/fstab: Permission denied
randolph@T-man:~$ /etc/passwd
bash: /etc/passwd: Permission denied


does this help????

---

### Post by astrobob.tk on 2012-04-25
> **iamrandy said:**
> randolph@T-man:~$ /etc/fstab
bash: /etc/fstab: Permission denied
randolph@T-man:~$ /etc/passwd
bash: /etc/passwd: Permission denied


does this help????

I did not read the whole thread, but from what you posted, you need use something to read the file:
```
gedit /etc/fstab
```

To edit the file, you should use sudo:

```
sudo gedit /etc/fstab
```

Similarly for the other command!

good luck

---

### Post by iamrandy on 2012-04-25
so what do i do with this


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1cd473cb-9654-4bcf-8d32-606909b78440 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b65403e8-5ed4-4e1e-9650-6ac3cf6a73f2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8

---

### Post by iamrandy on 2012-04-25
oh and thank you everyone for your help i'm really liking this ubuntu thing it's f ing awesome if i could just figure this one thing out i'd be so ecstatic and my experience would be perfect

---

### Post by souravc83 on 2012-04-25
Great. Thanks a lot. I think the second hard drive is not mounted.

So,put these commands one line at a time. When asked for the password, give your password, which you used while logging in.

[HTML]cd /media[/HTML]

[HTML]sudo mkdir new_hd[/HTML]

[HTML]sudo mount /dev/sdb6 /media/new_hd[/HTML]

Now, if the last command executes without an error, the hard drive should be mounted.
Next step. Click on that Home Folder on your Unity panel, you can see your mounted hard drive on the left hand side. 
Alternatively, you can use the command line to navigate through your hard drive. To do this, type in the terminal 

[HTML]cd /media/new_hd
[/HTML]
and you should be able to see the list of files on your new hard drive.

---

### Post by corrytonapple on 2012-04-25
Remember, your password is invisible when you enter it.  This is a security feature.  Just type it in as normal, although you can't see it, then hit enter.

BTW souravc, I'd use <code> tags instead of the <html> tags you are using.

---

### Post by iamrandy on 2012-04-25
randolph@T-man:~$ cd /media
randolph@T-man:/media$ sudo mkdir new_hd
[sudo] password for randolph: 
randolph@T-man:/media$ sudo mount /devsdb6 /media/new_hd
mount: special device /devsdb6 does not exist
randolph@T-man:/media$


this is what i got from the commands

thank you

---

### Post by xtjacob on 2012-04-25
You forgot the slash between dev and sdb6.

```
sudo mount /devsdb6 /media/new_hd
```
should be
```
sudo mount /dev/sdb6 /media/new_hd
```

---

### Post by iamrandy on 2012-04-25
[ATTACH]216587[/ATTACH]


this is my problem i can't save anything to it

---

### Post by souravc83 on 2012-04-25
Go to the terminal and type:

```
sudo chmod -R a+rw /media/new_hd
```

This should solve the problem

---

### Post by souravc83 on 2012-04-25
Also, you can copy the command from the browser, and paste it in the terminal. If you right click inside the terminal, you will get the paste option.

---

### Post by iamrandy on 2012-04-25
randolph@T-man:~$ sudo chmod -R a+rw /media/new_hd

this is what i put in [ATTACH]216592[/ATTACH]


this is what i got

---

### Post by souravc83 on 2012-04-25
But can you save files in the drive now?
Try copying some file and pasting it into the drive.
If I understand this correctly, What the screenshot says is that although you cannot change permissions, since you are not the root, owner, group and others (which means all) can create and delete files (i.e. write permission).
So, you should be able to save files in the hard drive now.

---

### Post by iamrandy on 2012-04-25
BOOOOOOOOOYAH BABY

that is totally gnarley dude 

thank you much appreciated

---

### Post by souravc83 on 2012-04-25
You're welcome. :)
Ubuntu is a great learning experience.

---

### Post by iamrandy on 2012-04-25
how do you let people know you figured it out

---

### Post by astrobob.tk on 2012-04-26
> **iamrandy said:**
> how do you let people know you figured it out

Glad that your problem has been sorted :D

You can click "Thread Tools" (in red at the top) & choose "Mark this thread as solved".

Tip: When in the terminal, use Ctrl+Shift+C to copy (instead of Ctrl+C which is an interrupting command) & use Ctrl+Shift+V to pate.

Note: In Linux & Ubuntu everyday you learn something knew (of course it all depends on how much you use it & how much you are ready to learn).

Welcome to the community.

---

### Post by cmcanulty on 2012-04-26
I believe you can get or change the password by running a live CD but someone else will have to explain the exact procedure

---

