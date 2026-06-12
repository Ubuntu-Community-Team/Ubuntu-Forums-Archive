---
title: "HOWTO: Gaim 2.0 CVS - .deb inside"
date: 2005-12-08
forum: Outdated Tutorials &amp; Tips
---

### Post by sapo on 2005-12-08
Yo fellows.. i m very happy today.. i ve been waiting for the new release of gaim for a long time, tough it isnt released yet, i just compiled the cvs version, and its great, so as i m a good guy and now i m in a good mood i m writing this quick guide to help you install gaim 2.0 from cvs, or if your lazy just got my .deb.

Screenshot:
[[IMG]http://img213.imageshack.us/img213/4939/gaim204fq.th.jpg[/IMG]](http://img213.imageshack.us/my.php?image=gaim204fq.jpg)

First of all, remove your gaim 1.5:

```
sudo apt-get remove gaim
```

Dont mind about the ubuntu-desktop, kubuntu-desktop, or kubuntu-desktop, they are just meta packages.

if you want to use MSN, do this:

```
sudo apt-get install libgnutls11-dev
```

I dont know ALL the dependencies, so if you miss something, post here so we can find out what is missing, i had everything except the libgnutls above.

If you are lazy, just grab the deb:

[http://xgn.com.br/fabio/gaim_2.0.0cvs2-1_i386.deb](http://xgn.com.br/fabio/gaim_2.0.0cvs2-1_i386.deb)

if you want to compile yourself, here we go:

ps: Ripped from: [http://gaim.sourceforge.net/downloads.php](http://gaim.sourceforge.net/downloads.php)

**Step 1. Check out the source**

Run the following commands in a directory that you have write access to (such as your home directory):

```
cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' login
(Just hit enter for the password)
cvs -z3 -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' checkout gaim
```

You should see it listing all the source files.

**Step 2. Build again**

Once you've checked gaim out of CVS, run the follwing commands:

```
cd gaim
sh autogen.sh
./configure --enable-gnutls=yes
```

If you see any errors here, you haven't installed everything you need. autogen.sh will also run ./configure for you once it's created, if it's created successfully. If you see any errors related to GLib or GTK, you haven't installed the devel packages.

Now, type:

```

make
sudo make install
```

Tip: if you want to create a deb and install it instead of the make install, dont type sudo make install, instead type this:

```
sudo apt-get install checkinstall
```

The type:

```
sudo checkinstall
```

it you ask you to fill some information, fill them out, and it will install the deb.

**Now some tips by bored2k:**

If you want to enable sounds in gaim, do this:

```
sudo apt-get install esound-clients
```

Now in the sound preferences of you gaim, chose metod: command, and fill the command field with: esdplay %s

**Sugestions by foxy123:**

If you want sound support, you need libao:

```
sudo apt-get install libao-dev
```

If you need spellchecking support, you need libgtkspell:

```
sudo apt-get install libgtkspell-dev
```

Enjoy :)

---

### Post by Turtle.net on 2005-12-09
Don't you need to do ```
./autogen.sh
``` before ./configure ?

---

### Post by sal on 2005-12-09
dose this version include the gaim-vv to do audio chats with msn,yahoo,googletalk?

---

### Post by lizardking on 2005-12-09
some screen or list of new features?

---

### Post by foxy123 on 2005-12-09
libgnutls10-dev wants to remove a lot of KDE dev packages which are used to build amarok from svn :(

---

### Post by foxy123 on 2005-12-09
OK, several suggestions:

1. 
> if you want to use MSN, do this:
Code:
sudo apt-get install libgnutls10-dev

Ubuntu official package is libgnutls11, you do not need 10. So do 
```
sudo apt-get install libgnutls11-dev
```
2. If you want sound support, you need libao:
```
sudo apt-get install libao-dev
```
3. If you need spellchecking support, you need libgtkspell:
```
sudo apt-get install libgtkspell-dev
```

---

### Post by sapo on 2005-12-09
Thanx guys, i ll add those to the howto :)

I dont know if you need to type autogen.sh first before the ./configure, do you need it?

---

### Post by SirKillalot on 2005-12-09
Gaim 2.0 is great! waiting for the official release..

---

### Post by doclivingston on 2005-12-09
[QUOTE=sapo]I dont know if you need to type autogen.sh first before the ./configure, do you need it?[/QUOTE]

You should always (re-)run autogen.sh when you first get or later update something from cvs (or equivalent). Not doing that can cause problems when compiling.

---

### Post by foxy123 on 2005-12-09
[QUOTE=sapo]Thanx guys, i ll add those to the howto :)

I dont know if you need to type autogen.sh first before the ./configure, do you need it?[/QUOTE]
yes, you need. also you do not need ./configure, just put all options after ./autogen.sh like:

```
./autogen.sh --enable-gnutls=yes
```

---

### Post by raublekick on 2005-12-09
can you provide some uninstall instructions incase something should be not working?

gaim is crashing on me a lot right now though, so i'm definitely gonna give this a shot

---

### Post by sapo on 2005-12-09
[QUOTE=raublekick]can you provide some uninstall instructions incase something should be not working?

gaim is crashing on me a lot right now though, so i'm definitely gonna give this a shot[/QUOTE]
unistall gaim 2.0 after installed you mean?

if you installed the deb just use 

```
sudo dpkg -r gaim
```

if you installed using make install, just enter the gaim folder that the cvs creater and type 

```
sudo make uninstall
```

---

### Post by christooss on 2005-12-09
Why gaim has to be uninstalled?

---

### Post by arpunk on 2005-12-09
[QUOTE=christooss]Why gaim has to be uninstalled?[/QUOTE]
To avoid errors with already installed files mostly, since gaim 2 and gaim will install in the same locations, you can just compile gaim 2 and leave it on ~/gaim2/ and run it from there, that will avoid installation and you can test it without problems.

---

### Post by christooss on 2005-12-09
Can someone else provide package which will install gaim2 beacause now when I run apt-get upgrade gaim gets rewriten with 1.1.5

I used deb provided by sapo

---

### Post by christooss on 2005-12-09
And MSN with sapo's deb doesnt work

I get support for ssl missing error

---

### Post by akurashy on 2005-12-09
Well I was planning to do this HOWTO but I guess sapo got faster than me xD, anyway I can provide this deb package I did 2 days ago around [http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb](http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb) 

It supose to have MSN support, (because I can use msn)

---

### Post by sapo on 2005-12-09
[QUOTE=christooss]And MSN with sapo's deb doesnt work

I get support for ssl missing error[/QUOTE]
You need to install the libgnutls11-dev to use MSN, try installing it, if it still doest work, try install the libgnutls10-dev.

good luck

---

### Post by bored2k on 2005-12-09
Though sapo's deb works ok, if I'm using aim and I try to change my status/displayed info, it disconnects and reconnects.. with the old status. It happened so much when i tried i even got a "disabled account for 10mins".

---

### Post by welsh_spud on 2005-12-09
Ignore post...

---

### Post by limit223 on 2005-12-09
This how-to I was lazzy.. just installed sap's .deb and I enjoy it . Thank you :)
 I'm wondering if there is way to be included in the package that plugin guifications and some theme as well..

---

### Post by raublekick on 2005-12-09
for some reason when i installed this i got two awat message things at the bottom of my buddy list instead of one. one of them had my screen name and the other didn't but they both affected my status. 

all in all i really don't like the new "all in one" functionality too much. and isn't gaim 2.0 supposed to have uPnP/NAT translation? i still can't send and recieve files :(

---

### Post by christooss on 2005-12-09
Akurashy thanks for the deb. It works fine now. And no problems with upgrade

Thanks sapo for this owto. I love new GAIM. Can any one tell me what have changed. Is there a list of changes?

Bye

---

### Post by akurashy on 2005-12-09
[quote=christooss]Akurashy thanks for the deb. It works fine now. And no problems with upgrade

Thanks sapo for this owto. I love new GAIM. Can any one tell me what have changed. Is there a list of changes?

Bye[/quote]

No probs!

---

### Post by gold4tune on 2005-12-09
Thx, everything worked fine for me.  Just want to try it now. :razz:

---

### Post by Jormundgand on 2005-12-09
When I tried to install the DEB provided by sapo it seemed to install correctly, no bugs reported, but when I actually ran up Gaim I was greeted by a window appearing momentarily and them closing abruptly. No data was lost and I was able to revert with no loss of functionality. Could anyone suggest a course of action to provide more information on the nature of this crash?

---

### Post by akurashy on 2005-12-09
[quote=Jormundgand]When I tried to install the DEB provided by sapo it seemed to install correctly, no bugs reported, but when I actually ran up Gaim I was greeted by a window appearing momentarily and them closing abruptly. No data was lost and I was able to revert with no loss of functionality. Could anyone suggest a course of action to provide more information on the nature of this crash?[/quote]
Have you tried opening it again?

---

### Post by Jormundgand on 2005-12-09
Yep, tried opening it multiple times to the same response. Opens a window, opens a second window and then abruptly dies. I'd even have been glad for a Windows-style "this application has crashed" box just to let me know I'm still here!

---

### Post by curtis on 2005-12-09
Works fine here.
I tried the deb attached and compiling it my self, both worked :)

---

### Post by Jormundgand on 2005-12-09
Odd. I installed again and it worked. Switching to the correct libgnutls corrects the SSL error.

Now how do I stop the upgrade program "upgrading" to the older version?

---

### Post by keybreckaba on 2005-12-09
to stop the update thing you can open synaptic and highlight the package and from the package menu pick lock version.

---

### Post by christooss on 2005-12-09
Jormundgand: Just use akurashys deb file

I had both problems fixed with one deb

Bye

My friend is asking if amd94 deb could be build. I there is any good soul out there please build one :)

---

### Post by Turtle.net on 2005-12-09
I followed step by step your howto but :(
I have the following problem when I do ```
$make
(...)
../libtool: line 1654: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
make[3]: *** [gaim] Erreur 1
(...)

```

Do you have any idea ???
:confused:

---

### Post by Chrissss on 2005-12-09
Works like a charm. Thanks for the hint!

Finally no annoying login window!
Saves last status as startup status!
etc...

Looking forward for the final version :)

---

### Post by MighMoS on 2005-12-09
[QUOTE=christooss]Jormundgand: Just use akurashys deb file

I had both problems fixed with one deb

Bye

My friend is asking if amd94 deb could be build. I there is any good soul out there please build one :)[/QUOTE]
If you mean amd**6**4 then I'm working on one that doesn't crash :-\

---

### Post by foxy123 on 2005-12-10
[QUOTE=Turtle.net]I followed step by step your howto but :(
I have the following problem when I do ```
$make
(...)
../libtool: line 1654: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
make[3]: *** [gaim] Erreur 1
(...)

```

Do you have any idea ???
:confused:[/QUOTE]
you have libtool installed, haven't you?

---

### Post by rwabel on 2005-12-10
thanks for the deb files. I'm on dapper and for me akurashy's deb file works fine. For the other I also get the SSL problem. Probably it would work when I install libgnutls-dev, but it would remove some other -dev files from the system at the moment.

---

### Post by MBro on 2005-12-10
Is anyone else not a fan of the new interface?  If you're connected on many accounts those buttons on the bottom get annoying.  Also if you are scrolling down your buddy list and you accidently go over one of the status buttons it'll switch your status.  Hmm, not liking this so far.

---

### Post by Turtle.net on 2005-12-10
[quote=foxy123]you have libtool installed, haven't you?[/quote]
Yes I have ```
$ sudo aptitude search libtool
iB  libtool                         - Generic library support script
p   libtool-doc                     - Generic library support script
p   libtool1.4                      - Generic library support script (obsolete
p   libtool1.4-doc                  - Generic library support script (obsolete

``` That's why I do not understand why the "make" failed...

---

### Post by bored2k on 2005-12-10
[QUOTE=Turtle.net]Yes I have ```
$ sudo aptitude search libtool
iB  libtool                         - Generic library support script
p   libtool-doc                     - Generic library support script
p   libtool1.4                      - Generic library support script (obsolete
p   libtool1.4-doc                  - Generic library support script (obsolete

``` That's why I do not understand why the "make" failed...[/QUOTE]
What about the -dev libtool?

---

### Post by foxy123 on 2005-12-10
[QUOTE=bored2k]What about the -dev libtool?[/QUOTE]
there is no dev for libtools...
what version of automake do you use?

---

### Post by sapo on 2005-12-10
I ve updated the .deb, compiled with aspell, libao and gnutls11, hope it works now.

Give me a feedback if you install it please :)

---

### Post by vtechstu on 2005-12-10
So, as it seems the people mentioning this so far have been ignored, is there anyway to remove the two gigantic buttons for away status on the bottum of the screen.

Thanks

If there is no way, How do I remove 2.0?  I have tried apt-get'ting gaim(1.5) but it installs and when i click the icon 2.0 still loads, so nothing seems to be overwritten.  Thanks.

---

### Post by christooss on 2005-12-10
sudo dpkg -r gaim should do the work

---

### Post by sapo on 2005-12-10
[QUOTE=vtechstu]So, as it seems the people mentioning this so far have been ignored, is there anyway to remove the two gigantic buttons for away status on the bottum of the screen.

Thanks

If there is no way, How do I remove 2.0?  I have tried apt-get'ting gaim(1.5) but it installs and when i click the icon 2.0 still loads, so nothing seems to be overwritten.  Thanks.[/QUOTE]
I dont know how to remove that gigantic button :(

And to remove it, if you installed my deb, just type:

```
sudo dpkg -r gaim
```

if you compile and used make install, just enter the gaim directory (the source that you downloaed using cvs) and type:

```
sudo make uninstall
```

---

### Post by vtechstu on 2005-12-10
Thank you for the replies. 

I'm not sure whose deb I used, one of the ones in this thread( not the first post, that does not work).  

But in any case, using sudo dpkg -r gaim gives the following error/warning.  

```
chase@ubuntu:~$ sudo dpkg -r gaim
dpkg - warning: ignoring request to remove gaim, only the config
 files of which are on the system.  Use --purge to remove them too.
chase@ubuntu:~$
```

---

### Post by sapo on 2005-12-10
[QUOTE=vtechstu]Thank you for the replies. 

I'm not sure whose deb I used, one of the ones in this thread( not the first post, that does not work).  

But in any case, using sudo dpkg -r gaim gives the following error/warning.  

```
chase@ubuntu:~$ sudo dpkg -r gaim
dpkg - warning: ignoring request to remove gaim, only the config
 files of which are on the system.  Use --purge to remove them too.
chase@ubuntu:~$
```[/QUOTE]
It seems that you dont have a deb package of gaim installed, try using sudo make uninstall from the gaim cvs folder

---

### Post by Turtle.net on 2005-12-10
[quote=foxy123]there is no dev for libtools...
what version of automake do you use?[/quote]
I used automake1.4, I will try the same procedure with automake1.9
....

---

### Post by rwabel on 2005-12-10
[quote=MBro]Is anyone else not a fan of the new interface?  If you're connected on many accounts those buttons on the bottom get annoying.  Also if you are scrolling down your buddy list and you accidently go over one of the status buttons it'll switch your status.  Hmm, not liking this so far.[/quote]

yeah it takes a lot of space to display the state of the different messenger

---

### Post by MicroChris on 2005-12-10
This is what I get:

```
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GLIB is incorrectly installed.configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/.
```

What actual package(s) do I have to grab? Thanks in advance.

---

### Post by MicroChris on 2005-12-10
Crap now what did I do...


```
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.9.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

Help!

---

### Post by MicroChris on 2005-12-10
Alright nevermind, I got rid of it.. How do I remove the directory from my desktop now?

sudo rm /gaim

doesnt work.

:(

---

### Post by sapo on 2005-12-10
[QUOTE=MicroChris]Alright nevermind, I got rid of it.. How do I remove the directory from my desktop now?

sudo rm /gaim

doesnt work.

:([/QUOTE]
rm -Rf gaim

---

### Post by MicroChris on 2005-12-10
Cool thanks man.

---

### Post by viscount on 2005-12-11
[QUOTE=foxy123]OK, several suggestions:

1. 

Ubuntu official package is libgnutls11, you do not need 10. So do 
```
sudo apt-get install libgnutls11-dev
```
2. If you want sound support, you need libao:
```
sudo apt-get install libao-dev
```
3. If you need spellchecking support, you need libgtkspell:
```
sudo apt-get install libgtkspell-dev
```[/QUOTE]


That worked for me, thanks foxy123 :KS 
..yeah, gaim2 is pretty nice.
But now synaptic keeps wanting to reinstall gaim1.5 :???: 
There must be some way to mask that version of gaim, but
Im too new to ubuntu to know how yet. meh.

---

### Post by foxy123 on 2005-12-11
[QUOTE=viscount]That worked for me, thanks foxy123 :KS 
..yeah, gaim2 is pretty nice.
But now synaptic keeps wanting to reinstall gaim1.5 :???: 
There must be some way to mask that version of gaim, but
Im too new to ubuntu to know how yet. meh.[/QUOTE]
if you use checkinstall, than when you see the 
```
This package will be built according to these values:
```
hit 3 and enter something like
```
2:2.0.0.0cvs
```

The easier way would be to 'lock' the version in Synaptic.

---

### Post by foxy123 on 2005-12-11
[QUOTE=Turtle.net]I used automake1.4, I will try the same procedure with automake1.9
....[/QUOTE]
please let us know the results....

---

### Post by SirKillalot on 2005-12-11
anyone got an idea how often the cvs repo gets updated? I found some unimportant bugs, and I wonder if they get fixed or whether I should try to fix them by myself :-/

---

### Post by foxy123 on 2005-12-11
[QUOTE=SirKillalot]anyone got an idea how often the cvs repo gets updated? I found some unimportant bugs, and I wonder if they get fixed or whether I should try to fix them by myself :-/[/QUOTE]
I guess it is constantly ubdated...

---

### Post by Chrissss on 2005-12-11
Hi there!

I can compile gaim 2.0 cvs gaim, but when i try to start it i get this error, and gaim wont start:

# gaim
*** glibc detected *** free(): invalid pointer: 0xb766a684 ***

Any ideas?

CU
 CHristoph

---

### Post by akurashy on 2005-12-11
[quote=Chrissss]Hi there!

I can compile gaim 2.0 cvs gaim, but when i try to start it i get this error, and gaim wont start:

# gaim
*** glibc detected *** free(): invalid pointer: 0xb766a684 ***

Any ideas?

CU
 CHristoph[/quote]

yea i got the same thing, (while trying to add gtkspell support and audio)
im trying to figure it out :)

---

### Post by Turtle.net on 2005-12-11
[quote=foxy123]please let us know the results....[/quote]
You know what...
That worked :D
Thanks for your help

---

### Post by Heliode on 2005-12-11
[QUOTE=akurashy]yea i got the same thing, (while trying to add gtkspell support and audio)
im trying to figure it out :)[/QUOTE]

Using your .deb right now... it's great, but it would be even greater if you managed to add those things. 

Keep up the good work!

---

### Post by curtis on 2005-12-11
Anyone had any luck with having sound in gAIM 2.x, when you use ALSA and not ESD?

---

### Post by monkeyface on 2005-12-11
Which packages do I need to install to enable video/voice support?

---

### Post by monkeyface on 2005-12-11
[QUOTE=curtis]Anyone had any luck with having sound in gAIM 2.x, when you use ALSA and not ESD?[/QUOTE]
Install sox, and use command "play %s" for playing sounds.

---

### Post by Chrissss on 2005-12-11
[QUOTE=akurashy]yea i got the same thing, (while trying to add gtkspell support and audio) im trying to figure it out :)[/QUOTE]
Ah, great, well not soo great. But at least it's not me screwing up the compilation... ;)

---

### Post by sapo on 2005-12-11
i ve changed my deb yesterday, and it now has gtkspell and audio support, try it out :P

---

### Post by Pedricko on 2005-12-11
Rah when will Gaim-VV be implemented dammit

---

### Post by curtis on 2005-12-11
My favourite bit(s) of gAIM 2.x are the buddy list with the status choosers and secondly the message windows, removing the send,block etc makes it a lot cleaner.
Scrolling down is nice as well, can't wait till they get Gaim-VV merged into it though...

---

### Post by sapo on 2005-12-11
[QUOTE=Pedricko]Rah when will Gaim-VV be implemented dammit[/QUOTE]
Dunno, but i want it too :(

---

### Post by rwabel on 2005-12-11
[quote=sapo]i ve changed my deb yesterday, and it now has gtkspell and audio support, try it out :P[/quote]

thanks a lot for it!

---

### Post by sapo on 2005-12-11
[QUOTE=rwabel]thanks a lot for it![/QUOTE]
Did it work how it is supposed to?

---

### Post by akurashy on 2005-12-11
[quote=Heliode]Using your .deb right now... it's great, but it would be even greater if you managed to add those things. 

Keep up the good work![/quote]

thanks a lot guys, i try to figure it out and fix the download link soon :)

---

### Post by MBro on 2005-12-11
[QUOTE=sapo]i ve changed my deb yesterday, and it now has gtkspell and audio support, try it out :P[/QUOTE]
Nice, I like it better

---

### Post by akurashy on 2005-12-11
For everyone here, I have updated my deb package, 

[http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb](http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb)

Now with Spell support and Audio

Output:

gaim 2.0.0cvs

Build Protocol Plugins........ : yes
Protocols to link statically.. :
Protocols to build dynamically : gg irc jabber msn novell oscar sametime simple yahoo zephyr

UI Library.................... : GTK+ 2.x
SSL Library/Libraries......... : Mozilla NSS and GNUTLS

Build with Plugin support..... : yes
Build with Mono support....... : yes
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : yes
Build with Audio support...... : yes
Build with GtkSpell support... : yes
Build with Voice/Video support : no
Build with DBUS support....... : no
Has you....................... : yes

Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification.......: yes

Print debugging messages...... : no


Also a tip for sapo, to add documentation support

sudo apt-get install doxygen doxygen-docs , if you knew well my bad, just thought it would be handy :)

---

### Post by i3dmaster on 2005-12-11
Great work both of your guys! Its awesome.

---

### Post by Kevin on 2005-12-12
> For everyone here, I have updated my deb package,

[http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb](http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb)

Now with Spell support and Audio

Using this .deb I now get that same earlier reported error... back to using the old one for now I guess ;) 

```
*** glibc detected *** free(): invalid pointer: 0xb7485684 ***
Aborted
```

---

### Post by Chrissss on 2005-12-12
Yep, i also get this error

*** glibc detected *** free(): invalid pointer: 0xb749e684 ***

is there a lib missing??

---

### Post by pomalin on 2005-12-12
*** glibc detected *** free(): invalid pointer: 0xb749e684 ***

I compil gaimcvs for a month now, each days, and this error comes when I have libmono, I have to remove beagle, and of course libmono to have gaim run without this error. I did a backtrace before, and it's mono that cause this error. (for me)
I have voice and video support enable, but no buttons, and nowhere to play with, I think it's enable, but not completely implemented.

---

### Post by Chrissss on 2005-12-12
Yep, you are right. When i deinstall libmono0 (and beagle, f-spot...) the current version starts...

---

### Post by akurashy on 2005-12-12
[quote=pomalin]*** glibc detected *** free(): invalid pointer: 0xb749e684 ***

I compil gaimcvs for a month now, each days, and this error comes when I have libmono, I have to remove beagle, and of course libmono to have gaim run without this error. I did a backtrace before, and it's mono that cause this error. (for me)
I have voice and video support enable, but no buttons, and nowhere to play with, I think it's enable, but not completely implemented.[/quote]

ohh how you enable voice/video support?, about the glib.. you guys got me there.., i had that error but somehow it got fixed.

---

### Post by Karma_Police on 2005-12-12
You can install the last one, and then do:
```
sudo rm /usr/local/lib/gaim/mono.*
```

No need to uninstall libmono and mono programs.

---

### Post by Chrissss on 2005-12-12
[QUOTE=Karma_Police]No need to uninstall libmono and mono programs.[/QUOTE]
Yes, this works. Thanks!

---

### Post by pomalin on 2005-12-12
to enable voice and video I install from source linphone/ilbc/speex.
and configure with --enable-vv.
thanks for the mono thing ;)

---

### Post by rwabel on 2005-12-12
[quote=sapo]Did it work how it is supposed to?[/quote]

yep spellchecker is working for me, but sound doesn't. but maybe gaim uses the wrong output device

---

### Post by MBro on 2005-12-12
[QUOTE=pomalin]to enable voice and video I install from source linphone/ilbc/speex.
and configure with --enable-vv.
thanks for the mono thing ;)[/QUOTE]
How well does vv work as of now?  If they were thinking about putting it into 2.0 it has to be at least fairly decent right?

---

### Post by pomalin on 2005-12-12
Like I say, it's enable, but I can't find a way to use it.

---

### Post by rwabel on 2005-12-12
[quote=MBro]How well does vv work as of now?  If they were thinking about putting it into 2.0 it has to be at least fairly decent right?[/quote]

I've heard they will release a beta version at the end of the week.

---

### Post by Pedricko on 2005-12-12
When VV beta is released could someone do instructions on implementation?

---

### Post by akurashy on 2005-12-12
[quote=Pedricko]When VV beta is released could someone do instructions on implementation?[/quote]

I be sure to add a little manual if sapo lets me here in this thread, and i be sure to add vv support in my deb :), its already added, but they haven't added it in the GUI it seems.

