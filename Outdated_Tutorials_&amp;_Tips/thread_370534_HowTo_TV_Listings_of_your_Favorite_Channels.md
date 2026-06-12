---
title: "HowTo: TV_Listings of your Favorite Channels"
date: 2007-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Gen2ly on 2007-02-25
This tutorial is useful for listing your favorite channels as an applet in your menu panel.

Here's what mine looks like:

[IMG]http://www.archive.org/download/ToddPartridgeOnTVonUbuntu/OnTV_Screenshot.png[/IMG]

Pretty simple.  I like to use the terminal as it will make this a little bit faster.  First we need to download xmltv which is our tv listings grabber.
```
sudo apt-get install xmltv
```

Now find the appropiate tv_grab for your location:
```
tv_find_grabbers
```

Mine was "tv_grab_na_dd"(north america).  Now it has to be configured:
```
sudo tv_grab_na_dd --configure
```

Several questions will be asked.
First it will ask for your GMT skew.

Next, it will need you to register:
> Free Data Direct registration required in advance.
You can get an ID at [http://labs.zap2it.com](http://labs.zap2it.com)

Control-clicking is in the terminal will open the link.

Register a new user.  Use the Certificate Code you see in the terminal.  Zap2it will ask a few questions.  Subscibe and add a lineup by selecting your area code, what tv service you have... blah blah.

Now, grab the listings.  Make sure you're in the home directory first:
```
cd ~
sudo tv_grab_na_dd --output=.listings.xml
```

This will save the TV listings as an invisible-file in your home directory.

The listings need to be sorted now:
```
tv_sort --output=.listings.xml .listings.xml
```

OnTV is the applet (the icon in the menu bar) that will tell us what programs there are.

sudo apt-get install ontv

right-click on menu panel and select "Add to Panel" and add OnTV to the menu bar.  Immediately a dialog will pop up with the preferences.  Put /home/(user)/.listings.xml (or whatever you chooose to name the xmltv file) in now.

Right-click on the OnTV icon and hit "Reload XMLTV file" now goto the Channels Tab and choose your favorite stations!

TV Listings are weekly so if putting a script in the cron.weekly directory this could automatically be updated every week.
```
sudo nano /etc/cron.weekly/tv_listings
```

Paste this text into the terminal:
```
#! /bin/sh

tv_grab_na_dd --output=/home/(user)/.listings.xml

tv_sort --output=/home/(user)/.listings.xml /home/(user)/.listings.xml

```

cntrl-x to save

Thats it!

---

### Post by PartisanEntity on 2007-05-17
HI, after I enter:

```
tv_grab_de_tvtoday --configure
```

I get:

```
using config filename /home/me/.xmltv/tv_grab_de_tvtoday.conf
getting list of channels
Can't call method "content_list" on an undefined value at /usr/bin/tv_grab_de_tvtoday line 1277.
```

---

### Post by chamberlain2006 on 2007-05-30
This guide might be a little old, but I just want to let people know about the project I'm working on, called Yabby.  It's still in early development, but check it out: [http://yabby.sourceforge.net](http://yabby.sourceforge.net).

---

### Post by k420 on 2007-06-10
I have a problem ```
tv_sort --output=.listings.xml .listings.xml
cannot write to .listings.xml
```

---

### Post by Gen2ly on 2007-06-16
k420,

Perhaps you saved you .listing.xml file as root?  If you won't have the necessary permissions to write to it.

chamberlain2006

That sounds pretty interesting.

*Yabby is a Gtk frontend to xmltv. It provides a simple way to view and sort TV Listings, as well as set reminders, and learn more about a specific listing.*

OnTV is OK, if you have like 5 channels you pretty much watch exclusive, otherwise...  Could I ask you to post a screenshot?  I'm curious now :)

---

### Post by davidw89 on 2008-08-08
After
tv_find_grabbers
i can't find the australian one

help
or post the xmltv needed for the screenlets whatsontv

---

### Post by Mitch72 on 2008-11-03
> **davidw89 said:**
> After
tv_find_grabbers
i can't find the australian one

help
or post the xmltv needed for the screenlets whatsontv
Using a screenlet called ["WhatsonTV"]("http://www.mediafire.com/?bgrdw1vg4lj") (thread [here]("http://forum.compiz-fusion.org/showthread.php?t=3561")). I was (kinda) able to do this for Australian programs.

For Australian networks, use [Shepherd]("http://svn.whuffy.com/wiki").
I did as you did (installed xmltv but couldn't find any grabbers). I then installed shepherd and followed the instructions on the site.

Following that, I launched the screenlet, right-clicked, properties, options, WhatsonTVScreenlet, and used the output.xmltv (for me it was in ~/.shepherd/) as my xmltv file. I'd assume you could use the same file for this program.

Good Luck!

EDIT: you may want to type:

~/.shepherd/tv_grab_au --disable imdb_augment_data

Shepherd gets additional movie info from IMDB. If you're only using it for time listings, you might aswell disable it with the above command, it takes awhile if you don't...

---

