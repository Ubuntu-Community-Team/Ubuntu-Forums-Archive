---
title: "Serious Problem as a Beginner"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by GreggyZed on 2008-11-16
Hello,

This morning I installed Ubuntu (using the Windows installer) and I really like what I've seen so far.  However, I cannot install any codecs or programs at all.  Everytime I do I get the problem that I need to run 'dpkg --configure -a'.  However, when I try to run this, I get the following:

```
Errors were encountered while processing:
 system-tools-backends
```

I know this is fairly broad, but are there any suggestions?

---

### Post by zenarcher on 2008-11-16
Hello and welcome to Linux,

You need to get your repositories set up and added, including Medibuntu, which will allow you go get all your codecs and packages you want.

I would strongly suggest taking a look at this link, as it will help you, even with visual steps and "copy and paste" to get everything you will probably want going.  The second page of the website will help you set up Medibuntu and add your restricted packages for Ubuntu.  Any problems, be sure to post back.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

Cheers,
zenarcher

---

### Post by shifty_powers on 2008-11-16
true, also run

```
sudo dpkg --configure -a
```

sudo gives you admin rights.

also have a look at psychocats

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by GreggyZed on 2008-11-16
Hi,

Thinks for the ridiculously fast reply.  I went through the steps and got to the one that states:

```
Import the gpg-key and update your package-list:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This returned the same error as I mentioned in the first post.  Any other thoughts?

EDIT: I didn't notice the second reply but I did use sudo when I ran the command.

---

### Post by GreggyZed on 2008-11-16
Every installation works but I always get the following error:

```
E: system-tools-backends: subprocess post-installation script returned error exit status 1
```

Anybody know if this can be ignored or is there actually something going wrong?

---

