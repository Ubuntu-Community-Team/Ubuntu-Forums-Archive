---
title: "set user permission for share"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by The_ALL on 2008-10-22
hi all,
i just install ubuntu desktop.the installation create an user that will write "sudo" before all commands.
But when i use "sudo mount" command,to mount a windows share on ubuntu,i can access to this share only with root user (sudo su) and i can't access with current user.
I always used root when using linux, so i have no experience with sudo comand and user permission.
Can you tell me where i must add/change permission to give access to current user to that share?
Thx

---

### Post by Sarmacid on 2008-10-22
First find out your uid and gid with the command

```
id
```

Then run this

```
sudo mkdir -p /media/mydisk
sudo mount -o uid=1000,gid=1000 /dev/sdb1 /media/mydisk
```

But change uid and gid and the device to adjust to your needs.

---

### Post by fr.theo on 2008-10-22
sudo is the only excepted way, but you can search for a way to change the permission of the directory/drive or file with the chmod command I try to find the right command hold on a sec.

---

### Post by fr.theo on 2008-10-22
sudo chmod 777 (the directory of file you need to change permission) in this case your windows share. by they way is this on a network or just on a drive, sorry got a head of my self should of asked first.

---

### Post by The_ALL on 2008-10-22
maybe i wrong explain,i write an example of what i done
------------------------------------------------
**$sudo mount -t cifs //"server_windows"/common -o username="windows_user",password="password" /mnt/common**
**$cd /mnt/common**
-bash: cd: /mnt/common: Permission denied
**$sudo su**
**#cd /mnt/common**
**/mnt/common#ls**
pippo
pluto
newfolder
**/mnt/common#**
------------------------------------------------------
but i want enter in that folder as current user not root
what have to do?

---

### Post by fr.theo on 2008-10-22
I know i am repeating my self but i am not trying to be rude is it on a local drive or network drive?

---

### Post by The_ALL on 2008-10-22
sorry
is a windows network drive

---

### Post by fr.theo on 2008-10-22
sorry to ask so many questions just trying to deduct any possibilities that would hinder your access.

have you given permission on the networked computer you wish to access to allow other computers to access it, also check if you have a anti virus software that includes its own fire wall, this will also prevent you from access. try to edit its network IP setting to allow the desired machine to gain access or simply switch it off until you get what you need.

---

### Post by alphaniner on 2008-10-22
If your only problem is that you can't cd into the directory, run

```
sudo chmod a+rx /mnt/common
```

this will give all users execute (cd into) and read access to the folder.

Are you wanting this share auto- or perma-mounted?  If you just browse the share from time to time you can type smb://xxx.xxx.xxx.xxx in the nautilus address bar.

---

### Post by The_ALL on 2008-10-22
............maybe write something wrong or else but i have no problem to access to this windows share
_i only want that a normal ubuntu user can access to this folder mounted, as root do_
why as user i can mount a share but not have access to this,and i must become root to access? is a linux internal permission problem. why i can't mount a share directly with my user without use "sudo"?

alphaniner i do 
**sudo chmod a+x /mnt/common**
and also 
**chown user /mnt/common**

but still i can't access to this folder as ubuntu user but only with ubuntu root

---

### Post by fr.theo on 2008-10-22
then your windows environment has not given permission to access this drive, are you using Vista or XP?, either way if your permissions on your windows is not set so that you can view it then you will not be able to gain access.

---

### Post by alphaniner on 2008-10-22
But he can access it as root, so it is not a problem on the windows end.

EDIT: I've never used mount to access a network share before, so forgive my ignorance.  But why are you using the cifs option and not smbfs?

---

### Post by The_ALL on 2008-10-22
> **alphaniner said:**
> But he can access it as root, so it is not a problem on the windows end.

many thx

---

### Post by fr.theo on 2008-10-22
good point, sorry about that, didn't take note of it my apologies.

---

### Post by fr.theo on 2008-10-22
do you have smbk4 installed?, if so go to settings and configure smbk4,


in network see if the network search is set to nmblookup or use smbclient.

I use smb4k its a gui interface but makes it easier to set up your network between windows and Ubuntu, sorry if I have troubled you or wasted your time, didn't mean to annoy you or any others on the forum. I also had great difficulty with my network access took me a while to fix it. 


see if that changes anything for you.

---

### Post by The_ALL on 2008-10-22
> **alphaniner said:**
> 
EDIT: I've never used mount to access a network share before, so forgive my ignorance.  But why are you using the cifs option and not smbfs?

smbfs works ok because you can run the command without append "sudo", so you can access as normal user to this share

but i have to use "mount" command to run same scripts
i thought was a simple problem to solve.

---

### Post by alphaniner on 2008-10-22
fr.theo: do you mean smb4k?  That's a KDE util.

The_ALL: I mean for *mount* one of the -t options is smbfs

---

### Post by fr.theo on 2008-10-22
alphaniner>> yes it is but it works in my ubuntu hardy 64 bit environment and it is a great GUI front end for samba configuration, helped me a lot when trying to set up my network.

---

### Post by The_ALL on 2008-10-22
> **alphaniner said:**
> 
The_ALL: I mean for *mount* one of the -t options is smbfs

-t smbsf not work on that type of filesystem

The problem is how to not append "sudo" to "mount" command, or add mount root permission to user.

---

### Post by alphaniner on 2008-10-22
Who owns directory you are mounting to before anything is mounted?

ie. have you tried making a folder in your home directory (so you don't have to use sudo to make it) and mounting there?

---

### Post by bodhi.zazen on 2008-10-22
This is basically a permissions problem.

permission of the mount point before the mount point are irrelevant and will change when you mount your samba share.

The problem is likely that your window user name is not the same as your Linux user name.

With the samba share mounted, please show us the output of

```
ls -l /mnt
```

And the output of

```
id
```

---

### Post by The_ALL on 2008-10-22
ok i solved.

create folder in /mnt/
$**sudo mkdir /mnt/**[COLOR="Red"]folder_mount[/COLOR]

change ownership on that folder
$**sudo chown **[COLOR="red"]current_ubuntu_user[/COLOR] **/mnt/**[COLOR="red"]folder_mount[/COLOR]

then i modify permission access ,adding a line at the end of this file 
--------------------/etc/fstab------------------------
//[COLOR="Red"]windows_server[/COLOR]/[COLOR="red"]share[/COLOR] /mnt/[COLOR="red"]folder_mount [/COLOR]cifs username=[COLOR="red"]windows_user[/COLOR],users,exec 0 0
------------------------------------------------------

the meaning is 
[COLOR="Green"]point_of_share point_of_mount type options_for_mount_command dump pass[/COLOR]
i put users in [COLOR="Green"]options_for_mount_command[/COLOR] to give permission to use mount and umount to all user for that share,and exec for execute files


Now as user i can use mount command for this share without "sudo"
$**mount** **//**[COLOR="red"]windows_server[/COLOR]**/**[COLOR="red"]share[/COLOR]
password:
$**cd /mnt/**[COLOR="red"]folder_mount[/COLOR]
/mnt/[COLOR="red"]folder_mount[/COLOR]$**ls**
pippo
pluto
newfolder
/mnt/[COLOR="red"]folder_mount[/COLOR]$

---

### Post by alphaniner on 2008-10-22
Congrats.  Clearly I had no idea what I was saying, my apoligies if I wasted any of your time.  There is one thing I don't understand though.  If you have that line in your fstab, isn't it mounted automatically at boot?

---

