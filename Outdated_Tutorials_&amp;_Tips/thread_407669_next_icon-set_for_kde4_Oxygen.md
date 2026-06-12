---
title: "next icon-set for kde4 Oxygen"
date: 2007-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ykpaiha on 2007-04-12
I will here explain how to get and follow the svn oxygen icon set from the dev sources

1) create a dir in your home
open a console
mkdir ~/svn
svn is an exemple call it as you wish 
"~"=your home

2) cd ~/svn
then type
svn co svn://anonsvn.kde.org/home/kde/trunk/KDE/kdelibs/pics/oxygen
if you do not have the right packages installed it will name it you just have to apt-get install it or them; usualy it only needs subversion 
if you get a question about the rights answer (p) for permanent

3)copy the fresh created "oxygen" directory in to /home/yourusername/.kde/share/icons. 
mv ~/svn/oxygen ~/.kde/share/icons
or 
cp -r ~/svn/oxygen ~/.kde/share/icons/  (if you want yo keep your /svn/dir it will then just check the update next time you use the svn rather to dwld the whole directory)
After that, go into KControl, and under icons you should see oxygen validate it

4) from time to time do the same procedure as oxygen is in a heavy dev part..

good luck and let me know if it is usefull to you.

added may 21st 

You can as well create a symbolic link to avoid the double oxygen directory and just refresh the svn will update the whole iconset
first remove the copied directory:
rmdir ~/.kde/share/icons/oxygen
then create a link:
ln -s  ~/svn/oxygen ~/.kde/share/icons/

Just relog in to see it and validate with kcontrol

almost 1000 reader for this post and just 1 or 2 hello so I do it mysellf 
HELLO!

---

### Post by ykpaiha on 2007-05-18
just changed today as 100 mo become a bit too big for my ftp...:lolflag:

---

### Post by rich.bradshaw on 2007-05-18
To let people know, it takes around 322MB of space, think the download is compressed though, as it didn't take very long...

Mine doesn't show in Control Center, tried adding the .theme file, but it says it's not a theme... any ideas?

---

### Post by ykpaiha on 2007-05-18
> **rich.bradshaw said:**
> To let people know, it takes around 322MB of space, think the download is compressed though, as it didn't take very long...

Mine doesn't show in Control Center, tried adding the .theme file, but it says it's not a theme... any ideas?

when i do the full procedure the oxygen-dir  is just 159mo so maybe something is wrong on your download.

---

### Post by pbw on 2007-05-19
I've been using the oxygen set for some time now. Must say it's coming along nicely and looking pretty slick :)

I'm in agreement with Rich, My iconset is the same size.

[quote=rich.bradshaw]
Mine doesn't show in Control Center, tried adding the .theme file, but it says it's not a theme... any ideas?
[/quote]

I'd remove your oxygen set altogether and recheck it from svn, should be fine.

-- pbw

---

### Post by ykpaiha on 2007-05-19
> **pbw said:**
> I've been using the oxygen set for some time now. Must say it's coming along nicely and looking pretty slick :)

I'm in agreement with Rich, My iconset is the same size.



I'd remove your oxygen set altogether and recheck it from svn, should be fine.

-- pbw

i do not undderstand how? i do a weekly update and my full icon directory show just 5501 elements and rarely more than 165 mo. and 159 on a fresh download and 100mo if I zip it
so maybe something left somewhere ...

for rich:
> **rich.bradshaw said:**
> To let people know, it takes around 322MB of space, think the download is compressed though, as it didn't take very long...

Mine doesn't show in Control Center, tried adding the .theme file, but it says it's not a theme... any ideas?

do not install with the kcontol ! Ihave tried already it doesn't work that way:
just copy into your home/your-name/./kde/share/icons as specified in point 3 of my small howto.

---

### Post by pbw on 2007-05-20
If you wish to install it via kcontrol, just tar up the svn checkout.

eg. tar czvf kde-oxygen.tar.gz oxygen 

Then in kcontrol select the tar.gz file to install.

-- pbw

---

### Post by TheMono on 2007-05-20
Instead of copying over the svn directory into the icons directory, would it to bad things if I was just to symlink to it?

---

### Post by pbw on 2007-05-20
Not sure why you'd want to?.. Just checkout svn in ~/.kde/share/icons. then you dont have to move, copy or recheckout from scratch, just svn update from that directory next time.

-- pbw

---

### Post by TheMono on 2007-05-20
Same idea. The only reason I'd do it my way is I have a bunch of svn stuff in the .svn folder in my home directory, so it would just be for purposes of cleanliness, and so I'm not constantly changing folders when I update all my svn stuff. My question was more if it will break things to have your iconset as the svn folder - and I presume your post is that it is fine to do that?

---

