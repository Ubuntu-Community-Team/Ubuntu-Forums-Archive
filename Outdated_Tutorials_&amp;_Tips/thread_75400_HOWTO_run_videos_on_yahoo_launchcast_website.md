---
title: "HOWTO: run videos on yahoo launchcast website"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
Thanks to **berserker** for a very useful tip.
U must have noticed that u need to be on IE/Netscape and on windows to play videos on [http://launchcast.yahoo.com](http://launchcast.yahoo.com)
Now therez a workaround to play those videos on firefox.
first of all do the following from terminal:
```
sudo apt-get install mozilla-mplayer mplayer-386
```
Now download the following firefox extension and install it by opening it in firefox:
[http://gc-group.dk/play-launch/play-launch-0.2.6.xpi](http://gc-group.dk/play-launch/play-launch-0.2.6.xpi) 
That should get u all set to enjoy the videos on [http://music.yahoo.com](http://music.yahoo.com) OR [http://launchcast.yahoo.com](http://launchcast.yahoo.com)

---

### Post by steil on 2005-10-13
Firefox always wants to use the totem plugin, however it gives me an error: Unable to find fd://0. How would I set mplayer to be the default plugin?

---

### Post by arnieboy on 2005-10-13
[QUOTE=steil]Firefox always wants to use the totem plugin, however it gives me an error: Unable to find fd://0. How would I set mplayer to be the default plugin?[/QUOTE]
do a
```
sudo apt-get remove mozplugger
```
U dont want mozplugger and mplayerplug-in clashes in firefox.

---

### Post by steil on 2005-10-13
I don't have mozplugger installed.

---

### Post by SilverTab on 2005-10-13
[QUOTE=steil]I don't have mozplugger installed.[/QUOTE]


same problem as you here...

it opens in Totem, and I dont have mozplugger installed

---

### Post by arnieboy on 2005-10-13
[QUOTE=SilverTab]same problem as you here...

it opens in Totem, and I dont have mozplugger installed[/QUOTE]
type the following in ur firefox browser and find out if u have a totem plugin anywhere:
```
about:plugins
```
it should be easy to find out. if there is, there will be a name of that file. search for it and delete it. but report to me the name of that file first before u delete anything.

---

### Post by SilverTab on 2005-10-13
[QUOTE=arnieboy]type the following in ur firefox browser and find out if u have a totem plugin anywhere:
```
about:plugins
```
it should be easy to find out. if there is, there will be a name of that file. search for it and delete it. but report to me the name of that file first before u delete anything.[/QUOTE]

libtotem_mozilla.so  seems to be the problem! :)

ill try that !

Edit: Its not a synaptic package so I guess its just a file?? Is it safe to just delete that file?

---

### Post by arnieboy on 2005-10-13
[QUOTE=SilverTab]libtotem_mozilla.so  seems to be the problem! :)

ill try that !

Edit: Its not a synaptic package so I guess its just a file?? Is it safe to just delete that file?[/QUOTE]
yes go ahead and delete all instances of it. u will have to delete them as root (so use sudo)

---

### Post by SilverTab on 2005-10-13
This is the list i get when I do locate libtotem:
/var/lib/dpkg/info/libtotem-plparser0.shlibs
/var/lib/dpkg/info/libtotem-plparser0.list
/var/lib/dpkg/info/libtotem-plparser0.postinst
/var/lib/dpkg/info/libtotem-plparser0.postrm
/var/lib/dpkg/info/libtotem-plparser0.md5sums
/usr/share/doc/libtotem-plparser0
/usr/share/doc/libtotem-plparser0/changelog.Debian.gz
/usr/share/doc/libtotem-plparser0/copyright
/usr/lib/nautilus/extensions-1.0/libtotem-properties-page.so
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so
/usr/lib/libtotem-plparser.so.0.1.0
/usr/lib/libtotem-plparser.so.0


should I delete the 2 mozilla-firefox/plugins files???

removing it via apt-get will also remove totem, rythmbox etc etc

---

### Post by arnieboy on 2005-10-13
[QUOTE=SilverTab]This is the list i get when I do locate libtotem:
/var/lib/dpkg/info/libtotem-plparser0.shlibs
/var/lib/dpkg/info/libtotem-plparser0.list
/var/lib/dpkg/info/libtotem-plparser0.postinst
/var/lib/dpkg/info/libtotem-plparser0.postrm
/var/lib/dpkg/info/libtotem-plparser0.md5sums
/usr/share/doc/libtotem-plparser0
/usr/share/doc/libtotem-plparser0/changelog.Debian.gz
/usr/share/doc/libtotem-plparser0/copyright
/usr/lib/nautilus/extensions-1.0/libtotem-properties-page.so
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so
/usr/lib/libtotem-plparser.so.0.1.0
/usr/lib/libtotem-plparser.so.0


should I delete the 2 mozilla-firefox/plugins files???

removing it via apt-get will also remove totem, rythmbox etc etc[/QUOTE]
delete the following:
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so
after deleting try running the videos on launchcast again. (by the way make sure u have w32codecs installed). How to do that? search on these forums. its illegal to download and install it in the US so I wont elaborate abt them here

---

### Post by SilverTab on 2005-10-13
[QUOTE=arnieboy]delete the following:
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt
/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so
after deleting try running the videos on launchcast again. (by the way make sure u have w32codecs installed). How to do that? search on these forums. its illegal to download and install it in the US so I wont elaborate abt them here[/QUOTE]


worked like a charm! thanks alot, really appreciated! :)

