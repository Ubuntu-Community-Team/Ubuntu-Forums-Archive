---
title: "Map folder?!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by robertmp on 2008-07-04
Hi Linux people

I am trying to setup an ftp server and have now managed to get the login system to work, but still missing some content on the server.

I tried searching for some "map folder" tutorials but came up empty. I have no idea how Linux does this and would like a hint on how to do this.

My problem is simple. Ftp users log into /home/ftp. How do I map /media/external250 so it gets visible from /home/ftp?

Or am I completely misunderstanding how this is done using Linux? :P

Thx in advance

---

### Post by ChameleonDave on 2008-07-04
Well, you could add a symbolic link, I suppose.

Type or paste this on to the command line.

```

ln -s /media/external250  /home/ftp

```

---

### Post by robertmp on 2008-07-04
thx ill try that. Will this persist after a reboot of the server?

Edit: 
Sadly that popped up as a LNK in the ftp server. I can't access it.
Think what I need in there is a folder.

---

### Post by hyper_ch on 2008-07-04
are you the only one who wants to access this computer by ftp?

---

### Post by robertmp on 2008-07-04
Nope. Myself and a few friends. No anonymous access

---

