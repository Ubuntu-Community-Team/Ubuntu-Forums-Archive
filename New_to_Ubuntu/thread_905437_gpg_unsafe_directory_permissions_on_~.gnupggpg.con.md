---
title: "gpg: unsafe directory permissions on ~/.gnupg/gpg.conf"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by RATM_Owns on 2008-08-30
Everytime I reboot, I can't log in so I have to log in to Failsafe Terminal and run a little script which does "sudo chown -hR andy:andy /home/andy" and whenever I use gpg now I get this error:
```
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/andy/.gnupg/gpg.conf'
```

So, could somebody help me fix that? And if possible, tell me a line to add in the fixing script so it will do that after taking control over /home/andy?

---

### Post by gmxgeek on 2008-08-30
Who is it trying to assign the owner or /home/andy to?

and what are the current permissions and owner of that config file, and its containing folder?

---

### Post by RATM_Owns on 2008-08-30
Err... I'm andy on the computer and I'm just trying to get back control of /home/andy so I can login.

---

### Post by gmxgeek on 2008-08-30
Please boot into recovery mode, drop into a root shell, and enter
```

ls -l /home

```

please copy and paste output here.

---

### Post by RATM_Owns on 2008-08-30
total 20
drwxrwxr-x 156 andy andy    12288 2008-08-30 11:37 andy
drwxr-xr-x   2 ftp  nogroup  4096 2008-08-29 16:24 ftp
drwxr-xr-x   3 root root     4096 2008-06-30 11:17 remastersys

I don't know if it matters, but since I'm way too lazy, I just opened up a root terminal.

---

### Post by gmxgeek on 2008-08-30
is this before or after going through
```

sudo chown -hR andy:andy /home/andy

``` 
as you previsouly stated?

---

### Post by RATM_Owns on 2008-08-30
After

---

### Post by gmxgeek on 2008-08-30
Okay, well, if you could do that before, (hence rebooting into recovery), then i can see who the system is trying to set the owner to on boot, since you said you have to run that command each time you boot.

The other error you are getting is because you are not the same user as that file is owned by. Please post
```

ls -l ~/.gnupg/gpg.conf

```
in addition to the above post request, both from root shell after reboot

---

### Post by RATM_Owns on 2008-08-30
It shows:

```
drwxr-xr-x 157 root root 12288 2008-08-30 12:20 andy
```

---

### Post by gmxgeek on 2008-08-30
ok, so it is being reset to root either on bootup or shutdown....
you could put a script in your startup to change it automatically, but that is just a cover, and doesn't address the root of the problem.

Also, can you post
```

ls -l ~/.gnupg/gpg.conf

```

so i can see who is the owner of that?

---

