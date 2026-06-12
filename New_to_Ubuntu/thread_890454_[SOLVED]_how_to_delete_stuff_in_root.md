---
title: "[SOLVED] how to delete stuff in /root?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
I have no idea how, but I accidentally created two folders in /root, and now I want to delete them, but Ubuntu won't let me. It says permission denied when I try to delete them, what do I do? Both folders are empty.

This is how I created the folders if you wanna know, I was actually just following some instructions on a FAQ page, and it ended up like this :p

```

sudo su
mkdir ~/blahblah/

```

---

### Post by iaculallad on 2008-08-15
> **zzzonked said:**
> I have no idea how, but I accidentally created two folders in /root, and now I want to delete them, but Ubuntu won't let me. It says permission denied when I try to delete them, what do I do? Both folders are empty.

This is how I created the folders if you wanna know, I was actually just following some instructions on a FAQ page, and it ended up like this :p

```

sudo su
mkdir ~/blahblah/

```

On your terminal, do the command below:

```
sudo su
rm -f ~/blahblah
```

Or, you could just do:

```
gksudo nautilus
```

and look for that folder, then delete it.

---

### Post by zzzonked on 2008-08-15
First option didn't work. It told me "cannot remove /root/blahblah is a directory".

Second one worked, but it felt dangerous. Like I could just delete anything off my hard drive, and there wasn't even a confirmation message, I'm never doing that again :p

---

### Post by iaculallad on 2008-08-15
> **zzzonked said:**
> First option didn't work. It told me "cannot remove /root/blahblah is a directory".

Second one worked, but it felt dangerous. Like I could just delete anything off my hard drive, and there wasn't even a confirmation message, I'm never doing that again :p

Yes, using **gksudo nautilus** would be very dangerous as you have the privilege to do whatever you want with folders and files. Just be very careful when using that option.

---

### Post by edm1 on 2008-08-15
```
sudo rm -R ~/blahblah
``` be very careful with this command!

---

### Post by zzzonked on 2008-08-15
Is there supposed to be an empty folder named "Desktop" in /root? Or is /root supposed to be empty? Now I'm not sure if I alse accidentally created another folder called Desktop -.-"

---

### Post by iaculallad on 2008-08-15
> **zzzonked said:**
> Is there supposed to be an empty folder named "Desktop" in /root? Or is /root supposed to be empty? Now I'm not sure if I alse accidentally created another folder called Desktop -.-"

Root has an empty Desktop folder by default.

To check it out:

```
sudo -i
```

input your password and on successful entry, type:

```
ls
cd Desktop
```

---

### Post by zzzonked on 2008-08-15
Okay, thanks, so I'll just leave that Desktop folder alone and never ever go near the "/" directory again :p

---

### Post by iaculallad on 2008-08-15
> **zzzonked said:**
> Okay, thanks, so I'll just leave that Desktop folder alone and never ever go near the "/" directory again :p

It's good to explore, its a way of learning. Just be sure that you know the adverse effect what you're doing.

-When you're into editing system configurations, just be sure to create backup first.

---

### Post by nicedude on 2008-08-15
you should also be careful using sudo su unless you have a real reason to since you can delete/change anything when logged in as root, thereby breaking system etc.

---

