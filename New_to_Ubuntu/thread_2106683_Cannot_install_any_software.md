---
title: "Cannot install any software"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by davals on 2013-01-19
I cannot install any software starting from vlc, bluemn and now bitlbee....the command is always the same but i always get same error...ref to image /home/nizor/Pictures/Screenshot-5.png

it Says E: Could'nt find package vlc
pls help
[EMAIL="davals@yahoo.com"]davals@yahoo.com[/EMAIL]
[EMAIL="omokhare@gmail.com"]omokhare@gmail.com[/EMAIL]

---

### Post by Daveth on 2013-01-19
that rather suggests that you have not installed it; just type vlc into the Ubuntu software centre search box at the top right hand side, and install when it shows it.

---

### Post by sudodus on 2013-01-19
> **Daveth said:**
> that rather suggests that you have not installed it; just type vlc into the Ubuntu software centre search box at the top right hand side, and install when it shows it.
Please remove your email addresses from your post before some spammer finds them!

Have you tried to install like this:

First make sure your system is up to date
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
and if some packages are held back
```
sudo apt-get dist-upgrade
```
Then install your packages for example
```
sudo apt-get install vlc
```

---

