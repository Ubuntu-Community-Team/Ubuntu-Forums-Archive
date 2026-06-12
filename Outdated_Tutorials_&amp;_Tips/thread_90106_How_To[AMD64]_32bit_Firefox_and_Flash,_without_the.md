---
title: "How To[AMD64]: 32bit Firefox and Flash, without the Chroot"
date: 2005-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by RAOF on 2005-11-14
For me the most annoying problem in 64bit Breezy is the lack of a 64bit flash plugin (a small gripe, true, but without flash there is no [Homestar Runner](www.homestarrunner.com)!).  However, after a bit of mucking around, and some help from other forumgoers (particularly Tux61), even this small gripe is now forever banished.

**Update:** now on the Ubuntu wiki, with bonus java plugin!
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

To get a working 32bit firefox, you can follow these steps:
**1)** Download a 32bit binary version of firefox from mozilla.org.  I used the 1.5RC2 build [here]("http://download.mozilla.org/?product=firefox-1.5rc2&os=linux&lang=en-US").  You should be able to use any i386/i686 build, but I haven't tested anything else.

**2)** Unpack the .tar.gz file to your favourite program-installation-directory.  I use a Programs directory under my home directory.  Installing firefox here means I have write privileges, so the automatic update works.  For people who have multiple users on their system, somewhere like /usr/local or /opt is probably a better choice.

**3)** Get the ia32 libs, and linux32 so we can fool firefox into downloading 32bit plugins.
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```

**4)** Create a /etc/pango32/pangorc file:
```
sudo gedit /etc/pango32/pangorc
```
and fill it with this:
```
[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
```

**5)** Create a firefox32 shell script
```
sudo gedit /usr/local/bin/firefox32
```
and fill it with this:
```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /path/to/firefox/firefox $@

```
And finally, make it executable:
```
sudo chmod +x /usr/local/bin/firefox32
```

**6)** Watch your friends be amazed!

You can now edit your firefox launcher(s) to launch firefox32, rather than firefox.  This will use your old firefox profile, and it seems that the Ubuntu packaged firefox & the new 1.5RC2 don't tread on each other's config too badly.  The exception being that I got a thick grey bar at the bottom of the Ubuntu firefox window after running the RC2.

To get flash working, just browse to a site using flash (once again, I suggest [Homestar Runner](www.homestarrunner.com) :)) - you can now just install the plugin normally though firefox!

**Problems:**
When I first installed flash, it sort of worked, and sound played, but where the visuals should have been was blank.  It turns out that this was due to my previous efforts to install flash.  Renaming the ~/.mozilla directory to something else, installing flash, and then copying my bookmarks etc into the new .mozilla directory fixed it.  You should be able to get away with just deleting the .mozilla/plugins directory, and possibly the ./mozilla/pluginreg.dat, but I didn't try that.

Flash sometimes doesn't have sound.  I think that this is due to something else locking the soundcard, but I haven't followed it up at all.  I suspect that following some of the instructions littering this board about flash and sound should fix it :)

---

### Post by jr.gotti on 2005-11-14
i love you?

lol...tiny fix..

you forgot the "sudo chmod 777 /usr/bin/local/firefox32"

other than that it works perfectly! thanks!!

---

### Post by RSX311 on 2005-11-14
awesome it works! sort of, I ran it in a terminal but I keep getting these errors 

```
(firefox-bin:14451): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

```

it just keeps going and going, but firefox still works.  It looks like its not drawing in the theme stuff in the window.   Also it doesn't highlight the pulldown menu items when I mouseover them.  Any ideas?

thanks for the how-to

---

### Post by Bender NZ on 2005-11-15
This is great - now I don't need to bother with a chroot, thanks!

Also - this works with Flock too, just replace the path to firefox with flock.

---

### Post by RSX311 on 2005-11-15
looks like installing a firefox theme fixed the gdkPixbuf error.  Looks like it didn't like my gtk theme. wo0t!

---

### Post by bierpullen on 2005-11-17
This is great !!!



------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.


[http://www.antarctica-rbak.nl/ubuntu/index.php](http://www.antarctica-rbak.nl/ubuntu/index.php)

---

### Post by JuanC on 2005-11-17
I hope the day that Macromedia release the 64bits plugin of Flash and we don't need these tricks to get flash plugin work in an amd64 Linux system.

---

### Post by joris.brus on 2005-11-17
Awesome.. thank you

---

### Post by Corbelius on 2005-11-18
Good howto, work fine ;)

---

### Post by angrykeyboarder on 2005-11-18
[quote=RAOF]For me the most annoying problem in 64bit Breezy is the lack of a 64bit flash plugin (a small gripe, true, but without flash there is no [Homestar Runner]("http://www.homestarrunner.com")!). However, after a bit of mucking around, and some help from other forumgoers (particularly Tux61), even this small gripe is now forever banished.

To get a working 32bit firefox, you can follow these steps:
**1)** Download a 32bit binary version of firefox from mozilla.org.  I used the 1.5RC2 build [here]("http://download.mozilla.org/?product=firefox-1.5rc2&os=linux&lang=en-US").  You should be able to use any i386/i686 build, but I haven't tested anything else.

**2)** Unpack the .tar.gz file to your favourite program-installation-directory. I use a Programs directory under my home directory. Installing firefox here means I have write privileges, so the automatic update works. For people who have multiple users on their system, somewhere like /usr/local or /opt is probably a better choice.

**3)** Get the ia32 libs, and linux32 so we can fool firefox into downloading 32bit plugins.
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
``` 
**4)** Create a /etc/pango32/pangorc file:
```
sudo gedit /etc/pango32/pangorc
``` and fill it with this:
```
[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
``` 
**5)** Create a firefox32 shell script
```
sudo gedit /usr/local/bin/firefox32
``` and fill it with this:
```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /path/to/firefox/firefox $@

``` And finally, make it executable:
```
sudo chmod +x /usr/local/bin/firefox32
``` 
**6)** Watch your friends be amazed!

