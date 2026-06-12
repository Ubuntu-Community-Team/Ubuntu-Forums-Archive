---
title: "File premission question"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by extracted on 2008-05-02
I know this has probly been covered countless times, but I can not find the info I am looking for :(.

I have a samba PDC and Multiable shares

each share is owned by its own group for example
acounting directory belongs to accounting

then I have users that belong to the accounting group that use windows (quick books ftl) Now if one of my users creates a file
the premissions are set to rwxr--r--

I want every file created in this directory to be rwx for the hole group  I have tried chmod 2770 and i have tried chmod g+s
to try to set it sticky

but alas if I create a file the premissions do not come out as I would like.

---

### Post by freebeer on 2008-05-02
I'm not sure, but have you looked into the "umask" directive?  I know I've used it for ftp access, and I believe Samba as well (but it's been so long ago that I can't be sure).

---

### Post by Cybergod on 2008-05-02
Add
```
create mask = 0777
directory mask = 0777
```
to your smb.conf for the shares you want and see what happens.

---

### Post by extracted on 2008-05-02
> **Cybergod said:**
> Add
```
create mask = 0777
directory mask = 0777
```
to your smb.conf for the shares you want and see what happens.

you are a god-send. I have been messing with the systems umask wich does work if I make the file localy with touch, but it would not work if I created the file from another computer on the network.

What you gave me worked perfectly  Thank you x1M

---

### Post by Cybergod on 2008-05-02
> **extracted said:**
> you are a god-send. I have been messing with the systems umask wich does work if I make the file localy with touch, but it would not work if I created the file from another computer on the network.

What you gave me worked perfectly  Thank you x1M

I'm glad to hear that, you're welcome :)

---

### Post by bodhi.zazen on 2008-05-02
Those settings work, however if you are security minded and do not want all these files executable ...

```
create mask = 0644[FONT=monospace]
[/FONT]directory mask = 0755
```

---

### Post by Cybergod on 2008-05-02
> **bodhi.zazen said:**
> Those settings work, however if you are security minded and do not want all these files executable ...

```
create mask = 0644[FONT=monospace]
[/FONT]directory mask = 0755
```

You are correct, thanks for pointing that out.

---

