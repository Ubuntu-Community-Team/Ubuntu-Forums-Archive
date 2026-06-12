---
title: "HOWTO: Install the latest Gaim, Firefox and Xchat on warty from hoary branch."
date: 2004-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-11-08
Ok so you got warty running but you want the latest and greatest Gaim. Firefox and XChat right? Easy stuff we will install it from the hoary branch but still maintain our warty release.
     
     1. Open a terminal
     2. sudo nano /etc/apt/sources.list
     3. Change all warty references to hoary then save the file
     4. sudo apt-get update
     5. sudo apt-get install gaim xchat mozilla-firefox
     6. sudo nano /etc/apt/sources.list
     7. Change the hoary  references back to warty then save the file
     8. sudo apt-get update
    
   This worked great for me on the machines I upgraded that needed to maintain a stable release. :)

---

### Post by infornography on 2004-11-08
I'd like to do this. But I have Firefox setup with Java, Flash and the Mplayer plugin etc. Will doing this break any of those, and if so, can I fix them?

---

### Post by jdong on 2004-11-08
A slightly easier way, using Apt::Default-release

In sources.list, copy everything and paste it, so you have a duplicate. Change one of your copies as described by Ubuntu-geek (warty to hoary). Save.

Now, edit/create /etc/apt/apt.conf. Add the line **Apt::Default-Release "Warty";**

---

### Post by malte on 2004-11-08
nice tip, i needed the latest aMule and now i have it runnin :)
but i didn't understand the "Apt::Default-Release" thing...

---

### Post by Julius on 2004-11-08
May I ask what version of firefox is available on hoary? 

Anyway, the final 1.0 will be coming up tomorrow :)

---

### Post by ubuntu-geek on 2004-11-08
[QUOTE=Julius]May I ask what version of firefox is available on hoary? 

Anyway, the final 1.0 will be coming up tomorrow :)[/QUOTE]
 Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.3) Gecko/20041104 Firefox/1.0RC1 (Ubuntu) (Ubuntu package 0.99+1.0RC1-3ubuntu1)

---

### Post by Julius on 2004-11-08
Do I have to install all the dependencies? !_!

Se instalarán los siguientes paquetes extras:
  libgcrypt11 libglib2.0-0 libglib2.0-data libglib2.0-dev libgnutls11 libgpg-error-dev libgpg-error0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtk2.0-dev libopencdk8 libopencdk8-dev libperl5.8 libpng12-0 libpng12-dev libstartup-notification0 libtasn1-2 libtasn1-2-dev perl perl-base
  perl-modules
Paquetes sugeridos:
  libzephyr3 libglib2.0-doc gnutls-bin libgtk2.0-doc perl-doc libterm-readline-perl-perl
Se instalarán los siguientes paquetes NUEVOS:
  libgcrypt11 libgnutls11
Se actualizarán los siguientes paquetes:
  gaim libglib2.0-0 libglib2.0-data libglib2.0-dev libgpg-error-dev libgpg-error0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libopencdk8
  libopencdk8-dev libperl5.8 libpng12-0 libpng12-dev libstartup-notification0 libtasn1-2 libtasn1-2-dev perl perl-base perl-modules

---

### Post by allen on 2004-11-08
if you do it the way explained in [post=13000]this post[/post] then it will grab all the dependencies for you when you go to install it.

---

### Post by Artiom on 2004-11-09
Do I need to remove those programs , before I install new version of them?

---

### Post by marsopia on 2004-11-09
I installed Firefox, Gaim and Thunderbird adding hoary branch to Synaptic, and unmarking Warty&#347; repositories.

Gaim and Thunderbird worked fine, but Firefox gives me this message on a window titled Gecko:

acceskey="&allowPopups.accesskey;"

and then, nothing more happens, and I dont know how to allow Poppups if Firefox does not start.

I wasnt able to downgrade forefox via Synaptic, so i installed Mozilla to acces the web

Is it possible to do that?

Thanks
Mariano

---

