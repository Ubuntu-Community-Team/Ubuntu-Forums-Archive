---
title: "dconf-editor woes"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by lowell.dennis on 2012-07-30
I am evaluating a piece of commercial software for my company and am experiencing issue getting it to work.  The tech guy is telling me to use dconf-editor to check some settings but for the life of me, I can find dconf-editor anywhere.

I have googled and found tons of paged that say 

sudo apt-get install dconf-tools

will install dconf-editor, but when I try that it says that it can't find the package.

I also see something about 

sudo apt-get install dconf

which works, but does not give me dconf-editor and if I type "dconf" at the command line I get all kinds of deprecation warnings and nothing else happens.

I am probably being think here, but can anyone help me get dconf-editor to run.

- Lowell

---

### Post by cortman on 2012-07-30
> **lowell.dennis said:**
> I am evaluating a piece of commercial software for my company and am experiencing issue getting it to work.  The tech guy is telling me to use dconf-editor to check some settings but for the life of me, I can find dconf-editor anywhere.

I have googled and found tons of paged that say 

sudo apt-get install dconf-tools

will install dconf-editor, but when I try that it says that it can't find the package.

I also see something about 

sudo apt-get install dconf

which works, but does not give me dconf-editor and if I type "dconf" at the command line I get all kinds of deprecation warnings and nothing else happens.

I am probably being think here, but can anyone help me get dconf-editor to run.

- Lowell

It's quite simple.

```
sudo apt-get install dconf-editor
```

To run, type

```
dconf-editor
```

:)

---

### Post by asmoore82 on 2012-07-30
Which version of Ubuntu are you running?

I'm on 10.04 here and can confirm dconf-editor is nowhere to be found:

```
**$ apt-cache search dconf**
asoundconf-gtk - Applet to select the default ALSA sound card
dconf - collect system information
libgrabcd-readconfig-perl - rip and encode audio CDs - common files
libmed-tools - Runtime tools to handle MED files
xnetcardconfig - A simple network card configuration wizard for X
libc-bin - Embedded GNU C Library: Binaries
```

I've used it on 12.04 but I always had lots of trouble finding it :D.

---

### Post by lowell.dennis on 2012-07-30
> **cortman said:**
> It's quite simple.

```
sudo apt-get install dconf-editor
```To run, type

```
dconf-editor
```:)

Does not work either.

I am using Ubuntu 10.04 64-bit.

---

### Post by evilsoup on 2012-07-30
Does dconf-editor even exist for 10.04? Try gconf-editor.

---

### Post by cortman on 2012-07-30
> **evilsoup said:**
> Does dconf-editor even exist for 10.04? Try gconf-editor.

This.

Dconf was meant to replace gconf- dconf is the gnome3 verison of gconf. The commands I gave will still work; just substitute the "g" for "d".

---

### Post by lowell.dennis on 2012-07-30
> **cortman said:**
> This.

Dconf was meant to replace gconf- dconf is the gnome3 verison of gconf. The commands I gave will still work; just substitute the "g" for "d".

Okay, but what is the equivalent for dconf org -> gnome -> desktop -> media-handling on gconf?

---

### Post by VinDSL on 2012-07-30
> **lowell.dennis said:**
> Okay, but what is the equivalent for dconf org -> gnome -> desktop -> media-handling on gconf?
Don't know what you're looking for, but...

Do a search for *media*.

---

