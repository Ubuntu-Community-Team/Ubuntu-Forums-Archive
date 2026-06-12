---
title: "OSX Spotlight like search tool"
date: 2006-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by art on 2006-01-18
I find this one of the best tools in Gnome, so wanted to share with everyone. Well, sure it is not as powerfull as Spotlight, but still extremely good in my opinion. All you need to get it is
sudo apt-get install deskbar-applet
and right clicking on the panel add Deskbar. Now when you type in the deskbar, you can search all your search engines, Beagle, dictionary and a lot more. RO change what you want to be searched, right click and in Properties choose to your liking. The defaulf Keyboard shortcut to get into deskbar is Alt-F3, but you can change it if you go to Applications->System Tools->Configuration Editor->Apps->deskbar and make it whatever you like. For more info look at 
[http://gnomefiles.org/app.php?soft_id=780](http://gnomefiles.org/app.php?soft_id=780)
I attach a little screenie too... Hope you'll find it useful.
EDIT(thanks to SlugO): In order for deskbar to launch firefox 1.5 when doing web search make sure you have changed your web browser preference in "Preferred Applications" to /usr/bin/firefox %s

**EDIT** New feature in deskbar-applet latest release (2.14.0.1) now allows you to use your Fireox Search engines (like Wikipedia etc.). And it also has nicer looking interface now! 
To install it:
0) Remove the previous version sudo dpkg --purge deskbar-applet
1) Download the source from [here]("http://ftp.gnome.org/pub/GNOME/sources/deskbar-applet/2.14/deskbar-applet-2.14.0.1.tar.bz2")
2) Untar and unzip it: tar jxf deskbar-applet-2.14.0.1.tar.bz2
3) cd deskbar-applet-2.14.0.1
4)  ./configure --prefix /usr
5) make 
6) sudo checkinstall -D make install
Enjoy!

---

### Post by SlugO on 2006-01-29
Hmm... I wonder how I could get it to launch Firefox 1.5 when
searching the web instead of the old one. (Installed it like [this]("https://wiki.ubuntu.com/FirefoxNewVersion").)

---

### Post by majikstreet on 2006-01-29
Woah. that's cool... makes me think about going back to gnome..

---

### Post by art on 2006-01-29
It opens the firefox 1.5 for me... Have you changed the entry for preferred web browser to /usr/bin/firefox in your Preferred Aplications?

---

### Post by Rob2687 on 2006-01-29
Installed this but I don't see a deskbar applet in the gnome-panel things.

---

### Post by SlugO on 2006-01-29
[QUOTE=art]It opens the firefox 1.5 for me... Have you changed the entry for preferred web browser to /usr/bin/firefox in your Preferred Aplications?[/QUOTE]
Thanks, I guess it was too obvious for me to notice :mrgreen:

---

### Post by art on 2006-01-29
[QUOTE=Rob2687]Installed this but I don't see a deskbar applet in the gnome-panel things.[/QUOTE]
 Do a killall gnome-panel in the terminal, or log out and log back in, and it should appear...

---

### Post by Alev on 2006-01-29
Awesome, really handy.

---

