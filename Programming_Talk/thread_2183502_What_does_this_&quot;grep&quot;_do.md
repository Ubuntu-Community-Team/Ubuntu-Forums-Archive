---
title: "What does this &quot;grep&quot; do?"
date: 2013-10-25
forum: Programming Talk
---

### Post by vasa1 on 2013-10-25
In [https://lists.ubuntu.com/archives/xubuntu-users/2013-October/006109.html](https://lists.ubuntu.com/archives/xubuntu-users/2013-October/006109.html), in a response about finding out whether libnotify was installed by default in Xubuntu 13.10, there is this code:
```
grep -m1 "apt-get --yes install" /var/log/apt/history.log |\grep libnotify;echo $?
```
What is going on after the "|"? What does "\grep libnotify;echo $?" do? 

Would not ```
grep -m1 -c libnotify /var/log/apt/history.log
```do the same?

---

### Post by sudodus on 2013-10-25
I think it is like this:

It finds the first matching line containing "apt-get --yes install"

and then tests if libnotify is found in that line.

echo $? prints the exit status (0 if successful, otherwise a higher number).

---

### Post by vasa1 on 2013-10-25
But what does "\" in front of "grep" do or mean?

---

### Post by sudodus on 2013-10-25
It means that the original grep is to be used, not an alias or some other special tweak.

A very evident example is this:

I have this alias in my .bashrc

```
 alias rm='rm -i'
```

which makes rm interactive (and safer). But if I want to remove a lot of files (for example a directory tree), I use

```
\rm -r directory-name
```

and it will not be interactive.

By the way

```
sudo rm file-name
```

does not use the aliases in my .bashrc, so I have to be careful.

---

### Post by vasa1 on 2013-10-25
All clear now. Thanks!

---

### Post by ajgreeny on 2013-10-25
If you want to ensure that **sudo rm** also acts interactively you can add the same alias to the  root's bashrc file at **/etc/bash.bashrc** as I have done.

---

### Post by sudodus on 2013-10-25
> **ajgreeny said:**
> If you want to ensure that **sudo rm** also acts interactively you can add the same alias to the  root's bashrc file at **/etc/bash.bashrc** as I have done.

Yes, that is a good idea :-)

---