You can now edit your firefox launcher(s) to launch firefox32, rather than firefox. This will use your old firefox profile, and it seems that the Ubuntu packaged firefox & the new 1.5RC2 don't tread on each other's config too badly. The exception being that I got a thick grey bar at the bottom of the Ubuntu firefox window after running the RC2.

To get flash working, just browse to a site using flash (once again, I suggest [Homestar Runner]("http://www.homestarrunner.com") :)) - you can now just install the plugin normally though firefox!

**Problems:**
When I first installed flash, it sort of worked, and sound played, but where the visuals should have been was blank. It turns out that this was due to my previous efforts to install flash. Renaming the ~/.mozilla directory to something else, installing flash, and then copying my bookmarks etc into the new .mozilla directory fixed it. You should be able to get away with just deleting the .mozilla/plugins directory, and possibly the ./mozilla/pluginreg.dat, but I didn't try that.

Flash sometimes doesn't have sound. I think that this is due to something else locking the soundcard, but I haven't followed it up at all. I suspect that following some of the instructions littering this board about flash and sound should fix it :)[/quote]

Can't one just

"sudo apt-get remove firefox"

and then....

sudo dpkg -i  "firefox_1.0.7-0ubuntu20_i386.deb" ?

---

### Post by jr.gotti on 2005-11-18
no. you cant just install 32 bit software on 64 bit hardware.

---

### Post by RAOF on 2005-11-19
[QUOTE=angrykeyboarder]Can't one just

"sudo apt-get remove firefox"

and then....

sudo dpkg -i  "firefox_1.0.7-0ubuntu20_i386.deb" ?[/QUOTE]
I don't think so, not quite.  Although it is true that you shouldn't have to install one of the mozilla.org builds.

While you **can** install 32bit software on the 64bit system (that's one of the big selling points of x86_64), you'll need to pass --force-architecture to dpkg (because the .deb will be for a "different" architecture, i386), and you'll probably still need most of the rest (pangorc, gtk_path stuff), because that makes sure that the 32bit binary can find the 32bit GTK stuff.

Essentially, it's written to install the 1.5RC because that's cooler than just installing the latest Ubuntu .deb :)

---

### Post by Robby89 on 2005-11-27
Great work, very much appreciated.

---

### Post by angrykeyboarder on 2005-11-27
[quote=RAOF]I don't think so, not quite.  Although it is true that you shouldn't have to install one of the mozilla.org builds.

While you **can** install 32bit software on the 64bit system (that's one of the big selling points of x86_64), you'll need to pass --force-architecture to dpkg (because the .deb will be for a "different" architecture, i386), and you'll probably still need most of the rest (pangorc, gtk_path stuff), because that makes sure that the 32bit binary can find the 32bit GTK stuff.

Essentially, it's written to install the 1.5RC because that's cooler than just installing the latest Ubuntu .deb :)[/quote] 
IMHO, one of the *few *advantages Fedora Core has over any Debian-based distribution is that it's primary package management system ([YUM]("http://linux.duke.edu/projects/yum/")) allows easy installation of 32-bit packages on a X86_64 (e.g. amd64) system.

Somehow, I thought it was all hype, but apparently it's true.

However, from a speed of installation perspective, "yum install <package x>" is no match for "apt-get install <package x>".

---

### Post by angrykeyboarder on 2005-11-27
[quote=pixelPOET]no. you cant just install 32 bit software on 64 bit hardware.[/quote]

Not true. See the posts that follow...

---

### Post by raydel on 2005-11-29
Thanks alot RAOF. Your setup worked flawlessly.  Perhaps I'm picky but, does anyone how I get the icon to show in window title.  I tried assigning a "custom icon" to the script then the run-mozilla.sh and firefox in my 32 bit directory.  Didn't work.  Should I be looking in gconf?  Or maybe a meta-city XML file?