sucks that the fullscreen mode doesnt really work though!...but hey, no biggie, its already more than I expected!

---

### Post by arnieboy on 2005-10-14
[QUOTE=SilverTab]worked like a charm! thanks alot, really appreciated! :)

sucks that the fullscreen mode doesnt really work though!...but hey, no biggie, its already more than I expected![/QUOTE]
what do u mean fullscreen doesnt really work? it should work flawlessly

---

### Post by SilverTab on 2005-10-14
[QUOTE=arnieboy]what do u mean fullscreen doesnt really work? it should work flawlessly[/QUOTE]


the actual video stays the same size...but its surrounded by a black screen....(so it basically goes to fullscreen mode, but the video itself is the same size)

---

### Post by arnieboy on 2005-10-14
[QUOTE=SilverTab]the actual video stays the same size...but its surrounded by a black screen....(so it basically goes to fullscreen mode, but the video itself is the same size)[/QUOTE]
alright herez the fix for that:
do the following:
```
sudo gedit /etc/mplayer/mplayer.conf
```
and look for the line **zoom=no**
change that to **zoom=yes**
save and exit, test ur videos and thank me again

---

### Post by SilverTab on 2005-10-14
Awesome! working just fine! :)

now if I can successfully install the damn ATI drivers it will be top notch!

thanks for this howto arnieboy!

---

### Post by Gandalf on 2005-10-14
Finally we can play Video and have control as well

Thanks for this great Howto

btw how to make it stream wmv as well?

---

### Post by Cathbard on 2005-10-14
I really want to get this running as I've rated over 1000 songs at launchcast. However after following this guide I still get:
            --------------------------------------------------------------------------
To use this application with Netscape, you must use a 4.7x or 7.1 version. Download now.

Please use the following error code when writing to Yahoo! Help. (Error Code: 12)
             -----------------------------------------------------------------------------

The plugin seems to be installed and I've restarted Firefox. :( I'm using breezy and Firefox1.0.7

---

### Post by arnieboy on 2005-10-14
[QUOTE=Cathbard]I really want to get this running as I've rated over 1000 songs at launchcast. However after following this guide I still get:
            --------------------------------------------------------------------------
To use this application with Netscape, you must use a 4.7x or 7.1 version. Download now.

Please use the following error code when writing to Yahoo! Help. (Error Code: 12)
             -----------------------------------------------------------------------------

The plugin seems to be installed and I've restarted Firefox. :( I'm using breezy and Firefox1.0.7[/QUOTE]

this is only for the videos.. not the songs

---

### Post by arnieboy on 2005-10-14
[QUOTE=Gandalf]Finally we can play Video and have control as well

Thanks for this great Howto

btw how to make it stream wmv as well?[/QUOTE]
w32codecs

---

### Post by Cathbard on 2005-10-14
That's a bummer. I get the same thing with the videos too. It's a conspiracy I tells ya!!

---

### Post by nix4me on 2005-10-14
Works like a champ.  Finally!

I can play streaming wmv too.

nix

---

### Post by viniosity on 2005-10-14
I can't seem to get this to work.  I downloaded and installed the extension and I have the latest mplayer plugins (the same ones you require) along with win32 codecs (I can watch quicktime trailers on apple.com) but when I try launchcast it tells me I need Netscape or IE.  

The extension seems active.  And to be sure I restarted my whole computer, but the error I get is:

Error

Sorry, we are unable to support Netscape 6.0+ at this time.

Error Code: 7 - 0

---

### Post by arnieboy on 2005-10-14
[QUOTE=viniosity]I can't seem to get this to work.  I downloaded and installed the extension and I have the latest mplayer plugins (the same ones you require) along with win32 codecs (I can watch quicktime trailers on apple.com) but when I try launchcast it tells me I need Netscape or IE.  

The extension seems active.  And to be sure I restarted my whole computer, but the error I get is:

Error

Sorry, we are unable to support Netscape 6.0+ at this time.

Error Code: 7 - 0[/QUOTE]the extension is for videos on launchcast, not songs.

---

### Post by viniosity on 2005-10-14
Got it.. works now. thanks!

---

### Post by Cathbard on 2005-10-15
Ok, it works but if you try to play your video station it crashes. The station mode has rating widgets and that requires more than this plugin. I'm not impressed that Yahoo forces people to use a non-compliant piece of crap like IE.

Such is life.

---

### Post by arnieboy on 2005-10-15
[QUOTE=Cathbard]Ok, it works but if you try to play your video station it crashes. The station mode has rating widgets and that requires more than this plugin. I'm not impressed that Yahoo forces people to use a non-compliant piece of crap like IE.

Such is life.[/QUOTE]
yes it only works only for direct video links.. not for playing stations.

---

