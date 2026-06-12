---
title: "desktop shortcut to command line prog"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by nginmu on 2016-01-22
[CENTER]I installed youtube-dl (a command line program) from the repos, and it works fine running it by name in LXTerminal. I'd like to have an icon on the desktop that I could click, that would directly open youtube-dl in an LXTerminal window. Is this possible? Could I somehow preconfigure the shortcut to cause youtube-dl to download to a specific folder (/home/me/Desktop/VIDS?)
[/CENTER]

---

### Post by HermanAB on 2016-01-23
TIMTOWTDI...

You can make a launcher with a right click on the desktop and then somewhere in there click a check box to make it run the targeted program from a shell, or you can make a little script in /usr/local/bin that will launch a shell and the program you want, then make a launcher on the desktop to run that script.  A little bit of googling will get you going, else ask again here for more support, but I don't want to spoil your fun...

---

### Post by nginmu on 2016-01-23
Thanks for the pointers Herman.

On lubuntu 15.10 the right click on the desktop seems to lack an option to directly create a launcher, however this got me going:

[http://askubuntu.com/questions/451887/cant-create-application-launcher-in-lubuntu-14-04](http://askubuntu.com/questions/451887/cant-create-application-launcher-in-lubuntu-14-04)

It allowed me to specify the desktop (/home/me/Desktop) as the working folder whilst referencing /usr/bin/youtube-dl as the target executable, which had the effect of downloading the content directly to the desktop after entering the command e.g. youtube-dl [http://www.etcetcetc](http://www.etcetcetc)

I still have to remember to type the command itself into the terminal window so, it isn't really that much more convenient than just directly opening a terminal as normal. I was kinda hoping to be able to launch a terminal window with the command pre-filled ready to execute after simply typing or pasting a video url.

So I started looking to see if I could find a graphical frontend for the youtube-dl command line program, and found a python version

[https://code.google.com/p/youtube-dl-gui/](https://code.google.com/p/youtube-dl-gui/)

It says it's no longer supported though so I guess I'll keep on Googling.. well Duck Duck Go'ing anyway :-)

(I'm not quite sure if the youtube-dl.py mentioned in the link above, will be the same as the youtube-dl I got from Synaptic Package Manager?)

I know, I know.. "what's wrong with the terminal anyway" lol

---

### Post by Dennis N on 2016-01-23
It's actually very easy. The first step is to create an entry in the main menu. Then, right-click on the entry you made and select "Add to Desktop".
To create a menu entry, use **Accessories > Menu Editor**.
Attached is screenshot of how I define a menu entry for terminal program htop to open in the terminal.
Select a category, use the + to add an entry, fill in the details on the right (don't forget the title and icon), then save it (2nd button at top).
Restart.

---

