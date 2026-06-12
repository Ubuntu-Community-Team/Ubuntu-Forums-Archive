---
title: "Rewriting a script"
date: 2010-09-18
forum: Programming Talk
---

### Post by Jonny87 on 2010-09-18
I'm trying to rewrite script that will copy files across a network to a samba share. I used it when i was using the standard gnome interface and now that I'm using kubuntu, it appears that I have to rewrite. It worked fine for me in the Gnome interface except for the one draw back that I had to first mount the shared directory for it to work.
I'm looking for someone that knows more about this stuff to be able offer a better script line.

Here is the original;
```
cp -ruv /home/jonny/Documents/* /home/jonny/.gvfs/jonny\ home\ on\ 192.168.1.64/Documents/
```

---

### Post by Jonny87 on 2010-09-20
*bumb*
is anyone able to provide any help with this? would be really good if I could get it going.

---

### Post by pbrane on 2010-09-20
/home/jonny/**.gvfs** is the GNOME virtual file system. So do you have GNOME installed too? I don't use KDE but I think that KIO is the KDE equivalent of gvfs.

---

### Post by Jonny87 on 2010-09-20
> **pbrane said:**
> /home/jonny/**.gvfs** is the GNOME virtual file system. So do you have GNOME installed too? I don't use KDE but I think that KIO is the KDE equivalent of gvfs.

Yea I realize that its the gnome virtual file system, thats the reason for this thread, to try and get some assistance to rewrite it for KDE. I posted the original as an example of what I'm trying to achieve. Or even if someone knows of a better way of doing it. I'm still getting used to the KDE way of things but so far I like the KDE environment.

---

### Post by raffaele181188 on 2010-09-21
Maybe this helps
```

REMOTE="//192.168.1.64/Documents"
LOCAL=~/Desktop/samba-share
#create mount point
mkdir $LOCAL
#mount samba share
sudo mount -t smbfs $REMOTE $LOCAL
#copy files
cp -ruv ~/jonny/Documents/* $LOCAL

```
This is a pure shell script, so you are not bound to any specific desktop

---

### Post by Jonny87 on 2010-09-21
> **raffaele181188 said:**
> Maybe this helps
```

REMOTE="//192.168.1.64/Documents"
LOCAL=~/Desktop/samba-share
#create mount point
mkdir $LOCAL
#mount samba share
sudo mount -t smbfs $REMOTE $LOCAL
#copy files
cp -ruv ~/jonny/Documents/* $LOCAL

```This is a pure shell script, so you are not bound to any specific desktop


Thanks I'll give it ago and let ya know if it works.

---

### Post by Jonny87 on 2010-10-04
> **raffaele181188 said:**
> Maybe this helps
```

REMOTE="//192.168.1.64/Documents"
LOCAL=~/Desktop/samba-share
#create mount point
mkdir $LOCAL
#mount samba share
sudo mount -t smbfs $REMOTE $LOCAL
#copy files
cp -ruv ~/jonny/Documents/* $LOCAL

```This is a pure shell script, so you are not bound to any specific desktop

I've tried it from both ends and keep getting the following;
```
jonny@jonny-desktop:~/Desktop$ ./Test_Sync.sh
[sudo] password for jonny: 
Password: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Any ideas?

---

### Post by Jonny87 on 2010-10-04
After some palying around I got it working. The Final result is as follows;
```

REMOTE="//192.168.1.65/Documents"
LOCAL=~/Desktop/jonny-laptop

#create mount point
mkdir $LOCAL

#mount samba share
kdesudo mount -t smbfs //jonny-laptop/Laptop $LOCAL -o credentials=/home/jonny/.Folder_Sync

#copy files
cp -ruv ~/Documents/* $LOCAL
cp -ruv $LOCAL ~/Documents/* 


```

---

