---
title: "Mounting an HDD Starting learnig"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Tuexnovia on 2013-03-10
Hi guys there I go again is hard to change but worth it... But I got some questions for you, if you don't mind...


If I mount the hdd in the folder /home/"Username" (Everything disappears) I mean...

Well I've notice that all what it was in that folder disappears and then when you restart the computers it shows up again why? where does it goes? is it safe?


I'm already about to finish touching the file /etc/fstab and I got few questions...
                               

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <> pass>
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0  $
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0


SO... When I mount the HDD with DISK it get mounted in /media/"Username"
I thought!!! that when I was mounting the ned HDD the file FSTAB would change, and it doesn't.
Then I got lost...

But If I do.:   Sudo fdisk -l I can see my hardrive before and after... and it makes sence...

I don't know if you know what I mean. I just want to understand a little bit more.


The last one, xD... If I want to mount automaticly the HDD called /sda3 from the beggining I'd have to do....

I didn't undesratnd the "UUID" But I understood that is the name of my HDD in linux /dev/"sda3"


When I mount I do

sudo mount /dev/sda3 /media (and it work)

To edit the fstab it would be...

/dev/sd3 /media "Type which one NTFS? automatic?"                                           <options>       <dump>  <pass>
                                                                                                                        NO IDEA       NO IDEA NO IDEA

THis is when I HAVE MOUNTED THE DISK, and it appears here, but not in FSTAB.file
> /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   122882047    61337600    7  HPFS/NTFS/exFAT
/dev/sda3       122882048   625137663   251127808    7  HPFS/NTFS/exFAT



Sorry for the mess...

---

### Post by Bashing-om on 2013-03-10
Tuexnovia; Hi !
Pleased that you are making an effort to learn. The following are links for tutorials. Read them to make a foundation upon which to launch your questions.
[URL="https://help.ubuntu.com/community/Fstab"]http://ubuntuforums.org/showthread.php?t=283131

https://help.ubuntu.com/community/Fstab[/URL]

[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Please do not feel that I am being short with you, These tutorials will instruct you much better then I can, overall,[INDENT=3]
I am try'n to help

[/INDENT]

---

### Post by prodigy_ on 2013-03-10
> **Tuexnovia said:**
> If I mount the hdd in the folder /home/"Username" (Everything disappears) I mean...
In this case /home/username folder is the mount point. After mounting it shows you the contents of the mounted partition instead of its own contents. But any subfolders/files in the mount point are not overwritten so you get them back after unmounting.

And editing /etc/fstab only makes the OS automatically mount the partition at boot.

In short, you want to use an empty folder. :)

---

### Post by sandyd on 2013-03-10
When you mount the HDD, the mount does not appear in FSTAB.

As said above - mounting into a folder with files in it already does not replace files/folders already in the directory

You have to manually add the entries to fstab if you want the OS to mount the drive at boot.

In this case,
```

/dev/sda3 /media/folder ntfs-3g defaults, 0 0
```, where *folder*is a folder in /media (please dont mount directly to /media, it drives some applications crazy because they need to mount other devices there too)

---

### Post by Tuexnovia on 2013-03-11
Guys everything clear, thanks for everything. Why have you put ntfs-3g instead of ntfs, and why because it says hpfs/ntfs/exfat
ok AND to know exactly which tipe of HD I got I've to do this...

sudo blkid

> /dev/loop0: UUID="a62c0e80-8458-4204-84ec-c2aaa5421ea2" TYPE="ext4" 
/dev/sda1: LABEL="System Reserved" UUID="D2B8F80CB8F7ED3B" TYPE="ntfs" 
/dev/sda2: UUID="8E20075820074725" TYPE="ntfs" 
/dev/sda3: LABEL="D" UUID="6C124DA4124D73DC" TYPE="ntfs" 


> **sandyd said:**
> 
In this case,
```

/dev/sda3 /media/folder ntfs-3g defaults, 0 0
```, where *folder*is  a folder in /media (please dont mount directly to /media, it drives  some applications crazy because they need to mount other devices there  too)

What's the diference between "ro,noauto,user,exec" or something like that, to "defaults"

Thanks guys... Just learning you know xDD

---

### Post by El Tito on 2013-03-11
ro = mount the filesystem read only.
noauto = If you don't want the device to be mounted automatically, the device can be mounted only explicitly.
user = allows normal users to mount the device, whereas nouser lets only the root to mount the device.
exec = lets you execute binaries that are on that partition.

