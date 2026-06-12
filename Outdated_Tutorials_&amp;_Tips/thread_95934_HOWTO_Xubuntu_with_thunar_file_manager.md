---
title: "HOWTO: Xubuntu with thunar file manager"
date: 2005-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by sapo on 2005-11-27
I tried Xubuntu here and it was love at first sight, but the only thing that i disliked about it was the rox-filer, not that its not good, its very fast, but for some reasons i think its too complicated, and i missed some nautilus features.

The purpose of this thread is to help you install Thunar from svn, its far easier than rox and looks like nautilus, so you will be at home.

Thunar is still in early development stage, so dont expect too much from it, but it can do the basic stuff, open, copy, move, delete files, etc.

For more info and screenshots, [click here](http://thunar.xfce.org/index.xhtml).

Here a screenshot:
[img]http://thunar.xfce.org/images/filewindow-1.png[/img]


Btw.. lets start.

To install xfce (Xubuntu) in breezy is simple:

```

sudo apt-get install xubuntu-desktop

```

To enter xfce just logoff from your Gnome or KDE Session, click on the session button and choose XFCE.


**Thunar Debs:**

Edit: If you are lazy, i made some debs, hope they work for you, if they dont, just uninstall them and use the svn below, here we go:

[libexo_0.3svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/libexo_0.3svn-1_i386.deb)
[xfce4-dev-tools_4.3.1svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/xfce4-dev-tools_4.3.1svn-1_i386.deb)
[thunar_0.1.4svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/thunar_0.1.4svn-1_i386.deb)



**Thunar SVN**
Now to install Thunar, open up a terminal and cut and paste, or type the following commands:

```

sudo apt-get install gtk-doc-tools libxml-parser-perl automake1.8 libxfce4util-dev subversion build-essential

svn co http://svn.xfce.org/svn/xfce/libexo/trunk xfce4-svn-source/libexo
svn co http://svn.xfce.org/svn/xfce/thunar/trunk xfce4-svn-source/thunar
svn co http://svn.xfce.org/svn/xfce/xfce4-dev-tools/trunk xfce4-svn-source/xfce4-dev-tools

cd xfce4-svn-source/xfce4-dev-tools
sh autogen.sh
make
sudo make install

cd ../libexo/
sh autogen.sh
make
sudo make install

cd ../thunar/
sh autogen.sh
make
sudo make install

```

Now to open up tunar, just create a shortcut to it, right click on the xfce panel, add new item, then select laucher, select an icon, and in the command fill with **thunar**

If you have some problems:
[QUOTE=lucas]This error loading the library:
```
thunar: error while loading shared libraries: libthunar-vfs-1.so.0: cannot open shared object file: No such file or directory
```

occurs beacuse the library chache isn't updated. do this with the **ldconfig** command. After updating the cache it works fine.[/QUOTE]

If you have some more tips about it, or any doubs please ask, so i can update the howto and make it better.

For now is just it, i just wanted to share it with all the ubuntu users, if you have a slow pc or if you would like to make you fast pc fly, give Xubuntu a try.

---

### Post by Logic* on 2005-11-29
Hi, thanks for the guide.

I followed your steps but have a problem at this point
```

**andrew@tux xfce4-dev-tools $ sh autogen.sh**
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
Makefile.am:13: require version 1.8, but have 1.4-p6
```

How can I fix this?

Thanks

---

### Post by sapo on 2005-11-29
[QUOTE=Logic*]Hi, thanks for the guide.

I followed your steps but have a problem at this point
```

**andrew@tux xfce4-dev-tools $ sh autogen.sh**
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
Makefile.am:13: require version 1.8, but have 1.4-p6
```

How can I fix this?

Thanks[/QUOTE]
sudo apt-get install automake1.8

maybe you will have to uninstall the 1.4 version for it to work, search for automake using synaptic.

I added those in the howto now, thats because i just tried it on a fresh install of breezy yesterday, and it was missing some dependencies... if something doesnt work please ask.

---

### Post by kaamos on 2005-11-29
Brilliant! Never really liked rox.. Got to try this out later.

Thanks for the howto!

---

### Post by Norm 2782 on 2005-11-29
Wow cool... looks a bit like Mac OS Finder (guess they got quite some inspiration from that). Would make me feel right at home, seeing that my main box is OS X ^^ Gonna try it on my Ubuntu lappy ASAP. Thanks!

---

### Post by r0nin on 2005-11-29
When I get to the svn part, the console tells me it doesn't know the command!

```

pierre@p4:~$ svn co http://svn.xfce.org/svn/xfce/libexo/trunk xfce4-svn-source/libexo
bash: svn: command not found

```

---

### Post by dabear on 2005-11-29
yeees? Do you have svn installed then? lolliloll

---

### Post by sapo on 2005-11-29
[QUOTE=r0nin]When I get to the svn part, the console tells me it doesn't know the command!

```

pierre@p4:~$ svn co http://svn.xfce.org/svn/xfce/libexo/trunk xfce4-svn-source/libexo
bash: svn: command not found

```[/QUOTE]
sudo apt-get install subversion

just do it and it will solve your problem, i ll add it to the how-to, i though that subversion would be installed by default in breezy, but it is not :(

---

### Post by j_baer on 2005-11-29
I was able to install Thunar via Synaptic by adding the sources noted in the following link.

[http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

By doing so will also upgrade your Xfce installation. I found Thunar very nice but incomplete at this time. Rumor has it the rc will be ready in February and I believe all who try it will love it.

Right now the best Xfce configurartion for me is a mix with Gnome.

Another tip for those who are new to Xfce. if you follow the guide at this thread

[http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

you will get window shadowing and more.

Cheers ...

---

### Post by sapo on 2005-11-29
[QUOTE=j_baer]I was able to install Thunar via Synaptic by adding the sources noted in the following link.

[http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

By doing so will also upgrade your Xfce installation. I found Thunar very nice but incomplete at this time. Rumor has it the rc will be ready in February and I believe all who try it will love it.

Right now the best Xfce configurartion for me is a mix with Gnome.

Another tip for those who are new to Xfce. if you follow the guide at this thread

[http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

you will get window shadowing and more.

Cheers ...[/QUOTE]

I installed thunar using this debian rep at first too. but that one didnt have anything, the new one from svn is usable, it can copy, move, paste, delete, set applications to open files, etc.

I think you should try the one from svn, its completelly different.

---

### Post by bored2k on 2005-11-29
Has anyone made a deb yet ?

BTW, sapo, your blog made me want to try xfce once AGAIN. Good persuasive writing ;).

I'll try to build a x86 deb once I have this.

---

### Post by bored2k on 2005-11-29
[QUOTE=Norm 2782]Wow cool... looks a bit like Mac OS Finder (guess they got quite some inspiration from that). Would make me feel right at home, seeing that my main box is OS X ^^ Gonna try it on my Ubuntu lappy ASAP. Thanks![/QUOTE]
Yes. They are taking ideas from Finder, Nautilus and some others (they said that).

---

### Post by sapo on 2005-11-29
[QUOTE=bored2k]Has anyone made a deb yet ?

BTW, sapo, your blog made me want to try xfce once AGAIN. Good persuasive writing ;).

I'll try to build a x86 deb once I have this.[/QUOTE]
omg, you really did read that?

I thought that nobody besides me read that...

btw.. i didnt find a deb for this svn version.. maybe you could make us one :)

---

### Post by lucas on 2005-11-29
A thunar deb would be great. Beacuse I can't be arsed to compile but I love xfce and i would love to try thunar. Maybe even xfce 4.3 svn debs? :)

---

### Post by bored2k on 2005-11-29
> **sapo]omg, you really did read that?[/QUOTE]"Surprise"  said:**
> 
btw.. i didnt find a deb for this svn version.. maybe you could make us one :)I was refering to someone creating their own. I'll try to make one after I have thunar installed.. which comes after installing xubuntu :P.

---

### Post by Logic* on 2005-11-29
Hi, the automake thing worked - I did have to remove the older package, as you said.

My next problem comes here

[QUOTE=sapo]
...
```

cd ../libexo/
sh autogen.sh

```
...
[/QUOTE]

I get this

```

...
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ca de el en_GB es fi fr ja pt_BR
checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${prefix}/share/locale
checking for additional xgettext flags... --keyword=Q_
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.19
checking for glib-2.0 >= 2.4.0... 2.8.3
checking GLIB_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GLIB_LIBS... -lglib-2.0
checking for gtk+-2.0 >= 2.4.0... not found
*** The required package gtk+-2.0 was not found on your system.
*** Please install gtk+-2.0 (atleast version 2.4.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

```

Do I need to install a different package here, or is it a configuration problem?

Thanks

---

### Post by varunus on 2005-11-29
Get the libgtk2.0-dev package from synaptic to fix this.

---

### Post by Logic* on 2005-11-29
Cool :)

