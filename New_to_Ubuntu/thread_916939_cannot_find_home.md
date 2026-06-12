---
title: "cannot find home"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Vic! on 2008-09-11
kina hoping theres a way to fix my friends laptop i put ubuntu 7.10 on it and right now when he logs in the splash screen it says the home directory is missing or is being ignored. so the only thing i can do is log into the terminal ...any way to fix this? im hoping i dont have to re install :(

---

### Post by t0p on 2008-09-11
> **Vic! said:**
> kina hoping theres a way to fix my friends laptop i put ubuntu 7.10 on it and right now when he logs in the splash screen it says the home directory is missing or is being ignored. so the only thing i can do is log into the terminal ...any way to fix this? im hoping i dont have to re install :(

Sorry, what exactly is the error msg you're getting?

---

### Post by Vic! on 2008-09-11
The exact error message is as follows

> your home directory is listed as '/home/mondoe' but it does not appear to exist.
Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

---

### Post by t0p on 2008-09-11
So ubuntu installed without making a home directory?  Wow.  I'm afraid I have no idea what to do.  Could it mean you will have to reinstall?

I guess you could try to make the home directory yourself, ie give the command
 ```
mkdir /home/mondoe
```

but then you'll need to change permissions and ownership so mondoe is the owner.  Maybe do this in recovery mode?

---

### Post by Titan8990 on 2008-09-11
This often happens when useradd is used instead of adduser. Personally, I would boot into recovery mode delete the user using deluser and then recreate the user accnt with adduser.

---

### Post by WRDN on 2008-09-11
Try using a different account/ recovery mode shell, and create a folder in the /home directory for the user:

```
mkdir /home/mondoe
```

Now, you must give the folderthe correct permissions:

```
sudo chown mondoe /home/mondoe
```

Now, try to login and the folder should be recognised.

---

### Post by Vic! on 2008-09-11
now that i recall he did want to add a second user to his computer so what is the best way to undo this?? deleting the new user or making a new home directory?

---

### Post by Vic! on 2008-09-12
what will happen if i make a new home directory??

---

### Post by Jay11 on 2008-09-12
Well....you could try it but usually / and /home are 2 different partitions..and im not sure if just creating the directory "home" on the partition "/" would fix your problem...best bet would probably be to re-install. It's a painless process and I would advise to try not to delete the /home directory and/or partition this time :). First thing to try would be to, as they said in the above posts, to ```
sudo mkdir /home/*username*
``` and ```
sudo chown *username* /home/*username*
```...and > what will happen if i make a new home directory?? ...well the directory doesn't exist anymore or it wouldn't be giving you that error message, and it isn't working as it is so...couldn't hurt to try. If it doesn't work, you could get back to where you were by doing ```
sudo rm -rf /home
``` _DO NOT_ ever use that command any other time for any reason.

---

### Post by Tatty on 2008-09-12
> **Titan8990 said:**
> This often happens when useradd is used instead of adduser. Personally, I would boot into recovery mode delete the user using deluser and then recreate the user accnt with adduser.

This sounds like the best advice, i would try this before doing anything else.

---

### Post by Jay11 on 2008-09-12
I agree with Titan, I would try that first...if that doesn't work then trying adding the directory. If all else fails, re-install.

---

### Post by Vic! on 2008-09-12
thx will try using deluser. anyone know how exactly to use this?? should i just type it in the command line and then the username that he just added?

---

