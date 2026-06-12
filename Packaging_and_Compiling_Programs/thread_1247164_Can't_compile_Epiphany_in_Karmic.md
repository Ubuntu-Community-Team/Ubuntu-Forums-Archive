---
title: "Can't compile Epiphany in Karmic"
date: 2009-08-22
forum: Packaging and Compiling Programs
---

### Post by ceramicm on 2009-08-22
I can't compile epiphany (webkit version) in Ubuntu 9.10 (Karmic Koala) alpha 4. Here's what I've tried so far:

```
sudo mkdir /opt
chown -R --from=root:root cer:cer /opt
cd /opt
sudo apt-get install git-core
git config --global user.name "cer"
git config --global user.email "cer@<snip>"
git clone git://git.gnome.org/epiphany
git clone git://git.gnome.org/epiphany-extensions
gksudo gedit /etc/apt/sources.list ## add deb-src lines
sudo apt-get update
sudo apt-get build-dep epiphany-browser
sudo apt-get build-dep epiphany-webkit
## sudo apt-get install other dependencies/assorted *-dev files I don't remember
cd /opt/epiphany
./autogen.sh --enable-network-manager --enable-introspection
make
```

make gives me the following error:
```
<snip>
Making all in embed
make[2]: Entering directory `/opt/epiphany/embed'
  GEN    stamp-ephy-embed-type-builtins.c
  GEN    stamp-ephy-embed-type-builtins.h
make  all-am
make[3]: Entering directory `/opt/epiphany/embed'
  CC     libephyembed_la-ephy-adblock.lo
  CC     libephyembed_la-ephy-adblock-manager.lo
  CC     libephyembed_la-downloader-view.lo
  CC     libephyembed_la-ephy-command-manager.lo
  CC     libephyembed_la-ephy-embed.lo
  CC     libephyembed_la-ephy-embed-container.lo
  CC     libephyembed_la-ephy-embed-dialog.lo
  CC     libephyembed_la-ephy-embed-event.lo
  CC     libephyembed_la-ephy-embed-persist.lo
  CC     libephyembed_la-ephy-embed-single.lo
ephy-embed-single.c: In function &#8216;ephy_embed_single_initialize&#8217;:
ephy-embed-single.c:354: error: &#8216;SOUP_TYPE_PASSWORD_MANAGER_GNOME&#8217; undeclared (first use in this function)
ephy-embed-single.c:354: error: (Each undeclared identifier is reported only once
ephy-embed-single.c:354: error: for each function it appears in.)
make[3]: *** [libephyembed_la-ephy-embed-single.lo] Error 1
make[3]: Leaving directory `/opt/epiphany/embed'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/opt/epiphany/embed'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/epiphany'
make: *** [all] Error 2
```

Anyone know of a solution? Thanks in advance!

---

### Post by maxfact on 2009-08-24
I too have the same error 
I think it is a problem in the construction of epiphany

---

### Post by maxfact on 2009-08-24
if yuo want use epiphany 2.27.90-1 look this repo on launchpad:

epiphany
[https://launchpad.net/~webkit-team/+archive/epiphany](https://launchpad.net/~webkit-team/+archive/epiphany)

webkit to run the latest version of epiphany
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

I hope to have helped

I think the error is due to the fact that you have to use a newer version libsoup 
:lolflag:

---

