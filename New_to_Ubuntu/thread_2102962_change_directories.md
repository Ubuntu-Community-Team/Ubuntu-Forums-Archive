---
title: "change directories"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by Wray on 2013-01-08
Whwray@wray-Satellite-L305D:~$ ls -l
total 48
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Desktop
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Documents
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Downloads
-rw-r--r-- 1 wray wray 8445 Jan  8 11:16 examples.desktop
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Music
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Pictures
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Public
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Templates
drwxrwxr-x 2 wray wray 4096 Jan  8 13:57 Ubuntu One
drwxr-xr-x 2 wray wray 4096 Jan  8 11:25 Videos
wray@wray-Satellite-L305D:~$ 

Why can i not get to /pictures?    cd /pictures doesn't do it , neither does cd /home/wray.
i can get to /home, and /wray but not to /pictures.
i have been trying for some time to copy photos from the cd drive to pictures directory,
but i have run out of ideas..not even sure how i refer to the cd drive.:(

---

### Post by howefield on 2013-01-08
Try

```
cd Pictures
```

---

### Post by Cheesemill on 2013-01-08
```
cd Pictures
```

Linux is case sensitive.

---

### Post by Vaphell on 2013-01-08
1. names are case sensitive
2. don't try calling local directories in current location with / at the beginning
/a/b/c/d is an absolute path that starts at the root dir /

**cd** alone should take you to your home, as should **cd ~** and **cd $HOME**
~ and $HOME are aliases of your home dir and can be used to create paths, eg ~/Pictures, $HOME/Pictures

cd drive is most likely inside /media (under root dir) so something like
**cp -r /media/cdrom/pic_dir -t ~/Pictures** (depending on the actual dir structure) should work


besides, why don't you just use file browser to go to cd drive and ctrl+c/ctrl+v?

---

### Post by Wray on 2013-01-08
> **Vaphell said:**
> 1. names are case sensitive
2. don't try calling local directories in current location with / at the beginning
/a/b/c/d is an absolute path that starts at the root dir /

**cd** alone should take you to your home, as should **cd ~** and **cd $HOME**
~ and $HOME are aliases of your home dir and can be used to create paths, eg ~/Pictures, $HOME/Pictures

cd drive is most likely inside /media (under root dir) so something like
**cp -r /media/cdrom/pic_dir -t ~/Pictures** (depending on the actual dir structure) should work


besides, why don't you just use file browser to go to cd drive and ctrl+c/ctrl+v?

Just trying to learn a bit about xterm shell scripts, etc.  i did a little DOS back in prehistory, before most people on this forum were born:D
Thanks for the help...i knew that, just had a brainfart!

---

### Post by audiomick on 2013-01-08
> **Wray said:**
> ... DOS back in prehistory, before most people on this forum were born:D

Don't generalise too much. We've got our fair share of more mature users too... ;)

---

