---
title: "HOWTO: Nice looking Opera"
date: 2005-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by monotux on 2005-10-18
I've seen one tutorial or two on this subject, but since none worked, I decided to write one, on how I did make it work.

**Install Opera**
If you haven't already, download opera from opera.com - I used opera_8.50-20050916.6-shared-qt_en_etch_i386.deb, and install it:
```
dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
```
...and install any missing dependencies:
```
apt-get install -f
```
*Unsure about dependencies?*
[http://ubuntuforums.org/showthread.php?t=78626](http://ubuntuforums.org/showthread.php?t=78626)

**Make it look good**
I'm not sure everyone knows this, but you can tell opera to use QT widgets instead of motif, by starting opera like this:
```
opera --style default
```

If you get a popup at startup, something about "operamotifwrapper", you need to create a symlink.
First, fire up a terminal and go to /usr/lib/opera/plugins.
Try to start operamotifwrapper-3 ("./operamotifwrapper-3"), and if the output is something similar to this:```
./operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
```
...you might have to do a quick hack.

This guide used a soft link to make this silly hack, but since I think it ruined more than helped, I think copy is the way to go.
```
cd /usr/lib; cp libXm.so.2 libXm.so.3
```

**The Smart Method (tm)**
I know there are a few debian zealots out there, who doesn't like to mess around in /usr/lib - so here is a solution for your sexuality ;)

*I haven't tested this - can someone confirm this actually works?*
It shouldn't matter where you do this from (paths etc):
```
ln -s ../../libXm.so.2.0.1 /usr/lib/opera/8.50-20050916.6/libXm.so.3

```
Note: Some might refer to this as a anal method.:smile: 

Try to start opera ("opera --style default") again.
It should work.

**Make it look even better**
When you get tired of starting opera with "--style default", there is another easy "hack" (well, it's not a hack, but I can't find any other description that's good enough) you can try!
First of all, take a backup of the opera starter - 
```
sudo cp /usr/bin/opera /root/opera-org
```

Then, open the opera starter (it's a text-file, not a binary) with your favourite editor  - 
```
sudo gedit /usr/bin/opera
```

Go down to line 8, that starts with "passflags=", and change it to something like this:
```
# Parse commandline parameters
passflags='--style default'
```

Now opera always will start with --style default.

**Changing QT-styles**
This isn't very hard either, and there's who way's to go at this point, and you can use them both.

*Using qtconfig*
Since a few people out there doesn't want to install any kde packages more than necessary, they can change the QT-theme by installing and using qtconfig - the package is called qt3-qtconfig.
```
sudo apt-get install qt3-qtconfig
```
Start qtconfig as a ordinary user, and from there, you can change how QT looks. There aren't many themes to choose between, and none of them are very exciting to look at, but it's better than nothing :)

Remember to save your preferences before quiting!

*Using kcontrol*
If you want some useful eyecandy, it's worth installing a few kde packages, and since this is ubuntu, it's not very hard either - ```
sudo apt-get install kcontrol
```
When the installation is done, simply start kcontrol, change styles, colours and fonts to your liking, and start opera.

*Using both*
I'm not entirely sure there is any need for this, but I've done anyway (just in case).
First, make sure you have both kcontrol and qtconfig installed.
Make your choices in kcontrol (styles etc), and close kcontrol.
Then start qtconfig again, and this time, you can choose between the ugly themes, and the themes from KDE - and pick your choice here (using the same style here as in kcontrol might be a good idea), and save it.

Now, if opera somehow wouldn't use KDE's settings, it will fall back on your qt-settings.

**Creating an application link**
I think I stole this from another thread, I just can't remember which.
If you want opera to show up in the Internet-menu without using sMeg, this is the way to go:
First,
```
sudo gedit /usr/share/applications/opera.desktop
```
and fill the empty file with this:

```

[Desktop Entry]
Encoding=UTF-8
Name=Opera Web Browser
GenericName=Web Browser
Comment=Simply the Best Internet Experience
Exec=opera %u
Terminal=false
MultipleArgs=true
Type=Application
Icon=/usr/X11R6/include/X11/bitmaps/opera.xpm
Categories=Application;Network
MimeType=text/html;image/gif;image/jpeg;image/png

```


Now - once last thing:
Have fun, be secure and surf fast! :)

---

### Post by Juippisi on 2005-10-18
Nice!

But, doesn't "Tools -> Appereance -> Color scheme -> System color scheme" (in Opera) do the same?

---

### Post by monotux on 2005-10-18
[QUOTE=Juippisi]Nice!

But, doesn't "Tools -> Appereance -> Color scheme -> System color scheme" (in Opera) do the same?[/QUOTE]

It changes the colorscheme :P

Using QT-widgets instead of motif alters how opera looks.

[http://oscar.vuln.se/tmp/opera-qt.png](http://oscar.vuln.se/tmp/opera-qt.png)

---

### Post by Juippisi on 2005-10-18
[QUOTE=monotux]It changes the colorscheme :P

Using QT-widgets instead of motif alters how opera looks.

[http://oscar.vuln.se/tmp/opera-qt.png](http://oscar.vuln.se/tmp/opera-qt.png)[/QUOTE]


Ah! I use KDE so Opera uses my KDE-theme ;-). And your Opera's menu looks sweet.

Btw, it's good that you gave some tips about errors when starting, it doesn't come as a suprise afterwards. 

And I recommend  everyone to read the next thread: [http://ubuntuforums.org/showthread.php?t=33945](http://ubuntuforums.org/showthread.php?t=33945) - Adblock for Opera :-).

---

### Post by majikstreet on 2005-10-18
Thanks!

(Fixed my issue with the code boxes on IRC with Juippis. I set Tools>>Preferences>>Web Pages>>Monospace font to Verdana size 13 :)

---

### Post by chadwick359 on 2005-10-19
Whenever I try to do that link, I just get "ln: 'libXm.so,2': Fille Exists"
but the link doesn't seem to be made, and the motifwrapper-3 still errors out. Any help would be appreiated!

---

### Post by monotux on 2005-10-19
[QUOTE=chadwick359]Whenever I try to do that link, I just get "ln: 'libXm.so,2': Fille Exists"
but the link doesn't seem to be made, and the motifwrapper-3 still errors out. Any help would be appreiated![/QUOTE]
Try to copy the file instead of linking to it.
It might work a bit better.

---

### Post by fantan on 2005-10-19
Hello Everybody!

My name is Albert Fazakas, I live in Hungary.

The problem is with this hack as follows
cd /usr/lib; ln -s libXm.so.3 libXm.so.2 <--- of course, this is an error, 
the proper thing is:
cd /usr/lib; ln -s libXm.so.2 libXm.so.3
After doing this, everithing will run without error message and the application starts with default style.

By

Albert

---

### Post by ferdy on 2005-10-19
You are looking for a very nice Opera Skin for Gnome?

[look here]("http://my.opera.com/community/customize/comments.dml?id=3255")

ferdy

---

### Post by NiceGuy on 2005-10-19
Ok, so after some messing around I've got opera working in my fresh breezy install, and as suggested tried opening opera using the "opera --style default" command and it seemed to have worked but then I noticed that none of my menu's were highlighting when the mouse went over them. Even when I clicked on them I got a sort of 'outline' not, as I expected. the deep brown 3Dish background ubuntu uses - any Ideas?

PS. As I said I'm using a fresh install of breezy and hense gnome.

---

### Post by monotux on 2005-10-21
[QUOTE=NiceGuy]Ok, so after some messing around I've got opera working in my fresh breezy install, and as suggested tried opening opera using the "opera --style default" command and it seemed to have worked but then I noticed that none of my menu's were highlighting when the mouse went over them. Even when I clicked on them I got a sort of 'outline' not, as I expected. the deep brown 3Dish background ubuntu uses - any Ideas?

PS. As I said I'm using a fresh install of breezy and hense gnome.[/QUOTE]

I think I know what your are talking about - and I think it's motif you are seeing (I've had the same problem, but I don't think I can reproduce it), and I think it's because you don't have qt installed / configured properly.

I'm adding a few things to the original article, I hope some of them will help you.

---

### Post by bluebyt on 2005-10-21
I dont have this file libXm.so.2, what should I do?

What I have to do to make the menu nicer, because now it look so ugly?

And finaly, I have the same problem as "NiceGuy"?

---

### Post by jpkotta on 2005-10-21
libXm.so.2 is provided by lesstif2 (lesstif is a LGPL version of motif, an old GUI library).

---

### Post by tofuconfetti on 2005-10-21
With regard to the libXm.so.2 symlink to avoid the startup error message, I don't have that file at all. Consquently, I have nothing to link to.  Which package needs to be there in order to install that file?  Opera works so far after I inadvertently got some xlibs updated (still not sure how I did that). 

I'm a Gentoo guy normally :-)

Sorry guys, I just saw the answer ... for some reason it wasn't on my browser when I posted this ... sorry.

I installed lesstif2 and issued this symlink:

  ln -s /usr/lib/libXm.so.2.0.1 /usr/lib/libXm.so.3

The libXm.so.2 is also a symlink to this file.

Now I have no startup errors.

---

### Post by ericP on 2005-11-20
strace revealed that opera was also looking in /usr/lib/opera/8.50-20050916.6/libXm.so.3 :
  strace -fo asdf opera --style default
  grep -E open\\\(\"/.\*libXm.so.3 asdf

If you are as anal as I (there are a few of you out there), you can
  ln -s ../../libXm.so.2.0.1 /usr/lib/opera/8.50-20050916.6/libXm.so.3
(from anywhere) and not clutter up your debian-controled /usr/lib .
BTW: I also don't need --style default

bon

---

### Post by monotux on 2005-11-20
[QUOTE=ericP]strace revealed that opera was also looking in /usr/lib/opera/8.50-20050916.6/libXm.so.3 :
  strace -fo asdf opera --style default
  grep -E open\\\(\"/.\*libXm.so.3 asdf

If you are as anal as I (there are a few of you out there), you can
  ln -s ../../libXm.so.2.0.1 /usr/lib/opera/8.50-20050916.6/libXm.so.3
(from anywhere) and not clutter up your debian-controled /usr/lib .
BTW: I also don't need --style default

bon[/QUOTE]

I can update the guide with an anal-edition, if you wish :P

---

### Post by bugmenot on 2005-12-14
Found a nice looking Clearlooks style skin today.

[http://my.opera.com/community/customize/comments.dml?id=3465](http://my.opera.com/community/customize/comments.dml?id=3465)


It's best to just switch off the main menu (saves vertical space) and put this [Button]("opera:/button/Show popup menu, "Browser Menu Bar",,,Menu") somewhere. I use key bindings anyway. The nice side effect lies in hiding the non-matching qt-based menu bar.

qt-config can be tweaked to have the same colors as the GTK theme.

---

### Post by cRoMo on 2006-01-01
Anyone has an idea on how to edit opera's 8.51 running script to set the style it is supposed to use? Apparently the script has changed since this HOWTO was written and there is no passflags variable anymore :(

---

### Post by kaamos on 2006-01-01
Has anyone else got very small fonts in the gui? For me this is the case with both qt and motif styles on opera. Also other qt apps like skype work properly, and changing the font size with qtconfig has no effect in opera.

Any ideas how to fix this?

---

### Post by cRoMo on 2006-01-01
Opera's gui font is unusually set in opera preferences - try there.

---

### Post by kaamos on 2006-01-01
[QUOTE=cRoMo]Opera's gui font is unusually set in opera preferences - try there.[/QUOTE]

Thanks, got that fixed. Now if anyone knows how to get rid of the windows-like hand-cursor that opera has in gnome, this app could be good to go.

---

### Post by monotux on 2006-01-02
[QUOTE=cRoMo]Anyone has an idea on how to edit opera's 8.51 running script to set the style it is supposed to use? Apparently the script has changed since this HOWTO was written and there is no passflags variable anymore :([/QUOTE]
I haven't found any smart solution here, but I'm still looking.
If I found any good method, I'll post it here :)

---

### Post by kaamos on 2006-01-02
[QUOTE=monotux]I haven't found any smart solution here, but I'm still looking.
If I found any good method, I'll post it here :)[/QUOTE]

This seems to work pretty well: do
```
echo "alias opera='opera --style default'" >> ~/.bashrc
```
and change the opera menu entry to
> opera --style default %u

---

### Post by breakman on 2006-01-08
[QUOTE=NiceGuy]Ok, so after some messing around I've got opera working in my fresh breezy install, and as suggested tried opening opera using the "opera --style default" command and it seemed to have worked but then I noticed that none of my menu's were highlighting when the mouse went over them. Even when I clicked on them I got a sort of 'outline' not, as I expected. the deep brown 3Dish background ubuntu uses - any Ideas?

PS. As I said I'm using a fresh install of breezy and hense gnome.[/QUOTE]

After installing Opera 8.51 for the first time it looked nice. But then after playing around in Ubuntu Opera startet to use motif. I tried everthing that i written in this thread but it was still using motif.

Then I created a new Ubuntu-user and there Opera was nice looking. Started to compare files i both users homedirs.

In the file ~/.qt/qt_plugins_3.3rc I found different that had to do whith motif.
The new test-user only had one line that looked like this:
```
[usr]
lib/qt3/plugins/styles/libqplatinumstyle.so=30304^e3^ei686 Linux g++-4.* full-config^e2005-09-10T02:28:15^e

```

My main-user had like 4-6 lines whith diffrent "styles" so I just removed everything but the line that the test-user had.

Doing a logout/login and Opera was back to its normal... :p 

Sorry for my bad english, hope you understand...

---

### Post by joshearl on 2006-01-13
Right off the bat i seem to be having some trouble! i've tried installing opera a few times but i always get errors. after downloading the .deb i *sudo dpkg -i opera*.deb* and recieve the following error:

stayj5@snoopaloop:~/Desktop$ sudo dpkg -i opera*.deb
Selecting previously deselected package opera.
(Reading database ... 59095 files and directories currently installed.)
Unpacking opera (from opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


I'm not sure what any of this means, but i would really like to install opera (i dislike firefox very much!) and then configure with your graphic tutorial. is there a previous installation not completely removed that is messing things up ( the line about selecting previously deselected package.)?

thanks.

---

### Post by breakman on 2006-01-25
Try to install these first:
libqt3-mt (>= 3.3.4)
libqt3c102-mt (>= 3.3.4)

---

### Post by ]Nbx*cmD[ on 2006-01-29
Hi all,
Does somebody know how to tell Gnome I want Opera as my default browser?
When I click links inside some apps (ex. gaim) firefox gets started :(
Thx!

---

### Post by monotux on 2006-01-29
[QUOTE=']Nbx*cmD[']Hi all,
Does somebody know how to tell Gnome I want Opera as my default browser?
When I click links inside some apps (ex. gaim) firefox gets started :(
Thx![/QUOTE]
Press ALT + F2 , and start this application:
gnome-default-applications-properties

You can set opera as your default browser from there :)

---

### Post by ]Nbx*cmD[ on 2006-01-29
great thx \\:D/

---

### Post by Tibor60 on 2006-02-01
Maybe a good browser, but I could not try, I could nort solve the installation problems, the howto page write only the problem, but no mention about the solution:
"If you you have choosen the qt-shared version, you need the libqt3c102-mt package. This is libqt3-mt in Ubuntu Breezy."

This is a good info, but absolutely not helping to install Opera. My error messages:

tibor@GOLDEN10:/usr/lib$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree... Done
libqt3-mt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tibor@GOLDEN10:/usr/lib$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
tibor@GOLDEN10:/usr/lib$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  opera: Depends: libqt3c102-mt but it is not installable
E: Broken packages


And what to do else?

---

### Post by Rhino1 on 2006-02-04
I just installed Opera - use the Wiki.Ubuntu.com/OperaBrowser Howto, it tells you how to fix everything you just mentioned.  No problems.  I even cut and pasted the text into my shell, pretty easy for a goofy like me.  Give it a Go!

---

