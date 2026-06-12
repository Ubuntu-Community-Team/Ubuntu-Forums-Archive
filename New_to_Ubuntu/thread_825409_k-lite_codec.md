---
title: "k-lite codec"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by hifen on 2008-06-10
i downloaded k-lite codec to help with some sound issues, since i'm new to linux u don't know how to run/implement it, double clicking on it fails to do anything. and the only option that has any results is wine, however i doubt that will be effective....  how do i run these types of programs?

---

### Post by fidamehran on 2008-06-11
I am not giving you solution. I don't have the knowlegde for that. But I think you downloaded the codec pack for Windows. That's why it's trying to open with Wine. As far as my knowledge goes, Windows Codecs shouldn't work in Linux. Check if KLite's website has codec for Linux, or look for the specific codecs in the Synaptic Package Manager.
This may be the solution. I am a COMPLETE newbie, so I might be wrong.

The veteran Ubuntu Gurus must have the absolute solution.

---

### Post by cariboo on 2008-06-11
I would be way easier to intall the ubuntu-restricted-extras package using synaptic. Synaptic is located in System-->Administration-->Synaptic Package Manager. Click the search button and search for ubuntu-restricted-extras, mark it for installation and click apply.

Jim

---

### Post by Kronie on 2008-06-11
klite is windows only application. you can either go with ubuntu-restricted-extras or u can go to the accessories->'add/remove' and search for word 'codec' there are 2 kinds of em, and they use same icon(i forgot its name T_T) first one is for video, and 2nd one for audio..u might want to install both.

---

### Post by Vivaldi Gloria on 2008-06-11
> **hifen said:**
> i downloaded k-lite codec to help with some sound issues, since i'm new to linux u don't know how to run/implement it, double clicking on it fails to do anything. and the only option that has any results is wine, however i doubt that will be effective....  how do i run these types of programs?

There are three ways of installing a program in ubuntu.

1) Using synaptic. This is the preferred way. If you want you can add more repositories to synaptic like [http://www.medibuntu.org/](http://www.medibuntu.org/) so that there are more programs available in synaptic.

2) Downloading a .deb file and double clicking it (just as you do with .exe files in windows). For example from [http://www.getdeb.net/](http://www.getdeb.net/)

3) Compiling from source (Advanced stuff, don't bother now).

There are equivalents of most windows programs in ubuntu. For example instead of klite-pack you install ubuntu-restricted-extras which is a collection of codecs and other stuff.

The advantage of using synaptic over other methods is that when you install a program using synaptic then ubuntu automatically updates that program as well. So you not only get new features, security updates etc. for ubuntu but you also get updates of all programs installed via synaptic.

---

### Post by Rhubarb on 2008-06-11
Go into Applications --> Terminal
Then enter this in:
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-schroedinger
```
Enter in your password and follow the prompts (just press "y" to any prompts).

Close the terminal and you should be able to play most video / audio files easily.

Otherwise, you should install the medibuntu repos (and w32codecs / w64codecs) and perhaps mplayer and vlc.

---

### Post by junaidatique on 2009-10-31
> **Rhubarb said:**
> Go into Applications --> Terminal
Then enter this in:
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-schroedinger
```Enter in your password and follow the prompts (just press "y" to any prompts).

Close the terminal and you should be able to play most video / audio files easily.

Otherwise, you should install the medibuntu repos (and w32codecs / w64codecs) and perhaps mplayer and vlc.


Hi , i have done the same thing as you have said, but nothing happened. please explain how can i play music on Ubuntu. i am new to it.

---

### Post by liquidbee on 2009-10-31
> **junaidatique said:**
> Hi , i have done the same thing as you have said, but nothing happened. please explain how can i play music on Ubuntu. i am new to it.

What kind of music is it ( format ) ?

---

### Post by Per_automatik on 2009-11-04
> **Kronie said:**
> klite is windows only application. you can either go with ubuntu-restricted-extras or u can go to the accessories->'add/remove' and search for word 'codec' there are 2 kinds of em, and they use same icon(i forgot its name T_T) first one is for video, and 2nd one for audio..u might want to install both.
i was thinking about this thread [http://zedomax.com/blog/2009/10/30/netbook-hack-how-to-make-your-hd-video-play-faster/](http://zedomax.com/blog/2009/10/30/netbook-hack-how-to-make-your-hd-video-play-faster/)

when i googled to this forumpost, do you think there is a solution to watch video at a bantered quality with a slow cpu or connection?

---

### Post by SunnyRabbiera on 2009-11-04
The closest Ubuntu has according to my searches is the ubuntu restricted extras package that covers most of what you need to play multimedia.
Plus you can install the windows codecs via medibuntu.
Also VLC and mplayer might take up the slack too, just keep in mind some codecs dont really work under linux as most of them are coded for windows only.

---

### Post by Per_automatik on 2009-11-04
well usual video is perfect. i was just thinking about tweaks to compensate relay old hardware, or streaming video at rely low connections speed, as the tutorial i linked mentioned, less lagg, more flow, if there might be a possible hack or modification of some sort?

---

### Post by viking1au on 2009-12-26
> **hifen said:**
> i downloaded k-lite codec to help with some sound issues, since i'm new to linux u don't know how to run/implement it, double clicking on it fails to do anything. and the only option that has any results is wine, however i doubt that will be effective....  how do i run these types of programs?
Try right clicking on the volume symbol in the top bar, click Sound prferences.. Then make sure the upper volume control reads 100%. The others can be lower so warning sounds are not so loud. ---If this fails, go to Synaptic & download Alsa mixer for Gnome. Rgds, newbie; viking1au

---

### Post by viking1au on 2010-02-04
> **hifen said:**
> i downloaded k-lite codec to help with some sound issues, since i'm new to linux u don't know how to run/implement it, double clicking on it fails to do anything. and the only option that has any results is wine, however i doubt that will be effective....  how do i run these types of programs?
Have used these codecs myself, in Windows only. They are good, Win Media Player was useless without the codecs but you need to look elsewhere in Linux. -- Those codecs are Windows only. (Unless I have missed something.) --- Use Synaptice to get & install a lot of the gstreamer codecs, and Alsa mixer. VLC Media player can overcome a few things. Banshee gets forgtten a bit but I think another tweak or two, and it is "there". Not a fan of xbmc; it is too messy to set up all the add ons.

---

### Post by viking1au on 2010-02-04
K-lITE is Windows only.

---

### Post by 3rdalbum on 2010-02-04
Please let this thread die the way it should have (back in 2008). Don't bump it again.

---

### Post by hoangtuanvnvn on 2011-07-15
> **Rhubarb said:**
> Go into Applications --> Terminal
Then enter this in:
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-schroedinger
```
Enter in your password and follow the prompts (just press "y" to any prompts).

Close the terminal and you should be able to play most video / audio files easily.

Otherwise, you should install the medibuntu repos (and w32codecs / w64codecs) and perhaps mplayer and vlc.

Thanks for help!:popcorn:

---

