---
title: "Howto easily install OpenOffice2"
date: 2005-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2005-10-23
[QUOTE=Matchless]Hi,
   There are a lot of questions as to how to install the latest OpenOffice2 as no further upgrades are appearing in the repositories. Some nice scripts are available also. The following works in both Breezy and Hoary!
There is an easy way to update to the latest, go to the website and download the latest .deb.tar.gz files at [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)
Extract the deb files into a directory called OpenOffice2 on your desktop. Create your own repository file, install by using Synaptic
Method:
Create a folder i.e Repository and copy the deb file folder OpenOffice2 into it.
Now in the console run:  dpkg-scanpackages .  /dev/null  |  gzip  -9c  >  Packages.gz
This will create the package list.
Now add the line:    deb file:/home/<username>/Desktop/Repository/ ./     in your sources.list or use Synaptic to add.
Open Synaptic, check that your repository is ticked, you may want to untick/uncomment all the other repos for the moment. Reload, search for openoffice and you should find all the OpenOffice 2 version 2.0.2 deb files, select ALL the files you extracted for installation and Bobs your aunty!
You can uninstall 1.9.129 with Synaptic.
Regards
Matchless[/QUOTE]

This is previously submitted and updated post, I have  just tested today and it works. ;) 
Enjoy

---

### Post by abandoned_hussam on 2005-10-27
will this require me to remove kubuntu-desktop?

---

### Post by jeremy on 2005-10-27
If you uninstall 1.9.129 you will have to remove  kubuntu-desktop.

---

### Post by Gordonbp531 on 2005-10-27
thanks for the info - went flawlessly!

---

### Post by Gordonbp531 on 2005-10-27
[QUOTE=hussam]will this require me to remove kubuntu-desktop?[/QUOTE]

Don't panic - it doesn't mean what you think it means!

---

### Post by desleep on 2005-10-27
I tried this method on hoary and it worked well, last night I installed a fresh copy of breezy and tried it again to get the latest openoffice but I got this error 

root@varuna:/home/paul/Desktop/Repository# dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
bash: dpkg-scanpackages: command not found

Ok, I used the old packages.gz list from the hoary install which seemed to update fine, but I cant see the updates in Adept. 

Is there something I am not doing on breezy?

---

### Post by desleep on 2005-10-27
ok, solved the dpkg problem. had to install dpkg-dev, all working fine now thanks!

---

### Post by Souseke on 2005-11-17
hi . I seem to be having problems. I am using kubuntu hoary.

I followed the guide word for word.

when i do the:

chchan@linux-chi:~/Desktop/Repository$ dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz 

i get the output:

** Packages in archive but missing from override file: **
  openoffice.org-base openoffice.org-calc openoffice.org-core01
  openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u
  openoffice.org-core04 openoffice.org-core04u openoffice.org-core05
  openoffice.org-core05u openoffice.org-core06 openoffice.org-core07
  openoffice.org-core08 openoffice.org-core09 openoffice.org-core10
  openoffice.org-debian-menus openoffice.org-draw openoffice.org-
  gnome-integration openoffice.org-graphicfilter openoffice.org-
  impress openoffice.org-javafilter openoffice.org-math
  openoffice.org-pyuno openoffice.org-spellcheck openoffice.org-
  testtool openoffice.org-writer openoffice.org-xsltfilter

i added this to the sources.list:

deb file:/home/chchan/Desktop/Repository/ ./

However when i open synaptic i get this error:

W: Couldn't stat source package list file: ./ Packages (/var/lib/apt/lists/_home_chchan_Desktop_Repository_._Packages) - stat (2 No such file or directory)

or if i try an apt get update i get:

Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Packages

can anyone help me please...

---

### Post by varunus on 2005-11-17
Instead of using this method, why not simply use the following:

Open up your /etc/apt/sources.list file with "sudo gedit", and add the following line:

```
deb http://people.ubuntu.com/~doko/OOo2 ./
```

This is openoffice.org 2.0, compiled for ubuntu/kubuntu by an Ubuntu Developer (and soon to be in backports).  After adding this repo and reloading in Synaptic, you will find that the OO.o packages simply show up as "available to upgrade" in synaptic.  No mess with kubuntu-desktop/ubuntu-desktop, and no problems with package conflicts.  They just replace the ones that come with the system.

I highly recommend using these packages instead...

---

