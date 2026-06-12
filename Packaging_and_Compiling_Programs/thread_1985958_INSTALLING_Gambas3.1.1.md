---
title: "INSTALLING Gambas3.1.1"
date: 2012-05-24
forum: Packaging and Compiling Programs
---

### Post by JASONFUSARO on 2012-05-24
[LEFT][RIGHT][CENTER][LEFT]Download [COLOR="orange"]*gambas3-3.1.1.tar.bz2*[/COLOR] from the following site 
[COLOR="orange"][http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)[/COLOR]

copy [COLOR="Orange"]*gambas3-3.1.1.tar.bz2*[/COLOR] to a folder [COLOR="Blue"]/src[/COLOR] created by you in your home folder
or copy it from your download folder either by terminal commands or using a file manager.

open up a terminal and from root ie. type [COLOR="blue"][COLOR="blue"]cd /[/COLOR][/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR] to get there then type [COLOR="blue"]cd /home/<your name>[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]

[COLOR="blue"]cp[/COLOR] Downloads/gambas3-3.1.1.tar.bz2 [COLOR="blue"]src/[/COLOR] or copy it there using a file manager

go to this site [COLOR="Orange"][http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html) [/COLOR]to get the list of development packages
you should have installed for your distro, this was my list yours may be different

For Natty: 
[COLOR="Navy"]sudo apt-get install build-essential autoconf libbz2-dev libfbclient2 libmysqlclient-dev unixodbc-dev libpq-dev libsqlite0-dev libsqlite3-dev libgtk2.0-dev libldap2-dev libcurl4-gnutls-dev libgtkglext1-dev libpcre3-dev libsdl-sound1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsage-dev libxml2-dev libxslt1-dev libbonobo2-dev libcos4-dev libomniorb4-dev librsvg2-dev libpoppler-dev libpoppler-glib-dev libasound2-dev libesd0-dev libdirectfb-dev libaa1-dev libxtst-dev libffi-dev kdelibs4-dev firebird2.1-dev libqt4-dev libglew1.5-dev libimlib2-dev libv4l-dev libsdl-ttf2.0-dev libgnome-keyring-dev libgdk-pixbuf2.0-dev linux-libc-dev[/COLOR]

open another terminal copy and paste it and [COLOR="DeepSkyBlue"]<enter>[/COLOR]

when complete

In the other terminal type 
	[COLOR="blue"]cd src[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	[COLOR="blue"]ls[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
        you should see     gambas3-3.1.1.tar.bz2
	type [COLOR="blue"]tar -jxf gambas3-3.1.1.tar.bz2[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	type [COLOR="blue"]cd gambas3-3.1.1[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	type [COLOR="blue"]reconf-all[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	when it finishes type [COLOR="blue"]configure -C[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	when it finishes if there were no errors type [COLOR="Blue"]make[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	when it finishes type [COLOR="blue"]sudo make install[/COLOR] [COLOR="DeepSkyBlue"]<enter>[/COLOR]
	type [COLOR="blue"]gambas3[/COLOR] and you should be all set!!!![/LEFT][/CENTER][/RIGHT][/LEFT]

---

### Post by wamukota on 2012-05-31
I have a strange problem running Gambas 3.1.1 under Precise that I did not have when running Gambas 3.1.1 under Oneiric.

I installed the 3.1.1 using the PPA ppa:nemh/gambas3 as I did under Oneiric. All went fine.

The problem I have is when I use the double quotes to delimited a string. The cursor moves one space to the right and is offset for the rest of the string. That makes it almost impossible to know where you are typing in the string. It is a real PITA when typing my SQL statements. If I cannot solve this problem I'll have to revert back to Oneiric :(

I use the Dutch language and the 'US keyboard'

I think the problem is somewhere upstream as I have encountered the same problem with Mint 13.

Any hints?

---

