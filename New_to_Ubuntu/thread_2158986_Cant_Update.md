---
title: "Cant Update"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by 3mutts on 2013-07-01
Ok, yesterday I try to update and I get this error:

> E:Encountered a section with no Package: header, Eproblem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.

Is there any fix for this?

BTW this is a 64 bit version of Ubuntu 13.04.

---

### Post by dino99 on 2013-07-01
dont worry, simply retry again

---

### Post by 3mutts on 2013-07-01
^ I tried that already, it still gives me the error. I also tried rebooting.

---

### Post by grahammechanical on 2013-07-01
You can try these tow commands. I have used them when I got that error.

```
sudo rm /var/lib/apt/lists/*
```

```
sudo apt-get update
```

The first command removes/deletes (rm) all the scripts in the lists directory, The second command will replace them.

Regards.

---

### Post by 3mutts on 2013-07-01
^ Yep I know what each means, I use the terminal to update! :D

Edit: fixed thanks.

---

### Post by Myglaren on 2013-07-01
^ Thanks for that.  I was unable to update either, similar reason.
Working properly again now as far as I am aware.

---

