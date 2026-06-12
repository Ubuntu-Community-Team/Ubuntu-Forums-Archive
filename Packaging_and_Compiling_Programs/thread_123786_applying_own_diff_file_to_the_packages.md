---
title: "applying own diff file to the packages"
date: 2006-01-31
forum: Packaging and Compiling Programs
---

### Post by Xterminal on 2006-01-31
Hi all,

I'm very new here. I got headache on how to patch own diff files. Let say the apps called "abc". I've done:

mkdir temp && cd temp
apt-get source abc
cd abc-xx-xx/debian/patches
ls -a (there was 01patch1.diff 02patch2.diff inside it)

the problem is, i would like to add my own patch called 03patch3.diff. I've already play with pbuilder and dpkg-buildpackage but when it say 'Trying to patch blabla....failed' (because of the i.e. the suppose to be patch file have been patch by i.e. 02patch2.diff while 03patch3.diff trying to overwrite the 02patch2.diff, sorry, i dont know how to explain it). This have cause 'failed'.

Is there any way to apply or create the 03patch3.diff ? I was thinking of :

1) tar xvfz abc_xxx_xx.orig.tar.gz
2) mv abc_xxx_xx abc_xxx_xx.orig
3) dpkg-source -x abc_xxx_xx.dsc (will create patched abc_xxx_xx dir)
4) diff -ruN those two dir (abc_xxx_xx and abc_xxx_xx.orig) - But the prob is, even if dpkg-souce -x the dsc, the patched dir still not yet been patch fully (where it does not apply the full dir of abc-xxx-xx but only applying the debian/ dir)

One important thing, is there a way for dpkg like 'rpmbuild -bp xx.spec'?
Because the rpmbuild -bp extract and applying patch all over the extracted dir then it's easier to just diff between the extracted folder and the .orig folder after making changes (Nowadays i'm switching fully to debian base distro coz i really like it).

Is there a dpkg apps which run like (for example) dpkg-source --extract-and-apply-full-patch-and-not-only-in-debian/-folder. Heheh

p/s : cd into abc-xxx-xx and executes a command "for i in ./debian/patches/*; do patch -p1 < $i; done;" also does not work.

Many thanks to u all. Btw, this ubuntu forums is great!!

---

