---
title: "Opera plugin WMV3 and others in Breezy, my first ubuntu HOWTO"
date: 2005-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by jannol on 2005-12-07
Yes it is possible to play wmv3 in Opera but this is probably not any big news. I'll try to explain in an easy way how I did. I use Breezy i386 and I don't know if this will work on other versions etc, hey I don't know if it will work for anyone else at all but it might ;)
However I cannot 'fullscreen' the embedded video but I can live with that.

Ok here goes >

First I used Automatix and installed a bunch of stuff, very very nice script btw but here is what I belive you will need from Automatix for this howto.

[b]- Multimedia codecs
- Firefox Plugins
- Mplayer with plugin
- Media Players (not sure if you need this)
- AUD-DVD codecs
- SUN JAVA 1.5[/b]

Now you wonder why I didn't install Opera from Automatix and the simple answer is that I tried but the 8.51 version seems to crash and I did not get java to work. You will also need to install mozplugger and some other 'good to have' so please fire up a terminal and type

**sudo apt-get install opera-static mozplugger libmotif3 lesstif1 lesstif2 motif-clients**

I do not know exactly from what repositories since I already used Automatix and had them there but I guess it is in ubuntu backports and multiverse.

Now start Opera and find your way into

[b]Tools > Preferences > Advanced > Content

Click Java options

type /usr/lib/j2re1.5-sun/lib/i386/ as java path or wherever your libjava.so file exists, yes you must have java support. Then click ok.

Click Plug-in options and Find new, it should find a bunch, click Ok. Mozplugger should now be listed under Detected plug-ins. Click Ok.

Make sure sound in web pages, java script, java and plug-ins is enabled, if not click in the checkboxes. Click Ok.[/b]

If you already opened a page that contain a windows media file embedded, reload it or close and reopen it.

Now most of the common video files should play.

Good Luck!

Test WMV3 and others [HERE](http://home.att.net/~cherokee67/mediatests.html)

One strange thing happend for me the first way around so I removed mozplugger with --purge and then installed it again (It didn't help with just --reinstall) so I guess there happend something with some conf file, but then again, it was probably my fault when I tried a bunch of stuff before I got this working.

One another thing while at it, if you have vlc installed along with libdvdcss, w32codecs an the usual bunch og vlc dependencies you can grab this version of vlc > [vlc-0.8.4-test2_DMO_i386](http://lenerve.free.fr/ubuntu/vlc-0.8.4-test2_DMO_i386.deb) and you can watch wmv3 with vlc also.

Oh, howto install that vlc file, well when you have downloaded it, open a terminal and type

sudo dpkg -i <Path_To_The_File>/vlc-0.8.4-test2_DMO_i386.deb

where you change <Path_To_The_File> to where you downloaded the file ex.

sudo dpkg -i /home/tux/Desktop/vlc-0.8.4-test2_DMO_i386.deb

---

