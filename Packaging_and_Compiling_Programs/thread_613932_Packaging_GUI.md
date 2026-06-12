---
title: "Packaging GUI"
date: 2007-11-15
forum: Packaging and Compiling Programs
---

### Post by ofir_k on 2007-11-15
Hello,

I want to write a program with a gui which creates packages.

The problem is that I don't know how to package and when I tried reading manuals (from the Ubuntu wiki, the Debian site and some other sites) I didn't understand them.

So, if someone (who knows how to package) can help me with this, I (and others who struggle to package their program) will be grateful.

Regards,
Ofir

---

### Post by az on 2007-11-15
> **ofir_k said:**
> Hello,

I want to write a program with a gui which creates packages.

The problem is that I don't know how to package and when I tried reading manuals (from the Ubuntu wiki, the Debian site and some other sites) I didn't understand them.

So, if someone (who knows how to package) can help me with this, I (and others who struggle to package their program) will be grateful.

Regards,
Ofir

[https://wiki.ubuntu.com/MOTU/Events#head-85289011736e6cd32528975e164376d78fae45ad](https://wiki.ubuntu.com/MOTU/Events#head-85289011736e6cd32528975e164376d78fae45ad)
[https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)
[http://daniel.holba.ch/blog/?p=62](http://daniel.holba.ch/blog/?p=62)

I would be weary of a deb package that was created by an automated tool.  Deb packages created by checkinstall are known to screw up your system.  One of the strengths of the package system in Debian/Ubuntu is that there is a competent human being who oversees the building and maintenance of each and every package.

---

### Post by ofir_k on 2007-11-15
I didn't understand you. What do you mean by "I would be weary of a deb package that was created by an automated tool"?

---

### Post by ofir_k on 2007-11-15
Someone is willing to help me with this?
I think that a gui would make this process a lot easier.

---

### Post by ofir_k on 2007-11-15
bump

Someone?
At least tell me what is neccsary for minimal package...

---

### Post by dholbach on 2007-11-16
Having a packaging GUI tool has been proposed lots of times already. The problem is that packaging an application is not necessarily trivial. There are a lot of things to respect and putting packages up for millions of users needs special care.

There are different types of packages (python, C, packages that just install some files, libraries, etc etc). I agree with you that packaging should be easier, but for me the proper way lies in simplifying the build tools we have already.

[http://wiki.ubuntu.com/PackagingGuide](http://wiki.ubuntu.com/PackagingGuide)

---

### Post by ofir_k on 2007-11-26
I read the documentation of the MUTO team, but found no reference to simple apps like, nautilus scripts, which only need to copy files to a specific directory.

I understand that for this type of packages, only a CHANGELOG, CONTROL and COPYRIGHT files are needed in the DEBIAN folder (since there is no need to compile the source...).
However, I don't understand how to structure the files hierarchy, since I want the files to be copied to ~/.gnome2/nautilus-scripts, but I don't know how to refer to the home directory.

---

### Post by ofir_k on 2007-11-26
So, how I package a nautilus script? (I wrote one a month ago, and for learning purposes I decided to package it...)

I have CONTROL, COPYRIGHT and CHANGELOG files, but I don't know how to arrange the directory tree (I want to place the file in ~/.gnome2/nautilus-scripts)

---

### Post by loell on 2007-11-26
in that case you can just build a simple deb with **dpkg**

[http://www.tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/]("http://www.tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/")

follow the **hands on** and you can build a deb package for your nautilus script in no time. ;)

---

### Post by dholbach on 2007-11-27
Check out [https://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages](https://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages) for reference packages. example-content and ubuntu-artwork just install a few files too.

---

