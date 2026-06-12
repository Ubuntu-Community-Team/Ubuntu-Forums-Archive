---
title: "Troubles with update"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by dingobass on 2014-05-20
Hi All,

I am a complete noob.... when I clicked the update this screen came up.
I have no idea what it means other than updates wont load :(

Help, Please! my putor is running really sluggish ATM...
[ATTACH=CONFIG]253314[/ATTACH][ATTACH=CONFIG]253314[/ATTACH]

Ooops... double post... told ya I was a Noob:p

---

### Post by slickymaster on 2014-05-20
Try it this way, please. Open a terminal window and run the following (one command at a time):```
sudo apt-get autoclean # this only remove files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update # to resync your package index
sudo apt-get upgrade
```

**Edit:**
Please post back any errors you might get

---

### Post by dingobass on 2014-05-20
Probably did something wrong here... I really don't know anything about how these things work....
[ATTACH=CONFIG]253327[/ATTACH]

---

### Post by Vladlenin5000 on 2014-05-20
> **dingobass said:**
> Probably did something wrong here... I really don't know anything about how these things work....
[ATTACH=CONFIG]253327[/ATTACH]

You missed the "sudo" part in all of them...

---

### Post by slickymaster on 2014-05-21
> **Vladlenin5000 said:**
> You missed the "sudo" part in all of them...

Exactly. The error message itself point you that when asking if you're root.

I would advise you to copy/past, one by one, the commands I posted before into your terminal window.

---

### Post by dingobass on 2014-05-24
Yhep.... Told ya I was a Noob...
Anyhoo, did as directed but when I hit enter- (assuming I was meant to)- I was asked for my password, no probs... or so I thought... It wouldnt work when I did so.. Kept saying wrong password?

---

### Post by LastDino on 2014-05-24
Your password is the one you typed out when you did the installation. Type that out same, you wont see anything on screen but it will be typed out as you press buttons, then hit enter. If it is same as you used during installation, it will be accepted.

---

### Post by Herbon on 2014-05-27
:-k

---

### Post by ian-weisser on 2014-05-27
Did you do what LastDino advised you to do?
He did give you the right answer.

---

