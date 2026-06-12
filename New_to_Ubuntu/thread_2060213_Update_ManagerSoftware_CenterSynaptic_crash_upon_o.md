---
title: "Update Manager/Software Center/Synaptic crash upon opening it"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by DRS5193 on 2012-09-19
I'm on Ubuntu 12.04 right now.  I updated from 11.10.  I am dual booting with Windows 7.  

Since updating, I've gotten an error message everytime I used the update manager or installed a program via synaptic or the software center.  It hasn't been an issue because the programs have still updated as described and the software I download works as well.  But now, I can't even open up the update manager, software center, or synaptic as I get a crash screen everytime I open it.

Help please?

---

### Post by newb85 on 2012-09-19
Please open a terminal (Ctrl+Alt+T) and issue the following command:

```
sudo apt-get update > log.txt && sudo apt-get upgrade >> log.txt && exit.
```

It will ask for your password.  Enter the password you set up when you installed Ubuntu and hit Enter.  You won't get any feedback as you enter your password, and that's normal.

Once the terminal closes, attach the file log.txt to a new post here.  (The file will be in your home folder.)

---

### Post by DRS5193 on 2012-09-19
> **newb85 said:**
> Please open a terminal (Ctrl+Alt+T) and issue the following command:

```
sudo apt-get update > log.txt && sudo apt-get upgrade >> log.txt && exit.
```It will ask for your password.  Enter the password you set up when you installed Ubuntu and hit Enter.  You won't get any feedback as you enter your password, and that's normal.

Once the terminal closes, attach the file log.txt to a new post here.  (The file will be in your home folder.)

Here's the log I got.  Thank you so, so much!

---

### Post by newb85 on 2012-09-20
So sorry, I neglected something important.  Please do it again with the following command instead:

```
sudo apt-get update &> log.txt && sudo apt-get upgrade &>> log.txt && exit
```

(This command will overwrite your original log.txt, if you haven't deleted it yet.)

---

### Post by DRS5193 on 2012-09-20
> **newb85 said:**
> So sorry, I neglected something important.  Please do it again with the following command instead:

```
sudo apt-get update &> log.txt && sudo apt-get upgrade &>> log.txt && exit
```(This command will overwrite your original log.txt, if you haven't deleted it yet.)

Here's the new document.  Thank you so much!

---

### Post by jrog on 2012-09-20
> **DRS5193 said:**
> Here's the new document.  Thank you so much!
As a way of possibly fixing the GPG key errors you are having (and this may fix the remaining problems, too), try:

```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```
See if the problem persists after that. If it does, please post a new log (using the same commands given to you in earlier posts).

---

### Post by DRS5193 on 2012-09-20
> **jrog said:**
> As a way of possibly fixing the GPG key errors you are having (and this may fix the remaining problems, too), try:

```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```See if the problem persists after that. If it does, please post a new log (using the same commands given to you in earlier posts).

I did exactly that.  The upgrade manager opened, but it's worth noting that it said it can only do a "partial upgrade" as "not all updates can be installed."  I'm running this now, however I should also mention that it's being labeled as a distribution upgrade and the upgrade screen looks closer to the one that popped up when I switched from 11.10 to 12.04.  Should I be concerned?

---