---

### Post by janfsd on 2005-11-29
i got a problem,when i want to execute firefox with firefox32 i got this error:

```
Cannot execute /home/juanito/programs/32b/firefox: Permission denied

```

plz can sbody help?

---

### Post by raydel on 2005-11-29
Did you make the script that RAOF posted and did you make exacutable?

---

### Post by janfsd on 2005-11-29
yeah i did everything, even checked the permission of the folder where firefox is, but all is ok. Ive tried to execute it manually with ./firefox and it works ok with the flash plugin, but sometimes i get some pango errors for example when i get to the preferences and in downloads section:

```
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9354): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./run-mozilla.sh: line 131:  9354 Aborted                 "$prog" ${1+"$@"}

```

but with firefox32 i still get the same error like before (permission denied)

---

### Post by RAOF on 2005-11-29
Are you **sure** you haven't ommitted the
```
sudo chmod +x /usr/local/bin/firefox32
```
step?  That gives you permissions to run the firefox32 script.

On second thought, looking at your actual error, is
```
/home/juanito/programs/32b/firefox
```
an actual file, or is it the firefox **directory**?  Perhaps you should have put
```
/home/juanito/programs/32b/firefox/firefox
``` in your script.

Incidentally, the pango errors you get when you just run ./firefox are becuase it's using the default (64bit) pango, and you can't load the 64bit libraries for a 32bit app.  That's what the script sets up :)

---

### Post by janfsd on 2005-12-01
Thanks RAOF, the problem was that i forgot the last .../firefox/firefox, now that works.
But about the pango error i cannot configure for example the downloads option 'cause it always makes firefox crash, does anybody have the same "pango" problem?

---

### Post by Bloot on 2005-12-01
Well it works for me, but now there's something annoying I would like to solve. How can I add an icon on the opened applications buttons? I mean this:

[img]http://www.telefonica.net/web/expressimages/Pantallazo.png[/img]

---

### Post by MeijUbuntu on 2005-12-01
This is great. It really works !!!

Only one little question. On my AMD64 it was possible with Firefox 1.0.7 to show some streams (i think totem plugin or something). On the new 1.5 (32 bits) it doesn't seems to work ?

Any ideas ?

Thnx

---

### Post by RAOF on 2005-12-01
@janfsd - Does that pango error happen even when you run firefox32?  Odd.  That doesn't happen to me.

@Bloot - Yeah, I don't know how to fix the icons.  And you might notice that **none** of the (GTK) icons work properly (even the "ok" icons etc).  This should be fixable, but I don't really know where to start.

@MeijUbuntu - I'm pretty sure that you won't be able to get totem integration with this 32bit binary, unless you also install a 32bit version of Totem.  It might be possible, but I think it'll be a lot of effort.

---

### Post by PolarBear64 on 2005-12-02
OK i need help on this, tried to do it and keep getting the mozilla quaility feed back agent no browser, here is exactly what i did.


sudo apt-get install ia32-libs ia32-libs-gtk linux32
"no problems with get install"

sudo gedit /etc/pango32/pangorc

Filled with-

