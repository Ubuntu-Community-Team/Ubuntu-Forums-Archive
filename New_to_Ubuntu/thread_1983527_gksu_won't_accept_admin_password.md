---
title: "gksu won't accept admin password"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by megalodonnl on 2012-05-20
Hi,

I have two user accounts, admin and one for me. Both passwords are NOT accepted when I try to do the following:

---------------------------------------------------------------------------------------------
_TERMINAL:_
mega@ubuntu:~$ sudo nautilus
[sudo] password for mega: 
Sorry, try again.
[sudo] password for mega: 
mega is not in the sudoers file.  This incident will be reported.
mega@ubuntu:~$ 
---------------------------------------------------------------------------------------------

I'd like to add that it's a bit confusing that the terminal asks for the '[sudo] password for mega', while it should simply  ask for the admin or sudo password PERIOD, since that's what I need to do admin tasks, right? 

The same for when I try accessing drives/parts in Nautilus: in the first explaining text it says correctly that a su password is needed, OK, I get that. But when you'd overread that and just read the bottom sentence, besides the input field, it asks for the 'password for mega', which is incorrect and confusing.

Both su and my own user passwords don't work and I'm 100% sure I typed it correctly (several times), which seems to have something to do with me not being in the sudoers file...

Also, trying su admin won't work either:
--------------------------------------------------
mega@ubuntu:~$ su admin
Unknown id: admin
--------------------------------------------------
Unknown id? I sure do got an admin account...


BTW: The reason why I want to run nautilus with admin rights is because, after changing my user password, suddenly, I'm not allowed to access my storage partition, which never has been a more special part then the others (=side note), while the other partitions are still totally accessible after I give the admin password.

Input is appreciated.

---

### Post by coffeecat on 2012-05-20
You would appear to be misunderstanding much about admin accounts. First, have a read of this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

A few specific points:

* - There is no such thing as a sudo or admin password in Ubuntu. An account which is in the admin group (pre-12.04) or sudo group (12.04) can gain admin privileges with its own password when sudo is used.

* - Your mega account is not in the admin/sudo group and not in the sudoers file. That is why the password prompt does not accept your mega password, and the password for your admin account is totally irrelevant when using the mega account. You would need to add mega to the admin/sudo group.

* - Do not use sudo with graphical apps. Use gksu or gksudo - see the above link for details.

* - Using a root nautilus because you haven't the permissions to access a partition is not good practice You need to adjust the permissions on the mounted partition or the mount options used to mount it. Post details and someone can help.

Do you want to add mega to the admin group?

---

### Post by megalodonnl on 2012-05-20
Yes, you're correct, I'm confused in that area, I'm totally used to being either an admin or a random user. I figured it would be the same for Ubuntu because it mentions 'admin' in the user accounts. Thnx for the link. I'll post back if I need more help.


> **coffeecat said:**
> You would appear to be misunderstanding much about admin accounts. First, have a read of this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)




---

### Post by megalodonnl on 2012-05-20
Well, I added myself as a sudo user in the sudoers file and I also took another look at the permissions. And the latter confuses me (again :) ), because the permissions are EXACTLY the same as for the other drives/partitions ( folder access, group, owner, etc.) and yet this particular drive I am not allowed to access (which was no problem before I changed my user password btw).

Also, the partition in question does NOT show up in Nautilus anymore, except when I use the admin account or when I 'sudo nautilus'.

---

### Post by coffeecat on 2012-05-20
OK then - we need to do a bit more investigating to see what's happening with this partition that you are having permissions problems with and which is no longer showing up in Nautilus.

First - a preamble which you might know already. The first created account will have a UID (user id) of 1000 and the default group for that account (the group name will be the same as the username) will have a GID of 1000. The second created account will have UID:GID of 1001:1001. My guess is that your admin account is the first with a UID of 1000, and the mega account the second with a UID of 1001. If files belonging to the first account are saved on a Linux filesystem with permissions of 660 (for example - read-write for owner, read-write for group, and none for anyone else), then the second account will not be able to open those files. Things are somewhat different for Microsoft filesystems which don't support Linux permissions and access will be determined by mount options.

Let's get some information. Open a terminal and post the output of these commands:

```
sudo fdisk -lu
sudo blkid
mount
cat /etc/fstab
```

You can copy the terminal outputs for pasting into your post by highlighting with the mouse, right-click -> copy. If you know which partition is causing you problems, please indicate this.

I'm puzzled as to why access to this partition changed after you changed your password. The two should not be related. But let's get the above information and take it from there.

