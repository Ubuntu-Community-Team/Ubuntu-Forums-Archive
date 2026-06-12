---
title: "installing a .tgz file"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by johndingli on 2008-11-23
I am trying to install a .tgz file but having problems any help please

---

### Post by fooman on 2008-11-23
before attempting that...what is it that you are trying to install?

perhaps there is a version in synaptic (system > administration > synaptic package manager) or a .deb available that you could download instead....far easier alternatives for someone not too familiar with linux.

anyways...if you right click the .tgz file and choose "extract here".  it will extract to a folder in the same directory as the .tgz file.  in that newly created folder you should find a "readme" which will give you some instructions on installing.

---

### Post by Michael.Godawski on 2008-11-23
Hi, 

what exactly do you want to install? Perhaps there are easier ways to do it, like through Synaptic or a deb file?

---

### Post by johndingli on 2008-11-23
antivir antivirus and there is no install in synaptic thanks

---

### Post by Michael.Godawski on 2008-11-23
Well, 

you really do not need an antivirus software if you are using Linux.
Read why:

[LIST]
[*][http://librenix.com/?inode=21](http://librenix.com/?inode=21)
[/LIST]
If you can't live without an  anti virus app have a look at clamav
[http://www.clamav.net/](http://www.clamav.net/)

---

### Post by -Zeus- on 2008-11-23
run these commands:

```
mkdir /tmp/tar/; cd /tmp/tar/; mv WHEREEVERTHETARIS ./; tar -xz ./*; ./configure; install; sudo make install
```

---

### Post by steveneddy on 2008-11-23
Why do you feel that you need antivirus on Ubuntu?

I haven't used it since using Linux and no issues yet.

Now when we were using Windows that was a different story.

I really don't feel as if you will need any antivirus while using Ubuntu, but this is only my opinion.

---

