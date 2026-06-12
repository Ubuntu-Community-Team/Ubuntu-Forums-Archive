---
title: "packaging a dictionary"
date: 2008-09-10
forum: Packaging and Compiling Programs
---

### Post by spanella47 on 2008-09-10
would like to package a Hunspell dictionary that is distributed as a single file called:
en_US_OpenMedSpel.dic

How do would I package it so it ends up in the right folder to be seen by OpenOffice, Firefox, etc? 

[http://www.e-medtools.com/Hunspel_openmedspel.html](http://www.e-medtools.com/Hunspel_openmedspel.html)

---

### Post by Pro-reason on 2008-09-24
Do you just want to create a DEB for yourself, or do you want to add it to a PPA repository?

---

### Post by spanella47 on 2008-09-24
either way really. I would imagine others would use it as well since its the only medical dictionary I've found. so getting it on a PPA or in the Ubuntu repositories would be good too.

---

### Post by InfinityCircuit on 2008-09-24
Read the debian policy

[http://dict-common.alioth.debian.org/](http://dict-common.alioth.debian.org/)

Really what you need to do is make a simple debian/rules file.  You should check if you have debhelper 7 installed--if you do you can use the new "dh" calls to automate the entirety of the process and then just put the dictionary's name and install path in debian/install

---

### Post by Pro-reason on 2008-09-26
See [my tutorial]("http://ubuntuforums.org/showthread.php?p=5862233").

---

### Post by UbuWu on 2008-09-26
Spanella, I hope you can get it in the repositories. That would be a great addition!

---

### Post by spanella47 on 2008-09-28
> **Pro-reason said:**
> See [my tutorial]("http://ubuntuforums.org/showthread.php?p=5862233").

thanks alot, well done guide!

any chance you could help me with my debain/rules file. think [the debian guide]("http://dict-common.alioth.debian.org/dsdt-policy.html") is saying that i need to have installdeb-myspell somewhere. then 2 extra scripts postinst and postrm, but should they have headers or just the text they gave?

---

### Post by Pro-reason on 2008-09-28
> **spanella47 said:**
> thanks alot, well done guide!

any chance you could help me with my debain/rules file. think [the debian guide]("http://dict-common.alioth.debian.org/dsdt-policy.html") is saying that i need to have installdeb-myspell somewhere. then 2 extra scripts postinst and postrm, but should they have headers or just the text they gave?

For a DEB file as simple as the one you want to make, you don't have to worry about postinst and postrm.  Just follow my tutorial instead.

---

### Post by spanella47 on 2008-09-28
> **Pro-reason said:**
> For a DEB file as simple as the one you want to make, you don't have to worry about postinst and postrm.  Just follow my tutorial instead.

hmm, looks like those scripts are used to update the dictionary.list file so OpenOffice, etc see the new dictionary. would have to call it separately after install if not during.

---

### Post by Pro-reason on 2008-09-28
> **spanella47 said:**
> hmm, looks like those scripts are used to update the dictionary.list file so OpenOffice, etc see the new dictionary. would have to call it separately after install if not during.

Ah, well, if there is anything like that, then yes, you need to add something to the postinst script.  The Debian guide should have all the info.

---

### Post by spanella47 on 2008-09-30
was able to get everything installed in the right place, but the postinst and postrm scripts aren't working.

OpenOffice is also crashing when the dictionary is installed. Seems related to the dictionary.lst. does anyone know how to add a medical dictionary properly?

---

### Post by Pro-reason on 2008-10-01
> **spanella47 said:**
> was able to get everything installed in the right place, but the postinst and postrm scripts aren't working.

OpenOffice is also crashing when the dictionary is installed. Seems related to the dictionary.lst. does anyone know how to add a medical dictionary properly?

If it is like any other OpenOffice dictionary, then it should be sufficient to add the following snippets to the *postinst* and *postrm* scripts:

```

if [ "$1" = "configure" ]; then
	**update-openoffice-dicts**
fi

```

```

if [ "$1" = "remove" ]; then
	**update-openoffice-dicts**
fi

```

---

### Post by spanella47 on 2008-10-01
should have included the whole script code. I copied the top part from another package. other one is similar.

```
#!/bin/sh
set -e
if [ "$1" = "configure" ]; then
    update-openoffice-dicts
fi
```

also where should they be? within the debian folder?

---

### Post by Pro-reason on 2008-10-01
> **spanella47 said:**
> should have included the whole script code. I copied the top part from another package. other one is similar.

also where should they be? within the debian folder?

That's a good idea.  Look at existing, working packages in order to find out how to do things.  Use the “apt-get source” command to get a package, and look inside.

You'll see that those scripts do indeed go in the debian directory.

Here's a complete script from one of the existing openoffice dictionaries:

```

#!/bin/sh

set -e

if [ "$1" = "configure" ]; then
	update-openoffice-dicts
fi

#DEBHELPER#

exit 0

```

---

### Post by spanella47 on 2008-10-01
Think I got everything working with the install, let me know if something isn't working.

So without furthur ado, the first Medical Dictionary in Ubuntu can be downloaded from my PPA:
[https://launchpad.net/~spanella/+archive](https://launchpad.net/~spanella/+archive)

things may work differently with OpenOffice 3.0, when i update to intrepid after final release I'll try to troubleshoot any problems that may arise.

---

