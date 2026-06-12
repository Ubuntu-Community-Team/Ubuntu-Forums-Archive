---
title: "Prefered Applications"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2008-04-29
Well so far my Ubuntu Hardy experience is great. i completely switched from windows xp to Hardy and i expect never EVER return with my tail between my legs :)

I have a few questions that have being bugging me for a while and still can't find a solution for. I have mplayer (with smplayer front-end), totem-gstreamer (hardy default) and VLC player.

Im usually watching a LOT of movies and videos in general in my laptop, put so far im having problems maintaining one video player as the default in gnome.

When i go to system>administration>prefered applications i see only a media tab:confused: (hating that) besides when i change the media default for "smplayer %s" (i add the %s because the tooltip showing says so)... Ok where was i... When i add that NOTHING happens, all my video files keep opening with totem. Then i manually change each file extension to open with smplayer. (right click>properties>open with>smplayer)

so far that solution has being somewhat unstable. When using deluge and double clicking on play video (from deluge) opens totem (which i hate :( no offense). I experimented so many times i got so tired that i just did "sudo apt-get remove totem-gstreamer". Oh boy if i knew...

    My videos thumbnails stop showing (at least new ones), i thing i reed something, somewhere about mplayer plugging for thumbnails, but i didn't knew (till now) that totem whas in charge of that.

    So after all this blah blah blah my question is how can i really make a default video player or audio player with such a poor gui offered by gnome in that area (maybe im missing something big?)

    I had to reinstall totem-gstreamer so my videos thumbs worked again.

    Thx for puting up with me.

    P.S: I don´t wanna start any flame war or something but since it came up... what do you think about smplayer? i dont like the way vlc player handles subs and mplayers GUI seems to crash all the time.

---

### Post by mivo on 2008-04-29
In Nautilus (file browser), right-click on one of your video files, select "Properties", then go to the "Open With" tab and select the player you want to use. All files of the same file type (i.e. .avi) will from now on be opened with that player. :)

Edit: Oops, you already tried that. Darn this lack of caffeine in my veins! Anyway, this method works well for me (I use VLC, though).

---

### Post by Ryuki_NdranC on 2008-04-29
> **mivo said:**
> In Nautilus (file browser), right-click on one of your video files, select "Properties", then go to the "Open With" tab and select the player you want to use. All files of the same file type (i.e. .avi) will from now on be opened with that player. :)

Edit: Oops, you already tried that. Darn this lack of caffeine in my veins! Anyway, this method works well for me (I use VLC, though).

yeah, i already try that. So far is good for my needs, but since i added deluge to my laptop, i can´t seem to open the files from deluge with the right Player. (it works with totem :()

Any way or tips you guys have used (or still use) in the matter of preferred applications??? I have read somewhere about ln command but i'm not so sure.

Thanks for the answer dough. :)

---

### Post by Tom--d on 2008-04-29
In don't think there is an option on that one. You can olny right click it and 'Open with'

Also, I'm going to look up smplayer :) See what it is like. 

Vlc just rocks tho :P

---

### Post by robalcorn on 2008-04-29
> **mivo said:**
> In Nautilus (file browser), right-click on one of your video files, select "Properties", then go to the "Open With" tab and select the player you want to use. All files of the same file type (i.e. .avi) will from now on be opened with that player. :)

Edit: Oops, you already tried that. Darn this lack of caffeine in my veins! Anyway, this method works well for me (I use VLC, though).
Wow i didnt know that trick i tried it with vlc and it works with every .avi ,thats great!

---

### Post by Ryuki_NdranC on 2008-04-30
> **robalcorn said:**
> Wow i didnt know that trick i tried it with vlc and it works with every .avi ,thats great!

xD glad my thread help one :)

Ok... im still in many doubts about picking a video player. There are soooooooooo many and with soooo many wierd stuff (at least for someone coming from "you haven't seen anything wrong here" Windows Vista).

Im using AWN and from an applet which lets me navigate any folder in a stackable way. when i launch a video from there it also opens totem no matter what :(

Im looking the gnome-config if i can change that, but so far i hate this particular thing about gnome desktops :(

I can't believe there isn't a way to change some cfg file hidden deep down the root hole (Alice :)) so my truly default player is smplayer (besides i still don't know with mplayer defalut crash on my pc but smplayer which its just a front-end of mplayer doesn't. I have to say... i like it, but it has some weird failures in my pc. Im trying to narrow down why they are happening.

I know there is a totem-xine or something, thats like the same totem but based in other kind of engine. VLC is good, but i really don't like the way it handles subtitles. I would hate to use 4 video players just for the sake of getting the best of each. :(

P.S: cr@p... i think im going off-topic a little. The thread still has the same purpose. Thanks for your answers.

---

### Post by mivo on 2008-04-30
I'm glad my lack of attention to the original post helped someone. :p

Ryuki, another option I found is in the Nautilus preferences (Edit -> Preferences -> Media), but that appears to be what is used when you enter new media that contains these media types or connect a new device (i.e. an iPod). You could probably look at Gnome's config files, too. Alt+F2, then type *gconf-editor*. But that's like fiddling with the Windows registry. KDE does better in that area.

---

### Post by Ryuki_NdranC on 2008-04-30
> **mivo said:**
> I'm glad my lack of attention to the original post helped someone. :p

Ryuki, another option I found is in the Nautilus preferences (Edit -> Preferences -> Media), but that appears to be what is used when you enter new media that contains these media types or connect a new device (i.e. an iPod). You could probably look at Gnome's config files, too. Alt+F2, then type *gconf-editor*. But that's like fiddling with the Windows registry. KDE does better in that area.

:( I'm beating myself up over that :( I'm a little obsesive/compulsive and this bugs like hell :(

I'm investigating something about making a symbolic link between smplayer and totem, so when totem gets called instead smplayer shows up (command ln i think). But I'm gonna get the time to read that tonight. I promise to add my findings. I usually post becouse I'm new at linux and even dough i can manage to find a way to do thinks, at first i fell more comfortable when i get the heads up from more experienced people.

Thanks for keeping the post in sight :)

---

