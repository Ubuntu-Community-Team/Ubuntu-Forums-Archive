---
title: "HOWTO: Automatically play CDs and DVD when inserted."
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2005-10-16
**Tested with x86 Dapper, Edgy, Feisty and Gutsy**

Here's a little HOWTO, but nevertheless a helpful one for automatically play your Music CDs and your DVD movies when they are inserted.

First go to **System** tab ---> **Preferences** ---> **Removable Drives and Media**
Or by command:
```
gnome-volume-properties
```
Now switch to **Multimedia** tab in Removable Drives and Media.



[size=4]_**Music Player_**[/size]

In the **Audio CD Disc** write this in the commandline box:

**_Xmms_**
```
xmms -p /media/cdrom
```

**_Beep Media Player (bmp)_ **
```
beep-media-player -p /media/cdrom
```

**_Audacious_ **
```
audacious -p /media/cdrom
```


[size=4]**_Movie Player**_[/size]

In the **Video DVD Disc** write this in the commandline box:

**_VLC**_
```
wxvlc dvd:///dev/dvd
```

**_Mplayer**_
```
gmplayer dvd://1 -dvd-device /dev/dvd
```


Now you can insert your Music Cds and DVDs and it startsup automatically. You might change it a little bit if you got multiply CD/DVD.
A logout may be needed before it can take effect.

---

### Post by XDevHald on 2005-10-16
Howto tested, and works like a charm, great job AI :D

---

### Post by Perfect Storm on 2005-10-16
Thanks, bro ^^

---

### Post by bionnaki on 2005-10-22
I use bmp for music & gxine for movies. can I use these instead?

---

### Post by Perfect Storm on 2005-10-22
I don't use any of these multi-media, but I guess bmp will work, dunno about xine.

---

### Post by kazuya on 2005-11-01
awesome. note to self. Must try this out.

---