---

### Post by Lisiano on 2012-05-20
> **megalodonnl said:**
> Well, I added myself as a sudo user in the sudoers file and I also took another look at the permissions.There was no need to modify sudoers, try reverting the changes and just making yourself an Administrator from User Accounts in System Settings. Or running this from a terminal from your admin account
```
sudo useradd mega sudo
sudo useradd mega adm
```
> **megalodonnl said:**
> 
Also, the partition in question does NOT show up in Nautilus anymore, except when I use the admin account or when I 'sudo nautilus'.
Don't run GUI applications using sudo, please use gksu or gksudo instead. For more information on why not to, refer here [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by megalodonnl on 2012-05-22
Hi again. Thanks for the advice so far. 

To my total amazement, I can access the partition AND it shows up normally in Nautilus. I have no clue why. I haven't been on Ubuntu for a whole day, didn't change anything.

I have a triple boot system. Could it perhaps be that by using that partition in another OS that this will influence Ubuntu?

Despite I have access again, I followed the instructions anyway and here's the output of the cmnd's (note the  # UNCONFIGURED FSTAB FOR BASE SYSTEM):

-----------------------------------
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78f65a0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   221151231   110574592    7  HPFS/NTFS/exFAT
/dev/sda2   *   221151232   384991231    81920000    7  HPFS/NTFS/exFAT
/dev/sda3       384997725  1953520064   784261170    5  Extended
/dev/sda5       384997788   466897094    40949653+   7  HPFS/NTFS/exFAT
/dev/sda6       466897158   776132279   154617561    7  HPFS/NTFS/exFAT
/dev/sda7       776132343  1349556389   286712023+   7  HPFS/NTFS/exFAT
/dev/sda8      1349556453  1953520064   301981806    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc65d81c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   976768064   488376000    f  W95 Ext'd (LBA)
/dev/sdb5           16128   488392064   244187968+   7  HPFS/NTFS/exFAT
/dev/sdb6       488392128   976768064   244187968+   7  HPFS/NTFS/exFAT
mega@ubuntu:/$ sudo blkid
/dev/loop0: UUID="3aeb87a9-b001-4bc4-a3b1-cb306b3e4e9c" TYPE="ext3" 
/dev/sda1: LABEL="winxp" UUID="E2D445AAD44581B1" TYPE="ntfs" 
/dev/sda2: LABEL="win7x64" UUID="3260447660444339" TYPE="ntfs" 
/dev/sda5: LABEL="media1" UUID="4FC7E27F05961DFC" TYPE="ntfs" 
/dev/sda6: LABEL="media2" UUID="515197124DCE8738" TYPE="ntfs" 
/dev/sda7: LABEL="273GB" UUID="339350F768CFFFB7" TYPE="ntfs" 
/dev/sda8: LABEL="storage" UUID="29A3CECF09EECF88" TYPE="ntfs" 
/dev/sdb5: LABEL="LIBS" UUID="38F8555BF8551888" TYPE="ntfs" 
/dev/sdb6: LABEL="AUDIO" UUID="EE3094093093D6C5" TYPE="ntfs" 
mega@ubuntu:/$ mount
/dev/loop0 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mega/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mega)
gvfs-fuse-daemon on /var/lib/lightdm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lightdm)
/dev/sda8 on /media/storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
mega@ubuntu:/$ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
mega@ubuntu:/$ 
```-------------------------------------------------------------------------------------------------

The problem partition was /dev/sda8: LABEL="storage"

I rather not change anything again in the sudoers stuff because at least I got access now, unless it's really strongly recommended. I decided to put some time in Learning @ [http://www.linuxcommand.org](http://www.linuxcommand.org), because I felt totally OK with Ubuntu (being Win user) until this weird partition problem occured after my passwords were not accepted. After that the partition disappeared as I mentioned... And now it reappeared like a German Uboat after WWII in Antartica :)

So I've reaad about this ' # UNCONFIGURED FSTAB FOR BASE SYSTEM' and I need to correct this to avoid the system becoming unstable? Is this true? This is what I've read: 

```
Grub2 debconf This is specific to Debian Squeeze and later and Ubuntu systems. 
This needs to be done, or the machine may become unbootable if grub2 is upgraded.
```

---

### Post by coffeecat on 2012-05-22
I'll post quickly because it's very late here and I will be logging off soon. I need to look at your outputs in detail and I'll do that tomorrow sometime - not for some hours yet. In the meantime:

You have a wubi installation. Somewhat unusually, your host partition is sda5, your media1 partition. I'll explain more tomorrow.

I'll need to do some looking into the unconfigured fstab. I think you've experienced an unusual bug, but it should be easy enough to edit /etc/fstab to complete it.

---

### Post by bcbc on 2012-05-23
This /etc/fstab issue has been around since 11.10 wubi (the standalone install using wubi.exe). It's still present in 12.04. Here is the bug report: [lpbug]857954[/lpbug]. I'm not sure it causes any problems (no clear cases since 11.10 was released) since the root is not mounted from /etc/fstab.

On the other issue, with Wubi it's a little confusing exactly which username you have (the one that will have sudo access) It's whatever you entered when you installed Wubi, but Wubi has the odd trick of using the Windows user name as the description.

e.g. You boot your 'admin' account in Windows, install Wubi with user 'fido'. When you log on to Ubuntu you'll see 'admin' not fido. Only if you go to the /home folder or look at a terminal will you see the real username. 
So this should clarify what your username really is:
```
ls /home
```

PS you can easily rename the description 'admin' by logging in as 'admin', clicking on 'admin' (top right), click on 'User accounts' (bottom of the drop down menu), then click on 'admin' (left pane), then click on 'admin' in the right pane, change it, hit Enter. Log off and log on to update the GUI. You don't have to do this but it might make things less confusing.

---

### Post by coffeecat on 2012-05-23
@megalodonnl, I'm glad bcbc posted because bcbc is expert on wubi systems.

Since you didn't mention that you had a wubi system at the beginning of the thread, I'll assume that you didn't realise that this was important information. Here's a useful wiki page for your bookmarks:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Since your partition access issue seems to have resolved itself, and since bcbc has reassured that /etc/fstab is unlikely to be a problem, do you have any problems now with your installation?

---

### Post by megalodonnl on 2012-05-23
Well, he wrote he is _*not sure*_ whether it causes any problems... 

But thanks guys, it must be the Wubi install then. At least I learned my lesson on using that. Indeed, I didn't know that it's related since nothing like this is mentioned on the Ubuntu's webpage on installing Ubuntu as far as I noticed anyway. Might be worth a warning (if it's not already there).

I was in Windows, logged in as 'megalodon',  and figured it sounded  handy to use Wubi cause I wouldn't need to burn a cd. I know it's always smart to have Ubuntu on cd/usbstick though. This Wubi install was more or less for testing purposes. I'll probably re-install when I'm comfortable enough in Linux.

This is what ls /home gives: 

```
mega@ubuntu:~$ ls /home
mega  megalodon

