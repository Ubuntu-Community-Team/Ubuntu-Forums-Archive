---
title: "howto kde eye-kandies avalable for breezee"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ykpaiha on 2005-10-19
Mainly for newcommers, or lazy breezers (lol)
I manage to build some usefull decoration for kde.
I didn't made any icon set as they are avalable by kde-look:

 color-schemes_1.0.0-..> 19-Oct-2005 11:24     9k  
 fraqtive_0.3.1-1_i38..> 19-Oct-2005 11:22   116k  
 kde-style-baghira_0...> 19-Oct-2005 11:22   699k  
kde-style-linspirecl..> 19-Oct-2005 11:22   111k  
 kde-style-polymer_0...> 19-Oct-2005 11:22   135k  
 kde-style-qtcurve_0...> 19-Oct-2005 11:22   149k  
 knetdockapp_0.62-1_i..> 19-Oct-2005 11:22    55k  
 ksplash-theme-baghir..> 19-Oct-2005 11:22   481k  
 ksplash-theme-deadra..> 19-Oct-2005 11:22   595k  
ksplash-theme-kkog_1..> 19-Oct-2005 11:22   188k  
 ksplash-theme-krysta..> 19-Oct-2005 11:23   223k  
 ksplash-theme-pinkbi..> 19-Oct-2005 11:23   231k  
 ksplash-theme-razr_0..> 19-Oct-2005 11:23   304k  
 kwin-decor-activehea..> 19-Oct-2005 11:23    73k  
 kwin-decor-akdc_1.0a..> 19-Oct-2005 11:23   105k  
 kwin-decor-baghira_0..> 19-Oct-2005 11:23    94k  
 kwin-decor-grover_1...> 19-Oct-2005 11:23    44k  
 kwin-decor-mallory_1..> 19-Oct-2005 11:23    48k  
 kwin-decor-neos_0.2b..> 19-Oct-2005 11:23    80k  
 kwin-decor-porcelain..> 19-Oct-2005 11:23    42k  
kwin-decor-powder_0...> 19-Oct-2005 11:23    59k  
kwin-decor-thedot_0...> 19-Oct-2005 11:23    79k  
 kwin-decor-thin-kera..> 19-Oct-2005 11:23   190k  
 kwin-style-activehea..> 19-Oct-2005 11:23   128k  
 kwin-style-alloy_0.5..> 19-Oct-2005 11:23    73k  
 kwin-style-comix_1.2..> 19-Oct-2005 11:23    92k  
kwin-style-knifty_0...> 19-Oct-2005 11:23    40k  
 kwin-style-konx_0.3-..> 19-Oct-2005 11:23    31k  
 kwin-style-lipstik_1..> 19-Oct-2005 11:23    77k  
 kwin-style-liquid_0...> 19-Oct-2005 11:23   118k  
 kwin-style-newstep_0..> 19-Oct-2005 11:23    51k  
 kwin-style-qinx_1.2-..> 19-Oct-2005 11:23    82k  
 kwin-style-tiblit_1...> 19-Oct-2005 11:23   141k  
 six_0.5.2-1_i386.deb    19-Oct-2005 11:23   160k  
 styleclock_0.5.1-1_i..> 19-Oct-2005 11:23   375k  
 superkaramba_0.37-RC..> 19-Oct-2005 11:23   260k  
 x11-cursor-crystal_1..> 19-Oct-2005 11:23   259k  

All rebuild with breezee and kde 3.4.3

Here it is:
[http://g.natacha.free.fr](http://g.natacha.free.fr)

To install it just click on the theme or package and download it (in case it does not work right click => save under...)
then when in your directory or wherever it is right click on it then => kubuntu package menu =>install
a window will open just give your root password and it will be installed in your system

You will find the new package in the folder apearence /theme of kconfigure.
just enjoy it  the new parameters of your kde.

---------------------------------------------------------------------------------------------------------------------------------------------

An other way is to compile yourself (if you want to learn a bit

easy to turn out (a bit as a spy-job but it works)

1) create a folder
mkdir /home/your-name/xxxxx(in fact whatever you want)

2)add a repo:
sudo gedit /etc/apt/sources.list
add this into it:
deb-src [http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable) ./

