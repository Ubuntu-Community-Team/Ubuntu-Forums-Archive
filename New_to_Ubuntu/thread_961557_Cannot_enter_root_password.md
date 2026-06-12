---
title: "Cannot enter root password"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by ewingmaestro on 2008-10-28
I installed eeebuntu on my eee pc and tried to login, finding that my username and password do not work.

I restarted and chose to drop to the root shell prompt, it says "give root password for maintanence", when i type, the cursor doesnt move and nothing appears, when i click enter it tells me its incorrect login. When i try to type my normal password anyway it doesnt work.

Is there any way to solve this or is there an alternative way to change my password or username??

thanks

---

### Post by namegame on 2008-10-28
At a shell prompt, your password will not appear at all while typing it as it remains invisible, but it is definitely there.

---

### Post by ewingmaestro on 2008-10-28
okay but what if i dont know my password??

---

### Post by bodhi.zazen on 2008-10-28
Just FYI, setting a root password is not advised. The only way you will be asked a root password when you boot to recovery mode is if you have set a password.

You have two options. One is to re-install.

The other is to set you user password from a live CD.

Boot the live CD, mount your ubuntu partition to /mnt 

then

sudo chroot /mnt

at the prompt enter

passwd <user>

where <user> is your Ubuntu password.

while you are there you can lock you root account if you wish with 

usermod --lock root

Reboot.

---

### Post by Bölvaður on 2008-10-28
> **ewingmaestro said:**
> okay but what if i dont know my password??

Reboot into recovery mode

type:
```

passwd

```
and then type the new password you want. Im not 100% this is exactly how it is, because my memory is faulty and because Im watching dummifying television... but I know there are better instructions on these forums if you search for the keyward passwd

---

### Post by bodhi.zazen on 2008-10-28
> **Bölvaður said:**
> Reboot into recovery mode

He tried that already :twisted:

> **ewingmaestro said:**
> I restarted and chose to drop to the root shell prompt, it says "give root password for maintanence", when i type, the cursor doesnt move and nothing appears, when i click enter it tells me its incorrect login.

---

