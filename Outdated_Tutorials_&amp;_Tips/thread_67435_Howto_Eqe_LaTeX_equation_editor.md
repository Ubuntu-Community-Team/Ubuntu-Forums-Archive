---
title: "Howto: Eqe: LaTeX equation editor"
date: 2005-09-20
forum: Outdated Tutorials &amp; Tips
---

### Post by parktownprawn on 2005-09-20
eqe:  Linux LaTeX equation editor ([http://rlehy.free.fr/](http://rlehy.free.fr/))

Eqe allows you to drag and drop latex formated equations into Open Office apps and many other apps. Its a clone of the MacOS X LaTeX equation editor. A windows equivalent would be Texpoint. 

The screenshot bellow shows an equation being dragged into an OpenOffice Impress presentation:

[IMG]http://rlehy.free.fr/screenshot_eqe.png[/IMG] 

To Install:

First you must have latex installed

```
sudo apt-get install tetex-bin tetex-base
``` 

then install the dependancies and get and install the package
```

sudo apt-get install libgtk2-perl libtemplate-perl imagemagick   tetex-extra libfile-slurp-perl 
wget http://rlehy.free.fr/eqe_1.2.0-1_all.deb
sudo dpkg -i eqe_1.2.0-1_all.deb
rm eqe_1.2.0-1_all.deb
```

---

### Post by engla on 2006-12-06
Oh so wonderful! How can this be so hard to find? I wish I had found this before when I was making a physics presentation in impress.. I resorted to some web page that did the same job, but that was painful.

This is a great application, and it still works (I tried it in edgy).

Simpler instructions:
[LIST]
[*]Download the ready-made package from the website: [eqe_1.3.0-2_all.deb]("http://rlehy.free.fr/eqe_1.3.0-2_all.deb") is the current one.
[*]Save it and double-click it (works in Ubuntu 6.06 or later)
[*]The package and its dependencies will be installed automatically if you follow the instructions.
[/LIST]


(make sure [universe is enabled]("http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories"))

---

### Post by andiii on 2006-12-13
That looks really neat, but I'm with texlive instead of tetex, so I can't install it..

edit: found [http://redsymbol.net/software/l2p/dist/l2p-doc.html](http://redsymbol.net/software/l2p/dist/l2p-doc.html) and this works

---

### Post by andresv on 2007-11-06
> **andiii said:**
> That looks really neat, but I'm with texlive instead of tetex, so I can't install it..

edit: found [http://redsymbol.net/software/l2p/dist/l2p-doc.html](http://redsymbol.net/software/l2p/dist/l2p-doc.html) and this works

Thanks for pointing out l2p! :) I was a user of eqe, but after I switched to texlive I was missing a program like that. l2p is perhaps less neat than eqe, but for the time being it is a good option.

---

### Post by parktownprawn on 2007-11-06
> **andiii said:**
> That looks really neat, but I'm with texlive instead of tetex, so I can't install it..

edit: found [http://redsymbol.net/software/l2p/dist/l2p-doc.html](http://redsymbol.net/software/l2p/dist/l2p-doc.html) and this works

You can use the modified deb i've attached or you  can hack the eqe deb yourself  to get it to work with texlive:

Extract the filesystem tree to a directory "packagename.x.x.x":
$ dpkg-deb -x packagename.x.x.x.deb packagename.x.x.x

Extract the control file information:
$ dpkg-deb -e packagename.x.x.x.deb packagename.x.x.x/DEBIAN


$ cd packagename.x.x.x/DEBIAN

Edit the file called: control

change the Depends line to:

Depends: coreutils, libgtk2-perl (>= 1.042-1), imagemagick, libfile-slurp-perl, libtemplate-perl, tetex-base | texlive-base, tetex-extra | texlive-latex-extra

$ cd ../../

Rebuild the deb package:
$ dpkg-deb -b packagename.x.x.x packagename.x.x.x.deb

---