3)open this mirror in your browser and you will see a numerous kwin and others "k"andies
they are all debian ready and so easely tranferable into kubuntu
[http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable)

4)you need to install every thing to compile
build essential, kde and kdelib -dev, fakeroot, autoconf, automake, debhelper...

5)then in a console (install mc it's easier) go in your new created dir
and simply type:
sudo apt-get source -b "the package name you like -you have seen in mirror pulsing"
after 1 minute or 2 you will get in the root of your dir a brand new *.deb package you can install or manage the way you want it

easy and educating !

if you have troubles in the compile you will see the messages error willtell you witch package is missing, you will find it easely in synaptic (quite often it's some *-dev)

have fun and let me know if it's usable for you

thanks to pusling in kde-ook for his job!
[http://www.kde-look.org/content/show.php?content=29317](http://www.kde-look.org/content/show.php?content=29317)

I hope you ''ll enjoy it
even a little thank is welcome!!..

---

### Post by NicP on 2005-10-19
screenshots?

---

### Post by ykpaiha on 2005-10-19
screenshot are avalaible on kde-look.org
on the search you juste type the name of the package you need.to see.
this is a compilation of several candies for kde...

---

### Post by ubuntu_demon on 2005-10-19
I moved this thread to the kde howto's section

ykpaiha: can you please explain this in a way that green users can understand it too ?

edit : thnx!

---

### Post by sal on 2005-10-19
could you do a suse theme such as the theme, style, color scheme, and such please.
thanks if you can.

---

### Post by jvoegele on 2005-10-19
[QUOTE=ykpaiha]Mainly for newcommers, or lazy breezers (lol)
I manage to build some usefull decoration for kde.[/QUOTE]

Thank you for putting this together.  I've been looking for such a repository for a long while.

---

### Post by shakin on 2005-10-20
I will echo jvoegele's thank you. This is an excellent repository. IMO, the (k)Ubuntu community needs an art repository full of icons, kwin/metacity themes, etc. There are so many out there and it's nearly always a hassle to install them. I've found Kwin themes especially difficult and I always end up copying the compiled theme's files manually into the right directories.

---

### Post by ykpaiha on 2005-10-20
[QUOTE=shakin]I will echo jvoegele's thank you. This is an excellent repository. IMO, the (k)Ubuntu community needs an art repository full of icons, kwin/metacity themes, etc. There are so many out there and it's nearly always a hassle to install them. I've found Kwin themes especially difficult and I always end up copying the compiled theme's files manually into the right directories.[/QUOTE]

If I can be usefull please ask 
I "ll see if it is possible to compile some more as i am not a "champion" do not ask for too hard (lol)..

on aktual statistics
the most downloaded is color-schemes; and linspire.

---

### Post by lucascr on 2005-10-21
First of all, thanks for these deb packages.
I installed styleclock but when I try to get the applet I receive the following error:

Styleclock needs OpenGL support, but your system doesn't support it.

Details:
QGLFormat::hasOpenGL() returned false, indication no OpenGL support for Qt

Of course I'm missing some package(s) but I can't figure out which one. Any idea?

Luca

---

### Post by ykpaiha on 2005-10-21
[QUOTE=lucascr]First of all, thanks for these deb packages.
I installed styleclock but when I try to get the applet I receive the following error:

Styleclock needs OpenGL support, but your system doesn't support it.

Details:
QGLFormat::hasOpenGL() returned false, indication no OpenGL support for Qt

Of course I'm missing some package(s) but I can't figure out which one. Any idea?

Luca[/QUOTE]

Sorry I forgot to mention :
my card is a nvidia so I installed as well the gl - dev .
so i suppose it has used it for this one in particular ..
I hope it does not make a lot of diif if you install yours.
maiby as well the glu-mesa can help if you could be more specific with your hardware I can give you more info.

---

