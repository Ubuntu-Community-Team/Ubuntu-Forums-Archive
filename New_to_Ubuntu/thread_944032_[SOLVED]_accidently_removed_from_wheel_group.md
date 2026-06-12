---
title: "[SOLVED] accidently removed from wheel group"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by cgkades on 2008-10-10
for those that don't like to read.. i DO NOT have sudo privlages anymore



for those that do like to read:
i think i removed myself from the wheel group or whatever group gives me access to sudo. how do i fix this? what i think i did wrong

sudo usermod -G vboxusers brett

i think this removed me from other "extra" groups.. like the wheel group. the main problem i have right now is that i dont have physical access to this computer. if i need physical access and there is no other way to do this, then i'll have to wait a week to fix it. (i'm on travel for work)

the error message if i do sudo [anything]

brett  is not in the sudoers file.  This incident will be reported.

---

### Post by iaculallad on 2008-10-10
On your terminal:

```
sudo useradd -G admin your_username
```

---

### Post by cgkades on 2008-10-10
> **iaculallad said:**
> On your terminal:

```
sudo useradd -G admin your_username
```

uhmmmm... yeah. i DONT have sudo privlages anymore

---

### Post by bodhi.zazen on 2008-10-10
You will need to boot to recovery mode. Then add your user to the admin group.

---

### Post by sokopok on 2008-10-10
If your root account has a password set (by default is hasn't though) you can user 'su', this will give you root credentials, so you can make the necessary changes:

su
usermod -a -G admin brett

this will allow you to sudo again

---

### Post by iaculallad on 2008-10-10
> **cgkades said:**
> uhmmmm... yeah. i DONT have sudo privlages anymore

Boot from the recovery mode and use the command:

```
useradd -G admin your_username
```

---

### Post by iaculallad on 2008-10-10
> **sokopok said:**
> If your root account has a password set (by default is hasn't though) you can user 'su', this will give you root credentials, so you can make the necessary changes:

su
usermod -a -G admin brett

this will allow you to sudo again

That if the OP enabled the root account, as Ubuntu by default disabled the root account. Only option would be to boot from Recovery Mode.

---

### Post by cgkades on 2008-10-10
physical access FTW.. ok. i'll have to call my wife and walk her through some fandangaling. thanks everyone for the help. oh and no i did not enable the root account

---

### Post by cgkades on 2008-10-11
ok fixed it. had the wife boot into recovery and issue the command usermod -a -G admin brett

then i had her reboot it and remotley i edited the group file via ssh and vim

---