### Post by puzzledm on 2004-11-18
[QUOTE=marsopia]I installed Firefox, Gaim and Thunderbird adding hoary branch to Synaptic, and unmarking Warty&#347; repositories.

Gaim and Thunderbird worked fine, but Firefox gives me this message on a window titled Gecko:

acceskey="&allowPopups.accesskey;"

and then, nothing more happens, and I dont know how to allow Poppups if Firefox does not start.

I wasnt able to downgrade forefox via Synaptic, so i installed Mozilla to acces the web

Is it possible to do that?

Thanks
Mariano[/QUOTE]
 I followed the instructions as above to install just firefox which seemed to work fine.  However when I turned the computer back on this morning X has troubles starting and I had to reconfigure Xserver-xfree86 and then delete /tmp/X0 something and 'startx'.

What has happened and how can I return it to it's stable state?

Also is there a way to return Ubuntu to it's original install state from CD without losing the contents of my home-file or the programs I have installed i.e. just system files!

---

### Post by Torben Linde on 2004-11-20
[QUOTE=puzzledm]I followed the instructions as above to install just firefox which seemed to work fine.  However when I turned the computer back on this morning X has troubles starting and I had to reconfigure Xserver-xfree86 and then delete /tmp/X0 something and 'startx'.

What has happened and how can I return it to it's stable state?[/QUOTE]


The same thing happen for me  :-?

---

### Post by Arnb on 2004-11-20
Same here. All I get is an X on the screen. Could someone please post instructions a Linux noobie can understand. 

Thanks
Arn

---

### Post by rbrimhall on 2004-11-20
You guys may be running hoary now... updating firefox will pull in  the hoary deps which would include xorg and all other hoary packages.

---

### Post by puzzledm on 2004-11-22
Is there a way of returning to warty?

---

### Post by rbrimhall on 2004-11-22
[QUOTE=puzzledm]Is there a way of returning to warty?[/QUOTE]
 You may not be running Hoary but when I tried this it seemed as if apt going to pull down a ton of deps just for mozilla-firefox which in debian has only one (libpng >= 1.2.7). I found it easier to just install firefox from mozilla.org and redo the synlinks to point to my installed version... while maintaining a "stable" warty...

---

### Post by puzzledm on 2004-11-22
Ahhhh hindsight is a beautiful thing!  

So there is no way, now I have messed up the system, of returning it to a 'stable' warty release?

---

### Post by DriftSK on 2004-11-26
I'm not sure it will work 100% but, if I were in you, I'd try this:

- set apt sources to warty
- sudo apt-get remove the updated "hoaryfied" applications you installed
- do a complete dist-upgrade to warty to try and fix all dependencies.

---

### Post by anklator on 2004-11-26
i prefer to compile myself this few apps, as i am newbye, the problem i have is that i dont know how to unisnstall programas that werent installed from a .deb file

---

### Post by LLucas7086 on 2004-11-28
[QUOTE=rbrimhall]You may not be running Hoary but when I tried this it seemed as if apt going to pull down a ton of deps just for mozilla-firefox which in debian has only one (libpng >= 1.2.7). I found it easier to just install firefox from mozilla.org and redo the synlinks to point to my installed version... while maintaining a "stable" warty...[/QUOTE]

agreed...

i had those same problems as others with X...two different machines, so its not a limited problem.  instead, downloaded latest firefox debs and libpng out of the Debian Sid branch, and installed.  works excellent...

---

### Post by tymark on 2004-11-29
[QUOTE=anklator]i prefer to compile myself this few apps, as i am newbye, the problem i have is that i dont know how to unisnstall programas that werent installed from a .deb file[/QUOTE]
If you installed it from source, just grab the source again, do the same ./configure as you did before (same arguements - i often use the --prefix=/usr option, but that's just a personal preference) and then "make uninstall"

be  careful, this won't check to see if any deps will break if you do it.  but for simple programs like xchat, etc. you should be fine.

---

### Post by mikeymike on 2004-12-03
this should be locked or topic changed cause it can mess up ur pc and not everybody is gonna look at the second page :)

