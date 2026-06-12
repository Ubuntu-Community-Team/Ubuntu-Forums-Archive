---
title: "Radio Tray"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-12-14
Can not seem to find anywhere on there site to write, so here i am :smile:

Came across radio tray yesterday through one of my Feed subscriptions.  So i installed it and its a great application. I want to add a couple of  English stations to the list.

I have managed to find out how to add them, and found the URL's of the  actual players, BUT every time i try to play a station i get this:

---

### Post by ron999 on 2011-12-14
> **MadMonkey1966 said:**
>  BUT every time i try to play a station i get this:

It's telling you "no suitable plugin found".
Needs a gstreamer plugin.

I use RadioTray.
The attachment shows which gstreamer plugins are installed on my system.

---

### Post by Frogs Hair on 2011-12-14
You can install  the Ubuntu Restricted Extras from the software if not already . Some stations have there own players that work through the browser only which is the case with one of the local stations I listen to .

I am unable to add the station stream to any media player except the one provided by the station .

---

### Post by MadMonkey1966 on 2011-12-14
> **ron999 said:**
> It's telling you "no suitable plugin found".
Needs a gstreamer plugin.

I use RadioTray.
The attachment shows which gstreamer plugins are installed on my system.

Thanks Ron, i have looked in Package Manager, and have loads & loads of gstreamer Plugins. Is there any way to find out which ones ? Some are ticked and some are not

---

### Post by MadMonkey1966 on 2011-12-14
> **Frogs Hair said:**
> You can install  the Ubuntu Restricted Extras from the software if not already . Some stations have there own players that work through the browser only which is the case with one of the local stations I listen to .

I am unable to add the station stream to any media player except the one provided by the station .

Thanks Frogs Hair, i will have a go. One of the stations is a local one, so i may not be able to have it. the other is alround one, so i will hope. lets have a go :)

---

### Post by ron999 on 2011-12-14
> **MadMonkey1966 said:**
> Thanks Ron, i have looked in Package Manager, and have loads & loads of gstreamer Plugins. Is there any way to find out which ones ? Some are ticked and some are not
Are the ones in my attachment ticked?

---

### Post by MadMonkey1966 on 2011-12-14
> **ron999 said:**
> Are the ones in my attachment ticked?

I have gone thorugh all yours, and they are all ticked and there apart from the last one:

gstreamer0.10-plugins-ugly-multiverse

It is not even showing in the list :(

---

### Post by ron999 on 2011-12-14
> **MadMonkey1966 said:**
> I have gone thorugh all yours, and they are all ticked and there apart from the last one:

[COLOR="Red"]gstreamer0.10-plugins-ugly-multiverse
[/COLOR]
It is not even showing in the list :(

OK
I think that one isn't available for Oneiric.
Not on the list here:- [http://packages.ubuntu.com/search?keywords=gstreamer0.10-plugins-ugly-multiverse]("http://packages.ubuntu.com/search?keywords=gstreamer0.10-plugins-ugly-multiverse")
Which URLs don't work?

---

### Post by MadMonkey1966 on 2011-12-14
> **ron999 said:**
> OK
I think that one isn't available for Oneiric.
Not on the list here:- [http://packages.ubuntu.com/search?keywords=gstreamer0.10-plugins-ugly-multiverse](http://packages.ubuntu.com/search?keywords=gstreamer0.10-plugins-ugly-multiverse)
Which URLs don't work?

These are the ones i have tried..

[http://ukrp.musicradio.com/heart/berkshire/live](http://ukrp.musicradio.com/heart/berkshire/live)
[http://ukrp.musicradio.com/capital/london/live](http://ukrp.musicradio.com/capital/london/live)
[http://www.bbc.co.uk/iplayer/console/bbc_radio_berkshire](http://www.bbc.co.uk/iplayer/console/bbc_radio_berkshire)

I can imagine the 3rd one not working as it goes through iplayer, but thought the others would:confused:

---

### Post by ron999 on 2011-12-14
> **MadMonkey1966 said:**
> 
[http://ukrp.musicradio.com/heart/berkshire/live](http://ukrp.musicradio.com/heart/berkshire/live)
[http://ukrp.musicradio.com/capital/london/live](http://ukrp.musicradio.com/capital/london/live)
[http://www.bbc.co.uk/iplayer/console/bbc_radio_berkshire](http://www.bbc.co.uk/iplayer/console/bbc_radio_berkshire)

Hi
Those links are for listening in browser, not suitable for RadioTray.:(

This link will probably be OK for HeartBerkshire --->
```
http://media-ice.musicradio.com/HeartBerkshire.m3u
```
:)

But some research is needed to find good links for other two stations.:cool:

---

### Post by MadMonkey1966 on 2011-12-14
> **ron999 said:**
> Hi
Those links are for listening in browser, not suitable for RadioTray.:(

This link will probably be OK for HeartBerkshire --->
```
http://media-ice.musicradio.com/HeartBerkshire.m3u
```:)

But some research is needed to find good links for other two stations.:cool:

Many Thanks, i will just have to wait i suppose. They have a Forum, but it does not look as if anyone can post in there but themselves.

Thanks again

---

### Post by ron999 on 2011-12-14
Hi
There is a link for local BBC Berkshire here --> ```
http://wmlive.bbc.co.uk/wms/england/lrberkshire
```
It will play OK in VLC player.:)

But it won't play for me in RadioTray.:(
Seems like another gstreamer plugin is still needed for this WMA stream,  


**EDIT**

OK
The plugin needed is:- [COLOR="Red"]gstreamer0.10-ffmpeg[/COLOR]
Then RE-BOOT
and for RadioTray use the lrberkshire link above.

It's working now.

---

### Post by MadMonkey1966 on 2011-12-14
> **ron999 said:**
> Hi
There is a link for local BBC Berkshire here --> ```
http://wmlive.bbc.co.uk/wms/england/lrberkshire
```It will play OK in VLC player.:)

But it won't play for me in RadioTray.:(
Seems like another gstreamer plugin is still needed for this WMA stream,  


**EDIT**

OK
The plugin needed is:- [COLOR=Red]gstreamer0.10-ffmpeg[/COLOR]
Then RE-BOOT
and for RadioTray use the lrberkshire link above.

It's working now.

Thanks Ron, you are a real STAR, that works great for Berkshire =D>

After doing that, i tracked down the feed play, and now have:
TalkSport
BBC Radio 5 live
BBC Radio 5 live sport extra

Thanks so much for your help, slowly with everyone help i am getting used to all this :lolflag::lolflag:

---

### Post by sprintexec on 2012-11-11
I followed this thread as I was looking for a way to play BBC Radio 4 and also BBC Radio Cornwall. 

I now have Radio Cornwall playing happily in radio tray using this link [http://wmlive.bbc.co.uk/wms/england/lrcornwall](http://wmlive.bbc.co.uk/wms/england/lrcornwall) 

Thanks especially to Ron ):P

---

