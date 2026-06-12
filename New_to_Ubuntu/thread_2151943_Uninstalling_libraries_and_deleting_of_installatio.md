---
title: "Uninstalling libraries and deleting of installation files"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by DreeDrunk on 2013-06-06
Hello there,

I installed some libraries for C++. This wasn't possible with the help of the Ubuntu-Software Center in form of packages. So I had to download a tar.gz file.
[LIST]
[*]What to do with that untarred file after the installation process (configure, make, make install)? 
[/LIST]
Because all the libraries and commands are now located in my usr/local/... folders. Can I safely delete the folder I downloaded? One problem I think this would bring on is the easy way of uninstalling the files if I no longer want them on my system. I read in the INSTALLATION file in the untarred folder, that you can type 'make uninstall' with a terminal in that location.
[LIST]
[*]How to uninstall libraries to which you only know some name (in my case: openFST 1.3.3)? 
[/LIST]
They do not appear in the package center under installed things. Is there a kind of log which things you installed without the software center?

Thanks for help,
Dree

---

### Post by dino99 on 2013-06-06
install synaptic, its a tool listing all the archives with dependencies/dependants for each package.

---

### Post by DreeDrunk on 2013-06-06
Thanks for the tip but I already did this and under the search I couldn't trace anything down. I installed openfst 1.3.3 and tested "fst", "open" and "openfst" without even one file that matches. I installed an optional package for synaptics that said to search for libs also.

Another idea? Or did I make a mistake with my search?

---

### Post by monkeybrain2012 on 2013-06-06
If you installed those from the tarball they won't show up in the package manager (unless you created a .deb with checkinstall first) In that case you would have to manually remove them but make sure you know what you want to remove. If you remove the wrong things you may break your system.

---

### Post by DreeDrunk on 2013-06-09
Okay, thanks for the confirmation.

[LIST=1]
[*]So it is the best way to **save the tarball** anywhere on the system to easily remove the libs if they got obsolete (if the dev has implemented the "make uninstall"-feature!!).
[*]Checkinstall seems to work good. I wonder why it hasn't made it in the OS as standard? Homepage is here [http://checkinstall.izto.org/](http://checkinstall.izto.org/). Can be found in software Center. 
[*]The other way is to **manually delete** the files? That could be very very tedious up to impossible I think. So one should always choose possibility #1 or #2.
[/LIST]
Greetings,
Dree

---