---

### Post by foxy123 on 2005-12-12
[QUOTE=akurashy]I be sure to add a little manual if sapo lets me here in this thread, and i be sure to add vv support in my deb :), its already added, but they haven't added it in the GUI it seems.[/QUOTE]
we all are looking forward to it!

---

### Post by sapo on 2005-12-12
[QUOTE=akurashy]I be sure to add a little manual if sapo lets me here in this thread, and i be sure to add vv support in my deb :), its already added, but they haven't added it in the GUI it seems.[/QUOTE]
do as you like, if you want ask bored to edit my post hehe i dont mind :P

---

### Post by akurashy on 2005-12-12
[quote=sapo]do as you like, if you want ask bored to edit my post hehe i dont mind :P[/quote]

ok! thanks :D

---

### Post by limit223 on 2005-12-12
[QUOTE=monkeyface]Install sox, and use command "play %s" for playing sounds.[/QUOTE]

I found "aplay %s" sounds much better....after installing alsaplayer.

---

### Post by bored2k on 2005-12-12
[QUOTE=limit223]I found "aplay %s" sounds much better....after installing alsaplayer.[/QUOTE]
Depends on what you use. For me, esdplay works best.

---

### Post by limit223 on 2005-12-13
yeap ..I was referring to alsasound, strictly which for my sound card works better ...esound in my system is deactivated...

---

### Post by -DarkMind- on 2005-12-13
thanks :)

---

### Post by Mahke on 2005-12-13
Great, thanks for the howto :)

---

### Post by Ride Jib on 2005-12-14
First off, the deb file worked great on my system.

The away message buttons on the bottom piss me off to no extent, as well as the width of the menu-bar due to the new contexts. Otherwise I like it.

The new file transferring works!!! Except I can't get it to transfer at anything faster than 10kb/s. Even with my roommate being on the same router!! Anyone else experiencing this problem?

---

### Post by akurashy on 2005-12-14
[quote=Ride Jib]First off, the deb file worked great on my system.

The away message buttons on the bottom piss me off to no extent, as well as the width of the menu-bar due to the new contexts. Otherwise I like it.

The new file transferring works!!! Except I can't get it to transfer at anything faster than 10kb/s. Even with my roommate being on the same router!! Anyone else experiencing this problem?[/quote]

Well I get 25kb/s sometimes, but yes sometimes is slow :(

---

### Post by christooss on 2005-12-14
You can remove Away buttons :)

---

### Post by Ride Jib on 2005-12-14
[QUOTE=christooss]You can remove Away buttons :)[/QUOTE]

Would you like to share with us how to go about doing this?

---

### Post by christooss on 2005-12-14
Im lying you cant remove them. but you can at least hide them

Grab the line between Friends list and those status buttons. Now move that line down :)

---

### Post by ameerirshad on 2005-12-14
Looks nice, looking forward to the other features, as voice-support for stuff like GTalk!

---

### Post by souled on 2005-12-14
Hmm in the Away/Idle tab in Preferences, I don't have any options for the "Change status to:" I click the arrow, but no options are present. Is this not implemented yet, or is there something wrong?

---

### Post by Ride Jib on 2005-12-14
[QUOTE=souled]Hmm in the Away/Idle tab in Preferences, I don't have any options for the "Change status to:" I click the arrow, but no options are present. Is this not implemented yet, or is there something wrong?[/QUOTE]

I'm guessing not implemented. Just like I don't have the ability to remove those annoying "idle times" from displaying in my buddy list window.

---

### Post by lysis on 2005-12-14
the debian package worked FLAWLESSLY.


i uninstalled gaim 1.5 and the debian went on without a hitch. i'm using it now and there's SO MUCH to say about it.


thanks for the how to my man.

---

### Post by thewayofzen on 2005-12-14
great how to.  with the two debs one of them had problems on my system with sounds not playing.. i had to change the sound output to play command  and then have it issue play %s.  other then that i found this great.  I still cannot figure out for the life of me how to UNBLOCK someone in gaim.  I dont think its possible but cannot understand why it isnt being added to 2.0

---

### Post by bored2k on 2005-12-14
[QUOTE=thewayofzen]great how to.  with the two debs one of them had problems on my system with sounds not playing.. i had to change the sound output to play command  and then have it issue play %s.  other then that i found this great.  I still cannot figure out for the life of me how to UNBLOCK someone in gaim.  I dont think its possible but cannot understand why it isnt being added to 2.0[/QUOTE]
[LIST]
[*]Unblocking users: Main window: Accounts: Privacy: Remove from the block list.
[*]Playing sounds: install the esound-clients package, and under the Sound tab in Preferences, type down esdplay %s.
[/LIST]

