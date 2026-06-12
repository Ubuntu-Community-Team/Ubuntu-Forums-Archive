---
title: "[SOLVED] tar.lzma"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-07
I went [http://tukaani.org/lzma/download](http://tukaani.org/lzma/download) to install the source code, because I'm not getting feedback from the apt-get.

I configured it. The command from: 
  2. Type `make' to compile the package.

I did `make' and it does:

ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$ `make'
> 

So, sits there. I tried `make install' and it stays there.

---

### Post by Pro-reason on 2008-09-07
Forget compiling from source.  Delete all the files you downloaded.

Do this in a terminal:

```

sudo apt-get update && sudo apt-get install lzma

```

If that fails, then you have serious problems with your packaging system, and fixing that is what needs to be done, rather than trying to compile lzma.

Edit: I can see that the reason why compilation didn't work is that you don't understand what quotation marks are.

---

### Post by Elephantman5 on 2008-09-07
> **Pro-reason said:**
> Forget compiling from source.  Delete all the files you downloaded.

Do this in a terminal:

```

sudo apt-get update && sudo apt-get install lzma

```If that fails, then you have serious problems with your packaging system, and fixing that is what needs to be done, rather than trying to compile lzma.

Edit: I can see that the reason that the reason why compilation didn't work is that you don't understand what quotation marks are.

Woh. Back off dude. There's a difference between ` ' " ok. And he specifically put ` before make and ' after.
I also tried it without and got a NOT A COMMAND error. So.
I'll go update again.

---

### Post by Elephantman5 on 2008-09-07
2. Type `make' to compile the package.

ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$ make
make: *** No targets specified and no makefile found.  Stop.
ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$

---

### Post by Pro-reason on 2008-09-07
I was just stating facts.

Technically, quotation marks should be like this:
```

&#8216;...&#8217;
&#8220;...&#8221;

```
But it is quite common on the Web to use any of the following as substitutes:
```

"..."
'...'
`...'
``...''

```

If you see anything like that, you should generally assume (or at least consider a possibility) that they are intended as quotation marks, and therefore what they contain is what should be copied verbatim.

You learn a new thing every day!

Anyway, as I said, forget about compiling.  It is highly advanced stuff.  Just install *lzma* from the repositories (with Synaptic or apt-get).

---

### Post by Pro-reason on 2008-09-07
> **Elephantman5 said:**
> 2. Type `make' to compile the package.

ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$ make
make: *** No targets specified and no makefile found.  Stop.
ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$
There are three main steps to follow:

```

sudo apt-get install build-essential
[B]./configure
make
make install[/B]
lzma -h

```

But, again, forget about compiling.

If you install from the repositories, you will be able to get automatic updates of lzma as they come out.  You won't get that if you install from your own compiled version.

---

### Post by Elephantman5 on 2008-09-07
> **Pro-reason said:**
> There are three main steps to follow:

```

sudo apt-get install build-essential
[B]./configure
make
make install[/B]
lzma -h

```But, again, forget about compiling.
Thanks. I never got any messages from make, make install last time. But I got more feedback after building essential.

```
ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$ sudo apt-get update && sudo apt-get install lzma
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lzma is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ajzimmerman@ajzimmerman-desktop:~/Desktop/lzma-4.32.7$
```

LZMA was supposedly installed but I'm still not able to extract LZMA tar archives.

---

### Post by Elephantman5 on 2008-09-07
[http://ubuntuforums.org/showthread.php?t=494359](http://ubuntuforums.org/showthread.php?t=494359)
I don't understand why after following yours and the other guy's directions, and looking everywhere for the solution I am still not able to solve this.

I don't understand why Ubuntu provides file roller support for creating archives it cannot extract.

Solution.
Install 7zip, 
Able to extract through File Roller.

---

### Post by Pro-reason on 2008-09-07
From the output above, I can see that you do indeed have the *lzma* package installed.

You are now able to use it to extract things from the command line.  For example, if you have a file called “stuff.tar.lzma” on the desktop, you can extract it like this:

```

cd ~/Desktop
lzma -d stuff.tar.lzma
tar -xvf stuff.tar

```

File-roller should now automatically be able to both create and open *lzma* files.  If it is not able to do so, try purging and reinstalling it.

To check, I myself have just gone and used file-roller to make such an archive, and then to extract.  It worked fine.  The only glitch was that file-roller was not set as the default for opening .lzma files from the GUI, so I had to choose file-roller manually.  It's very minor, but perhaps worth submitting as a bug report on Launchpad.

---

### Post by Elephantman5 on 2008-09-07
It's been sent as a bug. Found it on Google. 
And yes. I found later the Open With Another Application route worked indirectly.

---

