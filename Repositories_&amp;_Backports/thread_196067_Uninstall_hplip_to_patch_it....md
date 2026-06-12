---
title: "Uninstall hplip to patch it..."
date: 2006-06-13
forum: Repositories &amp; Backports
---

### Post by kewldude606 on 2006-06-13
I have a Dell 3000CN and it is working perfectly with Linux except that the output is 3/8 down on the page than it should be.  I then found this website called [Dell 3000CN and Linux]("http://www.mit.edu/~jik/3000cn/") which said I should install [this patch]("http://www.mit.edu/~jik/3000cn/hpijs-3000cn.patch.html") to the hplip package.  I googled for a bit to find a page on the HPLIP site that said [how to patch it]("http://www.mit.edu/~jik/3000cn/hpijs-3000cn.patch.html").  Basic directions:```
$ cd hplip-<version>
$ patch -p1 < hplip-<version>.patch
$ ./configure --prefix=/usr
$ make clean
$ make
$ su   (or use 'sudo make install')
# make install   (as root)
```It didn't look very hard...and I have already installed from source on ubuntu (I have build-essentials).  So I go into Synaptic to uninstall the HPLIP package so I could reinstall it with the patch from source.  Then I got an error message that said if I uninstalled that package then ubuntu-desktop would have to be uninstalled!  ([screenshot]("http://img61.imageshack.us/img61/8512/screenshot4an.png")).

Is it safe to uninstall?  Also, is there an easier way to patch it?

Thanks in advance.

---

### Post by danielph on 2006-06-14
ubuntu-desktop is just a hook to install other packages and can be safely removed.

regards

Dan

---

### Post by kewldude606 on 2006-06-14
OK thank you!  I was scared there.

So after I uninstall the hplip that my Ubuntu has now, and reinstall it with the patch, should I reinstall the ubuntu-desktop and foomatic?  Will that reinstall the old version of the HPLIP drivers?

---

### Post by danielph on 2006-06-14
From the description in Synaptic:```

The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).
```

Reinstalling foomatic will not change the version of HPLIP you have installed. HPLIP requires CUPS to work. I don't know if foomatic is required. I know it is used for LPD. If it is needed it will probably tell you. 

Let me know if you get this working as I had trouble compiling HPLIP from source.

Dan

---

### Post by kewldude606 on 2006-06-14
I must have not stated my question clearly.

foomatic and ubuntu-desktop have hplip listed as a dependency.  If I want to reinstall ubuntu-desktop and foomatic after installing the hplip from source, will Synaptic think that hplip isn't installed (because I didn't install from synaptic) and install it again?  So then I will have 2 installs of hplip.

Or should I just not reinstall ubuntu-desktop and foomatic?

---

### Post by danielph on 2006-06-15
Firstly, are you sure you need the patch? The article you refer to is nearly a year old. Do you have the problems it refers to running the current hplip?

If, so read on

I wasnt aware that HPLIPS was part of ubuntu-desktop. I have hplip 0.9.11 installed. When I reinstall ubuntu-desktop it will reinstall hplip 0.9.7. It will prompt you to keep configuration files. I just tried it (and chose to keep the config files) and running hp-check shows me I still have 0.9.11 installed (the latest version from hplip).

That said, it is still messy as synaptic now shows that hplip 0.9.7 is installed and no other version. I am not sure will happen when an updated hplip package comes along. 

I suggest leaving ubuntu-desktop uninstalled. There seems to be some discussion about this on the forum and most people say the same, only to reinstall it when upgrading between distributions (dist-upgrade). I am not aware of any problems leaving it uninstalled. As for foomatic, I didn't find it was needed for my purposes, but you should be able to install independently - I didnt find any dependency on hplip. 

I hope that answers your question.


Dan

---

### Post by kewldude606 on 2006-06-15
I am still having that problem (3/8" lower on the page), so I just uninstalled it.  Like you said, I didn't reinstall ubuntu-desktop (or foomatic).

Its working great now.  Thanks.

---

### Post by 11hjpphty76lkjj on 2006-06-20
Dan,

I'm curious what problems you had compiling HPLIP?

Thanks.

Aaron

---

### Post by kewldude606 on 2006-06-20
I never actually compiled it, I went to uninstall it so that I could compile it with a patch applied but when I went to uninstall it said that ubuntu-desktop would have to be uninstalled as well because HPLIP was a dependency of ubuntu-desktop.  I was scared that uninstalling ubuntu-desktop would have dire consequences because of its name.  But then I found a workaround.

---

### Post by danielph on 2006-06-21
[QUOTE=kalosaurusrex]Dan,

I'm curious what problems you had compiling HPLIP?

Thanks.

Aaron[/QUOTE]

Configure ok, and make ok, but sudo make install gave me the  
error below:

/bin/sh: line 9: hplip: command not found
> make[3]: *** [install-data-hook] Error 127
> make[3]: Leaving directory `/home/danielph/Desktop/hplip-0.9.11'
> make[2]: *** [install-data-am] Error 2
> make[2]: Leaving directory `/home/danielph/Desktop/hplip-0.9.11'
> make[1]: *** [install-am] Error 2
> make[1]: Leaving directory `/home/danielph/Desktop/hplip-0.9.11'
> make: *** [install-recursive] Error 1

It turned out to be a dependency problem and the fix was as follows:

sudo make uninstall
make clean
sudo rm -rf /usr/share/hplip/

then run:

sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev 
libsnmp9-dev libjpeg62-dev lsb libtool  automake1.9 libusb-dev

finally,

./configure --prefix=/usr
make
sudo make install
sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart

Regards 

Dan

---

### Post by kewldude606 on 2006-06-21
Ahh my name is dan too.  I didn't realise he was talking to you.

lol

---

### Post by danielph on 2006-06-21
No worries Dan,

Aaron, 

I posted the question on HPLIP help and I believed you helped me with it and are still helping me with getting it working. I just realized that you are the same person.

Perhaps we should all have unique numbers!

Dan

---

### Post by kewldude606 on 2006-06-22
I hope you were kidding about the unique numbers.  Because any form of certain ID on the Internet is bad IMHO.

---

### Post by danielph on 2006-06-22
I would never subscribe to something like that, yes I was kidding.

I think we should all be more free, but it is difficult or impossible in modern society, but that's another story.

---

