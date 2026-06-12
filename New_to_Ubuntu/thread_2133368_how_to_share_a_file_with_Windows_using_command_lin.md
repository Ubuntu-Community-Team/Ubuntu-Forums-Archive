---
title: "how to share a file with Windows using command line?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by user201304 on 2013-04-08
I've generated a file on my Ubuntu Server that needs to be copied to Windows. How do I allow access to the file using only shell commands?

---

### Post by agent-squirrel on 2013-04-08
Is Windows on the same machine? Or is it a separate machine?

if it's a separate one then you need to go down the route of installing SAMBA and setting up a share so the windows machine can then access it.

If its on the same machine just mount the Windows drive partition and copy it over to a folder in Windows.

Something Like; 
```

sudo apt-get install ntfs-3g

fdisk -l 
```

Jot down the windows device name (/dev/sda1)?

```
sudo mkdir /media/win

sudo mount -t ntfs-3g /dev/sda1 /media/win

sudo cp /path/to/file /media/win/path/to/directory/
```

---

### Post by Morbius1 on 2013-04-08
*** You need to make sure samba is installed if it's not there already:
```
sudo apt-get install samba
```
*** You need to make sure the samba service is running:
```
sudo service smbd start
```
Then you need to share the folder containing the file you wish the Windows machine to access. As an example let's say the file is in /home/Shared:

*** To create a samba share of that folder:
```
sudo net usershare add shared /home/Shared "Shared Directory" everyone:F guest_ok=y
```


**net usershare add** = is the command sequence to add

**shared** = is the name of the share the Windows machine will see.

**/home/Shared** = path to the directory you wish to share

**"Shared Directory"** = is the comments next to the share

**everyone:F** = this will grant read / write (F) access to the share. If you only want to allow read access then substitute R for  F.

**guest_ok=y** = will allow guest access. If you want only authenticated users change that to [COLOR=#0000cd]guest_ok=n[/COLOR]

[COLOR=#0000cd]*But then you will need to create users on the server and add them to the samba password database.*[/COLOR]

*** You will have to change the permissions on the target directory to allow "guests" to actually write to that share. For example:
```
sudo chmod 0777 /home/Shared
```

*** If this is a temporary share you can remove it with this command:
```
net usershare delete shared
```
[COLOR=#0000cd]*That removes the sharing of the folder not the folder itself.*[/COLOR]

---

### Post by steeldriver on 2013-04-08
> **user201304 said:**
> I've generated a file on my Ubuntu Server that needs to be copied to Windows. How do I allow access to the file using only shell commands?

to *copy* rather than actually share files you may find it more straightforward to install openssh-server on the Ubuntu machine and then use a Windows scp client (e.g. WinSCP or filezilla) to pull them across

---

### Post by Morbius1 on 2013-04-08
Other that ease of setting up another advantage of the ssh route is that the client will not only be able to copy the file that you want him to copy but ( depending on the underlying Linux permissions ) at a minimum have read access to everything on the server.

Of course if the client user is also the server administrator then it don't matter none.

---

