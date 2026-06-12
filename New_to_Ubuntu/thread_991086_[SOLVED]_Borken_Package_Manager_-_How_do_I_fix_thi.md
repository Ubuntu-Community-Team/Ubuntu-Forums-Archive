---
title: "[SOLVED] Borken Package Manager - How do I fix this?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by crjackson on 2008-11-23
I was installing a package when the computer locked up and the screen went rainbow colored.

After restarting I ran?
```
sudo apt-get install -f
```

it returned an error. Then I ran:
```
sudo dpkg --configure -a
```

it also returned an error. The same error was report when running both both commands. Please see the screen shot below.

I sure hope an re-install isn't needed.  Thanks.

---

### Post by beno1990 on 2008-11-23
```
gedit /var/dpkg/available
```

Copy/paste the contents of lines 1-5 please.

---

### Post by shifty_powers on 2008-11-23
do

```
sudo aptitude
```

go to actions and clean package cache

then exit (q) and

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by crjackson on 2008-11-23
> **beno1990 said:**
> ```
gedit /var/dpkg/available
```

Copy/paste the contents of lines 1-5 please.

results in screen shot.

---

### Post by crjackson on 2008-11-23
> **shifty_powers said:**
> do

```
sudo aptitude
```

go to actions and clean package cache

then exit (q) and

```
sudo aptitude update && sudo aptitude safe-upgrade
```

there is no optionto clean package cache under the actions menu.

---

### Post by bapoumba on 2008-11-23
Please try:
```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by beno1990 on 2008-11-23
> **crjackson said:**
> results in screen shot.

According to your original post, the error dpkg is encountering is a parse error in the file /var/dpkg/available. If directly going there from the terminal isn't working, I'd suggest trying to find it in Nautilus, there *should* be a folder at /var/dpkg, which has a file called "available" inside, which contains part of your dpkg configuration; dpkg is reporting there's an error at line 2.

---

### Post by crjackson on 2008-11-23
> **beno1990 said:**
> According to your original post, the error dpkg is encountering is a parse error in the file /var/dpkg/available. If directly going there from the terminal isn't working, I'd suggest trying to find it in Nautilus, there *should* be a folder at /var/dpkg, which has a file called "available" inside, which contains part of your dpkg configuration; dpkg is reporting there's an error at line 2.

Yes, please look at the screen shot. I did find the file and couldn't open it. It seems corrupted or something. I tried to open it using root privileges as well and got the same result as shown in the screen shot.

---

### Post by crjackson on 2008-11-23
> **bapoumba said:**
> Please try:
```
sudo dpkg --clear-avail && sudo apt-get update
```

Awesome, that fixed it. Quick question though. If I had simply deleted the file and ran sudo apt-get update, would that have fixed it too...

---

### Post by beno1990 on 2008-11-23
Try the following:

```

sudo rm /var/libs/dpkg/available && sudo mv /var/libs/dpkg/available-old /var/libs/dpkg/available

```

You should run a sudo apt-get update afterwards if it works.

Edit: oops, already fixed. :)

---

### Post by ale63 on 2008-11-23
ale@ale-laptop:~$ dpkg --configure -a
dpkg: l'operazione richiesta necessita dei privilegi di superuser
ale@ale-laptop:~$ su
Password: 
su: Authentication failure
ale@ale-laptop:~$ 

how do I solve?
thanks

---

### Post by drs305 on 2008-11-23
> **ale63 said:**
> ale@ale-laptop:~$ dpkg --configure -a
dpkg: l'operazione richiesta necessita dei privilegi di superuser
ale@ale-laptop:~$ su
Password: 
su: Authentication failure
ale@ale-laptop:~$ 

how do I solve?
thanks
```
sudo dpkg --configure -a
```

When asked, type your password fully and hit ENTER. You will not see it as you type.

---

