---
title: "unmount samba share in bash script"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by lunaz on 2008-08-30
i unmount my 2 samba shares before shutting down by doing it in the terminal:

```

sudo umount //ipaddress/luna
sudo umount //ipaddress/music

```

i tried to write a bash script with the commands in it, i thought it'd bring up a terminal & i'd just have to type my pw, but it didn't work. how would i go about getting that to work? i know almost nothing about bash scripting.

---

### Post by tuxulin on 2008-08-30
normally any command that you can write in the terminal 
does work in a bin bash script to.

after writing your script what happen ?
did you make the script executable ?
did you run it via ./ ?

Tuxulin

---

### Post by bodhi.zazen on 2008-08-30
```
#!/bin/bash

umount //ipaddress/luna
umount //ipaddress/music
```save this script in /root/bin, ro, executable by root.

then you can link it in /sbin

sudo ln -s /root/bin/script /sbin/script

then you can just

sudo script

If you want to run the script w/o a password, you will need to configure sudo to allow you to run the script w/o a password.

---

### Post by lunaz on 2008-08-30
wont let me do anything in /root/bin, even if i'm using root.

---

### Post by fwre01 on 2008-08-30
> **lunaz said:**
> i unmount my 2 samba shares before shutting down by doing it in the terminal:

```

sudo umount //ipaddress/luna
sudo umount //ipaddress/music

```

i tried to write a bash script with the commands in it, i thought it'd bring up a terminal & i'd just have to type my pw, but it didn't work. how would i go about getting that to work? i know almost nothing about bash scripting.

you could use "gksu" instead of sudo in your script, then a dialog box will appear for you to enter your password

---

### Post by bodhi.zazen on 2008-08-30
sudo mkdir /root/bin

gksu gedit

Write your script in gedit and save it in /root/bin

alternately

```
sudo -e /root/bin/script # for vi

sudo nano /root/bin/script # for nano
```

---

### Post by lunaz on 2008-08-30
Thanks much guys, it seems to work now :) i added a launcher on the desktop that does command scriptname, it asks for my pw, then un mounts the shares. the script in /root/bin has permissions 755.

---

