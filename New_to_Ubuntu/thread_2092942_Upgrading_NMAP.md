---
title: "Upgrading NMAP"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by mikeybinec on 2012-12-09
Running Ubuntu server 12.04 and I installed nmap and the version it gave me
is 5.21 I know the newest version is at 6.25 now but running yum upgrade is'nt giving me the newest version
 
Any advice?
 
Thanks

---

### Post by haqking on 2012-12-09
> **mikeybinec said:**
> Running Ubuntu server 12.04 and I installed nmap and the version it gave me
is 5.21 I know the newest version is at 6.25 now but running yum upgrade is'nt giving me the newest version
 
Any advice?
 
Thanks


[http://nmap.org/book/inst-linux.html](http://nmap.org/book/inst-linux.html)

---

### Post by mikeybinec on 2012-12-09
> **haqking said:**
> [http://nmap.org/book/inst-linux.html](http://nmap.org/book/inst-linux.html)
 
from your link:
 
"The proper **upgrade**/install command is **apt-get install nmap**. This works for Debian derivatives such as Ubuntu too. "
 
Hmmmm, ain't working for Ubuntu, but on the other hand I can only get up to 6.0.1 on Fedora.. At least Fedora is open to upgrades.
 
Thanks

---

### Post by haqking on 2012-12-09
> **mikeybinec said:**
> from your link:
 
"The proper **upgrade**/install command is **apt-get install nmap**. This works for Debian derivatives such as Ubuntu too. "
 
Hmmmm, ain't working for Ubuntu, but on the other hand I can only get up to 6.0.1 on Fedora.. At least Fedora is open to upgrades.
 
Thanks

I will let you read the page all the way to the bottom where it tells you how to install latest version using Alien.

In your first post you said you were using Yum in Ubuntu, I am presuming you installed Yum yourself as the default for .deb based distros is Apt.

Anyways deb repos will have an out of date version (as mentioned on the page) and as mentioned you can install latest by downloading the 6.25 or whatever version from the downloads page

---

### Post by DuckHook on 2012-12-09
> **mikeybinec said:**
> Running Ubuntu server 12.04 and I installed nmap and the version it gave me
is 5.21 I know the newest version is at 6.25 now but running yum upgrade is'nt giving me the newest version
 
Any advice?
 
Thanks

Unless you absolutely need a feature in the latest version, it is probably not a good idea for beginners to install from outside the repository. If not a beginner, then go for broke, which sometimes turns out to be literally the result.

BTW, Ubuntu and all Debian derivatives use *apt*, not *yum*. You will want to use the proper package manager.

---

### Post by SeijiSensei on 2012-12-09
Alternatively you can just download the [source code]("http://nmap.org/dist/nmap-6.25.tar.bz2") and build your own version.  I haven't compiled nmap in a while, but the last time I did, it did not require anything special beyond what comes in the build-essential package.

```
sudo apt-get install build-essential
cd ~
mkdir build
cd build
wget http://nmap.org/dist/nmap-6.25.tar.bz2
bzip2 -cd nmap-6.25.tar.bz2 | tar xvf -
cd nmap-6.25
./configure
make
sudo make install

```

The binary will be placed in /usr/local/bin, which supercedes executables in /usr/bin.

---

### Post by mikeybinec on 2012-12-16
> **SeijiSensei said:**
> Alternatively you can just download the [source code]("http://nmap.org/dist/nmap-6.25.tar.bz2") and build your own version.  I haven't compiled nmap in a while, but the last time I did, it did not require anything special beyond what comes in the build-essential package.

[code]sudo apt-get install build-essential
cd ~
mkdir build
cd build
wget http://nmap.org/dist/nmap-6.25.tar.bz2
bzip2 -cd nmap-6.25.tar.bz2 | tar xvf -
cd nmap-6.25
./configure
make
sudo make install



/code]The binary will be placed in /usr/local/bin, which supercedes executables in /usr/bin.



 couldnt get your bzip2 line to work so I changed it to bunzip and now I have a nmap*tar archive

I  ran tar -xvf nmap*.tar  (the * to save typing) and pretty much nothing  happens. No kick back error message  I'm going to try it again

---

### Post by mikeybinec on 2012-12-16
OK got the tar to extract and it made a nmap 6.25 directory. did the ./configure and it did a million lines or checking this and that and answering yes or no. 

But what i am looking for happened..I now see the dragon (in ansi obviously) and now I will do the make per your instuctions

thanks

---

### Post by haqking on 2012-12-16
> **mikeybinec said:**
> OK got the tar to extract and it made a nmap 6.25 directory. did the ./configure and it did a million lines or checking this and that and answering yes or no. 

But what i am looking for happened..I now see the dragon (in ansi obviously) and now I will do the make per your instuctions

thanks

is there a reason you want the latest version ?

You seem unfamiliar with Linux and CLI, of course that doesnt mean you are unfamiliar with NMAP but if you cant install it then I suspect you are.

I am a Penetration tester and I am still running 5.21 since god knows when, 2010 or so, apart from in Backtrack 5  which runs 5.5x and I use NMAP almost daily

---

### Post by mikeybinec on 2012-12-16
Excellent.. the make install went good and now Nmap is upgraded to 6.25

:guitar:

Except for the line bzip2 everything else went great..

thanks to sensei

---

