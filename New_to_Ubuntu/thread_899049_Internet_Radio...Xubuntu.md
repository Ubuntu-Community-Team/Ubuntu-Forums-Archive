---
title: "Internet Radio...Xubuntu"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by faron45 on 2008-08-23
Helllllllllllllp !! PLEASE !!!!!!!!!!!!!!!
  
 I need a fix !!  No,not that kind...Thank God I never really got into that particular sort of errrrr,[stuff].Uhhhhh.....would like to be able to listen to some errrrrrrr,uhhhhhhhhhh,Grateful Dead via internet radio.

 When I attempt to do so via trying to download realplayer I notice that this is a .exe file.And,from what I know about these types of files,they will not work under Linux os's.Hellllllllllllllp !! PLEASE !!!!!!!!!!!!!  What must I do ? And,please remember,I am basically a beginning comp user.


             Yer pal,faron45

---

### Post by kattman on 2008-08-23
Download Songbird!  its a winamp clone

---

### Post by ds[de] on 2008-08-23
Are you sure you can only listen to the radio stream with Real Player?

My first advice would be to try and play it with xmms or rhythmbox or something else.

If you want to use Realplayer, you need to download a .bin file (realplayer for linux can be found here: [http://www.real.com/linux](http://www.real.com/linux))

Download this file to your computer (usually to your home directory), then open a terminal (Applications -> Accessoires -> Terminal).
In the terminal, navigate to the folder you saved the .bin file to (if you saved it to your home directory, you're already there when opening the terminal).
Then make the file executable by 
```
chmod u+x RealPlayer11GOLD.bin
``` 
and after that, type
```
./RealPlayer11GOLD.bin
```

(you might have to adjust the filename to the example I used above)

Then you just have to follow the instructions and real player should be installed on your system if nothing goes wrong :)

Regards,
ds[de]

---

### Post by etnlIcarus on 2008-08-24
sudo apt-get install helix-player

Helix audio and video player
The Helix Player is an audio and video player based on the Helix DNA Client
engine. It includes a Mozilla browser plug-in and supports local file playback
and streaming over RTSP/RTP and HTTP. It supports video zoom in original,
double size, and full screen, and supports:

 * Theora (Alpha 3 encoded content), Vorbis, Ogg
 * Basic SMIL 2.0
 * H.263
 * RealPix, RealText, RealEvents
 * RAM and RPM playlist formats
 * RTSP streaming with RTP, HTTP streaming

This package contains just the player, install mozilla-helix-player for the
browser plugins for Mozilla based browsers.

That said, I like using Songbird with the audioscrobber extension.

---

### Post by faron45 on 2008-08-24
Thanks everybody.Much appreciated.Is "Audacious" also one of those types of programs ? What I'm assuming is that I have to have something that real & [others] can play through ?
        faron

---

### Post by nickgaydos on 2008-08-24
> **kattman said:**
> Download Songbird!  its a winamp clone

Looks like iTunes a bit but...I would have to agree it does feel like WinAmp :)

---

### Post by Therion on 2008-08-24
> **faron45 said:**
> ... would like to be able to listen to some Grateful Dead via internet radio.
Do you mean to say you want to stream internet radio stations via your media player?

I just copy the url's for the stations I want from, say, [Shoutcast](http://www.shoutcast.com/) and put them into Rhythmbox as station presets.  Amarok has Shoutcast built-in, but I just like Rhythmbox.

---

### Post by faron45 on 2008-08-24
Yes,Therion.Essentially,I believed that that was how it worked.

---

