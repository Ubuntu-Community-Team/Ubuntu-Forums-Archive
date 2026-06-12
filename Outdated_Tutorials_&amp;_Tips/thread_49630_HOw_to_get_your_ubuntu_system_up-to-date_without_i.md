---
title: "HOw to get your ubuntu system up-to-date without internet conection"
date: 2005-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by kosmic on 2005-07-17
Ok, my problem is the next, I have 10 pc with ubuntu in a network without internet acess, but I need to have the lastest security patches instaled and new programs.

The solution to this is, if you have a computer with a Internet conection and a DVD burner you are safe, just follow this steps...


first, get the program called... Debmirror :

sudo apt-get install debmirror


Next, to get the repositories of ubuntu to your hard disk do the following comand

debmirror --nosource -m -passive --host=archive.ubuntulinux.org --root=ubuntu/ --method=ftp --progress --dist-hoary --section=main,multiverse,universe,restricted --arch=i386 ubuntu/ --ignore-release-gpg

* - host=is the repositorie url you want to copy to your hard disc
* -dist = is the distribuition you want (warty, hoary ...)
* -section is the repositories you want in this case we want -main,multiverse,universe and restricted
* -arch is the processor type compliled code you want (ppc,i386,i686...)

Atention - some of this repositories have more than 1 GB and the total of all the repositories is bigger than a DVD, so we need to separate them with a program, called DEBPARTIAL.

Hope it helps anybody like me who needed the packages offline.

---

### Post by McQuaid on 2005-07-17
Thanks for this tip.   I have a friend who I want to set up with ubuntu and is only a modem user, and I know of a fair amount of apps that he'd like and I'd like to have a disc setup with the debs to install after.  

I'd prefer to be able to selectively grab the debs instead of the whole thing.  Also it would be nice if the disc could be set up in such a way that I could just add it as rep to his sources.list and just install via apt.  

Any tools/methods to accomplish this?

---

### Post by kosmic on 2005-07-18
Another way is, boot a fresh ubuntu install, and then go to a shell and do :

sudo apt-get -d install 'packages you want'


What the -d option do is to only donwload the package an do not install it.

after you have donwloaded all the programs you want do the following.

mkdir /tmp/debs
sudo mv /var/cache/apt/archives /tmp/debs

then.

cd /tmp
dpkg-scanpackages debs/.* | gzip > Packages.gz (Atention is Packages not packages)

*after this steps you can copy the folder debs to a CD and use it like a APT CDROM :)

finaly add the following line to your apt sources file.

file:/tmp debs/

after that 

sudo apt-get update
and then install the packages you want

 ```
Small update - do not forget to copy the file Packages.gz from /tmp to /tmp/debs
```

---

### Post by andlinux21 on 2005-07-18
Thanks I am a modem user but from time to time I have access to cable when I visit my sister.  I will make sure I do that so that I can get my laptops setup the way I want.

---

