---
title: "How to install the update?"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by tomzie on 2013-02-09
Hi, I see in my Ubuntu Server when I log in the following messages.
 
5 packages can be updated.
5 updates are security updates.
 
I try at command prompt this command, but when I log out and log back in, I see the same messages again. How do I install this updates?
 
$ sudo apt-get install update
 
Please advice. 
 
Thanks.

---

### Post by sudodus on 2013-02-09
> **tomzie said:**
> Hi, I see in my Ubuntu Server when I log in the following messages.
 
5 packages can be updated.
5 updates are security updates.
 
I try at command prompt this command, but when I log out and log back in, I see the same messages again. How do I install this updates?
 
$ sudo apt-get install update
 
Please advice. 
 
Thanks.

You can either run the GUI application, that is offered with the message, or run the following commands

```
sudo apt-get update
``` followed by
```
sudo apt-get upgrade
```
and if some packages are held back (for example kernel packages)
```
sudo apt-get dist-upgrade

```

---

### Post by tomzie on 2013-02-09
Thanks for the reply. However, I still see the same messages.

---

### Post by tomzie on 2013-02-09
Hi. Thanks. I will try the last command. Sorry, I did not see it.

---

### Post by tomzie on 2013-02-09
Thanks. I am okay now.

---

### Post by ibjsb4 on 2013-02-09
Sudodus method should of fixed it.  Did you get any errors?

You can try reinstalling update manger and core.

```
sudo apt-get install --reinstall update-manager-core update-manager
```

[COLOR=Blue]Edit:  nevermind[/COLOR]

---

### Post by sudodus on 2013-02-09
> **tomzie said:**
> Thanks. I am okay now.
Congratulations to an updated system :KS

---

### Post by Jake Sweeney on 2013-02-09
To receive the updates and install them, do the following command in the Terminal:
```
sudo apt-get install update && sudo apt-get upgrade
```

Then type in your sudo password et viola!

---

### Post by 3v3rgr33n on 2013-02-09
Please mark thread as Solved if it worked.

---

### Post by deadflowr on 2013-02-09
> **Jake Sweeney said:**
> To receive the updates and install them, do the following command in the Terminal:
```
sudo apt-get install update && sudo apt-get upgrade
```

Then type in your sudo password et viola!

Having never tried this, I don't know if a package called update exists.
So running that line might cause the system to think that you want to install the package 'update', which may or may not exist.

```
sudo apt-get update && sudo apt-get upgrade
```

seems more appropriate.

To the OP, running sudo apt-get update refreshes the package list.
You should do this for a variety of reasons. The simplest being, the repos are constantly being updated with newer versions of software, most often with patches for existing software. When a patch makes its way into the repo the package gets a newer version, so if you have an update for a package that has been sitting there for a while and it was updated in the repo, but you haven't refreshed your package list. When you try to install the upgrade the old package which your update says is there is no longer there as that particular version, then the upgrade will fail, as it can't find the obsolete package.

I really don't know if that makes any sense, but hey.

---