source: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by oldfred on 2013-03-11
You can use man from a terminal to learn basics, but it can be terse.

 man fstab
> defaults
                     use default options: rw, suid, dev, exec,  auto,  nouser,
                     and async.
some more info
man mount

Generally UUIDs are prefered over devices for mounting with fstab. I have several drives plugged in and did not notice I skipped a port on the motherboard. So sometimes my flash drive is sdb and sometimes sde, and then hard drives get changed around which as long as I use UUIDs do not cause any issues.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by Tuexnovia on 2013-03-11
Perfect guys really thanks, now I really feel ready to touch it for myself, and I got few questions 
in a future I won't be asking that much basically because I'm just learning how this system works...


> 
Well as far as I've seen, fstab is something like this.

file system - mount point - type - options - dump - pass
   -Good-       -Good-     -Good-   -lost-  -good- -good-

**[SIZE=3][COLOR=#0000cd]Question 1[/COLOR][/SIZE]:** dump and pass always 0 0 "I'll study this in a future but right now I think is not important"




I really don't understand this "[COLOR=#0000cd]options[/COLOR]"

how many options can be? just the next one?

[COLOR=#0000cd]Options[/COLOR]: 

auto,user,exec,ro,sync, (or defaults instead) 

I've read the manual 5 times and several of them and I still missing some points,
and then I've seen this in this order rw,**[SIZE=2][COLOR=#ff0000]suid, dev[/COLOR][/SIZE]**, exec, auto, nouser, (and much more like)
rw,nosuid,nodev,allow_other,default_permissions,bl  ksize=4096 0 0

> **[COLOR=#0000cd][SIZE=3]Question 2:[/SIZE][/COLOR]** then I realized and those other comands? where are the coming from?[COLOR=#ff0000] **"dev" "suid" **[/COLOR]and much more...


Well is very important for me to understand this I guess with an explanation of you guys, I'll be able 

to understand that little concept.


> [B]
[COLOR=#0000cd][SIZE=3]Question 3:[/SIZE][/COLOR][/B] I read somewhere use templates instead for NTFS.. and then this code

UUID="yourhdd" /media/"folder" ntfs defaults,nls=utf8,unmask=000,uid=1000,windows_names 0 0


what does it mean use templates? is a kind of code to properly be able to mount a NTFS partition without any problem?


Really thanks for your effort guys.

---

### Post by oldfred on 2013-03-11
A template is just the format mostly filled in, but where you have to change to your UUID and your mount point.

It is not always 0 0 for dump & pass.

       For more details please read man mount.

  >  # The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.


And since fsck cannot run on NTFS, then for NTFS it is 0. If you need to run file checks on NTFS you have to use your Windows repairCD.

---

### Post by Morbius1 on 2013-03-11
NOTE: I'm only posting because you asked. Unless I'm mistaken you have a  Wubi install so your NTFS partition is already mounted at /host. Not an expert on Wubi installs though ....:
> /host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 $
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0


> Question 3: I read somewhere use templates instead for NTFS.. and then this code

UUID="yourhdd" /media/"folder" ntfs defaults,nls=utf8,[COLOR=#0000cd]**umask**[/COLOR]=000,uid=1000,windows_name  s 0 0
[COLOR=#0000cd]* There's a mistake in that line- it's not unmask it's umask.*[/COLOR]

UUID="yourhdd" is the UUID ( universally unique identifier ) for that partition. You can find it using this command:
```
sudo blkid -c /dev/null
```
/media/folder is the mount point

ntfs is the filesystem ( [COLOR=#0000cd]ntfs points to ntfs-3g so it doesn't matter which one you use[/COLOR] )

defaults = rw, suid, dev, exec, auto, nouser, and async.
[COLOR=#0000cd]*I'm not going to go through each one but remember that some of them like rw ( mounts the partition read-writeable ) and exec ( mounts the partition executable ) is a statement of ability.  Making a mounted partition read-writeable does not necessarily make it rw to you.*[/COLOR]

nls=utf8 has to do with character encoding.

umask = the permissions you want to remove from the default for that NTFS partition which is 777 so a umask=000 removes no permissions.

uid = the user id of the user you want to own the mounted partition. In this case 1000 is usually you.

windows_names prevents you in Linux from saving a file with a name that contains characters that windows cannot interpret.

---

