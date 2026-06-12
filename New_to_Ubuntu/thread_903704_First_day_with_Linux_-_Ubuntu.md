---
title: "First day with Linux - Ubuntu"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-08-28
OK...so I decided to just plug my nose and take the jump.  Goodbye windows OS!  And I am glad I did.  Now, of course are the growing pains.

I have a few questions I would love to get feedback on:
1.  I have an HP OfficeJet 3640 printer.  Ubuntu sees it, even says its printing to it...but nothing prints.

2.  I learned about alien and RPMs, converted, for example, VMWare to deb and ran the package.  Says it installed, but I have no idea how to launch the application.

3.  Found some items such as Clam AV & Kmymoney.  I am getting a compiler error and don't know how to fix it.

eric@ctsg-desktop:~/Downloads/kmymoney2-0.9$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Thank you in advance to anyone who is willing to help me learn how to fish!!

:)

---

### Post by billgoldberg on 2008-08-28
Go to system -> administration -> synaptic package manager and have fun.

---

### Post by WRDN on 2008-08-28
Regarding the second question, look under Applications > System Tools for VMWare.
As for the 3rd question, you should be able to find those applications in Synaptic, and easily install them. If you want to compile the programs, then first install the build-essential packages, by opening the Terminal and typing:

```
sudo apt-get install build-essential
```

The package can also be found in Synaptic.

---

### Post by halitech on 2008-08-28
VMWare is usually under Applications - System Tools

ClamAV is in the repos, install it from there, its a lot less painful ;) I believe Kmymoney should be as well. Just a note though, if you are using Ubuntu and install Kmymoney, its a Kubuntu app so it will install some of the KDE required files as well.

---

### Post by J0hnnyBr@v0 on 2008-08-28
Yeah...I found that and used it to fix the KDE error.

I guess I should look up synaptic manager in Wiki...because I am not sure I totally understand what it is....

Looks like a bunch of programs that can be installed from Ubuntu sources?

Thanks,
Eric

---

### Post by imagenius on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by J0hnnyBr@v0 on 2008-08-28
> **halitech said:**
> VMWare is usually under Applications - System Tools

ClamAV is in the repos, install it from there, its a lot less painful ;) I believe Kmymoney should be as well. Just a note though, if you are using Ubuntu and install Kmymoney, its a Kubuntu app so it will install some of the KDE required files as well.

VMWare is not showing up there in System Tools

For Kmymoney, I installed KDE from Synaptic and it installed a ton of stuff...

---

### Post by halitech on 2008-08-28
Think of Synaptic package manager as the Add/remove program in windows on steriods :D basically, if the program can be installed from the list that the Ubuntu (and Debian developers) think is safe, its in there. You can also use it to remove programs you don't want/need anymore.

---

### Post by J0hnnyBr@v0 on 2008-08-28
> **WRDN said:**
> Regarding the second question, look under Applications > System Tools for VMWare.
As for the 3rd question, you should be able to find those applications in Synaptic, and easily install them. If you want to compile the programs, then first install the build-essential packages, by opening the Terminal and typing:

```
sudo apt-get install build-essential
```

The package can also be found in Synaptic.

kmymoney install worked like a charm after I used your code!  Thanks!

As far as VMWare....I don't see it there, as others have also pointed me there...wonder if I did something wrong during install.  I made sure I used alien with the --scripts option....  then just ran the package with package manager...says it installed ok.

Thanks,
Eric

---

### Post by halitech on 2008-08-28
not sure whats going on with VMWare, I usually just install it from the tar file that I downloaded without converting it and it works fine.

---

### Post by J0hnnyBr@v0 on 2008-08-28
> **halitech said:**
> not sure whats going on with VMWare, I usually just install it from the tar file that I downloaded without converting it and it works fine.

I'll give that a try....I purposely downloaded the RPM because I had just learned about alien.

Thanks again,
Eric
:o

---

### Post by piousp on 2008-08-28
For your printer, try to take a look in the link on my signature

---

### Post by PierreDeKat on 2008-08-28
Not absolutely sure about your specific printer, but when working out the setup for my HP Photosmart C4480, I found installing [HPLIP]("http://hplip.sourceforge.net/features.html") version 2.8.7 immensely helpful.

Don't bother with Synaptic on this one, because it will only give you version 2.8.2 (about 6 months old and far fewer HP printers supported).

There's an installer (.run) file that works quite similarly to an .exe file in Windows. Just follow the instructions [here]("http://hplip.sourceforge.net/downloads.html"). Scroll down to where it says: "Automatic Installer: HPLIP Self Extracting Installer" and follow the instructions.

But in addition to helping with regular printing functions, the latest version of HPLIP allows me to use my scanner, and even gives me a readout on my theoretical ink levels.

---

### Post by J0hnnyBr@v0 on 2008-08-28
> **piousp said:**
> For your printer, try to take a look in the link on my signature

Thanks!  I did a search and found the Linux HP page which sent me to this link: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

I am working on the install right now...

Eric

---

### Post by J0hnnyBr@v0 on 2008-08-28
> **PierreDeKat said:**
> Not absolutely sure about your specific printer, but when working out the setup for my HP Photosmart C4480, I found installing [HPLIP]("http://hplip.sourceforge.net/features.html") version 2.8.7 immensely helpful.

Don't bother with Synaptic on this one, because it will only give you version 2.8.2 (about 6 months old and far fewer HP printers supported).

There's an installer (.run) file that works quite similarly to an .exe file in Windows. Just follow the instructions [here]("http://hplip.sourceforge.net/downloads.html"). Scroll down to where it says: "Automatic Installer: HPLIP Self Extracting Installer" and follow the instructions.

But in addition to helping with regular printing functions, the latest version of HPLIP allows me to use my scanner, and even gives me a readout on my theoretical ink levels.

Found it, installed it and worked like a charm!!  Thanks for your help!!

:guitar:

---

### Post by piousp on 2008-08-28
Glad to hear that :KS

---