[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases

sudo gedit /usr/local/bin/firefox32

filled with-

#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pngorc
linux32 /home/firefox/firefox $@

and then executed

sudo chmod +x /usr/local/bin/firefox32

I have very little experience with linux so not sure if i am using command line right or have my directory paths right as there is no bar showing me the exact path to the folder i am in that I can find.

any help or comments would be greatly apreciated i am looking forward to learning how to use linux and Ubuntu has me feeling good so far.

thanks

---

### Post by MeijUbuntu on 2005-12-02
[QUOTE=PolarBear64]

sudo gedit /usr/local/bin/firefox32

filled with-

#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pngorc
linux32 /home/firefox/firefox $@

thanks[/QUOTE]

Hello Polarbear64,

are you sure you installed (untar) the firefoz files to the directory you mentioned in your /usr/local/bin/firefox32 file (linux32 /home/firefox/firefox $@).

And are they write enabled ?

---

### Post by John Mytton on 2005-12-02
Works awesomely. 

I thank you for gifting me with the ability to play celebrity strip games when I should be working :D

---

### Post by PolarBear64 on 2005-12-02
[QUOTE=MeijUbuntu]Hello Polarbear64,

are you sure you installed (untar) the firefoz files to the directory you mentioned in your /usr/local/bin/firefox32 file (linux32 /home/firefox/firefox $@).

And are they write enabled ?[/QUOTE]

with my limited knowledge I cant be 100% sure but i know i unpacked firefox in my home directory using console to unpack.  unpacker produced folder firefox in my home directory and need to run the firefox program in that folder so seems to me
that should be=

/home/firefox/firefox

I could be wrong

---

### Post by MeijUbuntu on 2005-12-02
[QUOTE=PolarBear64]with my limited knowledge I cant be 100% sure but i know i unpacked firefox in my home directory using console to unpack.  unpacker produced folder firefox in my home directory and need to run the firefox program in that folder so seems to me
that should be=

/home/firefox/firefox

I could be wrong[/QUOTE]

Normally your home directory will be : /home/polarbear64/firefox/firefox

Just replace polarbear64 with your real loginname !

---

### Post by makushimu on 2005-12-02
Thank you! Great how-to, worked well for me.

---

### Post by PolarBear64 on 2005-12-03
thanks for replies,

tried /home/don/firefox/firefox

no luck

still gives me the error report window thing

guess I will have to keep playing with it

if anyone thinks of anything else I apreciate all the help thanks

---

### Post by Bloot on 2005-12-03
[QUOTE=RAOF]Yeah, I don't know how to fix the icons.  And you might notice that **none** of the (GTK) icons work properly (even the "ok" icons etc).  This should be fixable, but I don't really know where to start.[/QUOTE]

Yes I guess there's something missing with the gtk engine. Anyway it's awesome to have flash player running on an amd64 ubuntu without all the chroot pain!. Thanks.

[QUOTE=PolarBear64]thanks for replies,

tried /home/don/firefox/firefox

no luck

still gives me the error report window thing

guess I will have to keep playing with it

if anyone thinks of anything else I apreciate all the help thanks[/QUOTE]

You must link the route to the script called firefox32 instead of the firefox launcher.

---

### Post by Bloot on 2005-12-03
sorry I just wanted to edit the post above.

---

### Post by PolarBear64 on 2005-12-03
Bloot, im not sure what you mean could you give me a terminal comand / or file edit 
example.

thanks

---

### Post by Bloot on 2005-12-03
Of course, I'll try.

You said you tried /home/don/firefox/firefox, that's the firefox path, but you must put instead the route to the script you created called firefox32 (because I assume you created it, as **RAOF**'s how-to says).

For example, in my case i had to type /usr/local/bin/firefox32 because that's the place I put the script.

The script launchs firefox.

Hope I could have helped you with my limited english (sorry).

---

### Post by PolarBear64 on 2005-12-03
Bloot,

took me some thinking what you were trying to tell me was to launch the script I made not the normal firefox program.

worked like a champ got it up and running thanks for the help.

now off to the hard ware section to try and figure out why my dvi no longer works just my vga portion of video card.

thanks for the great how to here.

---

### Post by curtistee on 2005-12-04
Umm... No workum w/Firefox 1.5. Looks like it does (installs plugin, blah woof), but movies show up as white screen. But then again, that's not necessarily a bad thing, is it?

---

### Post by RAOF on 2005-12-04
[QUOTE=curtistee]Umm... No workum w/Firefox 1.5. Looks like it does (installs plugin, blah woof), but movies show up as white screen. But then again, that's not necessarily a bad thing, is it?[/QUOTE]

I'd check out this:
[quote=RAOF]
When I first installed flash, it sort of worked, and sound played, but where the visuals should have been was blank. It turns out that this was due to my previous efforts to install flash. Renaming the ~/.mozilla directory to something else, installing flash, and then copying my bookmarks etc into the new .mozilla directory fixed it. You should be able to get away with just deleting the .mozilla/plugins directory, and possibly the ./mozilla/pluginreg.dat, but I didn't try that.
[/quote]

---

### Post by BorgHunter on 2005-12-06
[QUOTE=raydel]Thanks alot RAOF. Your setup worked flawlessly.  Perhaps I'm picky but, does anyone how I get the icon to show in window title.  I tried assigning a "custom icon" to the script then the run-mozilla.sh and firefox in my 32 bit directory.  Didn't work.  Should I be looking in gconf?  Or maybe a meta-city XML file?[/QUOTE]
Yeah, I'm having the same issue. Tried a couple things, including putting an XPM for firefox32 in /usr/share/pixmaps/, but no dice.

---

### Post by Nyvhek on 2005-12-06
Flash works fine for me, on Firefox 1.5, except for sound--but I'll leave that issue for later. Thanks for the guide.

I would actually like to use the 32-bit Firefox like this as my primary browser (instead of 64-bit Firefox), but I'm running into a problem--when I download a file and tell it to open it (instead of saving to disk), it doesn't work. The file downloads fine, but then the program to open it never launches. Clicking the Open link in the Download dialog doesn't do anything either. Is this some kind of problem with a 32-bit program trying to run a 64-bit one?

(Also, if anyone has managed to get the Acrobat Reader plugin working on this setup, please let me know how.)

---

### Post by RSX311 on 2005-12-06
[QUOTE=Nyvhek]Flash works fine for me, on Firefox 1.5, except for sound--but I'll leave that issue for later. Thanks for the guide.