---

### Post by nehalem on 2005-12-15
[QUOTE=Turtle.net]You know what...
That worked :D
Thanks for your help[/QUOTE]
Yet I'm having the same issue with automake 1.9....

I have libtool installed too.  I swear compiling never works for me.

---

### Post by nehalem on 2005-12-15
Well the deb works.  I don't really get the whole status changing part but overall gain is way better.  The interface is SO much cleaner.

---

### Post by nehalem on 2005-12-15
Yeah, the away stuff is messed up.  I had to change it so it never makes me away since when it goes to away automatically, it won't switch back to being present automatically.

Wierd.  How far off is gaim 2 from being release BTW?

Hmmm, after thinking about it I wonder it this is because it wants to use galago.  Will Dapper have galago?  Do any of the rest of you have problems with it not setting you available again?

---

### Post by sapo on 2005-12-15
[QUOTE=bored2k][LIST]
[*]Unblocking users: Main window: Accounts: Privacy: Remove from the block list.
[*]Playing sounds: install the esound-clients package, and under the Sound tab in Preferences, type down esdplay %s.
[/LIST][/QUOTE]
The last .deb i ve compile is with sound, you can just chose ALSA on the sound menu :p

---

### Post by MighMoS on 2005-12-15
[QUOTE=nehalem]Wierd.  How far off is gaim 2 from being release BTW?[/QUOTE]

Sometime recently, I heard the phrase "two weeks from beta".  That was maybe a week ago.  So two weeks, minus one week equals one week, plus last minute dev changes (1.5 weeks), minus half that - rolled back patches (1 week), plus lag to get to mirrors and packaging (1 day).  So the answer is .... maybe? :razz:

---

### Post by Karma_Police on 2005-12-15
[QUOTE=MighMoS]Sometime recently, I heard the phrase "two weeks from beta".  That was maybe a week ago. (...)[/QUOTE]

According to the news on the [official gaim site]("http://gaim.sourceforge.net/"), the beta should come out tomorrow (Friday, December 16th).

---

### Post by curtis on 2005-12-15
[QUOTE=Karma_Police]According to the news on the [official gaim site]("http://gaim.sourceforge.net/"), the beta should come out tomorrow (Friday, December 16th).[/QUOTE]
Sounds good, can't wait really.

---

### Post by ubuntu27 on 2005-12-15
Hey guys, I've been following this How-to.
And well, I am stack at step one:

```
ubuntu27@heaven:~$ cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' login
bash: cvs: command not found

```

---

### Post by foxy123 on 2005-12-16
[QUOTE=ubuntu27]Hey guys, I've been following this How-to.
And well, I am stack at step one:

```
ubuntu27@heaven:~$ cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' login
bash: cvs: command not found

```[/QUOTE]
install cvs, I guess it should be 
```
sudo apt-get install cvs
```

---

### Post by Jormundgand on 2005-12-17
In case you don't want the hairy situation of having gaim and gaim2.0.0 coexisting as separate package lines or be pestered by upgrade messages then I made [this package](http://ketsuban.net/gaim_2.0.0cvs2-1_i386.deb) which fixes the version issue of sapo's original.

---

### Post by Chrissss on 2005-12-17
Was somebody successfull compiling gaim with --enable-vv? Thats the Video and Voice Support. But when i try this make fails.

CU
 Christoph

---

### Post by WishMaster on 2005-12-17
[quote=Jormundgand]In case you don't want the hairy situation of having gaim and gaim2.0.0 coexisting as separate package lines or be pestered by upgrade messages then I made [this package]("http://ketsuban.net/gaim_2.0.0cvs2-1_i386.deb") which fixes the version issue of sapo's original.[/quote] 
Thanks man !
Synaptic is saying I have 2 broken packages: 
- gaim-dev (1.5)
- gaim-guifications (2.12)

So I have no guifications :cry: and my gaim-xmms doesn't work either :cry:
Oh well, it'll be solved when gaim2.0 goes public (instead of CVS).

1 annoying thing: the big "bars" from your accounts at the bottom. Waste of space.

I do like the way new message-lines get 'added' in a chat window.

I *REALLY* want to see webcam working (I got it working in aMSN 0.95b (CVS))

screenshot -->
[http://www.fileshare.be/img.php?img=Gaim2.jpg&yr=05]("http://www.fileshare.be/img.php?img=Gaim2.jpg&yr=05")

---

### Post by MBro on 2005-12-17
Grab the dotted part above your individual accounts and you can drag it down and hide them

---

### Post by WishMaster on 2005-12-17
I know :)
But that still leaves 1 big box from the gaim-account and the 'big' box saying "Hello!"
Anyway, it's a big improvement since 1.5

---

### Post by ameerirshad on 2005-12-17
I installed it, it runs fine........ some things are bothering though:

1) the fact that I see all my accounts at the bottom. Now I read somewhere that you can set the "away" setting to all accounts at once (you know what I mean?) But I can't find this feature

2) I continue to receive a update notifier saying there is a "new Gaim" version 1.5. So this version is not recognized by synaptic as being newer! Even though I removed Gaim 1.5...

I will stick it out till the official release. Btw, anyone knows what the status is of voip in this gaim?

---

### Post by christooss on 2005-12-17
> quote1) the fact that I see all my accounts at the bottom. Now I read somewhere that you can set the "away" setting to all accounts at once (you know what I mean?) But I can't find this feature


The  big button on bottom of List window. Under all those away buttons for each account

There is a gaim icon on that button

---

### Post by JimmyJazz on 2005-12-17
hey I compiled a gaim-guifications from CVS to work with GAIM 2.0

you can download it here:

[http://jimmyjazz.homeip.net:808/guifications2_guifications2-1_i386.deb]("http://jimmyjazz.homeip.net:808/guifications2_guifications2-1_i386.deb")

---

### Post by rwabel on 2005-12-17
[quote=JimmyJazz]hey I compiled a gaim-guifications from CVS to work with GAIM 2.0

you can download it here:

[http://jimmyjazz.homeip.net:808/guifications2_guifications2-1_i386.deb]("http://jimmyjazz.homeip.net:808/guifications2_guifications2-1_i386.deb")[/quote]

thanks

---

### Post by thechitowncubs on 2005-12-17
Gaim 2.0 Beta Released

[http://gaim.sourceforge.net](http://gaim.sourceforge.net)

---

### Post by MBro on 2005-12-17
Hmmm, I'll wait for a deb, i'm too busy to make one right now for everyone, sorry.

---

### Post by akurashy on 2005-12-17
right now checking this release :D

---

### Post by curtis on 2005-12-17
Weird, 
It worked fine before...
But now if I try the deb package, or compile it my self it results in:

```

*** glibc detected *** free(): invalid pointer: 0xb7476684 ***
Aborted

```
When I run gaim from the command line.
Might be due to my enviroment variables... I'm not sure.
This is what is in /etc/enviroment anyway:

```

LANGUAGE="en_GB:en"

LANG=en_GB.UTF-8

CFLAGS="-O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"
CXXFLAGS="-O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"



```

---

### Post by ubuntu27 on 2005-12-17
[QUOTE=foxy123]install cvs, I guess it should be 
```
sudo apt-get install cvs
```[/QUOTE]
Thank you foxy123 :)  I have Gaim 2.0 from CVS now :)

---

### Post by ubuntu27 on 2005-12-17
[QUOTE=thechitowncubs]Gaim 2.0 Beta Released

[http://gaim.sourceforge.net](http://gaim.sourceforge.net)[/QUOTE]
Yeah...
ANd I've installed Gaim 2.0 CVS just two days ago... :(

Shouldn't we use the BETA now ?

---

### Post by akurashy on 2005-12-17
Here is my deb contribution of GAIM Beta 1

[http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb](http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb)

Video/Voice support added but GAIM haven't added it directly

Enjoy!

---

### Post by MighMoS on 2005-12-17
[QUOTE=curtis]Weird, 
It worked fine before...
But now if I try the deb package, or compile it my self it results in:

```

*** glibc detected *** free(): invalid pointer: 0xb7476684 ***
Aborted

```
When I run gaim from the command line.
Might be due to my enviroment variables... I'm not sure.
This is what is in /etc/enviroment anyway:

```

LANGUAGE="en_GB:en"

LANG=en_GB.UTF-8

CFLAGS="-O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"
CXXFLAGS="-O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"



```[/QUOTE]
Looks worse than my Gentoo OS :razz: Anyway, what happens with "-O2 -pipe", and have you custom-compiled any other relevant libraries on your system?

---

### Post by Chrissss on 2005-12-17
[QUOTE=curtis]But now if I try the deb package, or compile it my self it results in:
```

*** glibc detected *** free(): invalid pointer: 0xb7476684 ***
Aborted
```[/QUOTE]
Take a look here

[http://www.ubuntuforums.org/showpost.php?p=566396&postcount=83](http://www.ubuntuforums.org/showpost.php?p=566396&postcount=83)

You've got to delete some files.

CU
 Christoph

---

### Post by rwabel on 2005-12-17
[quote=akurashy]Here is my deb contribution of GAIM Beta 1

[http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb]("http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb")

Video/Voice support added but GAIM haven't added it directly

Enjoy![/quote]

thanks for the deb file. I get the following message when I want to start up gaim
```
gaim: error while loading shared libraries: libsamplerate.so.0: cannot open shared object file: No such file or directory

```

---

### Post by akurashy on 2005-12-17
[quote=rwabel]thanks for the deb file. I get the following message when I want to start up gaim
```
gaim: error while loading shared libraries: libsamplerate.so.0: cannot open shared object file: No such file or directory

```[/quote]

try getting

sudo apt-get install ortp0
sudo apt-get install doxygen

---

### Post by rwabel on 2005-12-17
[quote=akurashy]try getting

sudo apt-get install ortp0
sudo apt-get install doxygen[/quote]

ortp0 doesn't exist, so I've installed libortp0 and oxygen...still no luck

---

### Post by akurashy on 2005-12-17
Oh my bad

sudo apt-get install libsamplerate0

---

### Post by rwabel on 2005-12-17
[quote=akurashy]Oh my bad

sudo apt-get install libsamplerate0[/quote]

damn now I've a problem. :-) I'm using dapper and I don't have libjack-0.8, but libjack0.100.0-0

```
/usr/local/bin/gaim: error while loading shared libraries: libjack-0.80.0.so.0: cannot open shared object file: No such file or directory
```

---

### Post by akurashy on 2005-12-17
[quote=rwabel]damn now I've a problem. :-) I'm using dapper and I don't have libjack-0.8, but libjack0.100.0-0

```
/usr/local/bin/gaim: error while loading shared libraries: libjack-0.80.0.so.0: cannot open shared object file: No such file or directory
```[/quote]

can't you get 0.80 from repo? :(

---

### Post by rwabel on 2005-12-17
no that's not really possible now under dapper, because jackd is already in the newer version. I think your version will only work under breezy due to the version change of some packages. But otherwise your version would work. I can start it but I've unmet dep. problems now ;-) I've to remove the package and your gaim won't work. isn't it possible to indicate a flexible dependency for the libjack? it's working the newer version too!!

```
Unpacking libjack0.80.0-0 (from libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libjack0.80.0-0:
 libjack0.80.0-0 depends on jackd (= 0.99.0-2ubuntu1); however:
  Version of jackd on system is 0.100.0-4.
dpkg: error processing libjack0.80.0-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libjack0.80.0-0
```

---

### Post by akurashy on 2005-12-17
[quote=rwabel]no that's not really possible now under dapper, because jackd is already in the newer version. I think your version will only work under breezy due to the version change of some packages. But otherwise your version would work. I can start it but I've unmet dep. problems now ;-) I've to remove the package and your gaim won't work. isn't it possible to indicate a flexible dependency for the libjack? it's working the newer version too!!

```
Unpacking libjack0.80.0-0 (from libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libjack0.80.0-0:
 libjack0.80.0-0 depends on jackd (= 0.99.0-2ubuntu1); however:
  Version of jackd on system is 0.100.0-4.
dpkg: error processing libjack0.80.0-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libjack0.80.0-0
```[/quote]

eeep, sadly i don't have dapper installed :(

---

### Post by rwabel on 2005-12-17
isn't there a file called DEBIAN/control?
I guess it would be enough to change the version of libjack to the dapper one. But I'm not a packager :-)

---

### Post by akurashy on 2005-12-17
[quote=rwabel]isn't there a file called DEBIAN/control?
I guess it would be enough to change the version of libjack to the dapper one. But I'm not a packager :-)[/quote]

i could compile jack 0.100 and do a version for dapper :), but i still don't know if it will work, and also that means it will screw my current things (libjack 0.80)

---

### Post by kleeman on 2005-12-17
I got the deb working after the following:
sudo apt-get install libortp

---

### Post by superm1 on 2005-12-18
[QUOTE=akurashy]i could compile jack 0.100 and do a version for dapper :), but i still don't know if it will work, and also that means it will screw my current things (libjack 0.80)[/QUOTE]
Whats actually involved with building the deb?  I'd gladly build one for dapper if someone described to me how to do so.

---

### Post by akurashy on 2005-12-18
[quote=superm1]Whats actually involved with building the deb?  I'd gladly build one for dapper if someone described to me how to do so.[/quote]

its very easy to build a deb,

if you are in dapper
./configure
then
make
then sudo apt-get install checkinstall
sudo checkinstall

(Checkinstall do a deb, after you get the deb you can upload it and contribute it here :)) also get libjack-dev 
it should work nicely :), but if you want to add more support, i sugggest you look at the first post :)

---

### Post by robertq on 2005-12-18
Uhh dudes...

For those with dapper...

Just go into /usr/lib
and run:

sudo ln -s libjack-0.100.0.so.0 libjack-0.80.0.so.0


No need to make a new deb for dapper!

Robert

---

### Post by superm1 on 2005-12-18
[QUOTE=robertq]Uhh dudes...

For those with dapper...

Just go into /usr/lib
and run:

sudo ln -s libjack-0.100.0.so.0 libjack-0.80.0.so.0


No need to make a new deb for dapper!

Robert[/QUOTE]

Well thats convient, I was running into some difficulties while building anyway.

---

### Post by curtis on 2005-12-18
[QUOTE=Chrissss]Take a look here

[http://www.ubuntuforums.org/showpost.php?p=566396&postcount=83](http://www.ubuntuforums.org/showpost.php?p=566396&postcount=83)

You've got to delete some files.

CU
 Christoph[/QUOTE]
Wow, it worked.
Thank you a lot... should of searched a bit more I guess...

---

### Post by WishMaster on 2005-12-18
[quote=akurashy]Here is my deb contribution of GAIM Beta 1
[http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb]("http://davidgonz.com/gaim-2.0.0_2.0.0-1_i386.deb")
Video/Voice support added but GAIM haven't added it directly
Enjoy![/quote]

Got that working with:
 - sudo apt-get install libortp0
 -  sudo apt-get install libsamplerate0

But I don't see any cam/voice support :confused:

---

### Post by rwabel on 2005-12-18
[akurashy]("http://ubuntuforums.org/member.php?u=292"): keep in mind, such deb files are not always working for others because they are simple debs and compiled with your system configuration. For personal usage I do the same. :-)