---

### Post by jazzorist on 2004-12-04
I also installed Firefox from Hoary and had the problem with GDM. (X server did start but GDM had problems) My guess was that one (or more) of the Firefox dependencies was also needed by GDM and I messed it up with the upgrade, so I upgraded GDM and after that everything was back to normal...

..J..

---

### Post by wallijonn on 2004-12-22
If you download the Firefox Linux binary file from the Mozilla site, unzip and install it, it installs just like a Windows installer but installs all the files in your /home/<username> directory. 

You might be able to work with it, BUT **[COLOR=Red]if you try to uninstall it[/COLOR]** (usually by re-installing it and telling it to unistall the "old" installation (not the original 9.3) **[COLOR=Red]it will delete all your files[/COLOR]** (documents, user directories, etc). 

**This is very destructive!!!** to say the least. 

**[COLOR=Red]Make sure you you backup all your files to a CDR before uninstalling Firefox with this method[/COLOR].**

---

### Post by YorHel on 2004-12-27
well.... I'm happy to have Firefox 1.0, but gdm broke...

[QUOTE=DriftSK]I'm not sure it will work 100% but, if I were in you, I'd try this:

- set apt sources to warty
- sudo apt-get remove the updated "hoaryfied" applications you installed
- do a complete dist-upgrade to warty to try and fix all dependencies.[/QUOTE]

tried that, but I couldn't remove all the updated pagackes (that would remove more than 100 packages, all those depencies :( )
anyone succeed in fixing this?

---

### Post by node on 2004-12-27
Ok, so I got screwed with the Xserver too :/
Have to login a new shell, rm -rf /tmp/.X0-lock and startx again.
Figured I'd apt-get remove the three packages, and re-install from warty sources.
Now apt wants the CD which I havent got here sigh...
So iv'e adjusted the apt sources to hoary again and reinstalled the three packages.
Figured something is fubar right now so might as well upgrade to hoary all the way, till I get my CD tomorrow ;)
Perhaps a note in the first post that this CAN wreck ur set-up ? ;)

---

### Post by kral on 2004-12-31
personally, for FF1.0, i used an ubuntu backport, and it run like a charm:

## Warty backports
deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

---

### Post by wallijonn on 2004-12-31
Thanks, Kral.

I downloaded & installed [COLOR=Red]mozilla-firefox_1.0-2ubuntu4-warty99_i386.deb[/COLOR]. I'll have to test everything though. 

Now I almost wish I hadn't, I miss the "Undoclosedtab", "Cookie Culler" extensions.

The DOM has to be installed separatedly. Presently there is no way to do this.

I see no advantage to updating Fire Fox from 0.93 to 1.0.

---

### Post by ubuntunoob on 2005-01-13
[QUOTE=ubuntu-geek]Ok so you got warty running but you want the latest and greatest Gaim. Firefox and XChat right? Easy stuff we will install it from the hoary branch but still maintain our warty release.
     
     1. Open a terminal
     2. sudo nano /etc/apt/sources.list
     3. Change all warty references to hoary then save the file
     4. sudo apt-get update
     5. sudo apt-get install gaim xchat mozilla-firefox
     6. sudo nano /etc/apt/sources.list
     7. Change the hoary  references back to warty then save the file
     8. sudo apt-get update
    
   This worked great for me on the machines I upgraded that needed to maintain a stable release. :)[/QUOTE]

sorry for the noobish question but how to do step 3??

---

### Post by akurashy on 2005-01-24
can i update my kernel to hoary latest one without a problem? or do i need to stick with warty updates?

---

### Post by Madman on 2005-06-04
[QUOTE=ubuntunoob]sorry for the noobish question but how to do step 3??[/QUOTE]
 Change Step 2 and Step 6 to:
sudo gedit /etc/apt/sources.list

Now you have a text editor with menus to edit the file - simply click Search, then replace, type warty in 'Find' and hoary in 'Replace' then click Replace All - reverse the two names for Step 6. Click save and then exit (to regain control of the terminal)

---

