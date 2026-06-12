---
title: "NPR live stream with Realplayer 10"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by retrow on 2006-11-10
I just figured out a way to directly play NPR 24 hour program streams using Realplayer. Of course, I am assuming that you already have Realplayer working properly and your .rm links open with realplayer and not Mplayer.

When you click on the "NPR Program Stream" link on the npr.org page, it fires up realplayer and plays an ad at the beginning and then it buffers the actual stream.

Once the stream is begins, open up terminal

[COLOR="Blue"]cd /tmp
ls *.smil[/COLOR]
then open the .smil file with a text editor

[COLOR="Blue"]gedit nprxxxx.smil[/COLOR]

You'll find 2 lines towards the end beginning with <audio src="rtsp://..................>

Copy the source link within the quotes with rstp://

Now in realplayer tabs, [COLOR="Blue"]Favorites[/COLOR] >[COLOR="Blue"] Manage Favorites[/COLOR] > [COLOR="Blue"]New[/COLOR] > [COLOR="Blue"]then add the location you copied from .smil file - edit the title to what you want it to be[/COLOR] > [COLOR="Blue"]close[/COLOR]

Now you can play NPR program stream by opening the player and choosing from favorite.

NOTE: The stream location changes from time to time, so if the player fails to load the stream from favorites you might need to follow the above steps and instead of adding a new location in the favorites, you can edit the link for the existing stream.

---

