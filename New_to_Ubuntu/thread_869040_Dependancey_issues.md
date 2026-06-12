---
title: "Dependancey issues"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by match002001 on 2008-07-24
Hello all,

I'm okay with Linux and navigation but I'm having an issue installing through the terminal.

Anything I install it keeps saying that I need to load GLib 2.0 or Glib 1.2.2 because my C compiler cannot compile information. I have searched high and low on this forum and cannot find anything on Glib or anything to get it installed. 

I know that after running ./configure it should tell me what I need to install I just can't find it in Synaptics.

Please help me

---

### Post by markbusu on 2008-07-24
Have you tried downloading the tarball and installing it from source:

[http://mail.gnome.org/archives/gnome-announce-list/2002-March/msg00068.html](http://mail.gnome.org/archives/gnome-announce-list/2002-March/msg00068.html)

---

### Post by oldos2er on 2008-07-24
What exactly are you trying to compile? Have you installed the package build-essential? Usually there is a README and/or INSTALL file that tells you which dependencies you need. You can try installing libglib1.2-dev and libglib2.0-dev and compiling again.

---

### Post by match002001 on 2008-07-24
Have not tried that exact file I will try that thank you.

Now here is an important question in my mind. Is GLib a backward compatible piece of software (i.e. XMMS requires 1.2.2 I have 2.0.1, will it still work?)

---

### Post by match002001 on 2008-07-24
> **oldos2er said:**
> What exactly are you trying to compile? Have you installed the package build-essential? Usually there is a README and/or INSTALL file that tells you which dependencies you need. You can try installing libglib1.2-dev and libglib2.0-dev and compiling again.


I've tried XMMS and Airsnort no success but I will try that link in post#2 and see what happens.

---

### Post by match002001 on 2008-07-24
Okay so I have the dependacnies and while installing GLib first during the ./configure it errored out and gave me this:
```
*** You must have either have gettext support in your C library, or use the
*** GNU gettext library. (http://www.gnu.org/software/gettext/gettext.html

```

I went to the site and I have gone in circles for the past hour

---

### Post by match002001 on 2008-07-24
HAHA I got everything working just took a little bit of digging thanks for all the help :)

---