[robertq]("http://ubuntuforums.org/member.php?u=60236"): yes right, how right and how simple...wasn't thinking a lot yesterday night :-)

---

### Post by akurashy on 2005-12-18
[quote=rwabel][akurashy]("http://ubuntuforums.org/member.php?u=292"): keep in mind, such deb files are not always working for others because they are simple debs and compiled with your system configuration. For personal usage I do the same. :-)
[/quote]

I know rwabel :), just like to help, I know it won't work with all the computers or maybe they just need to dependencies

[LEFT]**WishMaster: [B]They haven't added it yet completely :(**[/B]
[/LEFT]

---

### Post by akurashy on 2005-12-18
Eeep, this is a mini announcement

I'm going to be moving my debs to my personal site. this site will contain some amd64 debs (my friend is doing them) i'm doing x86 :) (i tell when the site is up)

---

### Post by MighMoS on 2005-12-18
[QUOTE=akurashy]Eeep, this is a mini announcement

I'm going to be moving my debs to my personal site. this site will contain some amd64 debs (my friend is doing them) i'm doing x86 :) (i tell when the site is up)[/QUOTE]
Arg!  I was going to do the same thing!  Only my AMD64 site was gonna have i386 debs as well!  ([http://mighmos.org](http://mighmos.org)) even though most of it isn't quite functional, *yet*.

---

### Post by akurashy on 2005-12-18
[quote=MighMoS]Arg!  I was going to do the same thing!  Only my AMD64 site was gonna have i386 debs as well!  ([http://mighmos.org]("http://mighmos.org")) even though most of it isn't quite functional, *yet*.[/quote]

Well all to contribute!, I bet people wouldn't mind more mirrors and options :D

---

### Post by chien on 2005-12-18
just installed the deb

WHERE IS the voice and video??????

---

### Post by akurashy on 2005-12-18
[quote=chien]just installed the deb

WHERE IS the voice and video??????[/quote]

Eeeep, that haven't been added, i think its going to be added next release i think

---

### Post by MighMoS on 2005-12-18
If anyone wants to use the same gaim format that Ubuntu uses, so its stops yelling at you about broken gaim packages, I have them here:

[http://mighmos.org/packages/gaim-2.0.0beta1-i386.tar.gz](http://mighmos.org/packages/gaim-2.0.0beta1-i386.tar.gz)
[http://mighmos.org/packages/gaim-2.0.0beta1-amd64.tar.gz](http://mighmos.org/packages/gaim-2.0.0beta1-amd64.tar.gz)
[http://mighmos.org/packages/gaim_2.0.0beta1-1unofficial0.tar.gz](http://mighmos.org/packages/gaim_2.0.0beta1-1unofficial0.tar.gz)

UPDATE:  Once you extract your arcitecture's tarball, you should specify all three files on the command line to correctly resolve dependencies.

---

### Post by MBro on 2005-12-18
sweet, thanks, works great

---

### Post by cbudden on 2005-12-18
Anyone noticed that you don't get the "user has closed the conversation window" message any more?

---

### Post by Karma_Police on 2005-12-18
[QUOTE=cbudden]Anyone noticed that you don't get the "user has closed the conversation window" message any more?[/QUOTE]

In the msn network? msn messenger 7 and up just close the conversation after 1 min anyway, so they took it out. They didn't want the users to have the wrong information... I had it turned off because of that anyway.

---

### Post by cbudden on 2005-12-18
[QUOTE=Karma_Police]In the msn network? msn messenger 7 and up just close the conversation after 1 min anyway, so they took it out. They didn't want the users to have the wrong information... I had it turned off because of that anyway.[/QUOTE]

Yes, this is in MSN, oh well thanks for the info.

---

### Post by mrgnash on 2005-12-18
[QUOTE=MighMoS]If anyone wants to use the same gaim format that Ubuntu uses, so its stops yelling at you about broken gaim packages, I have them here:

[http://mighmos.org/packages/gaim-2.0.0beta1-i386.tar.gz](http://mighmos.org/packages/gaim-2.0.0beta1-i386.tar.gz)
[http://mighmos.org/packages/gaim-2.0.0beta1-amd64.tar.gz](http://mighmos.org/packages/gaim-2.0.0beta1-amd64.tar.gz)
[http://mighmos.org/packages/gaim_2.0.0beta1-1unofficial0.tar.gz](http://mighmos.org/packages/gaim_2.0.0beta1-1unofficial0.tar.gz)[/QUOTE]

What do I do with those? I tried running dpkg -i with the packages contained in the AMD64 zip but I just keep getting errors about directories and archives.

Maybe it's because Gaim didn't uninstall properly? I used apt-get remove and it whined about unmet dependencies *sigh*

---

### Post by MighMoS on 2005-12-18
[QUOTE=mrgnash]Maybe it's because Gaim didn't uninstall properly? I used apt-get remove and it whined about unmet dependencies *sigh*[/QUOTE]

I'm guessing its because they're not in a repository that its having difficulty resolving how they depend on eachother.  Specify all three on the command line at once, and it should work.  I'm updating my post to reflect this.

---

### Post by mrgnash on 2005-12-18
That works, thanks :)

---

### Post by mattisking on 2005-12-19
[QUOTE=MighMoS]If anyone wants to use the same gaim format that Ubuntu uses, so its stops yelling at you about broken gaim packages, I have them here[/QUOTE]

Hey, Thanks! Kinda strange interface changes. I'm not sure what to do with all these huge buttons that are there now. I don't much care for them really.

---

### Post by MighMoS on 2005-12-19
You can hide them by dragging the bar.  I do.

---

### Post by superm1 on 2005-12-19
i'm wondering why the choice to get rid of all buttons in a window?  I personally liked being able to click the info and add buttons instead of having to chose the menu option.

---

### Post by christooss on 2005-12-19
How can I make my buddy icons smaler?

I can't find that in settings.

Thanks

---

### Post by NachoMas on 2005-12-19
Hi!
I am having problems compiling gaim 2.0 in my ubuntu box. I have an up to date drapper laptop and libgtk2.0-dev is installed, but the configure script keeps on complaining that I don't have gtk properly installed:

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.

The config.log complains about not finding gtk/gtk.h:

configure:31488: checking for GTK+ - version >= 2.0.0
configure:31633: result: no
configure:31666: gcc -o conftest -g -O3 -march=pentium3 -pipe -fomit-frame-pointer -funroll-loops -f
expensive-optimizations    conftest.c -lnsl -lresolv   >&5
conftest.c:113:21: error: gtk/gtk.h: No such file or directory

But gtk.h is installed:

ls -la /usr/include/gtk-2.0/gtk/gtk.h
-rw-r--r-- 1 root root 5945 Dec 13 14:02 /usr/include/gtk-2.0/gtk/gtk.h

I have tried to install gtk1.2-dev and remove and reinstall the dev packages, but nothing seems to work. I guess I must have something wrong in /usr/include/ but I canät find it:

ls /usr/include/gtk*
/usr/include/gtk-1.2:
gdk  gtk

/usr/include/gtk-2.0:
gdk  gdk-pixbuf  gdk-pixbuf-xlib  gtk

/usr/include/gtkspell-2.0:
gtkspell

So I am running out of ideas! Any help on what can be wrong? Why is the configure script not finding the gtk.h header?

Thanks for the help!
/Nacho

---

### Post by christooss on 2005-12-19
How can I make my buddy icons smaler?

I can't find that in settings.

Thanks

---

### Post by NachoMas on 2005-12-19
Hi!
I am having problems compiling gaim 2.0 in my ubuntu box. I have an up to date drapper laptop and libgtk2.0-dev is installed, but the configure script keeps on complaining that I don't have gtk properly installed:

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.

The config.log complains about not finding gtk/gtk.h:

configure:31488: checking for GTK+ - version >= 2.0.0
configure:31633: result: no
configure:31666: gcc -o conftest -g -O3 -march=pentium3 -pipe -fomit-frame-pointer -funroll-loops -f
expensive-optimizations    conftest.c -lnsl -lresolv   >&5
conftest.c:113:21: error: gtk/gtk.h: No such file or directory

But gtk.h is installed:

ls -la /usr/include/gtk-2.0/gtk/gtk.h
-rw-r--r-- 1 root root 5945 Dec 13 14:02 /usr/include/gtk-2.0/gtk/gtk.h

I have tried to install gtk1.2-dev and remove and reinstall the dev packages, but nothing seems to work. I guess I must have something wrong in /usr/include/ but I canät find it:

ls /usr/include/gtk*
/usr/include/gtk-1.2:
gdk  gtk

/usr/include/gtk-2.0:
gdk  gdk-pixbuf  gdk-pixbuf-xlib  gtk

/usr/include/gtkspell-2.0:
gtkspell

So I am running out of ideas! Any help on what can be wrong? Why is the configure script not finding the gtk.h header?

Thanks for the help!
/Nacho

---

### Post by Chrissss on 2005-12-19
[QUOTE=christooss]How can I make my buddy icons smaler? I can't find that in settings.[/QUOTE]

Buddies -> Deaktivate "Show Buddy Details"

CU
 Christoph

---

### Post by Revert on 2005-12-19
I'm not real sure what I did...

I got the source and everything fine.  ./configure, make, then did a checkinstall.  It said the .deb ended up failing, but GAIM 2's installed now.  I can't uninstall it using dpkg or make uninstall.

Any ideas what happened?  I didn't save any of the output from the checkinstall (hadn't noticed it was borked for awhile), but I'm sure I can replicate it if need be.

---

### Post by invisage01 on 2005-12-19
Nacho.. 

i have the exact same problem.. i got lost in it all last night.. gave up.. went to bed and was hoping someone had a solution for that bad boy yet!!! obviously not yet!!

here's hopin!

i.

---

### Post by Karma_Police on 2005-12-19
[QUOTE=Revert] (...) It said the .deb ended up failing, but GAIM 2's installed now.  I can't uninstall it using dpkg or make uninstall.

Any ideas what happened?  (..)[/QUOTE]


Did you have synaptic or apt-get running at the same time? The thing is, it first installs all the files, and then creates the deb and registers it somehow in the programs "database". So all the files were installed, but it couldn't run the deb because of a conflict with something else. I had the same thing happen to me, and it didn't output any error. just said it failed. then I noticed I still had synaptic open because I was installing some libs... :s

Try installing the deb again, and then uninstalling it.


Now, I compiled the beta myself but gaim seems to use gaim usage to set me away, instead of X usage... Anyone have any ideas about this?

---

### Post by Revert on 2005-12-19
Thanks, that worked. :)

---

### Post by superm1 on 2005-12-19
How do I actually properly build my plugins from source?  I wanted to build gaim-thinklight against gaim2, but I can't seem to grab the sources properly with apt.

supermario@portablemario:~/Desktop$ sudo apt-build build-source gaim-thinklight
E: Unable to find a source package for gaim-thinklight
Some error occured building package

---

### Post by Karma_Police on 2005-12-19
Can't you get the source from their site and compile it yourself?

Anyway, I don't think gaim 1.5 plugins are compatible with gaim 2.0 :???: They seem to have changed the plugins api. I think you need to wait for an updated plugin that suports gaim 2.0. Guifications seems to have done it allready.

---

### Post by superm1 on 2005-12-20
[QUOTE=Karma_Police]Can't you get the source from their site and compile it yourself?

Anyway, I don't think gaim 1.5 plugins are compatible with gaim 2.0 :???: They seem to have changed the plugins api. I think you need to wait for an updated plugin that suports gaim 2.0. Guifications seems to have done it allready.[/QUOTE]

Well the main site for it is actually housed at a debian stronghold somewhere.  I was assuming since that is where it came from, perhaps the source package might be directly available to apt.  I was hoping to avoid building it from scratch and then having a binary lingering that isn't in my apt database properly.  I'll grab the sources and see what sort of luck I churn out.  

Also for the curious, there is a mention of the gentoo forums gathering an ebuild that could get a working gaim-encryption.  So this can be soon rebuilt too.

---

### Post by akurashy on 2005-12-20
i have guifications installed in my gaim2 (i got it from CVS) i can do a deb of guifications IF needed

---

### Post by Ride Jib on 2005-12-20
I'm having trouble compiling the beta source on my machine. Can anyone diagnose this output? I do ./configure, and make fine. Then make install does this:

```
e:~/gaim-2.0.0beta1$ make install
Making install in doc
make[1]: Entering directory `/home/brad/gaim-2.0.0beta1/doc'
make[2]: Entering directory `/home/brad/gaim-2.0.0beta1/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/brad/gaim-2.0.0beta1/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/brad/gaim-2.0.0beta1/doc'
make: *** [install-recursive] Error 1

```

Thanks!

---

### Post by LoclynGrey on 2005-12-20
installed from .deb and working fine. cheers

---

### Post by akurashy on 2005-12-20
[quote=Ride Jib]I'm having trouble compiling the beta source on my machine. Can anyone diagnose this output? I do ./configure, and make fine. Then make install does this:

```
e:~/gaim-2.0.0beta1$ make install
Making install in doc
make[1]: Entering directory `/home/brad/gaim-2.0.0beta1/doc'
make[2]: Entering directory `/home/brad/gaim-2.0.0beta1/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/brad/gaim-2.0.0beta1/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/brad/gaim-2.0.0beta1/doc'
make: *** [install-recursive] Error 1

``` 
Thanks![/quote]

try 'sudo make install'

---

### Post by MaX on 2005-12-20
I just compiled from CVS and it segfaults directly.

Does anyone have a working version for AMD64 processors?
I can't use the debs you put up here since they are i386.

---

### Post by Ride Jib on 2005-12-20
[QUOTE=akurashy]try 'sudo make install'[/QUOTE]

I tried that, and it resulted in the exact same error. :???:

---

### Post by WishMaster on 2005-12-20
From [http://gaim.sourceforge.net/]("http://gaim.sourceforge.net/")

> On that note, please keep your feedback coming, but there are a few recurring reports we definitely already know about and are working on that you don't need to let us know about anymore:[LIST]
[*]The per-account statusboxes are a bad idea
[*]The statusboxes in general are too big.
[*]We intentionally removed more preferences than we should have, to see which ones absolutely can't be lived without. Some of them (e.g. Show idle times in buddy list, report idle time by Gaim usage) need to be ressurected
[*]Saved statuses need to be easier to get to
[*]Smooth scroll needs to be optional; people are very polar about how they feel about the smooth scroll
[*]Control-enter, though still optional (see [the    faq]("http://gaim.sourceforge.net/faq.php#q19")), is not particularly easy to find and should perhaps be added to the      gaimrc plugin.[/LIST]

---

### Post by Karma_Police on 2005-12-20
[QUOTE=Ride Jib]I'm having trouble compiling the beta source on my machine. Can anyone diagnose this output? I do ./configure, and make fine. Then make install does this:

(...)

Thanks![/QUOTE]


that happened to me.

What I did was move /usr/local/man to /usr/local/man.backup, install gaim, copy the contents from the /usr/local/man that gaim created to /usr/local/man.backup, then you can delete /usr/local/man and mv /usr/local/man.backup /usr/local/man

Hope you can understand that :???: If I wasn't clear enough, feel free to ask.

---

### Post by MighMoS on 2005-12-20
[QUOTE=MaX]I just compiled from CVS and it segfaults directly.

Does anyone have a working version for AMD64 processors?
I can't use the debs you put up here since they are i386.[/QUOTE]
Yeah, I posted them earlier.  Or just check out [http://mighmos.org/packages.php](http://mighmos.org/packages.php)

---

### Post by e2k on 2005-12-20
[QUOTE=Karma_Police]What I did was move /usr/local/man to /usr/local/man.backup, install gaim, copy the contents from the /usr/local/man that gaim created to /usr/local/man.backup, then you can delete /usr/local/man and mv /usr/local/man.backup /usr/local/man

Hope you can understand that :???: If I wasn't clear enough, feel free to ask.[/QUOTE]
Hmm, I tried to follow your advice and did this:
```
sudo mv /usr/local/man /usr/local/man.backup
```
Did I screw up something? This is what i get now:
```
$ ls -la /usr/local/
....
lrwxrwxrwx   1 root root    9 2005-12-09 18:06 man.backup -> share/man
```
Did I just make the man directory a symlink? There is no /usr/local/share/man :o

EDIT: Nevermind this, just noticed /usr/local/man **should** be a symlink ;)

---

### Post by 11hjpphty76lkjj on 2005-12-20
I know most of you have GAIM2 installed, but for those curious of what it looks likes go to the following link:

[http://www.kalosaurusrex.com/screenshots/gaim2/gaim2.html]("http://www.kalosaurusrex.com/screenshots/gaim2/gaim2.html")

I couldn't find any good screenshoots, I thought it might be interesting for those that haven't upgraded as of yet.

If someone else has already done this, sorry!

---

### Post by Ride Jib on 2005-12-20
[QUOTE=Karma_Police]that happened to me.

What I did was move /usr/local/man to /usr/local/man.backup, install gaim, copy the contents from the /usr/local/man that gaim created to /usr/local/man.backup, then you can delete /usr/local/man and mv /usr/local/man.backup /usr/local/man

Hope you can understand that :???: If I wasn't clear enough, feel free to ask.[/QUOTE]

Thanks man! Worked just fine.

Maybe next week I will put on the 64-bit kernel and post up a .deb for all you 64-bit users.

---

### Post by Grey on 2005-12-21
Just thought I would throw this out there.  I have created a few [debs](http://people.uleth.ca/~dave.brady/debs/)...

**Gaim 2.0.0 Beta 1** (Features idle based upon X usage, rather than Gaim usage, and Synaptic does not try to "upgrade" to 1.5)
**gaim-xmms-remote**  (A useful plugin for controlling xmms from gaim, or showing your current song to your friends)
**gaim-guifications** (Toaster popups for gaim events)
**VLC 0.8.5** (Features VC1 support, so it should play most WMV9s)

Just keep in mind that these are very very unofficial packages, and might not work, and might have undesirable side-effects.  But they work great on the 3 PCs I've tried them.

These are all 32-bit, as I have yet to actually upgrade to 64-bit Ubuntu.

---

### Post by MighMoS on 2005-12-21
[QUOTE=Grey]Just thought I would throw this out there.  I have created a few [debs](http://people.uleth.ca/~dave.brady/debs/)...

**Gaim 2.0.0 Beta 1** (Features idle based upon X usage, rather than Gaim usage, and Synaptic does not try to "upgrade" to 1.5)
**gaim-xmms-remote**  (A useful plugin for controlling xmms from gaim, or showing your current song to your friends)
**gaim-guifications** (Toaster popups for gaim events)
**VLC 0.8.5** (Features VC1 support, so it should play most WMV9s)

Just keep in mind that these are very very unofficial packages, and might not work, and might have undesirable side-effects.  But they work great on the 3 PCs I've tried them.

These are all 32-bit, as I have yet to actually upgrade to 64-bit Ubuntu.[/QUOTE]

Mind providing the source for these packages, so that you don't violate the GPL?  (It also has the advantage of other archs being able to use them) :smile:

---

### Post by Grey on 2005-12-21
I honestly have no idea how to go about building a deb-src package.  I just used checkinstall for each of those.  And the source I used was unmodified from the original sources I downloaded, with the exception of VLC.  VLC was compiled with [these instructions](http://www.nanocrew.net/2005/09/01/compiling-vlc/), with the exception that I compiled it with HAL enabled.  Uncertain about the legality of that one... I can remove it if you want.

Gaim was compiled with the instructions found at the start of this thread... more or less.  Source code can be found at the Gaim website.  It's unmodified.

Guifications and XMMS-Remote came from [here](http://guifications.sourceforge.net/).  Also compiled unaltered, with default options (against the default Gaim 2.0 source code).

I suppose technically, I am redistributing GPLed code, and I should include the sources with them.  But I am still pretty much a Linux newbie, and I lack the hosting space anyway.  (My University only gives me 30MB).  But I am mainly just thinking of this as a service to people who haven't been able to get these packages working properly yet.  Reading through the many Gaim threads, it seems to me that I've resolved a few problems that others are still facing.

---

### Post by MighMoS on 2005-12-21
I'd just point to a mirror if they're vanilla builds, but you said Gaim does Idle based on X rather than IM usage, so I thought there was some other patch applied.

---

### Post by Grey on 2005-12-21
Nah, that's just the lack of a required dependency for it to work.  I just used "sudo apt-get build-dep gaim" to get all the required stuff.  I think the exact needed package is libxss-dev in order to make it work.

---

### Post by limit223 on 2005-12-21
[QUOTE=Grey]Just thought I would throw this out there.  I have created a few [debs](http://people.uleth.ca/~dave.brady/debs/)...

**Gaim 2.0.0 Beta 1** (Features idle based upon X usage, rather than Gaim usage, and Synaptic does not try to "upgrade" to 1.5)
**gaim-xmms-remote**  (A useful plugin for controlling xmms from gaim, or showing your current song to your friends)
**gaim-guifications** (Toaster popups for gaim events)
**VLC 0.8.5** (Features VC1 support, so it should play most WMV9s)

Just keep in mind that these are very very unofficial packages, and might not work, and might have undesirable side-effects.  But they work great on the 3 PCs I've tried them.

These are all 32-bit, as I have yet to actually upgrade to 64-bit Ubuntu.[/QUOTE]


Thank you! Finally I've got my favorite plugin: guifications to work..nice job with your .deb's I installed them all.

---

### Post by Nano on 2005-12-21
I'm not really happy with the new version. I think I'll switch back to 1.5 until they release the voice-video features, which will be, in my opinion, the only reason to upgrade.
I've already seen they found out that some changes were bad ideas.
What I'd love more is a way to completely customize the look of the contact list, like remove contact icons next to names, etc. in order to have a very tiny window.

Just my 2 cents

---

### Post by MighMoS on 2005-12-21
Uncheck "show buddy details" in the buddies menu.

---

### Post by akurashy on 2005-12-21
Debs has been removed from my personal site. 

Debs are going to be uploaded in 

[http://ubuntu.akurashy.com](http://ubuntu.akurashy.com) 

There will be other debs there aswell, I'm not responsible for anything that happens to your computer, Use it at your own risk. I will provide support of course. 

There are other people contributing debs aswell

(Also if anyone is interested in contributing deb please pm me)

---

### Post by Grey on 2005-12-22
[QUOTE=limit223]Thank you! Finally I've got my favorite plugin: guifications to work..nice job with your .deb's I installed them all.[/QUOTE]

Glad that it could help you.  :)

I also just posted a Skype deb to the site, that will actually install on Ubuntu.  (I just modified the dependencies to the Ubuntu dependencies, rather than the Debian ones).

---

### Post by rbrugman on 2005-12-22
[QUOTE=raublekick]... isn't gaim 2.0 supposed to have uPnP/NAT translation? i still can't send and recieve files :([/QUOTE]

It is, and does!  Maybe it's your router.  I have a Linksys WRT54G (with dd-wrt firmware) and it works great.

---

### Post by akurashy on 2005-12-23
SOrry I took long! :D, the deb is here to stay! 

[http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb](http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb)

wget -c [http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb](http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb)

Lata! (PS. I might update it later!)

---

### Post by ShirishAg75 on 2005-12-24
you forgot a very simple command if it's a deb ```
dpkg -i gaim2.0whatever.deb
```, this needs to be part of the howto on the 1st page as well as the amsn & esounds thing which is on the 2nd page. Btw was able to install the default gaim2.0cvs*.deb without any issues. The sound & other stuff whenever u update then will do that. Thanx for that.

---

### Post by WishMaster on 2005-12-26
Just a question: is there an auto-reply (plugin) for the MSNnetwork?

---

### Post by cutOff on 2005-12-26
[QUOTE=akurashy]SOrry I took long! :D, the deb is here to stay! 

[http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb](http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb)

wget -c [http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb](http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb)

Lata! (PS. I might update it later!)[/QUOTE]
Thanks mate for packaging.

---

### Post by Rev. Nathan on 2006-01-05
Awesome. I still can't get make/install stuff to work for me, so after 20 minutes of doing that, tried your .deb file and that worked from the get-go. Thanks!

By the way, this is great! And the available messesages will go great with AIM Triton coming out soon.

---

### Post by Pedricko on 2006-01-05
I'm having a problem.

I tried to install Gaim 2 from the .deb file, but when I tried to load it up I got:

pedro@ubuntu:~$ gaim
gaim: error while loading shared libraries: libsamplerate.so.0: cannot open shared object file: No such file or directory

so I removed it and installled the one from apt-get yet still get the same error... help?

---

### Post by Suzan on 2006-01-06
Thanks grey! GAIM works great!

---

### Post by MrRoboto on 2006-01-06
[QUOTE=Pedricko]I'm having a problem.

I tried to install Gaim 2 from the .deb file, but when I tried to load it up I got:

pedro@ubuntu:~$ gaim
gaim: error while loading shared libraries: libsamplerate.so.0: cannot open shared object file: No such file or directory

so I removed it and installled the one from apt-get yet still get the same error... help?[/QUOTE]


symlink the libs:

sudo ln -s /usr/lib/libsamplerate.so.0.1.1 /usr/lib/libsamplerate.so.0


and so on..

---

### Post by LaSSarD on 2006-01-07
[QUOTE=Pedricko]I'm having a problem.

I tried to install Gaim 2 from the .deb file, but when I tried to load it up I got:

pedro@ubuntu:~$ gaim
gaim: error while loading shared libraries: libsamplerate.so.0: cannot open shared object file: No such file or directory

so I removed it and installled the one from apt-get yet still get the same error... help?[/QUOTE]
sudo apt-get install libsamplerate0 libjack0.80.0-0 libortp0

this command should take care of all the libs it will ask before running successfully (it did here)

good luck!

---

### Post by swoon on 2006-01-08
*** glibc detected *** free(): invalid pointer: 0xb7469a84 ***
Aborted

i get this when runing the gaim build posted in thisa thread. i'm not really sure what it means, really.

---

### Post by akurashy on 2006-01-08
[quote=swoon]*** glibc detected *** free(): invalid pointer: 0xb7469a84 ***
Aborted

i get this when runing the gaim build posted in thisa thread. i'm not really sure what it means, really.[/quote]


you need to install mono

---

### Post by swoon on 2006-01-09
sudo apt-get install mono
Password:
Reading package lists... Done
Building dependency tree... Done
mono is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

it looks like i have most of the other mono stuff installed, is there another dep i could be missing?

---

### Post by Azriphale on 2006-01-09
perhaps you can find out what other deps you are missing by grabbing the source from CVS, and just running "./autogen.sh" and "./configure" on it.

GNU Autoconf is usually pretty decent about telling you what deps you need.

Other than that, I can't help as I have not yet tried to compile/install Gaim 2 CVS.

---

### Post by akurashy on 2006-01-09
[quote=swoon]sudo apt-get install mono
Password:
Reading package lists... Done
Building dependency tree... Done
mono is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

it looks like i have most of the other mono stuff installed, is there another dep i could be missing?[/quote]

Try.
[I] sudo rm /usr/local/lib/gaim/mono.*
[I]
if you look at the thread there was some solutions in the other pages[/I]
[/I]

---

### Post by Jingo on 2006-01-13
Should this package have webcam support?
Can't seem to find it!?

---

### Post by akurashy on 2006-01-13
[quote=Jingo]Should this package have webcam support?
Can't seem to find it!?[/quote]

Not yet, they haven't added it =/

---

### Post by kakashi on 2006-01-15
bump

---

### Post by masingerz on 2006-01-15
[QUOTE=Grey]Just thought I would throw this out there.  I have created a few [debs](http://people.uleth.ca/~dave.brady/debs/)...

**Gaim 2.0.0 Beta 1** (Features idle based upon X usage, rather than Gaim usage, and Synaptic does not try to "upgrade" to 1.5)
**gaim-xmms-remote**  (A useful plugin for controlling xmms from gaim, or showing your current song to your friends)
**gaim-guifications** (Toaster popups for gaim events)
**VLC 0.8.5** (Features VC1 support, so it should play most WMV9s)

Just keep in mind that these are very very unofficial packages, and might not work, and might have undesirable side-effects.  But they work great on the 3 PCs I've tried them.

These are all 32-bit, as I have yet to actually upgrade to 64-bit Ubuntu.[/QUOTE]

Please help me installing these features.

By the Way I use BMPX: will it work?

-masingerz

---

### Post by hen3rz on 2006-01-15
Great tutorial! thanks heaps!

Is it weird that the auto updater keeps telling me to update to gaim 1.5 even though i have this installed, or is this normal?

---

### Post by christooss on 2006-01-16
[QUOTE=masingerz]Please help me installing these features.

By the Way I use BMPX: will it work?

-masingerz[/QUOTE]


I think you cannot install those futures beacause thay have to be packaged to 2.0 version.

I think bmpx won't work.

---

### Post by christooss on 2006-01-16
Ups now I saw. Click on Greys link

[http://people.uleth.ca/~dave.brady/debs/](http://people.uleth.ca/~dave.brady/debs/)

Download the debs and than where they are on your computer open the terminal and instal them with:

dpkg -i deb_package.deb

---

### Post by hamil on 2006-01-21
Thanks guys!

this was awsome!
Running Gaim 2.0.0CVS2.1 now, and it works just perfect!

Anyone have any idea if it will be possible for me to set a profile picture for my MSN account in Gaim in the future?

---

### Post by Stereotypical Rage on 2006-01-21
[QUOTE=Grey]Just thought I would throw this out there.  I have created a few [debs](http://people.uleth.ca/~dave.brady/debs/)...

**Gaim 2.0.0 Beta 1** (Features idle based upon X usage, rather than Gaim usage, and Synaptic does not try to "upgrade" to 1.5)
**gaim-xmms-remote**  (A useful plugin for controlling xmms from gaim, or showing your current song to your friends)
**gaim-guifications** (Toaster popups for gaim events)
**VLC 0.8.5** (Features VC1 support, so it should play most WMV9s)

Just keep in mind that these are very very unofficial packages, and might not work, and might have undesirable side-effects.  But they work great on the 3 PCs I've tried them.

These are all 32-bit, as I have yet to actually upgrade to 64-bit Ubuntu.[/QUOTE]
sudo dpkg -i gaim2.0.0-2beta1_i386.deb
(Reading database ... 92504 files and directories currently installed.)
Preparing to replace gaim 1:1.5.0-1ubuntu3 (using gaim2.0.0-2beta1_i386.deb) ...
Unpacking replacement gaim ...
dpkg: error processing gaim2.0.0-2beta1_i386.deb (--install):
 trying to overwrite `/usr/local/bin/gaim', which is also in package gaim-2.0.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim2.0.0-2beta1_i386.deb
======================
They don't work for me. 32 bit Ubuntu.:cry:

---

### Post by MBro on 2006-01-21
Try removing the original ubuntu 1.5 gaim package first.  I think that might help you.

---

### Post by WishMaster on 2006-01-24
> **Beta 2: The Sequel to Beta **

 [January 24th, 2006 - 5:08PM EST ]("http://gaim.sourceforge.net/index.php?id=166")
We're basically refining crude oil into a usable product. Only instead of refining crude oil, we're making Gaim better. But it's really the same thing. Really. 
 Please grab [beta 2]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=387865") and let us know what you think. With any luck we won't need to make any major changes, and Gaim 2.0.0 final will be out before you can prove the theory of special relativity.
 
Someone build me a .deb :D

---

### Post by HJThis on 2006-01-24
Hello,To all

Well i don't know why but it's the first time
i am having problems installing this here is
the error am gething.

---

### Post by WishMaster on 2006-01-24
Dude.... this is the GAIM-thread, not AMSN :p

Anyway --> [http://amsn.sourceforge.net/linux-downloads.php](http://amsn.sourceforge.net/linux-downloads.php)
Download the Ubuntu-deb
Open a terminal, cd to the directory where you downloaded the .deb and type:
sudo dpkg -i <amsn-filename-deb>

---

### Post by HJThis on 2006-01-24
Hi,WishMaster  	

Huh good god i  have to get off the CRACK bad
i been using the info for gaim to try & install amsn
so this is why i no longer have gaim.

please SLAP me

Thank you

---

### Post by MighMoS on 2006-01-24
I've built some new packages for gaim's new beta.  These packages preserve ubuntu's existing 3 package structure for gaim (base, data, and dev), so this should alleviate problems of Ubuntu telling you its out of date.

I'm unable to attach them right now, but they are available at [http://mighmos.org/packages.php](http://mighmos.org/packages.php) .

Also, if you've used my previous clearlooks theme (2.7.1), please upgrade, as it had a bug that would sometime crash Gaim in the accounts menu.

As always, not to break the GPL, source packages are available on my website.

---

### Post by zachtib on 2006-01-24
it installed great, any word on if/when then gaim-vv features will be added?

---

### Post by MighMoS on 2006-01-24
Sorry, I meant to talk about that.  Support for it is in the official Gaim branch, but I wasn't able to get it to install correctly.  I'll look into it over the next few days, but basically over some burocratic desicions, they went with linphone instead of gstreamer.

---

### Post by shanghaipi on 2006-01-24
I got this:

 gaim depends on libdbus-1-1 (>= 0.36.2); however:
  Package libdbus-1-1 is not installed.
 gaim depends on libdbus-glib-1-1 (>= 0.36.2); however:
  Package libdbus-glib-1-1 is not installed.

Hmmm...

---

### Post by Grey on 2006-01-24
Okay... this time it just doesn't work for me.  I get this when I try to run beta2.

```

*** glibc detected *** realloc(): invalid next size: 0x083afdc8 ***
Aborted

```

The 0x083afdc8 part changes every time I try to run it.  The really interesting thing though is that if I keep trying to run the package repeatedly... sometimes it works.  It just takes a lot of tries.

This happens both with the deb I just compiled and the deb posted by MighMos (Thanks a lot btw... that's a really nice deb).  I have also tried installing mono and libmono... to no effect.

---

### Post by arnieboy on 2006-01-24
[gaim 2.0 beta 2]("http://gaim.sourceforge.net/") has been released. the official announcement came 3 minutes back.. u guys oughta check it out.

---

### Post by makisupa123 on 2006-01-24
[QUOTE=MighMoS]I've built some new packages for gaim's new beta.  These packages preserve ubuntu's existing 3 package structure for gaim (base, data, and dev), so this should alleviate problems of Ubuntu telling you its out of date.

I'm unable to attach them right now, but they are available at [http://mighmos.org/packages.php](http://mighmos.org/packages.php) .

Also, if you've used my previous clearlooks theme (2.7.1), please upgrade, as it had a bug that would sometime crash Gaim in the accounts menu.

As always, not to break the GPL, source packages are available on my website.[/QUOTE]


Your deb worked perfectly.  Thanks Alot!!

---

### Post by Jingo on 2006-01-24
Will webcam support be part of version 2.0 ?
Does beta2 have it? Guess not...

Linux really lacks webcam support in the IM's !!

---

### Post by arnieboy on 2006-01-24
if u want webcam support on MSN, try amsn 0.95. there is a howto running for that in this forum.

---

### Post by MighMoS on 2006-01-24
These packages were built on Ubuntu *Breezy*.  I've heard they don't work on Dapper, because of dbus changes.  If anyone gets them working, a voice on how would be appriciated, and I don't have enough spare space for an exter dapper installation.

[QUOTE=Jingo]Will webcam support be part of version 2.0 ?
Does beta2 have it? Guess not...[/QUOTE]
I don't know if --enable-vv enables both voice and video (as one would think) or just voice.  But as I've stated earlier, I couldn't get it to resolve the dependencies.

---

### Post by Chrissss on 2006-01-24
Did nobody read the message on the Gaim Homepage ;)

> Gaim 2.0.0 beta 2 does not include voice or video ("vv") support for any protocols. We've done some work toward vv compatibility for Google Talk, but it isn't ready for the general public yet. It is unlikely this will change for the final release of Gaim 2.0.0, but vv will be a primary focus for the next major release of Gaim after that.

So, most likely there won't be video support in gaim2...

CU
 Christoph

---

### Post by christooss on 2006-01-24
Drapper package would be nice. Builded frombeta2 ofcourse :)

---

### Post by Logic* on 2006-01-24
[QUOTE=Grey]Okay... this time it just doesn't work for me.  I get this when I try to run beta2.

```

*** glibc detected *** realloc(): invalid next size: 0x083afdc8 ***
Aborted

```
[/QUOTE]

I get the same... any suggestions?

---

### Post by Rev. Nathan on 2006-01-25
What do I do in the ./configure to enable sound, spellcheck, and all the goodies as seen in the .debs?

Anyone want to share the command?

---

### Post by Grey on 2006-01-25
[QUOTE=Rev. Nathan]What do I do in the ./configure to enable sound, spellcheck, and all the goodies as seen in the .debs?

Anyone want to share the command?[/QUOTE]

You just need to have the dependencies.  Try "sudo apt-get build-dep gaim".  That should cover most of it...  I don't honestly remember what the exact packages are that you need.

---

### Post by MighMoS on 2006-01-25
You'll need a lot of -dev packages for basically everything you want.  If there's a feature you want, but its not compiled in, check to see if the corresponding $feature-dev package is installed.

./configure --help should also provide some insigts.

---

### Post by Orunitia on 2006-01-25
If you're trying to install from source, why not just grab the rpm and alien it? That's what I did.

---

### Post by cutOff on 2006-01-25
Hi there, I've compiled Gaim 2.0.0 Beta 2 for i386. I used '--enable-vv' flag. 
You can find here (scroll down to the bottom and choose Free. Wait a few seconds)

[http://rapidshare.de/files/11793408/gaim-2.0.0beta2_2.0.0beta2-1_i386.deb.html](http://rapidshare.de/files/11793408/gaim-2.0.0beta2_2.0.0beta2-1_i386.deb.html)

If anyone have issues with oRTP, have a look [here]("http://www.ubuntuforums.org/showpost.php?p=602241&postcount=2").


Regards

---

### Post by Nano on 2006-01-25
Thanks, cutOff, I'll check it out right now.

Fins ara

---

### Post by Nano on 2006-01-25
It seems to work pretty well after installing  the oRTP. It's a bit slower than 1.5, though.

Thanks again

---

### Post by cbudden on 2006-01-25
Has anyone got a working guifications plugin for 2.0b2?

---

### Post by rwabel on 2006-01-25
thanks works fine under dapper! which version of libortp did you install?

---

### Post by shanghaipi on 2006-01-25
I installed it for dapper and it works.  Though I need to install those versions of libortp on the bottom of your response. 

I even found a weird bug.  If you click on people in your buddy list, sometimes it behaves weirdly.  It puts people on the top of your buddy list if  you click on them or it will highlight them, which its supposed to do.  Weird.

---

### Post by cutOff on 2006-01-25
> **Nano]It seems to work pretty well after installing  the oRTP. It's a bit slower than 1.5, though.

Thanks again[/QUOTE]
hehe glad it worked.

Salut  said:**
> thanks works fine under dapper! which version of libortp did you install?

I had to remove both libortp0 and libortp0-dev packages before installing the other ones. The version of oRTP provided for Breezy is 1.0.1-6ubuntu7.

---

### Post by unf on 2006-01-25
[QUOTE=cutOff]I used '--enable-vv' flag. 
[/QUOTE]
Sorry...but where should I but --enable-vv?

---

### Post by bites on 2006-01-25
[QUOTE=shanghaipi]I installed it for dapper and it works.[/QUOTE]

Are you able to play sounds?  I installed it in Dapper as well but I can't play any sounds in Gaim now.  

Thanks for the quick .deb btw!

---

### Post by shanghaipi on 2006-01-25
yeah, there are no sounds built in.  That buddy list bug that i mentioned earlier might be annoying enough to uninstall.  Is anyone else using Dapper having this trouble?

---

### Post by MighMoS on 2006-01-25
What does --enable-vv do?  After reading the updated Gaim News page, it says it doesn't work with anything, just work has been done so that its easier to do in the future...

---

### Post by bites on 2006-01-25
I'm using Dapper and haven't got the buddy-list problem.  I've got both Jabber and MSN lists working fine.

---

### Post by shanghaipi on 2006-01-25
did you install that libortp package earlier in the thread.  I had to install that.  Maybe that's the problem.

---

### Post by WishMaster on 2006-01-25
Can anyone tell me the difference with beta1 ?

I have beta1, with working Guifications. Don't want beta2 without guifications if there aren't "important" changes in beta2.

---

### Post by rwabel on 2006-01-25
I'm using dapper and have no sound either but I don't get the buddy problem!

---

### Post by Grey on 2006-01-25
I've reverted to beta1, as I just couldn't get beta2 working properly.  But in the few cases that it WAS working, sound was working fine (select esd from the sound options), but I'm not sure if guifications was working.  If someone can fix my glib error, I would be happy to compile a new guifications deb.  :)

---

### Post by cutOff on 2006-01-25
To the people who haven't sound yet, try this.

Go to Preferences -> Sound. In **Method** option, select **Command**. 

In **Command for Sound**, type ***aplay***.

Now you can do a test by pressing the Test button.

---

### Post by bites on 2006-01-25
Thanks for the tip :)  It works fine now..

---

### Post by dailer on 2006-01-25
I made my own version, and sound is working :)

[http://www.sendspace.com/file/xnvdwr](http://www.sendspace.com/file/xnvdwr)

If gaim crashes at startup, you have to delete your profile. You dont have to delete all files, just try it out till it works.

---

### Post by rwabel on 2006-01-25
I get the following error message on my dapper when using aplay: aplay: main:533: audio open error: No such device (this message is from the shell)

---

### Post by cutOff on 2006-01-25
[QUOTE=rwabel]I get the following error message on my dapper when using aplay: aplay: main:533: audio open error: No such device (this message is from the shell)[/QUOTE]
Can you post the output of "**aplay -l**"?

---

### Post by shanghaipi on 2006-01-25
dailer:  I installed your version...I didn't have to have that libort file installed, which is cool.  But I still get this crazy reordering of my contact list sometimes when I'm clicking on my contacts.  Sometimes highlighting contacts, sometimes moving them around.  Very weird.

---

### Post by rwabel on 2006-01-25
rwabel@RALPH:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by cutOff on 2006-01-25
hmm.. weird thing. It looks like mine with SB Live. If you run 'aplay soundfile.wav' from the command line, does it happen?

---

### Post by Grey on 2006-01-26
[QUOTE=dailer]If gaim crashes at startup, you have to delete your profile. You dont have to delete all files, just try it out till it works.[/QUOTE]

That's what I was afraid of.  I'll try that out sometime when I have more time.  Thanks for the tip.

---

### Post by superm1 on 2006-01-26
[quote=Grey]That's what I was afraid of.  I'll try that out sometime when I have more time.  Thanks for the tip.[/quote]
I think the safer way to go is to copy your directory and then delete one at a time, so you can copy back the false positives when you are done.

---

### Post by MBro on 2006-01-26
Great improvements in beta 2 over beta 1.  Is anyone else getting a bug when you try to change your status where the menu shows a large grey box with only the first selection visible and then just a down arrow and you have to hold over the down arrow to see the rest of the menu entries?  I have a feeling this is a GTK bug and not gaim though.

---

### Post by superm1 on 2006-01-26
I am getting that bug.  It is a bit annoying still even if it is a gtk  bug.

---

### Post by christooss on 2006-01-26
Is anyone interested in deb packages for Dapper?

Im making one and I can put it on internet

---

### Post by rwabel on 2006-01-26
sure!

---

### Post by shanghaipi on 2006-01-26
Yes, please....I still get a buddy list bug with the .debs that are on here.

(which I'm still extremely grateful of...by the way)

---

### Post by mattisking on 2006-01-26
Yes please. I'd love a deb!

---

### Post by christooss on 2006-01-27
huh :)Checkinstall gives me error but with make install everything works perfectly.

So I hope deb will be avalible later today.

And I will make an howto. For beta2. Bye

---

### Post by drizzt on 2006-01-27
To install the beta2 you can download
[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=387865](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=387865)

```
sudo alien gaim-2.0.0-0.beta2.fc2.i386.rpm
sudo dpkg -i gaim_2.0.0-1_i386.deb
```

Of course if you don't have "alien" installed just run

```
sudo apt-get install alien
```

---

### Post by rwabel on 2006-01-27
what kind of error do you get? checkinstall doesn't work fine (or it didn't when I was trying it) under dapper. get the latest deb file from the checkinstall homepage and it should work. no more segmentation fault :-)

---

### Post by Riggs on 2006-01-27
I love beta 2.  Using it on both Windows and Ubuntu Breezy.  I would love to find out how to get guifications working....but, I'm still so new to linux that all that make, make install, and configure stuff scares me.  It never works for me when I try something that has me do those steps.

---

### Post by christooss on 2006-01-27
Here you go.
```
wget http://ahacic.5gigs.com/ubuntu/gaim_2.0.0beta2-1_i386.deb
```

```
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb
```

Sound support is included but I don't know how to make it workning. I did't changed anything in dapper about sound.

Please do tell me how to make working sound.

---

### Post by bored2k on 2006-01-27
[QUOTE=christooss]Here you go.
```
wget http://ahacic.5gigs.com/ubuntu/gaim_2.0.0beta2-1_i386.deb
```

```
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb
```

Sound support is included but I don't know how to make it workning. I did't changed anything in dapper about sound.

Please do tell me how to make working sound.[/QUOTE]
Install esound-clients, and in the sound preferences, select custom and enter esdplay %s. You'd also want libao-dev .

I'm using beta2. It's cool :). For the life of it I can't get it to connect to MSN (yes, gnutls is enabled), but heh, not a big issue, I just run aMSN for that.

---

### Post by woedend on 2006-01-27
on another note, do you know by chance how to get the gaim icon in the tray with the beta2?

---

### Post by grendelkhan on 2006-01-27
Dunno, I compiled it myself and it was there like magic.

Has anyone gotten it to compile with --enable-vv?  I know they said they weren't supporting it until the next major release but since the code was there I thought I'd try it anyway.

---

### Post by cutOff on 2006-01-27
[QUOTE=christooss]Here you go.
```
wget http://ahacic.5gigs.com/ubuntu/gaim_2.0.0beta2-1_i386.deb
```

```
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb
```

Sound support is included but I don't know how to make it workning. I did't changed anything in dapper about sound.

Please do tell me how to make working sound.[/QUOTE]
Thanks for that. I'll give it a try.

---

### Post by shanghaipi on 2006-01-28
Sound issues and sorting buddies by status (which I had problems with and noted in earlier posts) are known bugs.  Check it out at: gaim.sourceforge.com

I'm glad that my computer is not insane.

---

### Post by Geekboy on 2006-01-28
Is there a way to turn off the Update Notification for GAIM?

I used the .deb from the first post and GAIM is working fine.  I just want to get rid of that. 

Thanks.

---

### Post by shanghaipi on 2006-01-29
Click on Plugins in the Tools menu, and then unclick the Update Notification plugin.

---

### Post by louis_nichols on 2006-01-29
Gaim 2.0 is indeed great. And, now, with the upcoming merge with gaim-vv, we should see voice and webcam support sometime. So, great howto! Very useful.

Now, I've been using this plugin which I found useful, called autoprofile, and managed to compile t for gaim 2.0. Due to my inexperience in programming, I had to disable the HTTP component, but otherwise it works. It's very useful and I use it to show the XMMS song in the status message. I'm attaching it here.

How to install it:

cd <download folder>
unzip autoprofile.so.zip
mkdir ~/.gaim/plugins
cp autoprofile.so ~/.gaim/plugins/

Then, restart gaim, go to plugins and enable it and use it anyway you like. :) enjoy!

---

### Post by WishMaster on 2006-01-29
gaim2-beta1
- dropdown for sound
- status per account

gaim2-beta2
- sound: command (had to search for which command to use, dropdown is easier)
- no more option to set 1 account on Away. It's all accounts or nothing


What I would like to see:
Subgroups, voice, video, sending custom emoticon, ...

---

### Post by Chrissss on 2006-01-29
[QUOTE=WishMaster]- no more option to set 1 account on Away. It's all accounts or nothing[/QUOTE]
This is still possible, you can define your own status sets. Hit the gigantic status button and scroll down to new. A new window pops up where you can "Use a different status for some accounts". It works, but it is a damn complicated solution, which i personally don't like at all...

CU
 Christoph

---

### Post by WishMaster on 2006-01-29
Yes I know... I f*cking hate it...
I have 2 MSN accounts, 1 ICQ, 1 IRC

Pain in the *** if I just want to set 1 account to Away for a little time...

---

### Post by MighMoS on 2006-01-29
> Is there a way to turn off the Update Notification for GAIM?

I used the .deb from the first post and GAIM is working fine. I just want to get rid of that.

Thanks.Use my debs instead :-).  Or I think it could be that Gaim-data still wants to have the old version of Gaim installed.  Try removing all other gaim stuff, then reinstalling.

---

### Post by tagbre on 2006-01-30
I don't understand why the made so complicated to set different status for each account. Gaim just got unusable for me...:cry: 

I hope they change this for the final.

---

### Post by MighMoS on 2006-01-30
[QUOTE=tagbre]I don't understand why the made so complicated to set different status for each account. Gaim just got unusable for me...:cry: 

I hope they change this for the final.[/QUOTE]
I think its because its trying to make it unified, and not have it matter what account or protocol you're using.  However, due to how much noise I've heard about this, they may include some kind of functionality for ... if they know about it.  Has anyone posted a bug report?

---

### Post by angrykeyboarder on 2006-01-30
[SIZE=3]**If you don't want to mess with CVS.**[/SIZE]

1

$sudo apt-get install fakeroot alien

2

$ wget [http://easynews.dl.sourceforge.net/sourceforge/gaim/gaim-2.0.0-0.beta2.fc4.i386.rpm]("http://easynews.dl.sourceforge.net/sourceforge/gaim/gaim-2.0.0-0.beta2.fc4.i386.rpm")

3.

$ fakeroot alien gaim*.rpm

4

sudo dpkg -i gaim_*.deb

Badda Bing! Badda Boom!

I spent close to two hours trying to complie this thing from source.  After getting continual errors (I'd not properly dotted all the all the Is and crossed all the Ts after "./configure"), I gave up and went the RPM route.

I wanted to avoid that because I've had problems on occassion with RPM packages, but fortunately this went very well.

Gaim 2.0 has some nice new features.  Unfortunatly VV won't be one of them.  [Click here for details.]("http://gaim.sourceforge.net/index.php?id=166")

Also, if you're not a [Sourceforge]("http://sourceforge.net/") member, you might consider becoming one.  It's free.  You'll be able to keep track of your favorite projects that are hosted there and be notified by email when new files are released.  I'm keeping track of Gaim (and about 50 other projects) this way.

---

### Post by MighMoS on 2006-01-30
[QUOTE=angrykeyboarder][SIZE=3]**If you don't want to mess with CVS.**[/SIZE][/QUOTE]
CVS and binary packages are can be, and are, used very different purposed.  Binary packages are "stable" releases, or at least semi-approved.  CVS is used by crack-heads like myself occasionally who either a) want to develop a plugin and have it work with the latest release, b) have a bug in the current release and want to see if its been fixed, or c) just want the new features sooner (bad!  bad!)

But I don't understand the concept of going through converting a foreign format to deb, and going through all of this when there are at least three or four debs compiled for Gaim and linked to all over the place.  Your point is valid, but I think you've misunderstood.  CVS is for people who don't mind getting their hands (or systems) dirty.  But binary packages have been provided for those who just wish to reap the rewards.

---

### Post by Geekboy on 2006-01-30
[quote=MighMoS]Use my debs instead :-).  Or I think it could be that Gaim-data still wants to have the old version of Gaim installed.  Try removing all other gaim stuff, then reinstalling.[/quote] 
I tried you debs and ran into a little problem.  
```
geekboy@geekboypc:~/gaimcvs$ sudo dpkg -i gaim_2.0.0-1beta2_i386.deb
(Reading database ... 75592 files and directories currently installed.)
Preparing to replace gaim 1:2.0.0-1beta2 (using gaim_2.0.0-1beta2_i386.deb) ...
Unpacking replacement gaim ...
dpkg: dependency problems prevent configuration of gaim:
 gaim depends on gaim-data (= 1:2.0.0-1beta2); however:
  Version of gaim-data on system is 1:1.5.0-1ubuntu3.
dpkg: error processing gaim (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gaim

```Any ideas?  Thanks.

---

### Post by lyly on 2006-01-30
[QUOTE=christooss]Here you go.
```
wget http://ahacic.5gigs.com/ubuntu/gaim_2.0.0beta2-1_i386.deb
```
[/QUOTE]

I cannot download this file... I have a "connection refused" error...

---

### Post by MighMoS on 2006-01-30
[QUOTE=lyly]I cannot download this file... I have a "connection refused" error...[/QUOTE]
Install gaim-data and gaim at the same time on the command line.

---

### Post by Geekboy on 2006-01-30
Thanks MighMos, everything worked and Update Notification is off. I typed the following in console:

```
 sudo dpkg -i gaim_2.0.0-1beta2_i386.deb gaim-data_2.0.0-1beta2_all.deb gaim-dev_2.0.0-1beta2_i386.deb
```

---

### Post by christooss on 2006-01-31
iyly try to put url in Webbrowser and manualy download it. It works with me.

---

### Post by lyly on 2006-01-31
[QUOTE=christooss]iyly try to put url in Webbrowser and manualy download it. It works with me.[/QUOTE]

Fine! works well now :)

Thank you

---

### Post by limit223 on 2006-02-03
[QUOTE=WishMaster]Can anyone tell me the difference with beta1 ?

I have beta1, with working Guifications. Don't want beta2 without guifications if there aren't "important" changes in beta2.[/QUOTE]


Same here...and that's why I was thinking to share the new guifications ver deb file that I already made without any issue.

---

### Post by cutOff on 2006-02-04
[QUOTE=limit223]Same here...and that's why I was thinking to share the new guifications ver deb file that I already made without any issue.[/QUOTE]
Thanks for sharing. It works fine.

---

### Post by bschuteker on 2006-02-04
Does it receive offline messages in Yahoo? I have been having a problem with not getting them In 1.5.

---

### Post by BLTicklemonster on 2006-02-04
I got tired of trying, so I went here V and downloaded two, and removed gaim using synaptic, and used alient to create a deb and installed it using double click which can be found in my sig.

No big changes, just some frills from what I can see. 


I wish there was a linux yahoo that allowed voice chat.

---

### Post by Brando569 on 2006-02-05
any way to get rid of the huge away button, the stupid text box below it, and the idle times? if not im going back to 1.5, i can wait a lil while :)

---

### Post by limit223 on 2006-02-05
Does anyone know what perl-dev package do I have to install to include perl support in gaim compilation?

---

### Post by MighMoS on 2006-02-05
[QUOTE=limit223]Does anyone know what perl-dev package do I have to install to include perl support in gaim compilation?[/QUOTE]
No, you don't.  You can explicitly tell it to not enable perl support, or if you don't have perl, the configure script should recognize this, and not include it.  While I don't know if any, or which ones, you may wind up missing some plugins because of this.

---

### Post by limit223 on 2006-02-06
Build Protocol Plugins........ : yes
Protocols to link statically.. :
Protocols to build dynamically : gg irc jabber msn novell oscar simple yahoo zephyr

UI Library.................... : GTK+ 2.x
SSL Library/Libraries......... : GNUTLS

Build with Plugin support..... : yes
Build with Mono support....... : no
**Build with Perl support....... : yes**
Build with Tcl support........ : no
Build with Tk support......... : no
Build with Audio support...... : yes
Build with GtkSpell support... : yes
Build with Voice/Video support : no
Build with DBUS support....... : yes
DBUS session directory........ : /usr/share/dbus-1/services
Build with Cyrus SASL support. : no
Has you....................... : yes


Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification.......: no

Print debugging messages...... : no

Gaim will be installed in /usr/local/bin.

configure complete, now type 'make'


I've got it! I think the perl packages that should be installed in order to have perl support in gaim are: libperl5.8, libperl-dev, libplrpc-perl...
If someone knows exactly the perl packages may correct me, 'cause I installed  in block many other perl files at a time.

---

### Post by mrgnash on 2006-02-28
Thanks, the installation method worked fine :) For future CVS updates would I just follow the same steps again?

---

### Post by WishMaster on 2006-03-05
Just a little thought...

Below is a picture of GAIM beta2.
At the bottom you can see the HUGE "sleeping"-button, and a smaller "disconnected"-button.


[IMG]http://users.pandora.be/Nyx/Linux/Gaim_2.jpg[/IMG]




Why don't we throw away the HUGE buttons, and use smaller ones?
Take a look at picture below (a little fun with The Gimp), and I'll explain.


[IMG]http://users.pandora.be/Nyx/Linux/Gaim_3.jpg[/IMG]

First of all: go back to the beta1-settings, where you could expand the protocol-statusses. 
For example: all you would see, is the yellow "global gaim" button. The size is the small size like the "you disconnected" (from beta2).
You can drag the upperside of the button up, so you can see all the statusses of all your accounts. In the picture, I used 2 MSNaccounts, 1 ICQaccount.

You can set status for each account separetly: in the picture is an example for 1 MSNaccount.
Offcourse the same applies for the other MSNaccount, and the ICQaccount.

If you wish to set ALL your protocols to 1 status (for example: set all your protocols to "away"), then you can use the "global gaim"-button to set 1 status for all protocols.

I think this would be great... 1 SMALL button at the bottom of your contactslist, which you can expand. 
You can chose seperate statusses for each protocol, AND you can set all your protocols to 1 status.

 I know this should be posted in a GAIM-forum, but they suck :p
Anyway, what do you guys think?

---

### Post by lyly on 2006-03-06
[QUOTE=WishMaster]
I think this would be great... 1 SMALL button at the bottom of your contactslist, which you can expand. 
You can chose seperate statusses for each protocol, AND you can set all your protocols to 1 status.

 I know this should be posted in a GAIM-forum, but they suck :p
Anyway, what do you guys think?[/QUOTE]
I vote for it!!!

---

### Post by thewayofzen on 2006-03-12
Anyone having issues compiling the gaim 2.0 cvs in dapper..  as of todays flight 5 i am no longer able to get cvs to build..

---

### Post by christooss on 2006-03-12
matic@ubuntu:~/Desktop$ sudo dpkg -i gaim_2.0.0-1_i386.deb
dpkg - warning: downgrading gaim from 1:1.5.0+1.5.1cvs20051015-1ubuntu6 to 0:2.0.0-1.


How can I stop this? This hapens when I use my deb or if I aien rpm package from source forge.

What can I do????

---

### Post by Klejs on 2006-03-12
Thanks for the HOWTO, Gaim2 is great! :KS :KS :KS :KS :KS

---

### Post by dicecca112 on 2006-03-12
deb worked perfectly here, thanks for the guide

---

### Post by mrgnash on 2006-03-12
Receiving the following error message when I try and log into the cvs: ```
cvs [login aborted]: end of file from server (consult above messages if any)

```

---

### Post by pgmario on 2006-03-27
[quote=christooss]matic@ubuntu:~/Desktop$ sudo dpkg -i gaim_2.0.0-1_i386.deb
dpkg - warning: downgrading gaim from 1:1.5.0+1.5.1cvs20051015-1ubuntu6 to 0:2.0.0-1.


How can I stop this? This hapens when I use my deb or if I aien rpm package from source forge.

What can I do????[/quote]This will stop gaim from updating:```
echo gaim hold | sudo dpkg --set-selections
```This will prevent both apt and Synaptic from trying to update it (setting it in Synaptic won't help you with apt). When you want to update it again and reset it to normal behaviour, do: ```
echo gaim install | sudo dpkg --set-selections
```

---

### Post by Rizado on 2006-03-27
I don't know if anyone have said it yet but, in checkinstall don't name the package gaim. Call it gaim2 or something. Otherwise it can get owerwritten by the old package because it's also called gaim. Apt might try to "update" it.

---

### Post by pgmario on 2006-03-27
[quote=Rizado]I don't know if anyone have said it yet but, in checkinstall don't name the package gaim. Call it gaim2 or something. Otherwise it can get owerwritten by the old package because it's also called gaim. Apt might try to "update" it.[/quote]You could do that. Make sure that you remove the gaim package before installation, though. And, uhm, regarding your question if this was mentioned before...well, at least the fact that apt will try to 'update' it was mentioned **one post before yours**. ;)

---

### Post by Rizado on 2006-03-27
[QUOTE=pgmario]You could do that. Make sure that you remove the gaim package before installation, though. And, uhm, regarding your question if this was mentioned before...well, at least the fact that apt will try to 'update' it was mentioned **one post before yours**. ;)[/QUOTE]:neutral: Hrm Hrm, Yeah, well it is a long thread :p

---

### Post by MighMoS on 2006-03-29
Well, being the guy I am, I've noticed that Gaim Beta3 is tarballed an on the sourceforge mirrors, so I've built up some binaries (sorry, I have no PPC packages for beta3, but the source should build just fine).  They are available at [http://mighmos.org/packages.php](http://mighmos.org/packages.php) .  

These are built on Breezy Badger, I can not say if they will insult your mother, cause your computer to turn into the HAL 9000, or just flat out crash if you install them on Dapper Drake.  6.06 users, you've been warned.

---

### Post by superm1 on 2006-03-29
Wow you must really be on top of things.  I don't even see it mentioned on the gaim homepage yet!

---

### Post by superm1 on 2006-03-29
BTW, these don't run cleanly on dapper.

---

### Post by hey560 on 2006-03-29
[QUOTE=superm1]BTW, these don't run cleanly on dapper.[/QUOTE]

What exactly doesn't "run cleanly" with beta3?? I ask because I wonder its worth the trouble upgrading.

---

### Post by superm1 on 2006-03-29
Well, the breezy builds call for some older version of lib-dbus and lib-glib-dbus.  I just downloaded the tgz and made a checkinstall package to use for now.  I haven't found any *noticable* differences yet from beta 2, but i'm sure something has changed.

---

### Post by WishMaster on 2006-03-29
****

 > **Beta 3: What goes up must fall down? **

 [March 29th, 2006 - 1:27PM EST ]("http://gaim.sourceforge.net/index.php?id=167")
 Great day in the park, we've released Gaim 2.0.0 beta 3.  You know the drill--you can find [assorted builds on our sourceforge page]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=405479"). We'd like to note that none of the beta 3 RPMs include a Gadu-Gadu protocol plugin. So if you need Gadu-Gadu then you should stick with beta 2. And as my pappy always used to say: don't hitch your wagon to a stump if it has eyes. We never did know what he was talking about.
What's up with those (fedora) rpm's? :confused:
We want .deb's ! :)

Any noticable changes?

---

### Post by pgmario on 2006-03-29
[quote=WishMaster]

 What's up with those (fedora) rpm's? :confused:
We want .deb's ! :)

Any noticable changes?[/quote]No, seems as if this is a bugfix-only release. UI and options are exactly the same.

---

### Post by MighMoS on 2006-03-29
By not running cleanly, I mean I have no idea what will happen.  I don't have a Dapper Drake install right now (although I probably will test Flight 6).  Its quite possible everything will work fine, its quite possible nothing will go right.  If someone tests it, some feedback would be great.  

And there aren't too many noticable changes from -beta2 to -beta3.  Mostly bug fixes, translations, and polish.

---

### Post by pgmario on 2006-03-29
I just tried to attach my .deb of beta3 build on Dapper Drake, but it seems as if the forum doesn't allow uploading files that big. If someone wants to host it, send me a pm. 
It's only a checkinstall build and I cannot guarantee that it will work for you. I have an AMD processor, but I didn't compile it with any configuration options exept --enable-gnutls=yes. It works here, but use at your own risk.

---

### Post by pgmario on 2006-03-30
cerix was so kind to host my deb for dapper drake: [http://emailthatguy.shackspace.com/gaim_2.0.0beta3.tar.gz](http://emailthatguy.shackspace.com/gaim_2.0.0beta3.tar.gz)
But keep in mind that it's only a checkinstall build (see my post above).

---

### Post by MighMoS on 2006-03-30
[QUOTE=pgmario]cerix was so kind to host my deb for dapper drake: [http://emailthatguy.shackspace.com/gaim_2.0.0beta3.tar.gz](http://emailthatguy.shackspace.com/gaim_2.0.0beta3.tar.gz)
But keep in mind that it's only a checkinstall build (see my post above).[/QUOTE]
pgmario:  If you want to, just download and compile my source package for Gaim.  The binaries are for 5.10, but the source should compile anywhere.  Then you can have Gaim in the same format the upstream uses (there-by reducing headaches with dependency issues).

---

### Post by pgmario on 2006-03-30
[quote=MighMoS]pgmario:  If you want to, just download and compile my source package for Gaim.  The binaries are for 5.10, but the source should compile anywhere.  Then you can have Gaim in the same format the upstream uses (there-by reducing headaches with dependency issues).[/quote]Thank you for the offer, but it runs fine here. What exactly would be the difference if I recompiled from your source and the official beta3 source?

---

### Post by WishMaster on 2006-03-30
Okay, this is my evil twin speaking (:p)

Below is a screenshot with 
- Gaim2-beta2
- aMSN 0.96b (cvs-snapshot)

_Gaim:_
+ nicely blended with desktop (well duh, **g**nome and **g**aim)
- Very little options for msn-protocol

_aMSN:_
- buttugly (tcl/gtk is just fugly on any windowmanager (even in windows))
+ sending AND receiving of webcam works
+ customizing nicks (alias + nick + pers.msg)
+ sending custom emoticons
+ viewing *personal message* 

[_screenshot_]("http://users.pandora.be/Nyx/Linux/aMSN_0.96b.jpg")

I am not into the discussion wether something is bloated or not. It just shows that is *IS* possible in Linux. 
It would be extremely nice of gaim could incorporate these thingies too (custom nicks, pers.msg, webcam,..). The faster, the better :)

(*if any gaim developper should ever read this: yes I know, "do it yourself or don't moan"*)

---

### Post by lyly on 2006-04-07
[QUOTE=MighMoS]By not running cleanly, I mean I have no idea what will happen.  I don't have a Dapper Drake install right now (although I probably will test Flight 6).  Its quite possible everything will work fine, its quite possible nothing will go right.  If someone tests it, some feedback would be great.  

And there aren't too many noticable changes from -beta2 to -beta3.  Mostly bug fixes, translations, and polish.[/QUOTE]


Does someone also have packaged the guification plugin?

Thx

Lynda

---

### Post by WishMaster on 2006-04-09
Take a look here:
[http://www.ubuntuforums.org/showthread.php?t=152457](http://www.ubuntuforums.org/showthread.php?t=152457)

Gaim2-beta3 plugins

---

### Post by lyly on 2006-04-11
[QUOTE=WishMaster]Take a look here:
[http://www.ubuntuforums.org/showthread.php?t=152457](http://www.ubuntuforums.org/showthread.php?t=152457)

Gaim2-beta3 plugins[/QUOTE]

Thank you!

Lynda

---

### Post by geeknation on 2006-04-12
Just got it working! far better than the old Gaim!

---

### Post by starscalling on 2006-04-30
sudo apt-get build-dep gaim
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  build-essential cdbs comerr-dev g++ g++-4.0 gcc gcc-4.0 libao-dev libao2
  libaspell-dev libatk1.0-dev libaudiofile-dev libbonobo2-dev libc6-dev
  libcairo2-dev libcamel1.2-dev libebook1.2-dev libedata-book1.2-dev
  libedataserver1.2-dev libesd0-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgconf2-dev libgcrypt11-dev libglib2.0-dev libgnome2-dev
  libgnomevfs2-dev libgnutls11-dev libgpg-error-dev libgtk2.0-dev
  libgtkspell-dev libgtkspell0 libhesiod0 libice-dev libidl-dev libkadm55
  libkrb5-dev liblaunchpad-integration-dev libltdl3-dev libnspr-dev libnss-dev
  libopencdk8-dev liborbit2-dev libpango1.0-dev libpng12-dev libpopt-dev
  libsm-dev libstartup-notification0-dev libstdc++6-4.0-dev libtasn1-2-dev
  libx11-dev libxau-dev libxcursor-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev libzephyr-dev libzephyr3 linux-kernel-headers
  tcl8.4-dev tk8.4 tk8.4-dev x-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-scrnsaver-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
0 upgraded, 81 newly installed, 0 to remove and 12 not upgraded.
Need to get 22.6MB of archives.
After unpacking 86.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y



and there u have the supposed build-dep on my fresh breezy install

---

### Post by jk_warrior on 2006-06-06
I couldn't get Gaim2 work with the .deb files provided in this topic (even not the lateste that were compiled for Dapper).

I installed gaim with the .deb files compiled for Dapper provided on the following page:
[http://www.debuntu.org/2006/04/19/31-gaim-200beta3-deb-package-for-ubuntu-dapper](http://www.debuntu.org/2006/04/19/31-gaim-200beta3-deb-package-for-ubuntu-dapper)

I hope I can help people with this information

---

### Post by zarathustra on 2006-06-07
I keep getting this error when trying to install Gaim compiled from their Subversion repository:

> Making install in po
make[1]: Entering directory `/home/nick/svn/gaim/po'
/home/nick/svn/gaim/install_sh -d /usr/share/locale
make[1]: /home/nick/svn/gaim/install_sh: Command not found
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/nick/svn/gaim/po'
make: *** [install-recursive] Error 1


What does this mean? How do I fix it?

---

### Post by zarathustra on 2006-06-07
On an unrelated note, is there any way to display people's nicknames on Yahoo rather than just their usernames?

---

### Post by yorick on 2006-06-08
[QUOTE=zarathustra]On an unrelated note, is there any way to display people's nicknames on Yahoo rather than just their usernames?[/QUOTE]

You can give aliases to the contacts in Yahoo. The aliases will then appear instead of their Yahoo ID's.

---

### Post by Zottan on 2006-06-18
[QUOTE=zarathustra]I keep getting this error when trying to install Gaim compiled from their Subversion repository:



What does this mean? How do I fix it?[/QUOTE]


i have the same the same problem , maybe a error from subversion that could be fixes soon...

---

### Post by Zottan on 2006-06-18
[http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/](http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/)

for x86 and amd64

---

### Post by zarathustra on 2006-06-18
[QUOTE=Zottan][http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/](http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/)

for x86 and amd64[/QUOTE]

[QUOTE=Zottan]i have the same the same problem , maybe a error from subversion that could be fixes soon...[/QUOTE]

I tried asking on the Sourceforge forums for the Gaim project about this, and I was told that my "autotool version is too old" :confused: 

I've been having this problem with subversion versions for a while, even though the beta compiles perfectly.

---

### Post by ruimoura on 2006-06-20
Hi. What i did was getting the latest build of 2.0 for fedora 5 from the official page and then changed it with alien. Instaled. No problem at all. 
But then the update manager keeps tellin me over and over again that there's un update of gaim, that ofcourse is the default version (1.something) ... Can i trick the update manager so he doen't bother me again?

Ps: sorry if this is allready answered, but i did search a lot and didn find something like this ... ](*,)  ... Oh, and sorry about my english #-o

---

### Post by christooss on 2006-06-20
[http://www.debuntu.org/2006/04/19/31-gaim-200beta3-deb-package-for-ubuntu-dapper](http://www.debuntu.org/2006/04/19/31-gaim-200beta3-deb-package-for-ubuntu-dapper)

---

### Post by ruimoura on 2006-06-20
Thank you :)

---

### Post by evilhomer on 2006-06-23
anyone have otr working in 2.0beta3?

i get this from source:

checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 gaim >= 1.0... configure: error: glib
./configure: line 19502: exit: gtk: numeric argument required
./configure: line 19502: exit: gtk: numeric argument required

---

### Post by Zelut on 2006-08-20
evilhomer: I just put together a tutorial for otr 3.0.0 and gaim 2.0beta3.1.  I hope it works.  It uses a snapshot .deb of gaim, not the CVS, but seems to work well.

[Gaim 2.0beta3 + OTR 3.0.0]("http://christer.homeip.net/index.php/2006/08/20/gaim-20beta3-off-the-record-300-ubuntu-dapper/")

I'm looking for an update of gaim 2.0beta3 that doesn't crash when using a SOCKS 5 proxy (for Tor).  Anyone have any tips there?

UPDATE:  Gaim 2.0beta3.1 (released yesterday) solves the issue with the proxy that I had.  This is available in my tutorial on my site.  I hope this works for people.  Any feedback?

---

### Post by WishMaster on 2006-08-27
I installed your deb's (beta3.1, guific and OTR)
works perfect, thanks !

---

### Post by Patskumaster on 2006-08-28
> **kuyaedz said:**
> evilhomer: I just put together a tutorial for otr 3.0.0 and gaim 2.0beta3.1.  I hope it works.  It uses a snapshot .deb of gaim, not the CVS, but seems to work well.

[Gaim 2.0beta3 + OTR 3.0.0]("http://christer.homeip.net/index.php/2006/08/20/gaim-20beta3-off-the-record-300-ubuntu-dapper/")

I'm looking for an update of gaim 2.0beta3 that doesn't crash when using a SOCKS 5 proxy (for Tor).  Anyone have any tips there?

UPDATE:  Gaim 2.0beta3.1 (released yesterday) solves the issue with the proxy that I had.  This is available in my tutorial on my site.  I hope this works for people.  Any feedback?

Big Thanks! Works perfect.

---

### Post by WishMaster on 2006-10-19
Gaim2.0beta4 is out...
.deb's anywone ?

---

### Post by MighMoS on 2006-10-19
I tried packaging it yesterday, but although it compiled, it didn't run.  I'm currently looking into it (or maybe I just grabbed it too soon).

---

