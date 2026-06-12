---
title: "Nokia software problem."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-06-01
I have a nokia n73 and it needs a software upgrade. Its getting slow (like windows does hehe) Anyway, i tried installing the nokia software that came with the phone using wine and it juts says an error has occurred :( Is there a way to get this software working in ubuntu or is there some alternative open source software i could try. My goal is to backup all the contact data on the phone and then upgrade the software on the phone...

Also, when i try ```
sudo wine /media/cdrom0/NokiaInstaller.exe

```

i get ```
wine: /home/ben/.wine is not owned by you

```

---

### Post by sayakb on 2008-06-01
```
sudo chown user:group /home/ben/.wine
```
And try again

---

### Post by Majorix on 2008-06-01
You usually don't need sudo with wine, as wine installs in your home directory :)

---

### Post by e1ektrob0y on 2008-06-01
```
chown: invalid user: `user:group'

```
what am i doing wrong? thanks...

---

### Post by volkswagner on 2008-06-01
You sparked a new interest for me.  I have tried Wammu, multisync-gui, and others.  I had limited success.  I am going to give [Opensync](http://www.opensync.org) a try.  They have your phone listed as working.

EDIT:  UM, it is still alpha.  This may not be ready for prime time.

---

### Post by sayakb on 2008-06-01
> **Majorix said:**
> You usually don't need sudo with wine, as wine installs in your home directory :)
Yeah.. right :D

---

### Post by sayakb on 2008-06-01
> **e1ektrob0y said:**
> ```
chown: invalid user: `user:group'

```what am i doing wrong? thanks...

Replace user with your username. And group with the groupname.

---

### Post by e1ektrob0y on 2008-06-01
```
sudo chown ben:ben /home/ben/.wine
``` didn't work i still get the same error .wine is not owned by me :(

---

### Post by mister_pink on 2008-06-01
You don't need sudo on the wine command you're running. You're running it as root, so either its looking in /root/.wine and not liking it, or /home/youruser/.wine and seeing it isnt owned by root (which it shouldn't be).

---

### Post by e1ektrob0y on 2008-06-02
Bump :)

---