### Post by pbw on 2007-05-20
Pretty sure it'd be fine, only one way to find out for sure i guess. ;)

---

### Post by rich.bradshaw on 2007-05-21
Ok, mine seems to work now - I symlinked it, and it didn't like it!

Looks pretty good - had to log in/out to get it to show up, but apart from that, it's cool. Seems like there is a lot to get done though - whens it meant to be finished?

---

### Post by pbw on 2007-05-21
It'll be default in kde4, here's the official website you can check out [http://www.oxygen-icons.org/](http://www.oxygen-icons.org/)

---

### Post by ykpaiha on 2007-05-21
> **rich.bradshaw said:**
> Ok, mine seems to work now - I symlinked it, and it didn't like it!

Looks pretty good - had to log in/out to get it to show up, but apart from that, it's cool. Seems like there is a lot to get done though - whens it meant to be finished?

Just to confirm
It works as well with te sym-link I forgot that one.
I 'll add this to the how-to , just to confirm as well you have to log-out then in to see the icon set to appear in kcontrol with the link..

---

### Post by ykpaiha on 2007-06-10
it's still working today:popcorn:

---

### Post by chrisrx on 2007-06-16
My university's http proxy won't let me connect to subversion even after configuring ~/.subversions/servers.  Is there any other way to get this icon set?

---

### Post by ykpaiha on 2007-06-16
> **chrisrx said:**
> My university's http proxy won't let me connect to subversion even after configuring ~/.subversions/servers.  Is there any other way to get this icon set?

i will make a copy specialy for you on [http://g.natacha.free.fr/oxygen/](http://g.natacha.free.fr/oxygen/)
due to the bandwidth I wiil leave it only two days from tonight
is that ok for you ?

---

### Post by ykpaiha on 2007-06-16
done now 
[http://g.natacha.free.fr/oxygen/oxygen.tar.gz](http://g.natacha.free.fr/oxygen/oxygen.tar.gz)
size; 93,2 Mio (97720048 octets)
but remember 2 or 3 days only
sorry
good luck

---

### Post by chrisrx on 2007-06-17
Wow thanks that's really helpful:p:p:p.  I'm downloading now, can't wait to try it out.

---

### Post by chrisrx on 2007-06-17
It seems some icons just show the default gnome icons, like the folder icon for example.  Is there any way I can fix it?

---

### Post by Clay_Banger on 2007-06-17
> **chrisrx said:**
> It seems some icons just show the default gnome icons, like the folder icon for example.  Is there any way I can fix it?
gnome? are you trying to install these into gnome? if so, im not sure if they will entirely work.

---

### Post by chrisrx on 2007-06-17
Yes, but as far as I know the format for naming the icons and writing the .theme was standardised across gnome and kde

---

### Post by ykpaiha on 2007-06-18
yes i works partially in gnome I have tried it but only the index.theme has to be changed;
this one gave xome results
1)copy oxygen rep in your home/your name/.icons dir
2) change the index.them by this one here provided
3).use oxygen in the theme changer (icons)
 
feel free to post any change you have done on my basic file

---

### Post by ykpaiha on 2007-06-18
yes i works partially in gnome I have tried it but only the index.theme has to be changed;
this one gave xome results
1)copy oxygen rep in your home/your name/.icons dir
2) change the index.them by this one here provided
3).use oxygen in the theme changer (icons)
 
feel free to post any change you have done on my basic file

[Icon Theme]
Name=oxygen
Inherits=Tango,gnome,hicolor
Comment=Icon theme first released by Toby, revived and maintained in 2005-2007 by Kiddo
Directories=scalable/actions,scalable/apps,scalable/apps/48,scalable/spinner,scalable/places,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/emblems/48,scalable/stock,scalable/stock/64,scalable/stock/48

[scalable/actions]
Size=128
Context=Actions
Type=scalable

[scalable/emblems]
Size=180
Context=Emblems
Type=scalable

[scalable/emblems/48]
Size=48
Context=Emblems
Type=scalable

[scalable/apps]
Size=128
Context=Applications
Type=scalable

[scalable/apps/48]
Size=48
Context=Applications
Type=scalable

[scalable/spinner]
Size=36
Context=Applications
Type=scalable

[scalable/devices]
Size=128
Context=Devices
Type=scalable

[scalable/places]
Size=128
Context=places
Type=scalable

[scalable/mimetypes]
Size=128
Context=MimeTypes
Type=scalable

[scalable/stock]
Size=32
Context=Stock
Type=scalable

[scalable/stock/64]
Size=64
Context=Stock
Type=scalable

[scalable/stock/48]
Size=48
Context=Stock
Type=scalable

---

### Post by splitsch on 2007-08-02
Great how-to !
Thanks a lot...I kindda like those icon, but what I like most is to be at the edge...
I'm up for gutsy ;)

Bye !

---