### Post by Rob2687 on 2006-01-30
Can't type in it you're using kwin :(

---

### Post by art on 2006-01-30
Yeah, I know and it really annoys me...

---

### Post by benplaut on 2006-01-30
even better, put it in a drawer, expand the size of the drawer, and make the text box a bit smaller... works like a charm!

---

### Post by art on 2006-01-31
[QUOTE=benplaut]even better, put it in a drawer, expand the size of the drawer, and make the text box a bit smaller... works like a charm![/QUOTE]
Is there any keyboard shortcut to open the drawer, without clicking on it?

---

### Post by dexae on 2006-01-31
[quote=art]Is there any keyboard shortcut to open the drawer, without clicking on it?[/quote]
alt+f3

---

### Post by unique on 2006-02-01
Ok, it installed with no probs... I am running firefox 1.5 I have changed my preferred apps to /usr/bin/firefox... When I type somthing in and choose to search with google or yahoo it will open my browser but thats it... it dosen't search it just open firefox and stays at my home page? 

What am i missing?  This looks really cool if that would work...
Thanks

---

### Post by Moebius on 2006-02-01
change it from that to this

```
/usr/bin/firefox %s
```

---

### Post by unique on 2006-02-01
[QUOTE=Moebius]change it from that to this

```
/usr/bin/firefox %s
```[/QUOTE]


That did the trick! Thanks!  \\:D/

---

### Post by art on 2006-02-01
Yeah, true! Sorry I didn't mention this. I corrected the howto

---

### Post by unique on 2006-02-01
One more thing. It looks like it uses the search engines from firefox... well when I add some new search engines to firefox they don't show up in the deskbar?

How do I fix this?

---

### Post by kojikabuto_l on 2006-02-03
There is an equivalent SPotlight for Kde ?

thx

---

### Post by art on 2006-02-06
[QUOTE=unique]One more thing. It looks like it uses the search engines from firefox... well when I add some new search engines to firefox they don't show up in the deskbar?

How do I fix this?[/QUOTE]
I couldn't find a fix for this yet, but still looking for it
[QUOTE=kojikabuto_l]
There is an equivalent SPotlight for Kde ?
[/QUOTE]
 Searching Google there is Kat, but since I don't have KDE, can't tell how good or bad it is.

---

### Post by jjf on 2006-03-17
Holy Utility Belt, Batman, this applet is amazing!

"Beagle" never returned any results for my searches (it would say "not found" even to files I knew that I had), so I just unchecked it.  But I love the ability to search address book, dictionary, send emails, launch programs, all from one bar.

Thanks!

---

### Post by art on 2006-03-23
I just edited the first post to include instructions on how to install the latest deskbar applet with newer features.

---

### Post by adamkane on 2006-03-23
I had a difficult time installing this package. There are many packages that need to be installed before deskbar-applet can be installed from source. Here's an updated list of instructions:

0) Install the old deskbar-applet and its dependencies, then remove deskbar-applet:

```

sudo apt-get install deskbar-applet
sudo apt-get remove deskbar-applet
sudo apt-get install evolution-data-server-dev evolution-dev python-gnome2-dev python-gnome2-extras-dev libgnome-desktop-dev libxml-parser-perl

``` 
1) Download and install the new deskbar-applet:

```

cd ~
wget  http://ftp.gnome.org/pub/GNOME/sources/deskbar-applet/2.14/deskbar-applet-2.14.0.1.tar.bz2
tar xjf deskbar-applet-2.14.0.1.tar.bz2
cd deskbar-applet-2.14.0.1
./configure --prefix /usr
make
sudo checkinstall -D make install

```

---

### Post by Moebius on 2006-03-23
I'm having a little problem with the ./configure step

```
checking for DESKBAR... configure: error: Package requirements (gtk+-2.0       >= 2.6
        pygtk-2.0                               >= 2.6
        pygobject-2.0                   >= 2.6
        gnome-python-2.0                >= 2.10
        gnome-desktop-2.0               >= 2.10
) were not met:

Package gnome-desktop-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-desktop-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DESKBAR_CFLAGS
and DESKBAR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I have gnome-desktop installed, and some of the specified packages could not be found in synaptic (gnome-python).

Thanks

---

### Post by art on 2006-03-23
Try 
sudo apt-get install libgnome-desktop-dev
Should work...

---

### Post by Moebius on 2006-03-23
Indeed it did. Thanks again.

---

### Post by pain of salvation on 2006-03-23
Its not working for me...

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
alvaro@ubuntu:~/deskbar-applet-2.14.0.1$ make
make: *** Nenhum alvo indicado e nenhum arquivo make encontrado.  Pare. (translate: No target indicated and no make file found. Stop.)

---

### Post by Padrig Leamhnach on 2006-03-23
You need to install XML::Parser -

sudo apt-get install libxml-parser-perl

I think that should do it.

Jim

---

### Post by stalefries on 2006-04-27
How about this?
```
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

---

### Post by stalefries on 2006-04-27
Wait, I'm dumb. How does python-dev sound to you?

---

### Post by art on 2006-04-27
I think that might help:)

---

### Post by jms830 on 2006-04-28
how do i run this once its installed? alt+F3 isn't doing anything. is it located anywhere in the menu or via command?

---

### Post by art on 2006-04-28
Right click on the panel, Add to Panel and choose deskab-applet. Then you can either click on it and type in, or you can define a custom keyboard shortcut from the preferences menu.

---

### Post by MadsRH on 2008-01-07
What is the easiest way to install Deskbar in Gutsy??? Is it in Synaptic?

---

