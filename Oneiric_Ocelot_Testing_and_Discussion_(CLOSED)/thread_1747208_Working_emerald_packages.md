---
title: "Working emerald packages"
date: 2011-05-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by andrewthomas on 2011-05-02
I just got this to work.


First make sure that you don't have any emerald or libemeraldengine-dev package installed then:
```

mkdir emerald++
cd emerald++
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald/
git checkout -b compiz++ origin/compiz++
./autogen.sh --prefix /usr
make
sudo checkinstall 
# version 0.9.4
```if it fails then
```
sudo dpkg -i --force-all emerald_0.9.4-1_amd64.deb
```download [http://cgit.compiz.org/fusion/decorators/emerald-themes/snapshot/emerald-themes-0.6.0.tar.bz2](http://cgit.compiz.org/fusion/decorators/emerald-themes/snapshot/emerald-themes-0.6.0.tar.bz2)
extract
```
cd emerald-themes-0.6.0
./autogen.sh --prefix /usr
make
sudo checkinstall
```Works like a charm.


Here are two amd64 packages that I built on oneiric




[http://dl.dropbox.com/u/27872107/emerald-themes_0.6.0-1_amd64.deb](http://dl.dropbox.com/u/27872107/emerald-themes_0.6.0-1_amd64.deb) [http://dl.dropbox.com/u/27872107/emerald_0.9.4-1_amd64.deb](http://dl.dropbox.com/u/27872107/emerald_0.9.4-1_amd64.deb)

---

### Post by lidex on 2011-05-04
Good to have emerald back. Thankyou.

---

