---
title: "transcode w/apt I DID IT!!"
date: 2005-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by chipmonk010 on 2005-08-23
this has been one thing that has been quite hard to do with ubuntu but i figured it out if this has already been posted im sry.

this is my sources.list

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu/ hoary-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb ftp://ftp.nerim.net/debian-marillat/ sarge main
#deb ftp://ftp.nerim.net/debian-marillat/ etch main
#deb ftp://ftp.nerim.net/debian-marillat/ sid main
#deb ftp://ftp.nerim.net/debian-marillat/ experimental main
#deb-src ftp://ftp.nerim.net/debian-marillat/ sid main

deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging bleeding main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging bleeding main universe multiverse restricted 

#deb http://dijkstra.csh.rit.edu/~mdz/ubuntu hoary mythtv
#deb-src http://dijkstra.csh.rit.edu/~mdz/ubuntu hoary mythtv

# packages for multimedia and more, like mplayer



# deb http://pessoal.onda.com.br/rjamorim/debian/ ./

# deb http://www.rarewares.org/debian/packages/unstable/ ./

# deb http://debian.xmixahlx.com/packages/unstable/ ./


#deb http://ftp.debian.org/debian/ unstable main contrib non-free
``` 


un-comment these
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
#deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free

do:
sudo apt-get update
sudo apt-get install transcode

once finished re-comment those two sources so u dont break ur distro
DONE
now just install dvdrip
open it
goto debug>dependencies
and install everything thats red n ull be good to go

hope this helps some people cuz it took a while to figureout then i reinstalled ubuntu n forgot how i did it n had to re-figure it out lol

good luck all please report back if u did this and it worked

peace
Chris

---

### Post by bored2k on 2005-08-23
I just want to point out the fact using Marillat is quite unstable and could cripple further upgrades should the package ever reach Ubuntu. [COLOR=DarkRed]Use at your **own** risk.[/COLOR]

Not supported, yet Ubuntu compiled: [http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/)

---

### Post by chipmonk010 on 2005-08-23
bored2k is right USE AT YOUR OWN RISK

i forgot about the ubuntu version i beleive the dependencies problems for it were the same as the marillat version so you could download the ubuntu version from the link bored2k provided and only uncomment

#deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free

then  use
sudo dpkg -i /location/of/downloaded/deb

something to try i guess

---

