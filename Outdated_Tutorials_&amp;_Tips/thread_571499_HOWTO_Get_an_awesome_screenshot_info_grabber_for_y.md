---
title: "HOWTO: Get an awesome screenshot info grabber for your system"
date: 2007-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2007-10-09
[SIZE="6"]**Introduction**[/SIZE]

If you've ever frequented the [Arch Linux forums](http://bbs.archlinux.org/), you'd know that many a screenshot features this script. However, they've only developed it for Arch and Debian. Here's a guide that can let you get it on Ubuntu. :)

Here's the original topic that this guide is based off of:

[http://forum.beryl-project.org/viewtopic.php?f=51&t=5448](http://forum.beryl-project.org/viewtopic.php?f=51&t=5448)

Here's a screenshot of it in action (courtesy of Beryl Forums):

[[IMG]http://img216.imageshack.us/img216/919/20073mar7dp6.th.png[/IMG]](http://img216.imageshack.us/my.php?image=20073mar7dp6.png)

What's the point? Well, if nothing else, it saves you less typing for when you post in the Screenshots thread. ;)

[SIZE="6"]**Getting the script**[/SIZE]

You can download this script from here: [info.pl.tar.gz](http://forum.beryl-project.org/download.php?id=1012&f=51)

Open up a terminal (Applications>Accessories>Terminal), extract the file, and place it in ~/bin:

```
tar -xvf info.pl.tar.gz
mkdir ~/bin
mv info.pl ~/bin
```

By default, the script takes a screenshot of your screen after 10 seconds. To do this, you need to install scrot:

```
sudo apt-get install scrot
```

If you don't want this feature, you can edit info.pl and change it like so:

```
gedit ~/bin/info.pl
```

change line 17 from

```
my $shot = 0;
```

to

```
my $shot = 1;
```

save the file and exit.

[SIZE="6"]**Testing it out**[/SIZE]

To try it out, open up a terminal and run the following:

```
perl ~/bin/info.pl
```

It should all work well.

[SIZE="6"]**Going one step further: loading it when the console/terminal loads**[/SIZE]

This is a nice trick to make the console look a little nicer. Edit .bash_profile:

```
gedit ~/.bash_profile
```

and place in the following at the bottom of the file:

```
clear;
perl ~/bin/info.pl
```

Save the file and exit.

**Note that this only pertains to the system consoles (Ctrl+Alt+F1-F6)!** If you'd like to load it when the terminal opens up (Applications>Accessories>Terminal) then do the following:

Edit .bashrc:

```
gedit .bashrc
```

and place in the following at the bottom of the file:

```
perl ~/bin/info.pl
```

Save the file and exit.

[SIZE="6"]**The end!**[/SIZE]

And there you have it! A fancy script that works in almost all desktop environments and window managers. Have fun! :)

---

### Post by nikoPSK on 2007-12-10
thank you.

---

### Post by picpak on 2007-12-10
Glad to help you out. :)

---

### Post by nikoPSK on 2007-12-10
I ahd another one but didn't like it. :KS

---

### Post by Gourgi on 2007-12-11
nice one !
i didn't want screenshots and i wanted to load my gnome terminal quickly and not to wait 10 seconds, so i edited line 17 to :
[COLOR="Red"]changes are in red[/COLOR]
```

## Takes a screen shot if set to 0 ##
my $shot =[COLOR="Red"] 0[/COLOR];
## Command to run to take screen shot ##
my $command = "scrot -d [COLOR="Red"]0.2[/COLOR]";

```

few notes :
[LIST]
[*]better look for ubuntu logo would be more "eyecandy" ;)
[*]no compiz details  :( 
[*]neither emerald details  :(
[/LIST]

also when i try switching Alt+Ctrl+F1 and run the script i get this : 
```

giblib error: Can't open X display. It *is* running yeah? 

```
any ideas/fixes ? :confused:


also here's my screenshot

---

### Post by picpak on 2007-12-11
> **Gourgi said:**
> 

few notes :
[LIST]
[*]better look for ubuntu logo would be more "eyecandy" ;)
[*]no compiz details  :( 
[*]neither emerald details  :(
[/LIST]

Hmm, that's weird, maybe under this section

```
my %WMlist = ("Beryl", "beryl",
              "Fluxbox", "fluxbox",
              "Openbox", "openbox",
              "Blackbox", "blackbox",
              "Xfwm4", "xfwm4",
              "Metacity", "metacity",
              "Kwin", "kwin",
              "FVWM", "fvwm",
              "Enlightenment", "enlightenment",
              "IceWM", "icewm",
              "Window Maker", "wmaker",
              "PekWM","pekwm" );
```

try adding

```
my %WMlist = ("Beryl", "beryl",
              "Compiz", "compiz",
              "Emerald", "emerald",
              "Fluxbox", "fluxbox",
              "Openbox", "openbox",
              "Blackbox", "blackbox",
              "Xfwm4", "xfwm4",
              "Metacity", "metacity",
              "Kwin", "kwin",
              "FVWM", "fvwm",
              "Enlightenment", "enlightenment",
              "IceWM", "icewm",
              "Window Maker", "wmaker",
              "PekWM","pekwm" );
```

?

> **Gourgi said:**
> also when i try switching Alt+Ctrl+F1 and run the script i get this : 
```

giblib error: Can't open X display. It *is* running yeah? 

```
any ideas/fixes ? :confused:


also here's my screenshot

That's weird, it loads fine here. Are you running it along with X (Ctrl-Alt-F7)?

---

### Post by Gourgi on 2007-12-11
> **picpak said:**
> Hmm, that's weird, maybe under this section
try adding

```
my %WMlist = ("Beryl", "beryl",
              "Compiz", "compiz",
              "Emerald", "emerald",
              "Fluxbox", "fluxbox",
              "Openbox", "openbox",
              "Blackbox", "blackbox",
              "Xfwm4", "xfwm4",
              "Metacity", "metacity",
              "Kwin", "kwin",
              "FVWM", "fvwm",
              "Enlightenment", "enlightenment",
              "IceWM", "icewm",
              "Window Maker", "wmaker",
              "PekWM","pekwm" );
```
that worked thanks :D

> that's weird, it loads fine here. Are you running it along with X (Ctrl-Alt-F7)?
that message appears when i turn into terminal/console mode ( Alt+Ctrl+F1 ) , where obvisouly i don't run X display.
i wondered if there can be a "if ... fi" statement for console mode.
of course everything looks just fine in X display  ( Alt+Ctrl+F7 ) !

---

### Post by picpak on 2007-12-11
> **Gourgi said:**
> that message appears when i turn into terminal/console mode ( Alt+Ctrl+F1 ) , where obvisouly i don't run X display.

I meant is X running in the background. It should grab your settings from X, like it does for me.

> **Gourgi said:**
> i wondered if there can be a "if ... fi" statement for console mode.
of course everything looks just fine in X display  ( Alt+Ctrl+F7 ) !

a) I didn't write this script and b) I don't know perl, so I can't help you there. Sorry.

---

### Post by Gourgi on 2007-12-11
i found it
the script has no bugs at all !! 
the message appears only when the script is set to take screenshot and only for console mode. 
no problem :D
thanks again for sharing it

---

### Post by kodak on 2008-01-20
OS and Kernel are the only info that shows up :(

---

### Post by Nevon on 2008-01-20
I also only got OS and Kernel info, but I did some rather crude changes, and now it works.
I've changed the case "beryl" to "compiz" and changed "gnome-session" to "gnome-panel". This isn't quite right, since if you're not using the panel it won't recognize it as Gnome.

---

### Post by era506 on 2008-01-20
> **Nevon said:**
> I also only got OS and Kernel info, but I did some rather crude changes, and now it works.
I've changed the case "beryl" to "compiz" and changed "gnome-session" to "gnome-panel". This isn't quite right, since if you're not using the panel it won't recognize it as Gnome.

Hey, thanks for this one!!! Just a problem, it is displaying Emerald as my window manager and not Compiz Fusion, how can I change that? Also, I commented the part that searches for heliodor(metacity) theme and uncommented the part that looks for emerald theme but it display neither of them, how do I fix that?

---

### Post by American_Jesus on 2008-09-21
i've changed de Ubuntu logo for a better one

take a look

---

### Post by picpak on 2008-09-22
> **American_Jesus said:**
> i've changed de Ubuntu logo for a better one

take a look

[[img]http://lh3.ggpht.com/american.jesus.pt/SNbcYvambeI/AAAAAAAAALI/tDMtQR4xc1A/s288/CapturaEcra.png[/img]](http://lh3.ggpht.com/american.jesus.pt/SNbcYvambeI/AAAAAAAAALI/tDMtQR4xc1A/CapturaEcra.png)

That is indeed nicer, thanks for sharing!:)

---

### Post by billbank on 2008-09-22
Thanks that's  great help!

---

### Post by binbash on 2008-09-22
> **American_Jesus said:**
> i've changed de Ubuntu logo for a better one

take a look

It is very cool i am using it right now,

Thanks for the howto

---

### Post by jgrantham on 2008-09-24
What is the app running on your desktop to the right that shows a folder list and other info?

> **Gourgi said:**
> nice one !
i didn't want screenshots and i wanted to load my gnome terminal quickly and not to wait 10 seconds, so i edited line 17 to :
[COLOR="Red"]changes are in red[/COLOR]
```

## Takes a screen shot if set to 0 ##
my $shot =[COLOR="Red"] 0[/COLOR];
## Command to run to take screen shot ##
my $command = "scrot -d [COLOR="Red"]0.2[/COLOR]";

```

few notes :
[LIST]
[*]better look for ubuntu logo would be more "eyecandy" ;)
[*]no compiz details  :( 
[*]neither emerald details  :(
[/LIST]

also when i try switching Alt+Ctrl+F1 and run the script i get this : 
```

giblib error: Can't open X display. It *is* running yeah? 

```
any ideas/fixes ? :confused:


also here's my screenshot

---

### Post by American_Jesus on 2008-09-24
the conky?!

```
sudo apt-get install conky
```

see these thread
**[Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")**

---

### Post by Gourgi on 2008-09-25
yes indeed 
this is conky
an old one for me but i've done a good conf back then :lolflag:
i 'm trying to find it again

---

### Post by exjinn on 2009-08-22
I updated this script to show Crunchbang's (and Ubuntu's with a change in the script) theme info including the Openbox theme, GTK and icon theme names. It will then take a screenshot for you after 5 seconds. This little Perl script is great for screenshot addicts like myself. You can download it at http;//jinnfire.info

---