I would actually like to use the 32-bit Firefox like this as my primary browser (instead of 64-bit Firefox), but I'm running into a problem--when I download a file and tell it to open it (instead of saving to disk), it doesn't work. The file downloads fine, but then the program to open it never launches. Clicking the Open link in the Download dialog doesn't do anything either. Is this some kind of problem with a 32-bit program trying to run a 64-bit one?

(Also, if anyone has managed to get the Acrobat Reader plugin working on this setup, please let me know how.)[/QUOTE]

You have to go to Edit -> Preferences - > Downloads -> and edit the actions for each file type, pain in the butt....

---

### Post by Nyvhek on 2005-12-07
Doesn't seem to work...the same thing happens, it shows up in the download dialog and completes, but then the program never runs. Or is there something specific I'm supposed to be changing these actions to?

---

### Post by curtistee on 2005-12-08
[QUOTE=RAOF]I'd check out this:[/QUOTE]

WOOT! You'd think I'd know how to RTFM at this point ;-)

Works fine now; thanks for rubbing my nose in it.

---

### Post by HellSpawn on 2005-12-10
Hello!!

I made all the apt's checked the packges... re-checked every step.. and I still get this:

> igor@ubuntu:~$ /usr/local/bin/firefox32
/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory


After a locate I get this:
> root@ubuntu:/opt # locate libgtk-x11
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/vmware/lib/libgtk-x11-2.0.so.0
/usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.800.6


I'm kinf of lost here... any help on what I'm I missing??... What else should I check??
:confused: :confused: 

It seems to worked out allright for lots of people... So I must be missing something :confused: :(

---

### Post by RAOF on 2005-12-11
Are you **sure** you've got the ia32-libs-gtk package installed?  All of the libraries you have listed there are 64bit.

---

### Post by HellSpawn on 2005-12-11
[QUOTE=RAOF]Are you **sure** you've got the ia32-libs-gtk package installed?  All of the libraries you have listed there are 64bit.[/QUOTE]

Well... Yes I had it installed....

Here is the thing... there was some kind of conflict beetween the libs... so I tryed this

> sudo apt-get install  **--reinstall** ia32-libs-gtk

And it kind of worked for a moment, so I decided to do this

> sudo apt-get install **--reinstall** ia32-libs ia32-libs-gtk linux32

And it worked... but... Firefox 1.5 keeps crashing after a while and then it let me with problems with my Noia Theme on the firefox 64bits (1.5 updated it to an incompatible version)... so I forgot about the whole thing... I'll keep Wine + IE for flash stuff until Ubuntu gets a 1.5 Firefox 64bits and Macromedia gets 64 bits plugin....

---

### Post by WirelessMike on 2005-12-16
[QUOTE=HellSpawn]

*snip*

And it worked... but... Firefox 1.5 keeps crashing after a while and then it let me with problems with my Noia Theme on the firefox 64bits (1.5 updated it to an incompatible version)... so I forgot about the whole thing... I'll keep Wine + IE for flash stuff until Ubuntu gets a 1.5 Firefox 64bits and Macromedia gets 64 bits plugin....[/QUOTE]

I like that theme, too.  At the time I'm writing this, there isn't a backwards-compatible version of the Noia theme.

Say--  How did you get wine to work on 64?

By the way--  have you tried installing flock?  It's very similar to firefox, though slightly faster with pageloads, and doesn't access your firefox profile directory.  To make it stable, though, you'll still have to go through the setup RAOF outlines, only identifying the flock install directory instead of firefox, and naming the executable "flock32" or whatever to launch with.

Seriously, though--  I'm very interested in the wine install on 64...

---

### Post by HellSpawn on 2005-12-18
[QUOTE=WirelessMike]
Say--  How did you get wine to work on 64?

.............

Seriously, though--  I'm very interested in the wine install on 64...[/QUOTE]

I just got a CrossOver Office copy, it installed with no problems...
But I remember that I compiled wine on fedora 64 once... but couldn't run 32bits bins...

---

### Post by RAOF on 2005-12-19
[QUOTE=WirelessMike]...
Say--  How did you get wine to work on 64?
...[/QUOTE]
Short answer: Do the same thing as this guide (plus a tiny bit of extra fiddling), download a 32bit binary deb, and install using dpkg -i --force-architecture.

Long answer:  [see this thread]("http://www.ubuntuforums.org/showthread.php?t=96620").  It works.  At least, I think it does.  I have pretty low expectations of wine, and it runs at least some windows stuff for me.  I don't think I'll be putting this up as a howto, though.

---

### Post by rplantz on 2005-12-20
Firefox32 seems to work fine, but now my original (1.0.7 64-bit) is partially broken.

I say "partially" because it works fine for some sites (e.g., I'm using it now), but not for others. E.g. not on [http://www.sonoma.edu](http://www.sonoma.edu).

So, what have I broken?

Edit: I tried reinstalling the 64-bit version of Firefox; no change.

---

### Post by rplantz on 2005-12-20
I think I've figured out how this can break the 64-bit version.

I renamed my ~/.mozilla/plugins directory, which fixed the problem. Of course, firefox32 no longer has the plugins.

I think that when I started the 64-bit version and went to a page that uses flashplayer, the 32-bit flashplayer in the plugins directory was started. That causes (64-bit) firefox to crash. The example page I gave above will work without flashplayer.

---

### Post by wakingeden on 2005-12-23
~Keep this up there bump~

---

### Post by Luthy on 2006-01-01
[QUOTE=RAOF]For me the most annoying problem in 64bit Breezy is the lack of a 64bit flash plugin (a small gripe, true, but without flash there is no [Homestar Runner](www.homestarrunner.com)!).  However, after a bit of mucking around, and some help from other forumgoers (particularly Tux61), even this small gripe is now forever banished.

To get a working 32bit firefox, you can follow these steps:
**1)** Download a 32bit binary version of firefox from mozilla.org.  I used the 1.5RC2 build [here]("http://download.mozilla.org/?product=firefox-1.5rc2&os=linux&lang=en-US").  You should be able to use any i386/i686 build, but I haven't tested anything else.

**2)** Unpack the .tar.gz file to your favourite program-installation-directory.  I use a Programs directory under my home directory.  Installing firefox here means I have write privileges, so the automatic update works.  For people who have multiple users on their system, somewhere like /usr/local or /opt is probably a better choice.

