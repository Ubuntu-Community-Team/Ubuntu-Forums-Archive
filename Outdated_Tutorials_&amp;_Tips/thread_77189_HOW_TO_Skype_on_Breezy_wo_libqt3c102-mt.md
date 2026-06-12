---
title: "HOW TO: Skype on Breezy w/o libqt3c102-mt"
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by nbx909 on 2005-10-16
Note this is mainly if you need libqt3-mt for any reason if you do not need libqt-mt go to [http://www.ubuntuforums.org/showthread.php?t=75107&highlight=skype+breezy]("http://www.ubuntuforums.org/showthread.php?t=75107&highlight=skype+breezy") instead. Other wise follow these directions
1. ```
sudo apt-get install libqt3-mt

``` (if you don't already have it installed)
2.Download the Dynamic binary tar.bz2 verson from [http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/) and untar it.
3. copy the skype folder that you just untared to /usr/share/ and /usr/local/share/
for example
```
sudo cp /home/nbx909/skype /usr/share/
sudo cp /home/nbx909/skype /usr/local/share/
```
4.```
cd /usr/share/skype/icons
sudo cp skype_32_32.png /usr/share/pixmaps/

```
5. ```
sudo gedit /usr/share/applications/skype.desktop

```
and paste this into the new skype.desktop 
```

[Desktop Entry]
Name=Skype
Comment=Skype
Exec=/usr/share/skype/skype
Icon=skype_32_32.png
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Application;Network;

```
Save it
6. now refresh the gnome panel by doing 
```
killall gnome-panel

```
7. Go to Applications>Internet and you should see skype. Click on it and it will take a few seconds to load but it will work.

---

### Post by cbudden on 2005-10-16
Or alien a RPM.

---

### Post by nbx909 on 2005-10-16
Now where were you when before i did all of that? :(

---

### Post by kvidell on 2005-10-16
If you've just installed that lib, why can't you just go ahead and install it from the deb file they provide? ([http://skype.com/go/getskype-linux-deb](http://skype.com/go/getskype-linux-deb))
That's what I did, works fine.
- Kev

---

### Post by nbx909 on 2005-10-16
If you have libqt3c102-mt already go ahead and use the .deb. But some apps need the newer libqt3-mt so that is why i wrote this.

---

### Post by arnieboy on 2005-10-16
or just use automatix.. will save u all the trouble.
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by zenrox on 2005-10-16
[http://forum.skype.com/viewtopic.php?t=30291](http://forum.skype.com/viewtopic.php?t=30291) 
i assume you all ready have dynamic ver
skype

```

mv skype_1.2.0.17-1_i386.deb skype_1.2.0.17-1_i386.deb.orig
mkdir skype.tmp
dpkg-deb --extract skype_1.2.0.17-1_i386.deb.orig skype.tmp
dpkg-deb --control skype_1.2.0.17-1_i386.deb.orig skype.tmp/DEBIAN

```
# Now use your favorite editor to edit the Depends line as 
```

gedit  skype.tmp/DEBIAN/control

```
find this line 
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
and replace with 
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
then
```

dpkg --build skype.tmp
mv skype.tmp.deb skype_1.2.0.17-1_i386.deb 
sudo dpkg -i skype_1.2.0.17-1_i386.deb

```
and all should be find and dandy

---

### Post by Gandalf on 2005-10-16
The only effective way i've found is this

```

sudo apt-get install fakeroot alien
fakeroot alien --to-tgz skype_1.2.0.17-1_i386.deb
sudo apt-get install libqt3-mt
fakeroot alien --to-deb skype-1.2.0.17.tgz
sudo dpkg -i skype_1.2.0.17-2_all.deb

```
[Source](http://ubuntuforums.org/showpost.php?p=403154&postcount=5)

---

### Post by lhtown on 2005-10-20
[QUOTE=zenrox][http://forum.skype.com/viewtopic.php?t=30291](http://forum.skype.com/viewtopic.php?t=30291) 
i assume you all ready have dynamic ver
skype

```

mv skype_1.2.0.17-1_i386.deb skype_1.2.0.17-1_i386.deb.orig
mkdir skype.tmp
dpkg-deb --extract skype_1.2.0.17-1_i386.deb.orig skype.tmp
dpkg-deb --control skype_1.2.0.17-1_i386.deb.orig skype.tmp/DEBIAN

```
# Now use your favorite editor to edit the Depends line as 
```

gedit  skype.tmp/DEBIAN/control

```
find this line 
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
and replace with 
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
then
```

dpkg --build skype.tmp
mv skype.tmp.deb skype_1.2.0.17-1_i386.deb 
sudo dpkg -i skype_1.2.0.17-1_i386.deb

```
and all should be find and dandy[/QUOTE]

Works great for me. Now why can't Skype do that?

---

### Post by Mustard on 2005-10-22
[QUOTE=lhtown]Works great for me. Now why can't Skype do that?[/QUOTE]

Good question. :)

The libqt3c102-mt has been giving me grief for a while with all the conflicts it creates with other packages.  I'm glad to see there is a solution.

---

### Post by Mave^ on 2005-10-22
[quote=zenrox][http://forum.skype.com/viewtopic.php?t=30291]("http://forum.skype.com/viewtopic.php?t=30291") 
i assume you all ready have dynamic ver
skype

```

mv skype_1.2.0.17-1_i386.deb skype_1.2.0.17-1_i386.deb.orig
mkdir skype.tmp
dpkg-deb --extract skype_1.2.0.17-1_i386.deb.orig skype.tmp
dpkg-deb --control skype_1.2.0.17-1_i386.deb.orig skype.tmp/DEBIAN

``` # Now use your favorite editor to edit the Depends line as 
```

gedit  skype.tmp/DEBIAN/control

``` find this line 
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
and replace with 
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
then
```

dpkg --build skype.tmp
mv skype.tmp.deb skype_1.2.0.17-1_i386.deb 
sudo dpkg -i skype_1.2.0.17-1_i386.deb

``` and all should be find and dandy[/quote]
Thanks, works great for me :)

---

### Post by rama on 2005-10-22
I ve installed skype following the instructions in post #1 and it works just fine. It also appears under applications->Internet (I guess thats because of the skype.desktop file I ve created).

I m not sure this is the right place to ask but why do I get a "command not found" error when I type "skype" from a console? 
And why cp the folder to both /usr/share/ and /usr/local/share/?

---

### Post by jdawdy on 2005-10-22
Why not just download the Static binary tar.bz2 with Qt 3.2 compiled in?  Worked for me.

Jim

---

### Post by majikstreet on 2005-11-11
Hey,
I just followed zenrox's instructions in another thread about skype.. I downloaded the newest version ( 1.2.0.18 ) and made the changes to the deb. I tested it and it worked! So, I have uploaded it for all to take :)

Instructions:
```

wget -c http://majikstreet.org/files/deb/skype_1.2.0.18-1_i386.deb
sudo dpkg -i skype_1.2.0.18-1_i386.deb

```

Good luck! Just run "skype" to use it... I believe (but I'm not sure) that it will create an entry in the menu.

majikstreet

**DISCLAIMER: I am not a trained deb packager! I may have made a mistake in the packaging. It may not work on your computer. If your computer blows up, it's not my fault.**

---

### Post by majikstreet on 2005-11-11
hi all... I made a deb this way for 1.2.0.18 -- my thread should come up in the how-to's soon!

-m

---

### Post by ubuntu_demon on 2005-11-11
[QUOTE=majikstreet]hi all... I made a deb this way for 1.2.0.18 -- my thread should come up in the how-to's soon!

-m[/QUOTE]
Thnx for the effort!

But I don't think it warrants a seperate howto thread. Maybe there's gonna be a seperate place to put your deb's in the future.

---

### Post by majikstreet on 2005-11-11
oooh... so are you saying that you moderated it and deleted it?

if so, could you PM me the contents so I can post them here- I don't want to rewrite it.

EDIT: I just noticed that it's in this thread.. thanks.

---

### Post by nrayever on 2005-11-13
should this howto work with amd64 too?? 

sincerly nrayever

---

### Post by majikstreet on 2005-11-13
mine won't because I don't have a amd64 processor.

---

### Post by BLTicklemonster on 2005-11-18
I thought it was free?


[img]http://www.hawkwinds.com/tickle/skyperip.jpg[/img]

---

### Post by akurashy on 2005-11-18
[quote=majikstreet]Hey,
I just followed zenrox's instructions in another thread about skype.. I downloaded the newest version ( 1.2.0.18 ) and made the changes to the deb. I tested it and it worked! So, I have uploaded it for all to take :)

Instructions:
```

wget -c http://majikstreet.org/files/deb/skype_1.2.0.18-1_i386.deb
sudo dpkg -i skype_1.2.0.18-1_i386.deb

``` 
Good luck! Just run "skype" to use it... I believe (but I'm not sure) that it will create an entry in the menu.

majikstreet

**DISCLAIMER: I am not a trained deb packager! I may have made a mistake in the packaging. It may not work on your computer. If your computer blows up, it's not my fault.**[/quote]

I downloaded this and it installed perfectly. thanks a lot majik :)(didn't want to do the whole tut) :D

---

### Post by macewan on 2005-11-20
nice work, no problems noted:KS

---

### Post by majikstreet on 2005-11-26
BLTicklemonster: It is. That's to call to a regular phone....

thanks everyone :)

---

### Post by BLTicklemonster on 2005-11-27
So, it's like another IM? 


Weeeee.

---

### Post by gratefulfrog on 2005-11-27
[QUOTE=nrayever]should this howto work with amd64 too?? 
[/QUOTE]

I guess not?
On AMD64:

I followed all instructions, have libqt3-mt,
did everything exactly and...
first:
- no skype in the gnome menu, ok, I put it there by hand,
then no skype exectuion...

```
$ /usr/share/skype-1.2.0.18/skype
/usr/share/skype-1.2.0.18/skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

By the way, I did install the static qt version, but this only works for 1 call, afterwhich skype reports sound problem...

---

### Post by mikeymouse on 2005-12-01
I think I am in love again,hahah
 I wanted to install skype but did not want to go thru all the girations that seemed to be required,,,  then i saw Automatix and now i think i am in love.
 Automatix installed my skype without me even being here. 
 If anyone wants skype i would suggest trying Automatix  it works really well, at least for me..
  Thankyou to who ever has taken the time to create this little program.
 Ubuntu now seems much easier and interesting.. 
 Thankyou  mikeymouse

---

### Post by davidmaxwaterman on 2006-02-06
[QUOTE=Mave^]Thanks, works great for me :)[/QUOTE]

Any clues for getting it on an amd64 machine?

---

### Post by The Belgain on 2006-03-04
Making that change to the .deb package worked a treat for me too.

Has anyone suggested to Skype that they make this change to their .deb package?  Presumably this doesn't break Debian compatibility at all (it just relaxes the dependency rules for the package)?  It would be nice if installing Skype was as easy as just adding the Skype repository in Synaptic, and letting it install dependent packages...

Obviously it would be even nicer for Skype to let Ubuntu stick this in the universe/multiverse repository...

---

### Post by Lut!n on 2006-03-04
Hi,
just a stupid question : Why don't you use the package that's in the PLF repositories ?
It's fully compatible with ubuntu without doing any stuff ......

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free  (only i386 archs)

---

### Post by gnutux on 2006-03-04
about the one call problem, you MUST install skype_dsp_hijacker

gnutux

---

### Post by Tutankamon on 2006-03-12
Hi there,

My problems with skype is.. i heard the others person.. like robocop..   i understand nothing.. its a lot of noice..  and nothing clear..  why ?


Thx for help

---

