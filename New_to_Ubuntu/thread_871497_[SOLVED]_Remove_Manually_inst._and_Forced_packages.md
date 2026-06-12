---
title: "[SOLVED] Remove Manually inst. and Forced packages"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-27
Hi, 
I recently forced Avast 32bit onto my 64 bit Ubuntu only to discover that it's performance is shaky at best.
How can i now remove this, and what ever packages i may manually install or force architecture for in future ?
What should i be taking note of in the package names so that when removal time comes around, the going is smooth ?

---

### Post by eightmillion on 2008-07-27
How did you install it? Was it with dpkg? Did you install from a .deb file?

---

### Post by BGFG on 2008-07-27
Thanks for the response,I followed this HOWTO:
```

This is my first "howto", and it's very easy:

1. $apt-get install linux32 libc6
2. Download the .deb package from [http://www.avast.com/eng/download-av...x-edition.html](http://www.avast.com/eng/download-av...x-edition.html)
3. Register you license from [http://www.avast.com/i_kat_207.php?lang=ENG](http://www.avast.com/i_kat_207.php?lang=ENG)
4. Install it: sudo dpkg --force-architecture -i avast4workstation_VERSION_i386.deb

Everytime you wanna scan: $linux32 avastgui

```
But i would also like to know how to remove after using dpkg. This is a fact finding mission for me.

---

### Post by eightmillion on 2008-07-27
You should be able to use this command to remove it.
> sudo dpkg --purge avast4workstation

In the future, you can find out the architecture of a deb file by using...
> dpkg -I package.deb
There is a line which will say something like..
>  Architecture: i386

You can't always tell from the package name.

---

### Post by eightmillion on 2008-07-27
I should mention also that
> dpkg -l searchstring
will tell you the name of the installed package.
For example...
```
$ dpkg -l opera
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  opera                         9.50                          The Opera Web Browser

```

---

### Post by Oldsoldier2003 on 2008-07-27
> **BGFG said:**
> Thanks for the response,I followed this HOWTO:
```

This is my first "howto", and it's very easy:

1. $apt-get install linux32 libc6
2. Download the .deb package from [http://www.avast.com/eng/download-av...x-edition.html](http://www.avast.com/eng/download-av...x-edition.html)
3. Register you license from [http://www.avast.com/i_kat_207.php?lang=ENG](http://www.avast.com/i_kat_207.php?lang=ENG)
4. Install it: sudo dpkg --force-architecture -i avast4workstation_VERSION_i386.deb

Everytime you wanna scan: $linux32 avastgui

```
But i would also like to know how to remove after using dpkg. This is a fact finding mission for me.
You can uninstall in synaptic. look at the category installed (local or obsolete) you can also uninstall using
```
sudo apt-get remove <packagename>
```

---

### Post by BGFG on 2008-07-27
Thanks, Great Information.
As for synaptic, i just now checked and avast is listed neither in 'local or obsolete' nor in the 'all' area. even after a search. Had searched repeatedly before my post.
On a separate note, as it was brought up.. How exactly can a category exist in synaptic called 'local OR obsolete' ? to my mind the two are decidedly separate and apart.
I have a great noob story about a young guy who ran an update once. This guy dutifully ran through every package listed and saw that 'HAL' was in several of them.
After the update, and through browsing his spanking new linux system, the guy came across an area called 'local or obsolete'.... Rembering that he had just installed spanking new updated 'HAL' libraries, he proceded to mark what he believed to be the 'old' hal stuff for removal.Them being obsolete and all, logical thinking no ?

Now that particular action led to one of the most interesting spirals of events in my......, i mean HIS life, HIS! :D

Ok! so i should have known better (coming from 6+ years of HRIS support) 
New to a system but clicking all over the place and then the audacity to hit 'APPLY', so yes, my fault
But Local [COLOR="Red"]OR[/COLOR] Obsolete ? Really ?

---

### Post by Oldsoldier2003 on 2008-07-27
if it didn't show in synaptic then if you know the package name you can use dpkg -r

if you install a deb it is supposed to be able to be removed using synaptic or apt-get , but apparently this one doesn't follow the rules.

---

### Post by eightmillion on 2008-07-27
Actually, in synaptic if you click the button in the lower left that says origin, you'll see three categories, Local/main, Local/partner, and Local/restricted. All manually installed packages should show up in one of those categories. Most likely Local/main. And if you click on the Status button, you'll find the local or obsolete section that Oldsoldier2003 was speaking of.

---

### Post by BGFG on 2008-07-27
Thanks for the pointers,
But i am usually in the status tab, so local or obsolete is something i'm familiar with. I took a look in origin and still no luck finding avast....I have seen however, Limewire and deluge, two other programs that i installed from .deb files.
Should programs installed using the
```

./configure
make
make install 

```

commands also show up in synaptic ?

---

### Post by eightmillion on 2008-07-27
No, those programs have to be uninstalled with 'make uninstall' from the directory that they were installed from. If you replace 'make install' with 'checkinstall' it will build a package and install it with your package manager so you can uninstall it with dpkg or from synaptic.

---

