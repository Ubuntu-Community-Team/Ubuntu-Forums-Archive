---
title: "Opera Improved"
date: 2006-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by ice60 on 2006-04-08
[size=4]Here are just afew things which i think make Opera even better :) 

i'm going to add search engines, Userjs - JavaScript files which are like Firefox extensions, bookmarklets - more javascript which do cool things and block ads (post#5)

--------------------------------------------------------------------------------

**[color=blue]Note[/color]** i've added alot more search engines in the second post along with a link to download the search.ini file. it includes the Ubuntu Wiki, Ubuntu Package Search, Google Video, Wikipedia, TorrentSpy, World Time, Podzinger (maybe the best of the lot??) and many more. [color=red]EDIT[/color] i've now attached the file as a zip and added acouple more search places. the old rapidshare link expired


To add search engines you need to edit your ~/.opera/search.ini file [color=blue]while[/color] Opera is closed. [here's](http://nontroppo.org/wiki/SearchINIEditing) a link explaining how it's done if you want to learn more. 


so, to add the Ubuntu Package Search page you'd add this to your search.ini


[Search Engine 2] <---- make sure you put the correct number here
Name=Ubuntu Package Search 
URL=http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=%s&searchon=names&subword=1&version=breezy&release=all
Query=
Key=u
Is post=0
Has endseparator=0
Encoding=utf-8
Search Type=0
Verbtext=17063
Position=-1
Nameid=0

here's one for the Ubuntu Wiki, again make sure you put the correct Search Engine number in :)

[Search Engine 19]
Name=Ubuntu Wiki
URL=https://wiki.ubuntu.com/?action=fullsearch&context=180&value=%s&titlesearch=Titles
Query=
Key=wiki
Is post=0
Has endseparator=0
Encoding=utf-8
Search Type=0
Verbtext=17063
Position=-1
Nameid=0

Wikipedia

[Search Engine 4]
Name=&Wikipedia (EN)
URL=http://en.wikipedia.org/wiki/%s
Query=
Key=w
Encoding=iso-8859-1
Is post=0
Has endseparator=0
Search Type=0
VerbText=17063

-----------------------------------------------------------------

This next bit is about [Userjs](http://userjs.org/) they are similar to Firefox extensions. i'm going to show you how to get [Google suggest](http://userjs.org/scripts/site/enhancements/google-suggest) to work, but if you go through [all the scripts](http://userjs.org/scripts/) you'll find lots of other good ones.

1, Go to ~/.opera and make a directory called something like **userjs**

2, Go to Tools -> Preferences -> Advanced -> Content -> JavaScript Options. Add the location of your newly created script directory to My JavaScript files. mine looks like this (i called my directory my_userjs :D )
```
/home/iceni60/.opera/my_userjs/
```

3, Go to the [Google Suggest Script](http://userjs.org/scripts/site/enhancements/google-suggest) page and right-click on **Opera User JS** and download googlesuggest.js

4, put googlesuggest.js in your userjs directory, you might need to restart Opera, i'm not sure, and that's it.

here's a link if you get stuck [http://userjs.org/help/installation](http://userjs.org/help/installation)

now when you go to google you should have google suggest

[[IMG]http://img377.imageshack.us/img377/913/screenshotgoogleopera8547ve.th.png[/IMG]](http://img377.imageshack.us/my.php?image=screenshotgoogleopera8547ve.png)
-------------------------------------------------------------------------------

Now it's the [bookmarklets](http://en.wikipedia.org/wiki/Bookmarklets)

[here's](http://nontroppo.org/wiki/CustomButtons) a good place to start. let's just start by adding one. we'll try the first one - under **Navigation / Scroll Buttons** *Go to the top of the page* left click on *Go to the top of the page* and drag it directly upward to your toolbar. **[color=blue]Hint[/color]** if everything starts highlighting as you drag upward try again ;) 


when you have dragged the bookmarklet to your toolbar you'll be asked if you want to add the button, click yes (you can right-click and remove it later) now click your new button - magic - you've gone to the top of the page \\:D/  now pick some you like :) 

here are some more bookmarklets
[http://nontroppo.org/wiki/PowerButtons](http://nontroppo.org/wiki/PowerButtons)
[http://www.squarefree.com/bookmarklets/](http://www.squarefree.com/bookmarklets/)

i hope someone finds something here useful, if not it'll be useful for me when i next break my computer and need to reinstall everything ](*,)[/size]

---

### Post by ice60 on 2006-04-10
i have used up all the screenshots i'm allowed in one post (above) so i'm going to show you my full search engine list here along with a link for the search.ini so if you want it you can download it and use it too. :)

i've attached the search.ini as a zip

[img]http://img402.imageshack.us/img402/4859/searchengines3bx.png[/img]

-------------------------------------------------------------------------

here are some useful bookmarklets, just drag them up to your toolbar

Wayback Machine
this one is useful if you get something like a 404 for a page you want, just click on the bookmarklet button (after dragging to the toolbar) and see the page that way instead.

Links To this Page

Check Document Last Modified

Check site server

cookies from this site

List All Links on Page

Search google groups (New window)

all from 
[http://www.philburns.com/bookmarklets.html](http://www.philburns.com/bookmarklets.html)

-----------------------------------------------------------------------------

here are some useful userjs

[Download embeds](http://userjs.org/scripts/general/enhancements/download-embeds) - if you are having problems streaming a video, just double click on the page and a download link will appear which you can then download and play in your media player.

[Spoof as Firefox or Internet Explorer](http://userjs.org/scripts/browser/enhancements/zz-spoof-id) this one i think needs you to make some changes in ua.ini. you can then go to sites which normally don't let Linux/Opera users goto as talked about in [this](http://www.ubuntuforums.org/showthread.php?t=105428&highlight=gap.com) thread

there's lots more useful scripts and bookmarklets too, try some out. :)

---

### Post by lazyd2 on 2006-04-16
Thanks fir the tips!

Is there anyway of adding a search engine for debian packages like the one firefox has?

---

### Post by ice60 on 2006-05-22
[QUOTE=lazyd2]Thanks fir the tips!

Is there anyway of adding a search engine for debian packages like the one firefox has?[/QUOTE]
hi, lazy. sorry for being slow, i made this to search for Debian Stable Packages, it searches for all architectures. if you use it make sure you use the correct Search Engine number so it's in sequence with the others.

i haven't used the Firefox one so i'm not sure what it's like.


[Search Engine 24]
Name=Debian Stable Packages
URL=http://packages.debian.org/cgi-bin/search_packages.pl?keywords=%s&searchon=names&subword=1&version=stable&release=all
Query=
Key=dsp
Is post=0
Has endseparator=0
Encoding=utf-8
Search Type=0
Verbtext=17063
Position=-1
Nameid=0

[color=red]EDIT[/color] for some reason when i read the post there's a space here in the  URL=
```
subw ord
```
it should read 
```
subword
```

---

### Post by ice60 on 2006-05-22
to block ads i use [Privoxy](http://en.wikipedia.org/wiki/Privoxy) it's an HTTP proxy, so everything from the internet is filtered through Privoxy's filters before it gets to Opera.

```
sudo apt-get install privoxy
```

then goto Tools>Preferences>Advanced>Network>Proxy Servers

and copy the settings from the screenshot below. that should be it, Privoxy will startup with your computer. here are some useful commands
To detect whether privoxy is running, if it shows up it's running
```
ps -e |grep privoxy
```
if you need to start/stop it
```
sudo /etc/init.d/privoxy start
sudo /etc/init.d/privoxy stop
```

you can get support here
[http://www.privoxy.org/](http://www.privoxy.org/)

and here are some useful locations along with how to open them so you can edit the configuation files
```
sudo gedit /etc/privoxy/default.action
sudo gedit /etc/privoxy/config
sudo gedit /etc/privoxy/user.action
```

but just see how you go, you can just install it and forget about it.

---

### Post by Madpilot on 2006-05-23
Nice stuff - thanks!

Note that Opera 9 will (finally!) have a UI for customizing the search dropdown menu, which will make that part of this much, much easier.

Opera 9beta was released a while ago; there's an Ubuntu Breezy deb and it runs very nicely for me!

---

