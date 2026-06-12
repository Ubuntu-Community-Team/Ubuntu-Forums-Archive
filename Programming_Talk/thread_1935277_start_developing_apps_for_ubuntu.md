---
title: "start developing apps for ubuntu"
date: 2012-03-03
forum: Programming Talk
---

### Post by aoken1 on 2012-03-03
Hi there,

I want to develop apps for Ubuntu but I'm a little bit confused about the best practices doing it.

1- where to store configuration: is there any folders used by convention to store configuration data, do we have something like registry in Windows?

2- storing related data: do you recommend using database for that, e.g sqlite, or just store the data in files.

3- storing temporary data, or any default paths I should know to develop good Ubuntu app,such as /usr/bin and so.

thanks for helping me out.

---

### Post by Diametric on 2012-03-04
Hi there,

I would start here:

[http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.html](http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.html)

Point being, when you begin, you need to learn how to build .deb files (this is specific to Ubuntu and all other Debian based Linux distros...as opposed to .rpm)

Give this a read and if you have questions after you've played around with it a bit, there are very knowledgeable folks in the Development section of these forums.

Good Luck!

---

### Post by duncan12 on 2012-03-04
I'm no expert, but to answer Q1, the folder used to store config data is ```
~/.appname
```

(~ is users /home/user/ dir, the "." is important as it makes it a hidden folder)

This means that config data is a) can be different per user, b) each app has it's own folder for config.

To view these folders in Nautilus, open your home folder and hit Ctrl+H (show hidden). You'll see all your apps config there.

---

### Post by Tony Flury on 2012-03-04
@aoken1 - when it comes to storing data - choose what ever is sensible. If you only ever store a few items - then flat files are fine. If you are storing something larger - then maybe an sql engine would be right.

There are no hard and fast rules.

---

### Post by aoken1 on 2012-03-04
thanks for your help

I wanted to develop a podcast client.
I thought its good to store the episodes in Music directory,
and the podcast : name,url and last fetch in a flat file- for all of the podcasts - in a hidden folder in home dir.

is it OK?

---

### Post by Barrucadu on 2012-03-04
1. [http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html](http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html) - basically, configuration goes in $XDG_CONFIG_HOME/[program]/, or ~/.config/[program] if $XDG_CONFIG_HOME is empty.

2. That depends entirely on what sort of data you are storing, what you want to do with it, and how much of it there is.

3. [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