**3)** Get the ia32 libs, and linux32 so we can fool firefox into downloading 32bit plugins.
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```

**4)** Create a /etc/pango32/pangorc file:
```
sudo gedit /etc/pango32/pangorc
```
and fill it with this:
```
[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
```

**5)** Create a firefox32 shell script
```
sudo gedit /usr/local/bin/firefox32
```
and fill it with this:
```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /path/to/firefox/firefox $@

```
And finally, make it executable:
```
sudo chmod +x /usr/local/bin/firefox32
```

**6)** Watch your friends be amazed!

You can now edit your firefox launcher(s) to launch firefox32, rather than firefox.  This will use your old firefox profile, and it seems that the Ubuntu packaged firefox & the new 1.5RC2 don't tread on each other's config too badly.  The exception being that I got a thick grey bar at the bottom of the Ubuntu firefox window after running the RC2.

To get flash working, just browse to a site using flash (once again, I suggest [Homestar Runner](www.homestarrunner.com) :)) - you can now just install the plugin normally though firefox!

**Problems:**
When I first installed flash, it sort of worked, and sound played, but where the visuals should have been was blank.  It turns out that this was due to my previous efforts to install flash.  Renaming the ~/.mozilla directory to something else, installing flash, and then copying my bookmarks etc into the new .mozilla directory fixed it.  You should be able to get away with just deleting the .mozilla/plugins directory, and possibly the ./mozilla/pluginreg.dat, but I didn't try that.

Flash sometimes doesn't have sound.  I think that this is due to something else locking the soundcard, but I haven't followed it up at all.  I suspect that following some of the instructions littering this board about flash and sound should fix it :)[/QUOTE]

Your [www.homerunner.com](www.homerunner.com) i couldnt see anything. but how come i can see other flash programs? And im pretty much a newbie, can you be more detailed? Thanks!

---

### Post by Gsundbrunn on 2006-01-04
Hi,

worked quite well for me - thanks a lot. But.... I cannot start galeon or Epiphany anymore after following your installation manual. Get this error:

failed to initialize shared library libXt.so
failed to initialize shared library libXext.so 

Guess it was caused by:
sudo apt-get install ia32-libs ia32-libs-gtk linux32

Any chance to get all browsers to work??

Best regards

Stefan

---

### Post by APwrs on 2006-01-05
It'll be nice when Ubuntu gets a decent 32-bit compatability library up and running like Mandriva has, so that way 32-bit programs will "just work" without all of the extra messing around.

---

### Post by R3linquish3r on 2006-01-05
how do i get flash installed cause it will only let me manual install.

---

### Post by R3linquish3r on 2006-01-05
ok the thing is i was still on 64 when i tried to isntall flash. i cant get firefox32 to execute. i tried the icon and using shell. here is shell after a couple attempts:

> ed@ubuntu:~$ sudo chmod +x /usr/local/bin/firefox32
ed@ubuntu:~$ cd /usr/local/bin
ed@ubuntu:/usr/local/bin$ firefox32
Cannot execute home/ed/firefox/firefox-bin: No such file or directory
ed@ubuntu:/usr/local/bin$ ./firefox32
Cannot execute home/ed/firefox/firefox-bin: No such file or directory
ed@ubuntu:/usr/local/bin$ .firefox32
bash: .firefox32: command not found
ed@ubuntu:/usr/local/bin$ cd
ed@ubuntu:~$ sudo chmod +x /usr/local/bin/firefox32


/home/ed/firefox is the direxctory the i383 one that i downloaded per instructions resides in. here is my firefox32 script:

> #!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /home/ed/firefox/firefox


anyone know waht i have wrong?

note: i did the chmod thing to make it exacutable already.

---

### Post by R3linquish3r on 2006-01-05
wait i figured out waht i was oding wrong. works fine now. thx for it :D

---

### Post by Josef K. on 2006-01-11
GREAT HOWTO!!!

but how can I add multimedia plugin (like kaffeine or totem...) to firefox using 
this system? :confused:

---

### Post by hunteramor on 2006-02-10
great work!  great to be able to rearrange tabs finally.

count me among the frustrated, though, when it comes to the icons disappearing.  lots of... respect to the person that figures out how to fix that issue!

---

### Post by neufena on 2006-02-10
Does anyone know how to install the java plugin on firefox32 without a chroot?

Thanks,

---

### Post by thcpuffnstuff on 2006-02-14
Currently experiencing some difficulty with this installation, followed the instructions as accurately as possible, but getting the following errors..

sdf@ubuntu:~$ /usr/local/bin/firefox32

(firefox-bin:10000): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:10000): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:10000): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
Pango:/etc/pango32/pangorc:1: A [SECTION] declaration must occur first

(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10000): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/local/firefox32/run-mozilla.sh: line 131: 10000 Aborted                 "$prog" ${1+"$@"}

The mozilla quality feedback wizard opens up immediately after.

I have thus far tried most of the steps and solutions offered to those with similar troubles in this thread, however to no avail. 

Any Advice?

---

### Post by RavenMokel on 2006-02-14
thanks a lot for this howto, now i have a working ff 1.5 with flash (and just installed the flashblock extension because of some annoying flash banners, but at least now i **can** watch flash anims, if i want to...).

there are only two problems left, that other people on this already mentioned:

1. how to get a java-plugin working with this?
2. why doesn't it open anything directly if i click "open with..." on a download link? the other program seems to be run, but seems to hang indefinitely...

-Raven

---

### Post by RAOF on 2006-02-14
There's a slightly fuller howto on the wiki now - it includes installing a java plugin.  Check it out at [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

---

### Post by tomthetux on 2006-03-22
I get this error if I will execute the 32bit FireFox!

```

(firefox-bin:13173): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:13173): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:13173): Gtk-WARNING **: cannot open display:

