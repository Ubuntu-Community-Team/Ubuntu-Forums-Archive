---
title: "timeout in locking authority file and lightdm"
date: 2011-06-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-26
I'm no more able to launch applications using 'gksu'
It seems there is some kind of issue with the authority file and lightdm, but I haven't yet traced the issue down.

note: using sudo there are no problems.

```
$ gksu synaptic 
/usr/bin/xauth:  timeout in locking authority file /var/run/lightdm/authority/4
/usr/bin/xauth:  timeout in locking authority file /var/run/lightdm/authority/4
glibtop: Non-standard uts for running kernel:
release 3.0-1-generic=3.0.0 gives version code 196608
```

after printing these warning synaptic is not loaded.

anyone else is getting this issue?

---

### Post by dino99 on 2011-06-26
same thing here, and have seen yesterday somebody having gksu issue too.

---

### Post by lucazade on 2011-06-26
> **dino99 said:**
> same thing here, and have seen yesterday somebody having gksu issue too.

thanks dino99 for confirming.. now i'm going to search if a bug report is already available for this.

---

### Post by Harry33 on 2011-06-26
> **lucazade said:**
> I'm no more able to launch applications using 'gksu'
It seems there is some kind of issue with the authority file and lightdm, but I haven't yet traced the issue down.
note: using sudo there are no problems.
```
$ gksu synaptic 
/usr/bin/xauth:  timeout in locking authority file /var/run/lightdm/authority/4
/usr/bin/xauth:  timeout in locking authority file /var/run/lightdm/authority/4
glibtop: Non-standard uts for running kernel:
release 3.0-1-generic=3.0.0 gives version code 196608
```
after printing these warning synaptic is not loaded.
anyone else is getting this issue?

Well I can use command
```

gksu nautilus

```

And Nautilus with root priviledges open OK.
However I get some Gtk-warnigs, but that has been going on for some time now. Doesn't seem to harm anyway.

```
(nautilus:1528): Gtk-WARNING **: gtk_widget_size_allocate():
```

---

### Post by dino99 on 2011-06-27
back to normal today (temporary trouble gone)

---

### Post by lucazade on 2011-06-27
> **dino99 said:**
> back to normal today (temporary trouble gone)

here not unfortunately.. I'm trying to figure out the problem right now.

the only way to use 'gksu' here is to switch its backend from 'su' to 'sudo'
using 'gksu-properties' dialog.

maybe something related to users and groups.. hints?

---

### Post by lucazade on 2011-06-27
Visudo file seems identical to natty's one and also switching to gdm doesn't help. arg!!

---

### Post by dino99 on 2011-06-27
maybe not related, but previously have:
- removed ppas
- downgraded related packages

to get a standard Oneiric i386

---

### Post by lucazade on 2011-06-27
This is issue from what I understand happens only when installing Ubuntu from mini image..

"Synaptic and gksu not working after minimal installation
gksu and synaptic (package manager) may not work after a minimal installtion. To fix it, install gconf-editor (sudo apt-get install gconf-editor), launch it, go to /apps/gksu/ and check sudo-mode."

From Lubuntu release notes:
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat)

Which is more or less the same solution of changing backend from 'gksu-properties'

Now I'm wondering which package sets this option during a normal ubuntu installation.

---

### Post by seeker5528 on 2011-06-27
> **lucazade said:**
> the only way to use 'gksu' here is to switch its backend from 'su' to 'sudo' using 'gksu-properties' dialog.

That makes sense if you don't have a root account enabled, looked for the settings for mine and it's already set to use sudo.

Probably could have avoided the whole situation by typing 'gksudo' instead. Is it *that* much pain to type two extra letters? ;)

EDIT: Yep, if I change it to su mode, gksu doesn't work, but gksudo still does.

Later, Seeker

---

### Post by lucazade on 2011-06-27
> **seeker5528 said:**
> That makes sense if you don't have a root account enabled, looked for the settings for mine and it's already set to use sudo.

Probably could have avoided the whole situation by typing 'gksudo' instead. Is it *that* much pain to type two extra letters? ;)

EDIT: Yep, if I change it to su mode, gksu doesn't work, but gksudo still does.

Later, Seeker

no, no pain for 2 extra letters.. i'm lazy but not that much :)
I already have the launchers in system menu that use 'gksu', so I didn't want to change all of those.

anyway it seems strange that gksu is set by default to use sudo instead of su. Isn't it?
This way gksu is the same of sudo, I thought these were different.

---

### Post by seeker5528 on 2011-06-29
> **lucazade said:**
> anyway it seems strange that gksu is set by default to use sudo instead of su. Isn't it?
This way gksu is the same of sudo, I thought these were different.

Since the default in Ubuntu is to not enable the root account, there is an argument for changing gksu to use sudo by default.

The biggest thing would probably be for script compatibility, for people attempting to use scripts targeted at debian or other distributions where many people prefer to use su instead of sudo.

Later, Seeker

---

### Post by lucazade on 2011-06-29
> **seeker5528 said:**
> Since the default in Ubuntu is to not enable the root account, there is an argument for changing gksu to use sudo by default.

The biggest thing would probably be for script compatibility, for people attempting to use scripts targeted at debian or other distributions where many people prefer to use su instead of sudo.

Later, Seeker

Absolutely a good point, haven't thought to this.
It makes sense now!

---

