---
title: "chowned entire filesystem"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Cha1n5aW on 2008-05-20
I was trying to get a program to work right, and accidentally typed..
```
shawn@compaq:~$ sudo chown -hR shawn /*
``` 
thinking I was just changing ownership on the contents of a particular directory, but I think I changed ownership on alot of thing, because now when I use sudo I get 
```
shawn@compaq:~$ sudo mkdir test
sudo: /etc/sudoers is owned by uid 1000, should be 0

```
So I know now for sure I really messed up bad, how can I fix this, or am I doomed to reinstall from scratch?

Thanks
- Shawn

---

### Post by tamoneya on 2008-05-20
that is going to be very painful to fix.  And once you think it is fixed you are going to keep getting permissions errors because of things you missed.  If it was me I would go with the reinstall.

---

### Post by iaculallad on 2008-05-20
Execute this script to reset the chown'ed folders. This will recurse in your directory.

#!/bin/sh
for u in `ls /folder`
do
chown $u:GID -R /test/$u/.
done

Replace /folder with /home or wherever other folder you want it's permission to be reset.
Replace GID with a group GID from your system (get it at System->Administration->Users and Group, located in the Advance tab.)

---

### Post by tamoneya on 2008-05-20
> **iaculallad said:**
> Execute this script to reset the chown'ed folders. This will recurse in your directory.

#!/bin/sh
for u in `ls /folder`
do
chown $u:GID -R /test/$u/.
done

Replace /folder with /home or wherever other folder you want it's permission to be reset.
Replace GID with a group GID from your system (get it at System->Administration->Users and Group, located in the Advance tab.)

That only seems to work on the home folders.  Currently he is having problems with sudoers and many of the other system files /home is a trivial matter to fix.

---

### Post by iaculallad on 2008-05-20
Yap, go with the fresh install instead. Changing sudoers will only take time prompting you for more errors regarding permissions.

---

### Post by Cha1n5aW on 2008-05-20
okay, I set up the script like this to try and undo the whole thing

```
#!/bin/sh
for u in `ls /*`
do
chown $u:0 -R /test/$u/.
done

```

but when I run it I get 
```
chown: invalid user: `/initrd.img:0'
chown: invalid user: `/initrd.img.old:0'
chown: invalid user: `/vmlinuz:0'
chown: invalid user: `/vmlinuz.old:0'
chown: invalid user: `/bin::0'
chown: invalid user: `bash:0'
....etc...


```

which just seems to go on & on & on... until I ctrl+c.   I got the GID where you suggested in user settings, on the advanced tab of the properties for the root user it states root ID as 0 when I go to "manage groups" the roots group is also 0.

---

### Post by tamoneya on 2008-05-20
> **Cha1n5aW said:**
> okay, I set up the script like this to try and undo the whole thing

```
#!/bin/sh
for u in `ls /*`
do
chown $u:0 -R /test/$u/.
done

```

but when I run it I get 
```
chown: invalid user: `/initrd.img:0'
chown: invalid user: `/initrd.img.old:0'
chown: invalid user: `/vmlinuz:0'
chown: invalid user: `/vmlinuz.old:0'
chown: invalid user: `/bin::0'
chown: invalid user: `bash:0'
....etc...


```

which just seems to go on & on & on... until I ctrl+c.   I got the GID where you suggested in user settings, on the advanced tab of the properties for the root user it states root ID as 0 when I go to "manage groups" the roots group is also 0.

That is because it is really only meant to be run on the home directory not the entire filesystem.

---

### Post by Cha1n5aW on 2008-05-20
waaa, that really blows.  Guess I shoulda been more careful, I should really have know better too, just tired and doin stuff I read on forums w/o actually thinkin about it.

Thanks for all your help.

- Shawn

---

### Post by garyed on 2008-05-20
Before doing a reinstall you might try reversing your original code by putting root instead of shawn:
```
 shawn@compaq:~$  chown -hR root /* 
```


If it works then you could change permissions on your home directories.
The majority of stuff outside of "home" is owned by root anyways. 
It still would take some time to get right but it might be an alternative if you don't want to do a reinstall.

---

### Post by Cha1n5aW on 2008-05-21
> **garyed said:**
> Before doing a reinstall you might try reversing your original code by putting root instead of shawn:
```
 shawn@compaq:~$  chown -hR root /* 
```


If it works then you could change permissions on your home directories.
The majority of stuff outside of "home" is owned by root anyways. 
It still would take some time to get right but it might be an alternative if you don't want to do a reinstall.

thanks, that was the first thing I did, unfortunately it didn't work.

---

### Post by aeiah on 2008-05-21
i did a similar thing a while ago with my /usr/bin/ folder. i did reinstall everything in the end, but it wasnt convenient for a while so i spent a few weeks just using the root/recovery boot option in grub and starting gdm manually from the command line. perhaps you can run these commands from there, since you have root permissions when you boot into that.

---

### Post by Cha1n5aW on 2008-05-21
Thats a good idea Aeiah, when I'm done backup I'll try the script from there, maybe if its run as root it will work.  I haven't restarted yet because once I do, I know nothing will work.  Right now, I'm finishing backups and stuff, then I'll restart and give that a shot.

---

### Post by ThreeTrees on 2008-05-21
It's not clear from this thread if you realize where your original problem was --> [SIZE="3"]**/***[/SIZE]

That's pretty risky to use if you don't know what it means.

Apologies if you do know what it means.

---