```

I set all permissions right, I think :/
What should I do now?

tomthetux

---

### Post by linuxted on 2006-03-22
When I try getting flash (after agreeing to the Macromedia terms) the GUI just sits there for minutes (last I tried it was fifteen minutes before I gave up).  Are there any suggestions?  I really would like flash working on my system.

I was trying to download Flash on my 32bit firefox by the way.


thanks

[QUOTE=RAOF]For me the most annoying problem in 64bit Breezy is the lack of a 64bit flash plugin (a small gripe, true, but without flash there is no [Homestar Runner](www.homestarrunner.com)!).  However, after a bit of mucking around, and some help from other forumgoers (particularly Tux61), even this small gripe is now forever banished.

**Update:** now on the Ubuntu wiki, with bonus java plugin!
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

To get a working 32bit firefox, you can follow these steps:
**1)** Download a 32bit binary version of firefox from mozilla.org.  I used the 1.5RC2 build [here]("http://download.mozilla.org/?product=firefox-1.5rc2&os=linux&lang=en-US").  You should be able to use any i386/i686 build, but I haven't tested anything else.

**2)** Unpack the .tar.gz file to your favourite program-installation-directory.  I use a Programs directory under my home directory.  Installing firefox here means I have write privileges, so the automatic update works.  For people who have multiple users on their system, somewhere like /usr/local or /opt is probably a better choice.

**3)** Get the ia32 libs, and linux32 so we can fool firefox into downloading 32bit plugins.
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```

**4)** Create a /etc/pango32/pangorc file:
```
sudo gedit /etc/pango32/pangorc
```
and fill it with this:
```
[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
```

**5)** Create a firefox32 shell script
```
sudo gedit /usr/local/bin/firefox32
```
and fill it with this:
```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /path/to/firefox/firefox $@

```
And finally, make it executable:
```
sudo chmod +x /usr/local/bin/firefox32
```

**6)** Watch your friends be amazed!

You can now edit your firefox launcher(s) to launch firefox32, rather than firefox.  This will use your old firefox profile, and it seems that the Ubuntu packaged firefox & the new 1.5RC2 don't tread on each other's config too badly.  The exception being that I got a thick grey bar at the bottom of the Ubuntu firefox window after running the RC2.

To get flash working, just browse to a site using flash (once again, I suggest [Homestar Runner](www.homestarrunner.com) :)) - you can now just install the plugin normally though firefox!

