---
title: "Can only mount USB Hard Drive as Root!"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by RealG187 on 2008-09-03
Okay I cannot mount this hard drive unless I am on root.

When I plug it in I get the message in screenshot 1 (1.png, the left attachment). I thought something was wrong with the drive, but it just so happens that I ran Nautilus as root and the drive mounted! I could access it from the nautilus as root, but if I try to access the finally mounted drive I get the error in screenshot 2 (2.png, the right attachment).

I think what happened is one day I plugged it in while running Nautilus as root and therefor it was mounted as root. So now everytime I wanna mount or access it, I have to be root!

---

### Post by solaceinsilence9 on 2008-09-03
> **RealG187 said:**
> Okay I cannot mount this hard drive unless I am on root.

When I plug it in I get the message in screenshot 1 (1.png, the left attachment). I thought something was wrong with the drive, but it just so happens that I ran Nautilus as root and the drive mounted! I could access it from the nautilus as root, but if I try to access the finally mounted drive I get the error in screenshot 2 (2.png, the right attachment).

I think what happened is one day I plugged it in while running Nautilus as root and therefor it was mounted as root. So now everytime I wanna mount or access it, I have to be root!


hmmm let me give it a shot.... the first image you posted (far left) tells me that you have an invalid name for the drive, like an illegal character in your mount point... 

for the second image try going to System>Administration>Users and Groups... then unlock it with your passy and click the properties of your user name that your using to try to mount the drive with... then click the User Privileges tab and make sure that the "Access external storage drive automatically" is checked.

---

### Post by RealG187 on 2008-09-03
I can access external storage. My other drives work, just not this one.

The name is VertbatimHDD which is fine, if it was the name then it wouldn't mount as root either, but it does. I thought it could be, but since it mounts as root I doubt that...

EDIT: Also Windows reads it perfectly, and windows is more picky about illegal characters! (example, cant have \ ? or " [I think] in a fileanme, but in Linux you can!)

---

### Post by RealG187 on 2008-09-04
I still need to mount it as non root

---

### Post by falcon61102 on 2008-09-04
You could mount it as root and change the permission for it once it's mounted.  Don't know if it will last once you disconnect though.  Mount it as root then change permissions with:

```
sudo chown -R username /media/disk
```

Just change username to your user name and /media/disk to whatever the mount point is.

---

### Post by RealG187 on 2008-09-05
When I did that I got this messae for every file (where [color=red]filename[/color] is the file name for everyfile (I closed the terminal cuz this was gonna go on forever!)

> chown: changing ownership of `/media/VERBATIMHDD/[color=red]filename[/color]': Operation not permitted

---

### Post by falcon61102 on 2008-09-05
You shouldn't have to change the permissions for every file if you change the permissions for the entire drive.  Try this instead:
```
sudo chown username /media/VERBATIMHDD
```

Just replace username with your user name

---

### Post by RealG187 on 2008-09-05
> mpg@MIKED5:~$ sudo chown mpg /media/VERBATIMHDD
[sudo] password for mpg: 
chown: changing ownership of `/media/VERBATIMHDD': Operation not permitted
mpg@MIKED5:~$ 

Seems to be something more than permissions, I think Ubuntu locks a drive mounted by root

---

### Post by falcon61102 on 2008-09-05
That should have done it.  Try mounting it in a different location and changing the permissions there.

---

### Post by kjohansen on 2008-09-05
there are user settings that can limit a user from being able to load external media.

System->Users and Groups

Select the user you are having problems with, hit properties, then go to the users priveleges tab.  the first one listed on mine is "Access external storage devices automatically"

---

### Post by RealG187 on 2008-09-06
@falcon61102: I went into Windows and changed the volume labal (therefor changing the mount point, it was actually "Verbatim" I just added HDD to make it "VerbatimHDD"

@kjohansen: That was suggested in the 2nd post, and it is enabled. (I can access any other hard drive or USB Device...)

---

### Post by RealG187 on 2008-09-11
I cant access this hard drive at all on my Friend's laptop with Ubuntu. Not even as root!

PLEASE HELP!

---

### Post by Ntweat on 2008-09-11
try checking ur fstab....

---