Thankyou very much

---

### Post by ksousa on 2005-11-29
First...Tks to SAPO for the great howto;
Second...Since i ve discovered Xubuntu i only work with him, cause is fast and reliable...and of course beautiful;
Three...Finally i give all my computer to Xubuntu and finish forever with Gates Boy;

Thanks for all the comunity of Ubuntu for this wonderful product

---

### Post by sapo on 2005-11-29
[QUOTE=ksousa]First...Tks to SAPO for the great howto;
Second...Since i ve discovered Xubuntu i only work with him, cause is fast and reliable...and of course beautiful;
Three...Finally i give all my computer to Xubuntu and finish forever with Gates Boy;

Thanks for all the comunity of Ubuntu for this wonderful product[/QUOTE]
You should thank the guys from #thunar @ irc.freenode.org, they helped me install it so i could me the how-to :)

---

### Post by j_baer on 2005-11-29
Hey Logic*

What theme are you using? I really like your desktop ...

Cheers

---

### Post by bored2k on 2005-11-29
```
thunar: error while loading shared libraries: libthunar-vfs-1.so.0: cannot open shared object file: No such file or directory
```
:(

---

### Post by sapo on 2005-11-29
[QUOTE=bored2k]```
thunar: error while loading shared libraries: libthunar-vfs-1.so.0: cannot open shared object file: No such file or directory
```
:([/QUOTE]
Did you do a make install?

This lib is compiled with Thunar, how can you not have it O_o

---

### Post by bored2k on 2005-11-29
[QUOTE=sapo]Did you do a make install?

This lib is compiled with Thunar, how can you not have it O_o[/QUOTE]
Yes I did :s.

Note: the make is getting done via automake1.9 not automake1.8. Any difference? will now try removing 1.8.

---

### Post by sapo on 2005-11-29
[QUOTE=bored2k]Yes I did :s.

Note: the make is getting done via automake1.9 not automake1.8. Any difference? will now try removing 1.8.[/QUOTE]
you need to remove the 1.9 not 1.8 O_o

---

### Post by bored2k on 2005-11-29
[QUOTE=sapo]you need to remove the 1.9 not 1.8 O_o[/QUOTE]
That's what I meant.

Well, I retried and got the same.

---

### Post by sapo on 2005-11-29
this is kinda weird O_o

I compiled it here, and in my last install without any problems like it, sorry but:

/j #thunar @ irc.freenode.org

---

### Post by Logic* on 2005-11-29
[QUOTE=j_baer]Hey Logic*

What theme are you using? I really like your desktop ...

Cheers[/QUOTE]

I'm using the Humanitarian theme, found in the attachment in this post 

[http://www.ubuntuforums.org/showthread.php?t=92395](http://www.ubuntuforums.org/showthread.php?t=92395)

---

### Post by j_baer on 2005-11-29
Didn't work here ...

The sh autogen.sh script posted the following errors.

/home/j_baer/thunar/xfce4-svn-source/xfce4-dev-tools/missing: Unknown `--run' option
Try `/home/j_baer/thunar/xfce4-svn-source/xfce4-dev-tools/missing --help' for more information

The result is no "make" file.

  :(

---

### Post by henriquemaia on 2005-11-30
[QUOTE=bored2k]That's what I meant.

Well, I retried and got the same.[/QUOTE]

I got the same problem here. I really like thunar (I installed it previously through a .deb). Any Ideas?

Btw, sapo, your blog is really cool. One more reader. Looks there are 3 now.

---

### Post by sapo on 2005-11-30
[QUOTE=henriquemaia]I got the same problem here. I really like thunar (I installed it previously through a .deb). Any Ideas?

Btw, sapo, your blog is really cool. One more reader. Looks there are 3 now.[/QUOTE]
regarding the problems, i dont know what can be giving the errors, sorry guys but i cant help you :(

And about the blog, thanx, i ll try to update that more often, but i kinda have a lot to work here, so i dont have too much time to post there :(

But thanx for reading it, post a comment there if possible :)

---

### Post by foxy123 on 2005-11-30
[QUOTE=bored2k]```
thunar: error while loading shared libraries: libthunar-vfs-1.so.0: cannot open shared object file: No such file or directory
```
:([/QUOTE]
do you have the latest libexo?

---

### Post by henriquemaia on 2005-12-01
[QUOTE=sapo]regarding the problems, i dont know what can be giving the errors, sorry guys but i cant help you :(

And about the blog, thanx, i ll try to update that more often, but i kinda have a lot to work here, so i dont have too much time to post there :(

But thanx for reading it, post a comment there if possible :)[/QUOTE]


Problem solved. Did nothing, just went to bed and today, after reading this thread again, made another try on thunar. 

When all else fails, reboot your computer.

Thunar is whole lot cooler now!

---

### Post by bored2k on 2005-12-01
[QUOTE=foxy123]do you have the latest libexo?[/QUOTE]
Yes. Sapo even sent me his debs.

---

### Post by henriquemaia on 2005-12-01
[QUOTE=bored2k]Yes. Sapo even sent me his debs.[/QUOTE]

Stupid question, but have you rebooted since your instalation? That did the trick to me.

---

### Post by bored2k on 2005-12-01
[QUOTE=henriquemaia]Stupid question, but have you rebooted since your instalation? That did the trick to me.[/QUOTE]
This is ... embarrassing. It works now. This has no explanation.

Wow. This app owns. Buh bye nautilus.

---

### Post by sapo on 2005-12-01
[QUOTE=henriquemaia]Stupid question, but have you rebooted since your instalation? That did the trick to me.[/QUOTE]
As far as i know him.. he should have unistalled before rebooting hehe

---

### Post by j_baer on 2005-12-01
[QUOTE=bored2k]Yes. Sapo even sent me his debs.[/QUOTE]

Ok bored2k or Sapo, are you going to share the debs?

:)

---

### Post by Logic* on 2005-12-01
Glad to hear everyones got it working :D 

I have crashes when moving and copying some files, but to me, its intuitiveness makes it a far better choice than rox-filer for general file management.

Would I just repeat the steps of this howto to get an updated version of thunar in future?

---

### Post by jrincon87 on 2005-12-01
Hey. I followed all the steps without getting any errors, but I can't launch Thunar. There is no executable in /usr/bin.

---

### Post by sapo on 2005-12-02
[QUOTE=jrincon87]Hey. I followed all the steps without getting any errors, but I can't launch Thunar. There is no executable in /usr/bin.[/QUOTE]
/usr/local/bin i guess..

Did you run sudo make install? did it give you errors?

---

### Post by bored2k on 2005-12-02
Dude... this manager is SO good. Ultra cheers sapo!

---

### Post by mcwtlg on 2005-12-02
I will start off on a positive note.
  
Your instructions were good and easy to follow.
Thunar is very quick and usable.  I just need to get it to work as if it was logged in as root.

Now negative side.  I tried to compile this 5 or 6 times, each time getting a bit further.  For whatever reason, I was missing compiler files and added a few at a time until I finally was able to get the darned thing installed.  It was very aggrevating mostly because I am newer to linux.

---

### Post by lucas on 2005-12-02
I was too curious to wait, so i compiled it anyway. thanks for the howto sapo. It compiled and works fine. Does anyone know how to set the icons size, they are quite big for me?

This error loading the library:
```
thunar: error while loading shared libraries: libthunar-vfs-1.so.0: cannot open shared object file: No such file or directory
```

occurs beacuse the library chache isn't updated. do this with the **ldconfig** command. After updating the cache it works fine.

---

### Post by j_baer on 2005-12-02
Second time is the charm!

Thunar is quick and to the point. I also like the bookmark feature. Nice job!

It would be nice to have a one (1) click option and I hope that will be included by the release date.

Thanks for the how-to ...

Cheers

---

### Post by picpak on 2005-12-02
Thunar crashes every time I open a text file. And then it says:

```
libxfce4util-CRITICAL **: simple_add_entry: assertion `locale == NULL' failed
aborting...
Aborted
```

Any ideas?

---

### Post by henriquemaia on 2005-12-02
[QUOTE=jrincon87]Hey. I followed all the steps without getting any errors, but I can't launch Thunar. There is no executable in /usr/bin.[/QUOTE]

Have you tried 

```
whereis thunar
```?

mine is located in 

```
/usr/local/bin/thunar
```


ps: *whereis* is an actual command. Reading without knowing, I would doubt my sanity...

---

### Post by sapo on 2005-12-03
[QUOTE=mcwtlg]I will start off on a positive note.
  
Your instructions were good and easy to follow.
Thunar is very quick and usable.  I just need to get it to work as if it was logged in as root.

Now negative side.  I tried to compile this 5 or 6 times, each time getting a bit further.  For whatever reason, I was missing compiler files and added a few at a time until I finally was able to get the darned thing installed.  It was very aggrevating mostly because I am newer to linux.[/QUOTE]
Thanx, and sorry.

I didnt added the build-essential package to the apt-get command to install the dependencies, it is one of the first thing that i install on my ubuntu, but i think that isnt everyone that installs it.. so i added it in the howto now.

---

### Post by trevorv on 2005-12-03
Just to say thanks a lot for this guide, it helped a lot! Rox was the one thing (well, that and the search dialogue) that made me shudder about Xubuntu. Now it's almost perfect!

---

### Post by sapo on 2005-12-03
[QUOTE=trevorv]Just to say thanks a lot for this guide, it helped a lot! Rox was the one thing (well, that and the search dialogue) that made me shudder about Xubuntu. Now it's almost perfect![/QUOTE]
If you have gnome installed, just use the gnome-search-tool, just type it on a terminal or create a launcher for it.

And why not beagle?

---

### Post by j_baer on 2005-12-03
sapo,

What is the syntax for the gnome search tool? And wouldn't be nice to have the Beagle damon load at boot ...

Cheers

---

### Post by sapo on 2005-12-03
[QUOTE=j_baer]sapo,

What is the syntax for the gnome search tool? And wouldn't be nice to have the Beagle damon load at boot ...

Cheers[/QUOTE]
The command is gnome-search-tool, just type it on a terminal, or in the Run dialog.

---

### Post by -DarkMind- on 2005-12-05
excelent file manager!

thanks for the how-to

i upload the debs ;)

[http://rapidshare.de/files/8672254/xfce4-dev-tools_1.0-1_i386.deb.html](http://rapidshare.de/files/8672254/xfce4-dev-tools_1.0-1_i386.deb.html)

[http://rapidshare.de/files/8672317/libexo_1.0-1_i386.deb.html](http://rapidshare.de/files/8672317/libexo_1.0-1_i386.deb.html)

[http://rapidshare.de/files/8672338/thunar_1.0-1_i386.deb.html](http://rapidshare.de/files/8672338/thunar_1.0-1_i386.deb.html)


:)




compiled: 12/5/2005 :)

---

### Post by -DarkMind- on 2005-12-05
i have a problem :(

when i tried to open a file without association, thunar died

or when i click in "Open With" exit and says:


```
libxfce4util-CRITICAL **: simple_add_entry: assertion `locale == NULL' failed
aborting...
Abortado

```



:(

---

### Post by mike4ubuntu on 2005-12-05
I got as far as:


sudo apt-get install gtk-doc-tools libxml-parser-perl automake1.8 libxfce4util-dev subversion build-essential
sudo apt-get remove automake1.4
sudo apt-get install automake1.8

svn co [http://svn.xfce.org/svn/xfce/libexo/trunk](http://svn.xfce.org/svn/xfce/libexo/trunk) xfce4-svn-source/libexo
svn co [http://svn.xfce.org/svn/xfce/thunar/trunk](http://svn.xfce.org/svn/xfce/thunar/trunk) xfce4-svn-source/thunar
svn co [http://svn.xfce.org/svn/xfce/xfce4-dev-tools/trunk](http://svn.xfce.org/svn/xfce/xfce4-dev-tools/trunk) xfce4-svn-source/xfce4-dev-tools

cd xfce4-svn-source/xfce4-dev-tools
sh autogen.sh
make
sudo make install

cd ../libexo/
sh autogen.sh
make
sudo make install

cd ../thunar/
sh autogen.sh

----
but then failed with:

mike@lic4:~/thunar/xfce4-svn-source/thunar$ sh autogen.sh
Preparing package directory /home/mike/thunar/xfce4-svn-source/thunar...
Creating /home/mike/thunar/xfce4-svn-source/thunar/aclocal.m4...
Running glib-gettextize --force --copy...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize --automake --copy --force
Patching file 'po/Makefile.in.in'
Running libtoolize --force --copy...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running gtkdocize --copy...
...

checking for exo-0.3 >= 0.3.1.1... not found
*** The required package exo-0.3 was not found on your system.
*** Please install exo-0.3 (atleast version 0.3.1.1) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

---

### Post by mike4ubuntu on 2005-12-05
It actually seems to be easier to update

/etc/apt/sources.list

with

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

then

$ sudo apt-get install thunar

---

### Post by -DarkMind- on 2005-12-05
[QUOTE=mike4ubuntu]It actually seems to be easier to update

/etc/apt/sources.list

with

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

then

$ sudo apt-get install thunar[/QUOTE]

the repo have the svn version??

---

### Post by picpak on 2005-12-05
[QUOTE=-DarkMind-]i have a problem :(

when i tried to open a file without association, thunar died

or when i click in "Open With" exit and says:


```
libxfce4util-CRITICAL **: simple_add_entry: assertion `locale == NULL' failed
aborting...
Abortado

```

:([/QUOTE]


Same here. Any ideas?

---

### Post by carlosqueso on 2005-12-08
[QUOTE=mike4ubuntu]I got as far as:


sudo apt-get install gtk-doc-tools libxml-parser-perl automake1.8 libxfce4util-dev subversion build-essential
sudo apt-get remove automake1.4
sudo apt-get install automake1.8

svn co [http://svn.xfce.org/svn/xfce/libexo/trunk](http://svn.xfce.org/svn/xfce/libexo/trunk) xfce4-svn-source/libexo
svn co [http://svn.xfce.org/svn/xfce/thunar/trunk](http://svn.xfce.org/svn/xfce/thunar/trunk) xfce4-svn-source/thunar
svn co [http://svn.xfce.org/svn/xfce/xfce4-dev-tools/trunk](http://svn.xfce.org/svn/xfce/xfce4-dev-tools/trunk) xfce4-svn-source/xfce4-dev-tools

cd xfce4-svn-source/xfce4-dev-tools
sh autogen.sh
make
sudo make install

cd ../libexo/
sh autogen.sh
make
sudo make install

cd ../thunar/
sh autogen.sh

----
but then failed with:

mike@lic4:~/thunar/xfce4-svn-source/thunar$ sh autogen.sh
Preparing package directory /home/mike/thunar/xfce4-svn-source/thunar...
Creating /home/mike/thunar/xfce4-svn-source/thunar/aclocal.m4...
Running glib-gettextize --force --copy...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize --automake --copy --force
Patching file 'po/Makefile.in.in'
Running libtoolize --force --copy...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running gtkdocize --copy...
...

checking for exo-0.3 >= 0.3.1.1... not found
*** The required package exo-0.3 was not found on your system.
*** Please install exo-0.3 (atleast version 0.3.1.1) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.[/QUOTE]

I had the same problem....it means you had a problem with the stuff in the libexo folder....did you forget to sudo make install like I did perhaps?

Anyway...I'm loving the thunar file manager...thanks folks

---

### Post by sapo on 2005-12-08
[QUOTE=-DarkMind-]the repo have the svn version??[/QUOTE]
That repo have a very outdate version.. i dont recommend that =x

---

### Post by Cromie on 2005-12-08
Well got one major problem for a newbie, when i start the xfce now, nothing works as far as, the mouse button.. Like right click on the screen and no menu choice, plus i cant change the background image anymore. 

I was playing around the Theme section when all this happen.. 

So i really dont know how to trace the problem down can anyone help with hunting the problem down..

Its all a learning curve for me...](*,)

---

### Post by sapo on 2005-12-08
[QUOTE=Cromie]Well got one major problem for a newbie, when i start the xfce now, nothing works as far as, the mouse button.. Like right click on the screen and no menu choice, plus i cant change the background image anymore. 

I was playing around the Theme section when all this happen.. 

So i really dont know how to trace the problem down can anyone help with hunting the problem down..

Its all a learning curve for me...](*,)[/QUOTE]
just press Alt + F2 and type: xfdesktop

---

### Post by Cromie on 2005-12-08
Thanks Sapo, That worked. 

Can i asked what was that command ? 

Plus what would you recommend for getting this learing curve up the hill, so i can at least see the top of the hill. 
 

Linux really makes me feel like a Homer](*,)

---

### Post by Jeconais on 2005-12-09
I found that this:

[http://www.loculus.nl/xfce/documentation/docs-4.2/](http://www.loculus.nl/xfce/documentation/docs-4.2/)

really helped me understand what was going on...

J.

---

### Post by sapo on 2005-12-09
[QUOTE=Cromie]Thanks Sapo, That worked. 

Can i asked what was that command ? 

Plus what would you recommend for getting this learing curve up the hill, so i can at least see the top of the hill. 
 

Linux really makes me feel like a Homer](*,)[/QUOTE]
That is an app that controls your desktop stuff, you can read more about it here:
[http://www.loculus.nl/xfce/documentation/docs-4.2/xfdesktop.html](http://www.loculus.nl/xfce/documentation/docs-4.2/xfdesktop.html)

In gnome what do the same thing is nautilus, and in windows is the explorer..

So basically, it draws your wallpaper, and makes your desktop interactive..

---

### Post by mustang on 2005-12-09
[QUOTE=-DarkMind-]i have a problem :(

when i tried to open a file without association, thunar died

or when i click in "Open With" exit and says:


```
libxfce4util-CRITICAL **: simple_add_entry: assertion `locale == NULL' failed
aborting...
Abortado

```

:([/QUOTE]

I'm also having this problem.

---

### Post by psychicdragon on 2005-12-11
[QUOTE=mustang]I'm also having this problem.[/QUOTE]
I think Everyone is going to have this problem. Unless you have the svn version of Xfce installed.

---

### Post by kaamos on 2005-12-11
[QUOTE=psychicdragon]I think Everyone is going to have this problem. Unless you have the svn version of Xfce installed.[/QUOTE]

Nope, it the problem is there even with the svn version. :(
Otherwise.. whoa the never xfce from svn is cool!

---

### Post by psychicdragon on 2005-12-11
So, you have the svn version of libxfce4util on your system?

The new panel in Xfce svn is looking really nice. I was running Xfce from svn on my Hoary system, but I found the panel to be a little crashy so I went back to the stable Xfce packages when I installed Breezy. I can't wait for Xfce 4.4 to drop, it's going to be amazing :KS

Some good news: Looks like someone is making some Debian packages of Thunar, exo etc. Hopefully we'll be able to use them without any problems. [Link]("http://foo-projects.org/pipermail/thunar-dev/2005-December/001546.html")

---

### Post by sapo on 2005-12-11
[QUOTE=psychicdragon]So, you have the svn version of libxfce4util on your system?

The new panel in Xfce svn is looking really nice. I was running Xfce from svn on my Hoary system, but I found the panel to be a little crashy so I went back to the stable Xfce packages when I installed Breezy. I can't wait for Xfce 4.4 to drop, it's going to be amazing :KS

Some good news: Looks like someone is making some Debian packages of Thunar, exo etc. Hopefully we'll be able to use them without any problems. [Link]("http://foo-projects.org/pipermail/thunar-dev/2005-December/001546.html")[/QUOTE]
I ve made some debian packages too, someone could test them please?

[libexo_0.3svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/libexo_0.3svn-1_i386.deb)
[xfce4-dev-tools_4.3.1svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/xfce4-dev-tools_4.3.1svn-1_i386.deb)
[thunar_0.1.4svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/thunar_0.1.4svn-1_i386.deb)

---

### Post by j_baer on 2005-12-11
[QUOTE=sapo]I ve made some debian packages too, someone could test them please?

[libexo_0.3svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/libexo_0.3svn-1_i386.deb)
[xfce4-dev-tools_4.3.1svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/xfce4-dev-tools_4.3.1svn-1_i386.deb)
[thunar_0.1.4svn-1_i386.deb](http://xgn.com.br/fabio/ubuntu/debs/thunar_0.1.4svn-1_i386.deb)[/QUOTE]

sapo,

Installed your debs and everything is Ok ...

Thanks

---

### Post by psychicdragon on 2005-12-12
Nice work with the .deb's Sapo :cool: 

They seem to be working fine.

---

### Post by foxy123 on 2005-12-12
[QUOTE=kaamos]Nope, it the problem is there even with the svn version. :(
Otherwise.. whoa the never xfce from svn is cool![/QUOTE]
it's strange, because I am running xfce-svn as well and it works fine...

---

### Post by suoko on 2005-12-12
Hi,

does the current version of thunar support desktop icons or is it still on the "todo list"?

---

### Post by lucas on 2005-12-12
No it doesnt (mine is a week old, maybe it has changed). however xfwm 4.3 places minimized windows on the desktop. :)

---

### Post by foxy123 on 2005-12-12
[QUOTE=suoko]Hi,

does the current version of thunar support desktop icons or is it still on the "todo list"?[/QUOTE]
xffm from svn supports this feature...

---

### Post by kaamos on 2005-12-12
[QUOTE=foxy123]it's strange, because I am running xfce-svn as well and it works fine...[/QUOTE]

Thanks for letting me know!

Found out that I had an older version of libexo installed in addition to the new one. Removed that, recompiled thunar, works like a charm. :)

Does editing the shortcut keys sometimes crash xfce-mcs-manager on your system? This causes everything to start looking like gtk1-apps.. Easily solved by restarting mcs, but I was wondering if I'm the only one with this issue.

---

### Post by foxy123 on 2005-12-12
[QUOTE=kaamos]Thanks for letting me know!

Found out that I had an older version of libexo installed in addition to the new one. Removed that, recompiled thunar, works like a charm. :)

Does the editing the shortcut keys sometimes crash xfce-mcs-manager on your system? This causes to everything to start looking like gtk1-apps.. Easily solved by restarting mcs, but I was wondering if I'm the only one with this issue.[/QUOTE]
frankly speaking I do not use shortcuts... however, it looks like some changes have been recently made in the shortcuts plugin. I have not be able to compile xfce-mcs-plugins since this morning...

---

### Post by Turambar on 2005-12-13
Thunar is great, thanks for the deb-file.

Do you people know if it is possible to make the icons in Thunar smaller? The file and folder icons are huge, and I have to scroll a lot. I also wonder if it is possible yet to disable thumbnailing (and text preview) and to change the side panel to a tree view like in Nautilus?

---

### Post by jeffreyvergara.NET on 2005-12-24
Hello, I have a problem starting Thunar.
> $ thunar

Gdk-WARNING **: locale not supported by Xlib
aborting...
Aborted


---

### Post by chaumurky on 2005-12-26
I have this runnung but how do I set default file associations for thunar - and/or xfce?

---

### Post by Onos on 2006-01-08
I encountered this error when following the HOWTO:

[COLOR="DarkGreen"]me@computer:[/COLOR]~$ cd xfce4-svn-source/xfce4-dev-tools
```
[COLOR="DarkGreen"]me@computer:[/COLOR]~/xfce4-svn-source/xfce4-dev-tools$ sh autogen.sh
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
[COLOR="Red"]Makefile.am:13: require version 1.8, but have 1.4-p6[/COLOR]
[COLOR="DarkGreen"]me@computer:[/COLOR]~/xfce4-svn-source/xfce4-dev-tools$ make
[COLOR="Red"]bash: make: command not found[/COLOR]
```

And when I tried to apt-get automake:

```
[COLOR="DarkGreen"]me@computer:[/COLOR]~$ sudo apt-get install automake
Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.[/COLOR]
```


Silly newbie question # 1 -* is there a way to get automake 1.8+ ?*

My build is (x)ubuntu Breezy Badger 5.10 with Xfce 4.2, no gnome or KDE is my computer is quite old and likes a light GUI.

Silly newbie question #2 - *Where / How do I get xfce-svn?*

---

### Post by Gray. on 2006-01-08
Thanks for this HOW-TO! It's so much better than rox or xffm. And Onos, go into Synaptic and Mark automake1.8 for installation and uninstall automake1.4. and make is in there as well.

---

### Post by kaamos on 2006-01-08
[QUOTE=Onos]
Silly newbie question # 1 -* is there a way to get automake 1.8+?*[/QUOTE]

sudo apt-get install automake1.8

---

### Post by Onos on 2006-01-08
I got automake installed, but now some other wierdness I have no idea about (my apologies, I am quite new to Linux, and am a tad overwhelmed by the learning curve at the moment) :p 

I ran these lines per the wiki:
```

cd xfce4-svn-source/xfce4-dev-tools
sh autogen.sh
make
sudo make install
```

That went off without a hitch... but when I tried to do the part for libexo,
```

cd ../libexo/
sh autogen.sh
```
...

 I got this:


```
[COLOR="Green"]me@computer:[/COLOR]~/xfce4-svn-source/libexo$ sh autogen.sh
Preparing package directory /home/me/xfce4-svn-source/libexo...
Running glib-gettextize --force --copy...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

**Please add the files**
[COLOR="DarkOrange"]  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4[/COLOR]
from the[COLOR="Green"] /usr/share/aclocal[/COLOR] directory to your autoconf macro directory
or directly to your [COLOR="Green"]aclocal.m4[/COLOR] file.
You will also need [COLOR="DarkOrange"]config.guess[/COLOR] and [COLOR="DarkOrange"]config.sub[/COLOR], which you can get from
**ftp://ftp.gnu.org/pub/gnu/config/.**

Patching file 'po/Makefile.in.in'
Running libtoolize --force --copy...
Running gtkdocize --copy...
Running aclocal-1.9   -I /usr/local/share/xfce4/dev-tools/m4macros -I /usr/local/share/xfce4/dev-tools/m4macros...
Running autoheader...
Running automake-1.9 --add-missing --copy --gnu...
Running autoconf...

Running /home/me/xfce4-svn-source/libexo/configure --enable-maintainer-mode ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
[COLOR="DarkOrange"]checking whether we are using the GNU C++ compiler... no[/COLOR]
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
[COLOR="Red"]configure: error: C++ preprocessor "/lib/cpp" fails sanity check[/COLOR]
See `config.log' for more details.
```

I have a feeling that this is not a goood thing; and I am not sure how to go about moving those files (highlighted in orange) - could that break other things if I did that?

I fear for my ability to pass a sanity check at this point... :p

---

### Post by kaamos on 2006-01-08
Try installing the package "g++". That should install the GNU C++ compiler.

---

### Post by Onos on 2006-01-08
Excellent.... installing g++ did the trick.

Thanks very much!

---

### Post by Onos on 2006-01-08
I got thunar up and running, but I get this:

[IMG]http://www.kweh.net/stuff/thunar_grab.png[/IMG]

Did I miss anything in the wiki, or is there another step I need to take to "pretty it up" (such as making folders have folder icons, text files have a text file icon, etc.) ?

---

### Post by kaamos on 2006-01-08
Try changing the icon theme. Maybe the one you have does not go by the standards that thunar expects it to.. Other that that, I have no suggestions. :(

---

### Post by Onos on 2006-01-08
New twist... I tried switching around different icon themes and desktop themes hoping that something would "trigger" the correct MIME-type icons in thunar, but all to no avail.

But on the upshot, at least my wife can see the full-blown thunar in all its glory, as it installed nicely for her to use on her profile:

[IMG]http://www.kweh.net/stuff/mari_thunar.png[/IMG]

As for me, I am still totally baffled as to how to fix it on my profile... and I am not so sure that I want to try hacking Gtk+ code just yet.  There does not seem to be any configuration files for this. :???:

---

### Post by 3x3cvt0r on 2006-01-09
Hi!   I tried using Sapo's deb files and I am getting the following errors when I try to run thunar:

> Gdk-WARNING **: locale not supported by Xlib
aborting...
Aborted


Can anyone help?

---

### Post by psychicdragon on 2006-01-22
There's a new (alpha) release of Thunar out now.

[http://foo-projects.org/pipermail/thunar-dev/2006-January/001647.html](http://foo-projects.org/pipermail/thunar-dev/2006-January/001647.html)

---

### Post by psychicdragon on 2006-01-22
Whoops :rolleyes:

---

### Post by alpopel on 2006-01-22
best filemanager ever!! thanks for the howto!

---

### Post by Vinze on 2006-01-24
W007! Lazy I am indeed! Thanks for the .debs, they worked perfectly, and Thunar rocks!

---

### Post by spockrock on 2006-02-07
I followed the instructions and this works perfectly, but how did you guys get the trash, a seperator line , or increase the icon size in the left panel??

---

### Post by Vinze on 2006-02-08
[QUOTE=spockrock]I followed the instructions and this works perfectly, but how did you guys get the trash, a seperator line , or increase the icon size in the left panel??[/QUOTE]

I can't do that, I know it should be possible but I think only with the svn version.

---

