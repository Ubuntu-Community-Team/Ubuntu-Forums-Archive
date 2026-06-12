---
title: "Multiple RAR archives."
date: 2008-10-09
forum: New to Ubuntu
---

### Post by redlegion on 2008-10-09
I need an easy solution for extracting the contents of numerous RAR archives at once. It would be nice if I could simply specify a base directory that a program could recurse through every directory and extract the contents of every archive throughout the directory structure, but I somehow doubt that what I'm looking for exists...

In other words, let's say I have an entire season of some popular television series in XviD format, RAR'd all pretty and such in subdirectories named by the episode in the season, and each archive split into sections of 15,000,000 bytes. Is there any command line tool or shell script in existance that can parse the subdirectories and spit out the XviD's for each episode in a specified output folder for me?

It's a serious pain to type rar x /path/to/crap.part01.rar . && rar x etc. and so forth.

Should I just get started on writing my own shell script to do what I need done?

---

### Post by quibbler on 2008-10-09
> **redlegion said:**
> I need an easy solution for extracting the contents of numerous RAR archives at once. It would be nice if I could simply specify a base directory that a program could recurse through every directory and extract the contents of every archive throughout the directory structure, but I somehow doubt that what I'm looking for exists...

In other words, let's say I have an entire season of some popular television series in XviD format, RAR'd all pretty and such in subdirectories named by the episode in the season, and each archive split into sections of 15,000,000 bytes. Is there any command line tool or shell script in existance that can parse the subdirectories and spit out the XviD's for each episode in a specified output folder for me?

It's a serious pain to type rar x /path/to/crap.part01.rar . && rar x etc. and so forth.

Should I just get started on writing my own shell script to do what I need done?
You can install unrar from the Synaptic Package Manager and use the
Archive Manager to do that.
Another option is to install winrar with wine.

Regards quibbler

---

### Post by redlegion on 2008-10-09
Unfortunately File-roller doesn't have that functionality. It can open single archives, but it can't handle a queue of multiple archives.

I don't think I quite made clear what I wanted.

For instance, check out a program called "Extractnow". It's a windows based program that can extract multiple archives, one after the other.

I need extractnow's ability in command line form. Is there a program that can do that?

---

### Post by medic2000 on 2008-10-09
No you can do it.(Cause i am doing) Just right click an archive and select open. It will open everyone of them and give you a complete directory.

If it is not just try the 7-zip

---

### Post by jerome1232 on 2008-10-09
> **redlegion said:**
> I need an easy solution for extracting the contents of numerous RAR archives at once. It would be nice if I could simply specify a base directory that a program could recurse through every directory and extract the contents of every archive throughout the directory structure, but I somehow doubt that what I'm looking for exists...

In other words, let's say I have an entire season of some popular television series in XviD format, RAR'd all pretty and such in subdirectories named by the episode in the season, and each archive split into sections of 15,000,000 bytes. Is there any command line tool or shell script in existance that can parse the subdirectories and spit out the XviD's for each episode in a specified output folder for me?

It's a serious pain to type rar x /path/to/crap.part01.rar . && rar x etc. and so forth.

Should I just get started on writing my own shell script to do what I need done?

Shouldn't be too hard to make a script that searchs directories for .rar's and then feeds them one by one to unrar.

---

