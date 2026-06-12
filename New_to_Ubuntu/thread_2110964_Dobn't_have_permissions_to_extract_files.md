---
title: "Dobn't have permissions to extract files"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by tiamat2009 on 2013-01-31
I want to extract the tango icons to usr/share/Tango

How can I do this? When I try and drag the files from the archive to the folder It says I don't have permission.... and no I don't want to use the terminal... its 2012 not 1970

---

### Post by omeomi on 2013-01-31
> **tiamat2009 said:**
> and no I don't want to use the terminal... its 2012 not 1970

Sorry buddy but that's what you need to do :-) (also it is 2013!)

```
sudo tar -xvf ARCHIVE.tar /usr/share/Tango
```

---

### Post by tiamat2009 on 2013-01-31
Thanks.... and how can I edit etc/hosts?

In gedit it is read only... there must be some way I can edit it... there are several other files I need to edit to but can't (like apache config).

Is there some way of opening gedit as root or something?

---

### Post by deadflowr on 2013-01-31
Why not extract them first into your home folders .themes folder?

You can extract them there, peruse whether you actually like them ,and then if so, later on copy them to the /usr/share/themes folder.

Extracting them into the ~/.themes folder does not require root.

Though they would only be available for that user.

---

### Post by omeomi on 2013-01-31
> **tiamat2009 said:**
> Is there some way of opening gedit as root or something?

```
gksudo gedit
```

---