**Problems:**
When I first installed flash, it sort of worked, and sound played, but where the visuals should have been was blank.  It turns out that this was due to my previous efforts to install flash.  Renaming the ~/.mozilla directory to something else, installing flash, and then copying my bookmarks etc into the new .mozilla directory fixed it.  You should be able to get away with just deleting the .mozilla/plugins directory, and possibly the ./mozilla/pluginreg.dat, but I didn't try that.

Flash sometimes doesn't have sound.  I think that this is due to something else locking the soundcard, but I haven't followed it up at all.  I suspect that following some of the instructions littering this board about flash and sound should fix it :)[/QUOTE]

---

### Post by matsur on 2006-03-26
I get the locale error now too... which package upgrade broke it?!?!

---

### Post by matsur on 2006-03-26
[QUOTE=linuxted]When I try getting flash (after agreeing to the Macromedia terms) the GUI just sits there for minutes (last I tried it was fifteen minutes before I gave up).  Are there any suggestions?  I really would like flash working on my system.

I was trying to download Flash on my 32bit firefox by the way.


thanks[/QUOTE]
If you launch firefox32 from a terminal I bet you will get the locale error.

Launching firefox32 from my chroot (mostly) works. Last time I got locale errors a restart fixed the problem; no such luck the second time the error manifested itself.

---

### Post by dcstar on 2006-04-02
If you want to get an AMD optimised version of Firefox, look here:

[http://ubuntuforums.org/showthread.php?t=142798](http://ubuntuforums.org/showthread.php?t=142798)

---

### Post by The Running Board on 2006-04-03
I thought that the wiki seemed straight forward...and I did everything as it said other than I didnt use /usr/local/firefox32, but rather used /home/kyle/firefox32 (maybe thats my prob). Anyways, when I redirected firefoxs launcher to the new one, it crashes everytime and tries to send a reports to mozilla. And when I firefox32 & in terminal I get this...

> kyle@lappyUBUNTU64:~$ firefox32 &
/usr/local/bin/firefox32: line 1: config.log: command not found
[1] 8611
kyle@lappyUBUNTU64:~$
(firefox-bin:8623): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:8623): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8623): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported


---

### Post by avidsensei on 2006-05-16
i cant get firefox32 to launch... heres what i did to set it up
1. i downloaded firefox32 1.5 from the link posted in the how to then i ran these commands


kyle@fast64:~$ sudo apt-get install ia32-libs ia32-libs-gtk linux32
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
linux32 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kyle@fast64:~$ sudo gedit /etc/pango32/pangorc
kyle@fast64:~$ sudo gedit /usr/local/bin/firefox32
kyle@fast64:~$ sudo chmod +x /usr/local/bin/firefox32
kyle@fast64:~$ sudo chmod 777 /usr/bin/local/firefox32
chmod: cannot access `/usr/bin/local/firefox32': No such file or directory
kyle@fast64:~$ sudo chmod 777 /usr/bin/local/firefox32
chmod: cannot access `/usr/bin/local/firefox32': No such file or directory
kyle@fast64:~$ sudo chmod +x /usr/local/bin/firefox32
kyle@fast64:~$



in the gedit files i deleted everything then i repasted the stuff suggested. any help would be apreciated

---

### Post by panurge77 on 2006-05-22
I'm having this error while trying to download from sourceforge. Any idea how to fix it?

floyd@tchs:~$ firefox32

(firefox-bin:4915): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory

(firefox-bin:4915): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(firefox-bin:4915): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory
/opt/swiftfox/run-mozilla.sh: line 131: 4915 Segmentation fault "$prog" ${1+"$@"}

---

### Post by panurge77 on 2006-05-24
Ok. Now I'm only missing sound on youtube. Anyone got that fixed?

---

### Post by frodon on 2006-06-05
Does this guide works for dapper ?

---

### Post by holomorph on 2006-06-23
[QUOTE=HellSpawn] I'll keep Wine + IE for flash stuff until Ubuntu gets a 1.5 Firefox 64bits and Macromedia gets 64 bits plugin....[/QUOTE]

why not install windows firefox under wine?  That's my setup currently, flash free browsing most of the time, unless i realy want to see it *cough*strongbad*cough* and then I fire up windows firefox. 

But I guess you probably installed IE when you installed wine so it's already there.

And for the person who asked how to install wine on 64 bit, I *think* it was as easy as downloading the .deb and doing dpkg -i --force-architecture wine (or whatever that package was called).  I've seen posts on compiling wine for 64 bit, but then I wouldn't be surprised if it didn't run 32 bit windows apps too well.

---

### Post by jinacio on 2006-06-23
howto fix the "GdkPixbuf-CRITICAL" problem:

most probably you have a theme that either firefox or ia32-libs-gtk don't seem to like.

edit /usr/local/bin/firefox32 and add this line somewhere before the "linux32" cmd:
```
export GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc
```

This will fix firefox to use the Human theme. you can also use other themes (like clearlooks, or try others that work)

Hope it helps

---

