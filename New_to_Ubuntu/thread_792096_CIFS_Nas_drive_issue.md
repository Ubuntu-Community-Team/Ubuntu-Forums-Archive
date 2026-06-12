---
title: "CIFS Nas drive issue"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DamonChyld on 2008-05-12
I am having an issue reestablishing my NAS connection after a reinstall following my cheat-sheet here:
```

**synaptic-package-manager**
samba
smbfs

**Terminal**
sudo gedit /root/.credentials
   username=****
   password=****
sudo chmod 600 /root/.credentials
cd /
sudo mkdir BigDisk
sudo gedit /etc/fstab
   //192.168.0.66/bigdisk /BigDisk cifs credentials=/root/.credentials,rw,auto,uid=dna,gid=dna

sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
sudo mount -a (or restart)
``` 

I did my laptop at the same time and am not having any issues with using these steps. If I take off the .credentials and put in my user/pass it will connect, though then I have my login info in fstab and a desktop icon (I am mounting it to /BigDisk so that I can make a shortcut on my top panel and not have to have the icon laying around all the time). 

I appreciate any help on this ;)

---

### Post by Paqman on 2008-05-15
Since the problem seems to be the authentication step, what happens if you chmod your smbcredentials file to 700?

---

### Post by DamonChyld on 2008-05-15
Thank you for getting back to me.

I chmod'd the credentials file to 700 but still get the same error:
```
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

---

### Post by bobblehat on 2008-05-15
Did .credentials already exist before you did this? If so it might be worth checking the owner is correct?

Just trying to think through all the possibilities - sorry if that's too obvious.

---

### Post by DamonChyld on 2008-05-15
I appreciate the obvious answers, sometimes the those problems are the most annoying to troubleshoot as you think you already had it covered! 

Unfortunately that was not the case here, I followed the steps outlined in my first post exactly :) I also compared the credentials file on my laptop (working mount) with my desktop (the one with the issue) and they appear to be identical (content & permissions).

---

### Post by bodhi.zazen on 2008-05-15
Two suggestions.

First the line in fstab should read :

> 
//192.168.0.66/bigdisk /BigDisk cifs credentials=/root/.credentials,rw,auto,uid=dna,gid=dna  **0 0**

Second, did you add your user (in the credentials file) to samba on the server ?

Third, the credentials file may need spaces, not sure on that.

username = ****
password = ****

Try manually mounting with the options

sudo mount -t cifs //192.168.0.66/bigdisk /BigDisk -o username=***,password=***

just for debugging

---

### Post by DamonChyld on 2008-05-16
Thanks for your reply bodhi.zazen. Unfortunately the issue did not resolve though your debugging step did mount it properly.

I added the two trailing 0's to my fstab, did not have a samba user setup (didn't need one on the laptop with the working share) so added one using "sudo smbpasswd -a usernamesudo" and restarted samba but still get the "Mount error 13" output.

:confused:

---

### Post by bodhi.zazen on 2008-05-16
I assume it is a typo in your credentials file then.

I was in error, there is not space in the syntax

username=samba_user
password=samba_password

Otherwise, can you post the exact error message ?

---

### Post by DamonChyld on 2008-05-16
Hmm, my credentials file contains only:
```
username=usr
password=pass
```
I did try it with the space but reverted when it did not sole the issue.

Error message:
```
~$ sudo mount -a
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

---

### Post by bodhi.zazen on 2008-05-16
Not to ask the obvious ... 

you do know that you need to change "usr" to the samba user (on the server) and "pass" to the actual password ?

---

### Post by DamonChyld on 2008-05-17
Heh.. no, I changed them for posting :)

I created the samba user using sudo smbpasswd -a <username> and then restarted, is this all I needed to do? 

I have not got into samba so I could easily be missing something obvious there. I did not need to change anything on the laptop though, and do not recall having to get into it the first time I installed Ubuntu.

---

### Post by bodhi.zazen on 2008-05-17
Well, if it works from the command line :

```
sudo mount -t cifs //192.168.0.66/bigdisk /BigDisk -o username=***,password=***
```samba is configured properly.

your fstab entry is fine (I tested it with my fstab changing the relevant information).

that leaves, by process of elimination, your credentials file ...

---

### Post by DamonChyld on 2008-05-18
I am traveling over the weekend but will try to delete and recreate the .credentials file when I get back to the desktop. Again, thank you for troubleshooting me through this!

---

