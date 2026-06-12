---
title: "How do i install compiz stackswitch in gutsy?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by sharks on 2008-06-28
How do i install compiz stackswitch in gutsy?

---

### Post by st33med on 2008-06-29
You need to compile compiz fusion.
[This link]("http://wiki.compiz-fusion.org/Installation") will tell you how to install it. You will need to install from git, however, to use stackswitch.
Also, you will need to remove compiz everything from Ubuntu before you install, else it will not install the git version correctly.
```
sudo apt-get remove ubuntu-desktop compiz*
```

Don't worry, ubuntu-desktop is a meta-package, or a package that contains multiple installation files. That will not stall, freeze, or do whatever to your Ubuntu installation.
Once you have compiled compiz fusion, you need to do this to install stackswitch:
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/stackswitch 
cd ~/stackswitch
make
sudo make install
```
What you are asking is a very advanced thing to do. It is worth it, however.

Post back if you have questions or problems.

---

### Post by sayakb on 2008-06-29
```
glade@Mean-Machine:~/stackswitch$ make
convert   : stackswitch.xml.in -> build/stackswitch.xml
bcop'ing  : build/stackswitch.xml -> build/stackswitch_options.h
bcop'ing  : build/stackswitch.xml -> build/stackswitch_options.c
schema    : build/stackswitch.xml -> build/compiz-stackswitch.schema
compiling : stackswitch.c -> build/stackswitch.lostackswitch.c: In function &#8216;stackswitchRenderWindowTitle&#8217;:
stackswitch.c:230: error: &#8216;TEXT_STYLE_BACKGROUND&#8217; undeclared (first use in this function)
stackswitch.c:230: error: (Each undeclared identifier is reported only once
stackswitch.c:230: error: for each function it appears in.)
stackswitch.c:233: error: &#8216;CompTextAttrib&#8217; has no member named &#8216;backgroundHMargin&#8217;
stackswitch.c:234: error: &#8216;CompTextAttrib&#8217; has no member named &#8216;backgroundVMargin&#8217;
stackswitch.c:235: error: &#8216;CompTextAttrib&#8217; has no member named &#8216;backgroundColor&#8217;
stackswitch.c:236: error: &#8216;CompTextAttrib&#8217; has no member named &#8216;backgroundColor&#8217;
stackswitch.c:237: error: &#8216;CompTextAttrib&#8217; has no member named &#8216;backgroundColor&#8217;
stackswitch.c:238: error: &#8216;CompTextAttrib&#8217; has no member named &#8216;backgroundColor&#8217;
make: *** [build/stackswitch.lo] Error 1
glade@Mean-Machine:~/stackswitch$ 

```Does this mean that I can't have it on this version of Compiz?

PS: I didn't remove Compiz though, since other plugins (except for 3D) install fine.

---

### Post by Enlitend on 2008-06-29
You can use the Compiz PPA  if you don't have the Git version:

[https://launchpad.net/~compiz/+archive]("https://launchpad.net/~compiz/+archive")
:)

---

### Post by st33med on 2008-06-29
I will make note of this again:
[SIZE="4"]You need to compile compiz fusion and the plugin from the master git.[/SIZE]
LinuxIsInnovation: You will need to remove the precompiled compiz-fusion in order to compile compiz fusion.
Enlitend: That does not have stackswith, I believe, because it is still not supported or in the unsupported plugins. In other words, it is too recent to have it in the default plugin package.

---

### Post by Enlitend on 2008-06-29
It has the stackswitch plugin.
All I have to do is install it manually in the terminal after putting the ppa  in my software sources.

Oh and it has the deformation plugin too after the upgrade. :)

p.s. Check out the link I provided on the previous post. The packager currently supports gusty,hardy and intrepid:).
     The stackswitch is on the bottom list, the last line.

---

### Post by borlosky on 2008-07-11
would i have to uninstall compiz if i've already installed compiz from git? just need the stack switch plugin now.

---

