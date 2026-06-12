---
title: "Program Installation in Ubuntu"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by coover on 2008-05-14
I downloaded Open Office 3 Beta and got a .tar.tar file. Right clicking it, one of the options was to extract, which I did. I them got a directory BEA300_m2_native_packed-2_en-us.9301.

Assuming the key to installing this package was to open the directory and to find something to install, I opened it and found four directories; installdata, licenses, readmes, and RPMS along with 3 files; javasetup.jar, setup, and update. 

I read the readme just in case it would give me a clue on how to install the application (I really am a Linux newbee, I simply do not know how to do it). There was no installation information there).

So jumping right in, I clicked on the setup file. One of the things that was opted was Run. I Ran. 

A Black Box opened on the screen with an error message ... Failed to extract Java Runtime Environment files....Press Return to continue ...

I return and the black box goes away but nothing else happens. 

I also tried a few other things including an attempt to open javasetup.jar, but was not sucessfull. 

Obviously I do not know what the heck I am doing. Can anyone help me out?

---

### Post by shifty_powers on 2008-05-14
heh you downloaded the wrong version.

rpm files are package files for red hat based distros.

go back and make sure you get the tar for ubuntu/debain based distros.

untar it and go to the DEB folder. find the right deb, (for life of me can't think which one it is, should be obvious), and double click it ;)

---

### Post by macaholic on 2008-05-14
The packages you want to install are in the RPMS directory, but those are not meant for ubuntu. You can isntall them, but I would recommend redownloading the debs instead.[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta)
After you download and untar it, go into a terminal, cd into the directory, and install them all at once with```
sudo dpkg -i *.deb
```

---

### Post by shifty_powers on 2008-05-14
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta)

there we go ;)

---

### Post by shifty_powers on 2008-05-14
heh god you have to be quick in this place ;)

---

### Post by coover on 2008-05-14
Thanks, Guys. 

I was able to download the correct file, found the debs folder, and since it wasn't obvious which file to click, eventually clicked them all. Some gave me a choice to install and some gave me an error message. Those with the install choice were installed, but now I can't find any shortcuts to run the program. When I go to the menu on the Office Menu on the desktop, all I find are shortcuts to Oper Office 2.4. 

Obviously I'm missing something (like a brain).

---

### Post by ugm6hr on 2008-05-14
Where to download: [http://ubuntuforums.org/showpost.php?p=4904332&postcount=10](http://ubuntuforums.org/showpost.php?p=4904332&postcount=10)
How to install: [http://ubuntuforums.org/showpost.php?p=4904960&postcount=14](http://ubuntuforums.org/showpost.php?p=4904960&postcount=14)
How to launch: [http://ubuntuforums.org/showthread.php?p=4905766#post4905766](http://ubuntuforums.org/showthread.php?p=4905766#post4905766)

---

### Post by macaholic on 2008-05-14
> **ugm6hr said:**
> Where to download: [http://ubuntuforums.org/showpost.php?p=4904332&postcount=10](http://ubuntuforums.org/showpost.php?p=4904332&postcount=10)
How to install: [http://ubuntuforums.org/showpost.php?p=4904960&postcount=14](http://ubuntuforums.org/showpost.php?p=4904960&postcount=14)
How to launch: [http://ubuntuforums.org/showthread.php?p=4905766#post4905766](http://ubuntuforums.org/showthread.php?p=4905766#post4905766)
It's amazing how many answers some forum searching can yield eh?:)

---