```As far as I'm concerned, there's no problem at this point 'cause I can access my drives. But I'll probably reinstall anyway when I get around to it. I guess this is also the reason why I'm always asked to supply a password for 'megalodon' while my usr name is 'mega'....

---

### Post by bcbc on 2012-05-23
> **megalodonnl said:**
> Well, he wrote he is _*not sure*_ whether it causes any problems... 

But thanks guys, it must be the Wubi install then. At least I learned my lesson on using that. Indeed, I didn't know that it's related since nothing like this is mentioned on the Ubuntu's webpage on installing Ubuntu as far as I noticed anyway. Might be worth a warning (if it's not already there).

I was in Windows, logged in as 'megalodon',  and figured it sounded  handy to use Wubi cause I wouldn't need to burn a cd. I know it's always smart to have Ubuntu on cd/usbstick though. This Wubi install was more or less for testing purposes. I'll probably re-install when I'm comfortable enough in Linux.

This is what ls /home gives: 

```
mega@ubuntu:~$ ls /home
mega  megalodon

```

As far as I'm concerned, there's no problem at this point 'cause I can access my drives. But I'll probably reinstall anyway when I get around to it.

I say I'm *not sure* because the absence of a problem doesn't mean that it doesn't exist. Of course if you want to conclude that this or generally 'Wubi' caused the sudo problem, that's okay with me (it didn't). It *is* definitely better to have a normal dual boot. Good luck :)

PS megalodon has the sudo rights

---

### Post by megalodonnl on 2012-05-23
> **bcbc said:**
> 
PS megalodon has the sudo rights

Yes, admin = megalodon. I just renamed admin to megalodon.

---

### Post by megalodonnl on 2012-05-23
BTW: one thing Wubi did correctly is detecting my other OS's. I just finished a manual install of Ubuntu and now only Win7 is in the Grub menu and WinXP is ignored. I guess this is a good way to keep oneself occupied :)

---

