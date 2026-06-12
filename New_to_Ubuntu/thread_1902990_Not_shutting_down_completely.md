---
title: "Not shutting down completely"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by roodypoo on 2012-01-01
Running 11.10. Sometimes when I shutdown I get the normal splash screen and it shuts down normal. 50% of the time it freezes on the attached screen and I have to turn it off by holding the power button.

Any ideas?

---

### Post by roodypoo on 2012-01-01
Bump for help

---

### Post by fdrake on 2012-01-01
try running the updates and reinstalling the kernel
```

sudo apt-get update && sudo apt-get upgrade

```

also what kernel are you running?
```

uname -a && cat /etc/lsb-release

```

---

### Post by roodypoo on 2012-01-01
Everything was up to date

```

c@c:~$ uname -a && cat /etc/lsb-release
Linux c 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

```

---

### Post by fdrake on 2012-01-01
try reinstalling the kernel:
```

sudo apt-get install --reinstall linux-headers-3.0.0-14-generic linux-image-3.0.0-14-generic

```

---

### Post by DS McGuire on 2012-01-01
I also have this problem, sometimes it will get to the shutdown splash screen and just crash... I'm going to watch this thread for any help. Yes, I am a thread jacker...

---

### Post by corrytonapple on 2012-01-02
Remember, only bump every 24 hours.  We're quick, but not that quick.  :P
If you want to make sure you are doing a "secure shutdown", meaning swap is emptied, and the hard disk can do what it needs to do, go to the Terminal (Just type "Terminal" in Unity) then type:
```
sudo shutdown -P now
```
Enter your password.  It won't appear in any way as you type it.
For Restart: 
```
sudo shutdown -r now
```
But it may be just fine restarting....

---

### Post by roodypoo on 2012-01-02
Sorry for the premature bump :)

I reinstalled the kernel and it is still happening. It does it whether I coose shutdown or restart.

Also, there is no swap space. Could that be the cause?

---

### Post by KdotJ on 2012-01-02
How did you install Ubuntu? There must be a swap space.

---

### Post by roodypoo on 2012-01-02
When I installed Ubuntu I deleted the swap partition.

I set up an encrypted LVM without swap because I have a small HD and a lot of RAM.

---

### Post by audiomick on 2012-01-02
> **KdotJ said:**
> How did you install Ubuntu? There must be a swap space.
For a default install, this is true. It is, however, possible to install without a swap space. With modern amounts of RAM, the system will most likely run ok, but I still don't like the idea of running without swap. Hibernate will not work without a swap equal in size to RAM.

---

### Post by corrytonapple on 2012-01-02
OP says it is only Shutdown that sometimes crashes.
I forget how, but if you hit "INS" on your keyboard, which is near the delete key, print screen, and all that stuff.  Hit that key as your system shuts down, and if it happens to be a time when it crashes on shutdown, you can see where it is going wrong.  Just write down the {ERROR] messages.

---

### Post by audiomick on 2012-01-02
Wild guess: your shutdown problem has something to do with the encrypted LVM. No idea how to investigate this, though. Sorry.

---

### Post by roodypoo on 2012-01-02
> **corrytonapple said:**
> OP says it is only Shutdown that sometimes crashes.
I forget how, but if you hit "INS" on your keyboard, which is near the delete key, print screen, and all that stuff.  Hit that key as your system shuts down, and if it happens to be a time when it crashes on shutdown, you can see where it is going wrong.  Just write down the {ERROR] messages.

It is either reboot or shutdown and it is not consistent.

I don't use hibernate and I have 8 gigs of RAM that hardly ever gets more than 50 % used.

---

### Post by KdotJ on 2012-01-02
> **audiomick said:**
> For a default install, this is true. It is, however, possible to install without a swap space. With modern amounts of RAM, the system will most likely run ok, but I still don't like the idea of running without swap. Hibernate will not work without a swap equal in size to RAM.

Off-tioic quickly, thanks for the info! I wasn't aware that's the case now.

---

### Post by corrytonapple on 2012-01-02
> **roodypoo said:**
> It is either reboot or shutdown and it is not consistent.

I don't use hibernate and I have 8 gigs of RAM that hardly ever gets more than 50 % used.
Please report what you get from the above testing method.

---

