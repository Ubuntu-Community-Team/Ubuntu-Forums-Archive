---
title: "Detecting applications who create folders"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2013-03-12
Hi

When I install apps in my pc, most of the time they create hidden folders in my home directory. Is it possible to monitor, and perhaps obtain the application name of every app
 which creates a folder in my home directory?

Regards,

Adeeb

---

### Post by Frogs Hair on 2013-03-12
I would say that most of my installed application _do not or have not_ created a folder in home. hidden folders. I don't know a way to detect that without looking at the code granted you know what to look for. You would somehow have to know this prior to the package being extracted during installation.

---

### Post by schragge on 2013-03-12
If what you mean are the folders under *~/.config* and *~/.local/share* then they are usually named after applications that created them.

---

### Post by mamamia88 on 2013-03-12
You could go into synaptic package manager (need top install in ubuntu)  and right click an installed package and click properties and there is an installed files tab that lists all files that the package installs on your system

---

### Post by schragge on 2013-03-12
@**mamamia88**
However, that list won't contain anything created under $HOME as folders there are typically created not when installing application, but when running it for the first time or when configuring it.

---

### Post by mamamia88 on 2013-03-12
> **schragge said:**
> @**mamamia88**
However, that list won't contain anything created under $HOME

yeah i just realized that sorry.  i too would like to know that rather than just digging through dot files and deleting stuff i know i don't need.

---

### Post by schragge on 2013-03-12
The only way I know to keep the full track of any changes in your home folder is described [post=12544012]here[/post].

---

### Post by 3v3rgr33n on 2013-03-12
> **schragge said:**
> The only way I know to keep the full track of any changes in your home folder is described [post=12544012]here[/post].

I'll look into this. I just get tired of havin' to remove a bunch of folders I no longer need from the home dir manually. Applications don't clean up after themselves when I remove them.

---

### Post by vasa1 on 2013-03-12
> **3v3rgr33n said:**
> I'll look into this. I just get tired of havin' to remove a bunch of folders I no longer need from the home dir manually. Applications don't clean up after themselves when I remove them.
So what is your question exactly? Do you want to find the files and folders you want to remove or do you want applications to remove the folders and files from /home when you "remove" the applications?

If it's the first, you could do a recursive listing of the contents /home before and after installing software and running the software a couple of times. Then you could do a diff. That should give you a clue.

---

### Post by eriktheblu on 2013-03-12
How about: ```
ls ~/.*
```?

---

### Post by 3v3rgr33n on 2013-03-13
> **eriktheblu said:**
> How about: ```
ls ~/.*
```?

That would require me to manually remove the folders. I was planning on making an application (in c++ , just to polish my skills) that will do that for me. 
I figured I need to see if two things are possible.

1. To register/capture the name of every application that creates folders in my home directory
2. To also get the name of the application which is being uninstalled through 'apt-get remove'

Makes sense?

---

### Post by schragge on 2013-03-13
The second task is easy once you know the name of the binary that created the folder.
```

[COLOR=green]$[/COLOR] dpkg-query -S `which ssh`
[COLOR=green]openssh-client: /usr/bin/ssh[/COLOR]

```

---

