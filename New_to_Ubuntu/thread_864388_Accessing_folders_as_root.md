---
title: "Accessing folders as root"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by le singe on 2008-07-19
Hello again.

Trying to delete a particular folder, when I select "move to trash" I get an error telling me the "device or resource busy."  Looking at the permissions under its properties I see that the owner is root and "you are not the owner, so you can't change these permissions."

I think all I need to do in order to delete it is either login as root or do a sudo root thing.  If I restart under "restore mode" will I then have root access?  I read as well in another post that in the console "sudo -i" will work, so if I type this will I have root access across the board, or is this specific to the program you want to open?

Can I mess anything up loading in "restore mode?"  I can be careful...

---

### Post by neurostu on 2008-07-19
Yes if you reboot in restore mode then you are logged in as root.

Its easier to just open a terminal and use the following commands:
```

sudo - do as root
rm - remove or delete
rmdir - remove directory (only works if the dir is emptry)

```

** REMEMBER ** sudo rm -rf <dir> : this will completely remove a directory... be very careful with this command as it can be used to cause permanent damage to your system.

---

### Post by sisco311 on 2008-07-19
or open the file browser as root:
```
gksu nautilus
```
be very careful with this too.

---

### Post by maybeway36 on 2008-07-19
Rule of thumb: always add -v to rm, so you know what's going on.

---

### Post by daimaru on 2008-07-19
> **neurostu said:**
> Yes if you reboot in restore mode then you are logged in as root.

Its easier to just open a terminal and use the following commands:
```

sudo - do as root
rm - remove or delete
rmdir - remove directory (only works if the dir is emptry)

```** REMEMBER ** sudo rm -rf <dir> : this will completely remove a directory... be very careful with this command as it can be used to cause permanent damage to your system.

if u try to remove a directory that is not empty use -r parameter for recursive 
```
sudo rm -r foldertodelete
```

---

### Post by rockerphil on 2008-07-19
any of the former suggestions will work, but here's what i found easiest when performing root tasks. open up a terminal and run this

[snip]

that will allow you to set the password for the actual "root" user accoutnt, so just go through the questions it asks you, then once done log out of your account and you'll be able to log in as user "root" with the new password you set. this will give you unrestricted access to the system. hope this info helps, 

Phil

---

### Post by Vakman on 2008-07-19
I agree with Rockerphil. That certainly is the easiest way, I also find.

---

### Post by sisco311 on 2008-07-19
> **rockerphil said:**
> any of the former suggestions will work, but here's what i found easiest when performing root tasks. open up a terminal and run this

(*command deleted*)

that will allow you to set the password for the actual "root" user accoutnt, so just go through the questions it asks you, then once done log out of your account and you'll be able to log in as user "root" with the new password you set. this will give you unrestricted access to the system. hope this info helps, 

Phil
[URL="http://ubuntuforums.org/showthread.php?t=765414"]
**Forum policy on log-in-as-root tutorials**[/URL]

---

### Post by daimaru on 2008-07-19
> **rockerphil said:**
> any of the former suggestions will work, but here's what i found easiest when performing root tasks. open up a terminal and run this

sudo passwd

that will allow you to set the password for the actual "root" user accoutnt, so just go through the questions it asks you, then once done log out of your account and you'll be able to log in as user "root" with the new password you set. this will give you unrestricted access to the system. hope this info helps, 

Phil
guys that means you are enableing root, which might be a security risk. [snip - root login unsupported]

it is still better to leave the root login and use 
```
sudo -i
```
instead, which drops you to the root prompt but does not setup a root account.
for grafical folder access as root use 
```
gksu nautilus
```

---

### Post by rockerphil on 2008-07-19
much apologies, i do try to keep up with forum policies and standards, but was unaware of that particular policy, i'm simply accustomed to logging in as user root for certain administrative tasks, but thank you for informing me of my mistake, much regards,

Phil

---

