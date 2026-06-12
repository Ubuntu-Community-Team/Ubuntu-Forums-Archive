---
title: "[SOLVED] Creating a folder in /etc"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Cuban_Eight on 2008-09-09
I'm using mdadm to create a raid5 array for my MythTV backend server and I've got to the stage where I have to make a "mdadm.conf" file and put it in the /etc folder.

There's no way I can write anything into /etc.  I can't create a folder, paste a file or folder or anything.  I'm logged on as the user MythTV creates when its installed, which has root permissions I believe.  All the mdadm guides I've read just say to create the conf. file in /etc and its all good, so I've obviously missed something somewhere...

anyone got a clue for me?

---

### Post by Dougie187 on 2008-09-09
you need to use sudo to create or move things to /etc

---

### Post by elmer_42 on 2008-09-09
As Dougie said, you need to use sudo for any terminal commands you use to write to /etc. However if you are using a graphical application (like Nautilus) you should use gksu, as sudo is only meant to be used with terminal commands.

---

### Post by Cuban_Eight on 2008-09-09
Okay, I used

sudo mkdir /etc/mdadm

and created a folder no worries.  Creating the .conf file is still causing me trouble.  The commands I'm trying to use are..

sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf

which gives me a 'permission denied'
and then

sudo mdadm --detail --scan >> /etc/mdamd/mdadm.conf

which gives me a 'permission denied' also..

---

### Post by Dougie187 on 2008-09-09
echo doesn't work how you would think with sudo. At least from my experiences. it would be easier done if you wanted to make that .conf file in your home directory and then move it with sudo mv.

---

### Post by shirilover on 2008-09-09
You probably need to create the file first by using

sudo touch /etc/mdadm/mdadm.conf

---

### Post by Cuban_Eight on 2008-09-09
Thanks guys,  I tried the mv command, as I'd already created the mdadm.conf file elsewhere when I was fiddling around.

sudo mv mdadm.conf /etc/mdadm

did the trick.

---

### Post by Vivaldi Gloria on 2008-09-09
If you are on the command line edit using

```
sudo nano /path/file
```

and in gnome press ALT+F2 and start

```
gksudo gedit /path/file
```

Also you can use

```
gksudo nautilus
```

to browse as root.

---

