---
title: "Permission problems with a NAS"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Gopler on 2008-05-22
Hi 
I switched to ubuntu a few weeks ago and so far everything is great. 
I have a maxtor shared storage II on my network. I can mount it with no problems, and i can copy FROM it, But i can't copy TO it. it gives me a "permission denied" error.

What can i do to be able to put files on it?

---

### Post by Iowan on 2008-05-22
I haven't gotten to the "saving files to" stage yet, but another thread suggested adding your user to the **usershare** group in **/etc/group**. (That'd most likely be for files shared from your Ubuntu box).  How is it mounted (What command did you use?)

---

### Post by quelx on 2008-05-22
Are you prompted for credentials to login the device?  Are you a guest?

I'd suggest mounting the drive from fstab.  From the terminal (**ALT-F2** > **gnome-terminal**)

get your group number (probably 1000, but best to check, **username** is your username)

```
cat /etc/group|grep username:
```

```
nano -w ~/.smbpasswd
```
enter two lines (the user and pass you need to access the share from windows```
shareusername
sharepassword
```
**CTRL-X** to save and exit

```
chmod 600 ~/.smbpasswd
```
to make it readable only to you (and root)

```
sudo nano -w /etc/fstab
```
add a line:

```
//sambaserver/sharename /home/username/share smbfs credentials=/home/username/.smbpasswd,uid=1000,gid=1000	0	0
```

in this example do ```
mkdir ~/share
```

```
sudo mount /home/username/share
```

---

### Post by Gopler on 2008-05-26
followed your steps, but at the very last part i get an error "mount error 13= permission denied"

---