### Post by maxdevis on 2006-01-29
it doesn't work with me
:(

when i put this wxvlc dvd:///dev/dvd in a terminal, it starts playing, but when i just insert a disk, it doesn't play?

---

### Post by Perfect Storm on 2006-02-02
update: added beep media player

---

### Post by Perfect Storm on 2006-02-25
Updated: 
Rewritten the howto.
Added Mplayer to autoplay.

---

### Post by Perfect Storm on 2006-02-25
[QUOTE=maxdevis]it doesn't work with me
:(

when i put this wxvlc dvd:///dev/dvd in a terminal, it starts playing, but when i just insert a disk, it doesn't play?[/QUOTE]

You need to logout and login before it works.

---

### Post by mrgnash on 2006-02-25
I'd actually like to know how to turn this OFF under KDE. It loads Totem which promptly crashes and bombs out the sound system.

---

### Post by Perfect Storm on 2006-02-26
Sorry, I don't use KDE so I can't help you there. But I'm 100 % sure that it can be done and also it's possible to change default DVD/CD player in KDE.

---

### Post by snooze on 2006-02-26
Thanks for the tip, A.I.
It's funny, but I never even looked at 'Removable Drives and Media' before.
Since you pointed it out, I'm now using k3b to auto-start when inserting blank DVD's.

Thanks again:)

---

### Post by ekeefe41 on 2006-07-28
Anyone know how to do this in Xubuntu. There seem to be no settings for.

**System tab ---> Preferences ---> Removable Drives and Media**

Is there anything in comand line i can enter to change this setting?

---

### Post by oyvindaa on 2006-09-10
> **bionnaki said:**
> I use bmp for music & gxine for movies. can I use these instead?

You've probably sorted this by now, but in case someone else is wondering:

To autostart gxine when inserting a DVD:

```

gxine dvd:///dev/dvd

```

I'm not sure why, but gxine is the only media player that plays DVDs properly on my laptop. On some, the sound is bad, on others the graphic lags.

---

### Post by Perfect Storm on 2006-11-24
Howto updated, added Audacious to the list.

---

### Post by Perfect Storm on 2007-05-01
Updated and tested in Feisty.

---

### Post by schaumkeks on 2007-12-26
Nice HOWTO. It would get even better if you replace the device nodes with the special parameter %d to make this work in a more general way, e.g.:
```
gxine dvd://%d
```
This is useful for additonal external drives which cannot be accessed with /dev/dvd or /dev/cdrom.
I really miss the explanation of these special parameters in the dialog...
* %d means device node name,
* %m means mount point name,
* %h means HAL UDI.

Bye, Sven

---

### Post by Wikzo on 2008-05-12
Can't find the Movie and DVD tab in Hardy Heron. Where is it?

---

### Post by Perfect Storm on 2008-05-12
I don't know, I think it's replaced by something else. But that "something" I simple can't find/figure out.

---

### Post by schaumkeks on 2008-05-12
Why oh why did they do that???
[http://ubuntuforums.org/showthread.php?t=713724](http://ubuntuforums.org/showthread.php?t=713724)

Please don't mess with the system as they do in this thread (change .desktop files or delete binaries from /usr/bin). You can alway override things with files in the /usr/local path.

---

### Post by Perfect Storm on 2008-05-12
Well, it says now it's under preferences in nautilus instead. Strange place to put it.

[[img]http://www.imageviper.com/displayimage/119697/0/nautiluspreferences-pre-pre.png[/img]](http://www.imageviper.com/displayimage/119695/0/nautiluspreferences.png)
[size=1]*click to enlarge*[/size]

---

### Post by schaumkeks on 2008-05-12
Strange indeed.
And because there are not many applications that are already shipped with a desktop file for the new mime types, we have to do some manual work.

An easy approach with VLC as player for Video-DVDs without messing with any existing system files (I've seen some cruel hacks in the forums) would be the following:

1. Create an alternative launcher for VLC
A: (system wide) in the systems overlay directory (different name or we would override the original):
```
$ sudo cp /usr/share/applications/vlc.desktop /usr/local/share/applications/vlc_video-dvd.desktop
```
OR
B: (per user) in the users overlay directory
```
$ cp /usr/share/applications/vlc.desktop ~/.local/share/applications/vlc_video-dvd.desktop
```

2. Edit the copied file (with sudo nano or your preferred editor):
A: ```
$ sudo nano /usr/local/share/applications/vlc_video-dvd.desktop
```
OR
B: ```
$ sudo nano ~/.local/share/applications/vlc_video-dvd.desktop
```
and add or change the following entries:

3. Change command:
```
Exec=vlc %f
```

4. With this line VLC appears in the Video-DVD list in nautilus preferences:
```
MimeType=x-content/video-dvd;
```

5. Hide the entry from the applications menu:
```
NoDisplay=true
```

6. (Only necessary if the system wide approach 1A has been done) Update the desktop-database to make the entry visible:
```
$sudo update-desktop-database
```

Bye, schaumkeks

---

### Post by Perfect Storm on 2008-05-12
Going to play around a little bit with this. Most multimedia application I compile for myself on Ubuntu. So I have to make a eg. vlc.desktop file from scratch...

Thanks, schaumkeks.

[size=1](and no thanks to the gnome devs to make it a bit tat difficult)[/size]

---

### Post by Lantesh on 2008-05-16
schaumkeks, thank you so much.  Your solution worked like a charm.  I was scratching my head the last two days trying to figure out how to fix this.  I can't believe they took away the ability to simply enter a custom command.  Oh well problem solved.  Thanks again.

---

### Post by DancemasterGlenn on 2008-05-25
Just wanted to say thanks for helping me get Audacious to play cds a long time ago (when I first stumbled across this thread). Unfortunately, the command broke a few releases later... Now inserting a cd just opens audacious, with no playback (or even adding the cd to the playlist). Suffice it to say, I don't believe -p works anymore (even though it still shows up as "play" when I type 'audacious --help' in terminal). I gave up on this a while back, but I came through here again and was wondering if you had any ideas on the matter? Thanks for your time.

---

### Post by Perfect Storm on 2008-05-25
I havn't been able to do it. I can single out a track on a CD with -p but then I have to give it full path plus name to that file on the CD.

---

### Post by DancemasterGlenn on 2008-05-25
Hm. Lame. I tried to get some clarification at the audacious forums while they were still up, but nothing ever came of it. Thanks for your response. If I find out how to make it work at some point I'll post it up here.

---

### Post by schaumkeks on 2008-05-25
CD-Audio autostart with audacious seems to be impossible due to missing commandline options (typical GUI application). The cdaudio-ng plugin added support for cdda urls, but only for single tracks and this feature seems to be broken atm anyway.
see [http://hg.atheme.org/audacious-plugins/log/32d4d5f7020b/src/cdaudio-ng/cdaudio-ng.c](http://hg.atheme.org/audacious-plugins/log/32d4d5f7020b/src/cdaudio-ng/cdaudio-ng.c)
Additionally, this won't work for multiple devices.
The GUI way, selecting "Plugin Services -> Add CD" from the context menu is available but useless for autostart and you can't explicitly choose a device (has to be changed in the plugin configuration).

---

### Post by DancemasterGlenn on 2008-05-25
I figured as much... that newer plugin gave me nothing but trouble. I couldn't even figure out how to make cddb work for a long time (though that might have been a problem with the plugin itself). Sometimes I think about switching back to the 1.3 release, even though I know they've fixed a lot of bugs since then. Oh well.

---

### Post by oddsock on 2008-07-15
Thanks schaumkeks!

That method worked for me.  I short cut it a little, just adding x-content/video-dvd; to the mimetypes list in the existing vlc.desktop gets vlc into the menu choices.  But without changing the "exec=vlc %U" to "exec vlc %f" when I insert a dvd vlc opens but isn't responsive.  

Can you tell me what the %f vs %U does? or where I can find out?

---

### Post by schaumkeks on 2008-07-15
> **oddsock said:**
> 
That method worked for me.  I short cut it a little, just adding x-content/video-dvd; to the mimetypes list in the existing vlc.desktop gets vlc into the menu choices.  But without changing the "exec=vlc %U" to "exec vlc %f" when I insert a dvd vlc opens but isn't responsive.  

Can you tell me what the %f vs %U does? or where I can find out?

The available placeholders are described in the [desktop entry specification]("http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html"). Only %u and %f and their uppercase versions are important for our needs. While %u/%U provides a URL/list of URLs, %f/%F provides a file path.

For (Video-)DVDs the placeholders are replaced like this (example):
%u - file:///media/cdrom0
%f - /media/cdrom0

While testing I found out, that vlc does not play the DVD if you pass the URL form. The %f placeholder works, so we have to use a seperate desktop file for this special purpose. Changing the original one is not recommended (it never is, believe me) as you might break already working things.

A better way for DVD access would be to call vlc with the device name (e.g., /dev/scd0), but such a placeholder does not exist.

---

### Post by oddsock on 2008-07-17
Ah, so by changing the placeholder in the orginal I might be breaking something that requires a url rather than a file to be passed in.  Yeah, the url form in a terminal makes vlc act very strange for my dvds.

Thanks for the info, and the link.

---

### Post by ChrisC on 2008-07-20
Hi all -

I've got a completely vanilla install of Hardy/8.04.  With my Dapper/6.06 install I forked off in all sorts of directions with the media apps and ultimately I couldn't get anything to work.

This time I'm trying to stay with default applications as long as I can, which in this case means trying to get this to work with Rhythmbox.

So, can someone tell me how to get Rhythmbox to start playing a music CD right away?  I already have the Nautilus -> Prefs -> Media set to OPEN Rhythmbox, it's just not autoplaying.

---

### Post by schaumkeks on 2008-07-21
> **ChrisC said:**
> So, can someone tell me how to get Rhythmbox to start playing a music CD right away?  I already have the Nautilus -> Prefs -> Media set to OPEN Rhythmbox, it's just not autoplaying.

There is no autoplay option for the rhythmbox command. Rhythmbox instances are controlled with the rhythmbox-client command which has the --play-uri=URI option. But this is buggy (plays tracks in playing queue if not empty instead of URI) and won't help in this case. Have a look at the (unrecommended) hack at [https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/20170](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/20170).

---

### Post by jmjohn on 2008-08-04
Hi Everyone,

Thanks for your posts. 

In Hardy Heron 8.04, When I navigate to System-> Prefereces -> Removable Drives and Media, I find no "Media" or "Multimedia" tab that I could change the DVD autoplayer in.  

I know what code I want to run when I insert a DVD ( [http://ubuntuforums.org/showthread.php?t=243812](http://ubuntuforums.org/showthread.php?t=243812) ) but where do I put it?

Thanks much,
-glass.dimly

---

### Post by cenhfan on 2008-08-15
Same problem here, the tab jmjohn mentioned seems to be missing in kde 4.1...

Is there some other way?

Thanks,
Timo

---

### Post by mwclark4453 on 2008-08-22
Ditto on the last two posts.  I'm not seeing MultiMedia tab under the System-> Preferences -> Removable Drivers and Media.

I've just got Cameras, PDAs, Printers & Scanners, and Input Devices tabs.

I checked Synaptic to see if I might be missing a package but didn't notice anything with the search of "volume manager".

I am getting RhythmBox up when I plug my iPod in so there is an association but I haven't found the conf file that contains it yet.  Thought I would try the GUI first.

---

### Post by Gourgi on 2008-08-22
> **mwclark4453 said:**
> Ditto on the last two posts.  I'm not seeing MultiMedia tab under the System-> Preferences -> Removable Drivers and Media.

RUN from command line or Alt+F2```
gnome-volume-properties
```

---

### Post by graabein on 2008-08-27
> **Gourgi said:**
> RUN from command line or Alt+F2```
gnome-volume-properties
```

That brings up the same dialogbox but I can't see a tab for (multi)media either. I've got *Cameras*, *PDAs*, *Printers & Scanners* and *Input Devices*.

I want to stop GNOME Music Player from autostarting when I insert audio CD's BTW.

---

### Post by TheTank on 2008-08-27
Thanks for the guide AI.

I have a question and I hope it is not to far OT but is there some kind of system hook that is called when a CD or DVD or whatever is inserted?

I am wondering because I'd like to do certain stuff in this case and it might also be interesting for people who do not use a GUI or this GUI.

Thanks again.

---

### Post by Perfect Storm on 2008-08-28
> **graabein said:**
> That brings up the same dialogbox but I can't see a tab for (multi)media either. I've got *Cameras*, *PDAs*, *Printers & Scanners* and *Input Devices*.

I want to stop GNOME Music Player from autostarting when I insert audio CD's BTW.

It's moved to Nautilus.

---

### Post by Swynndla on 2008-09-30
> **cenhfan said:**
> Same problem here, the tab jmjohn mentioned seems to be missing in kde 4.1...

Is there some other way?

Thanks,
Timo

I got it working under KDE by following the instructions [here](http://www.kde-forum.org/artikel/15286/howto-auto-play-dvd-in-xine-with-kde.html)

---

