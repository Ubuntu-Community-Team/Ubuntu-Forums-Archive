---
title: "last-exit last.fm player"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by reda_ea on 2006-07-11
last-exit is a program to play music from last.fm
(not just update your profile, it really streams music from there)

officiel site is here :
[http://www.o-hand.com/~iain/last-exit/]("http://www.o-hand.com/~iain/last-exit/")

here is a little package I made for ubuntu (in attachment)

also, the old version 0.2 with a save song patch is here
[http://www.ubuntuforums.org/showthread.php?t=149018]("http://www.ubuntuforums.org/showthread.php?t=149018")

enjoy

EDIT
Added the "save song" patched version (last-exit_1.0-1ubuntu2_i386.deb.tar.bz2).

EDIT 2
Added a patch file for the "save song" feature.

EDIT 3
Added the lastest version 2.0 without save song for the moment

EDIT 4
Patched version 2.0 (thanx to hazart) packaged for i386 and amd64, and the patch file of course.

EDIT 5
Bug with "lastfm:" urls corrected

EDIT 6
Version 3.0 patched is available here:
[http://rapidshare.com/files/334255/last-exit_3-1_i386.deb.html]("http://rapidshare.com/files/334255/last-exit_3-1_i386.deb.html")
thanks to [ferdy]("http://ubuntuforums.org/showpost.php?p=1651014&postcount=100") and [ZeBob]("http://ubuntuforums.org/showpost.php?p=1650061&postcount=99")

EDIT 7
added [SIZE="4"]version 5[/SIZE] thanks to [introspectif]("http://ubuntuforums.org/showpost.php?p=2930297&postcount=194") (I corrected his deb and repackaged it so download this even if you already have his package)
oh and sorry this is for feisty and theres no 64bit version for the moment

---

### Post by buttari on 2006-07-11
Hi,
configure didn't go throug for me. It complains about some dependencies that are, indeed, already installed on my machine.
```

checking for LASTEXIT... configure: error: Package requirements (gconf-2.0                gdk-pixbuf-2.0                  gtk+-2.0 >= 2.6                 gstreamer-0.10 >= 0.10.0                gstreamer-base-0.10                                   gstreamer-plugins-base-0.10 >= 0.10.0) were not met:

No package 'gconf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LASTEXIT_CFLAGS
and LASTEXIT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
can you help me with this?

alfredo

---

### Post by reda_ea on 2006-07-11
install these packages

libgconf2-dev
libgstreamer0.10-dev
libgstreamer-plugins-base0.10-dev
libgdk-pixbuf-dev
libgtk2.0-dev
libmono-dev
libgnome2.0-cil
mono-mcs
mono-gac

it should compile without problems

---

### Post by hazart on 2006-07-12
Compiles fine, works fine, plays fine :-)

I have created an amd64 .deb for it.

---

### Post by mazirian on 2006-07-12
Debian/Gnome developer Ross Burton has packages for this in his repository as well: [http://burtonini.com/debian/](http://burtonini.com/debian/)

---

### Post by PriceChild on 2006-07-12
As far as i know, amarok will stream from last.fm too?

---

### Post by reda_ea on 2006-07-12
> As far as i know, amarok will stream from last.fm too?

yes it does .. and it's very ugly.

and amarok isn't gnome, does a very different task than just listening to a radio stream..

that's why i like last-exit

---

### Post by theturtlemoves on 2006-07-12
(edit: never mind)

---

### Post by reda_ea on 2006-07-15
I tried working a little bit on that save song patch that was availaible for version 0.2, and well .. IT WORKS

I also changed the interface a little bit, it's not perfect yet, but better than before.

As always, here's a .deb package (link to attachement in first post)
[http://www.ubuntuforums.org/attachment.php?attachmentid=12755&d=1152941427]("http://www.ubuntuforums.org/attachment.php?attachmentid=12755&d=1152941427")

and a screenshot of how it looks.

---

### Post by OrganicPanda on 2006-07-18
wow, just wow, this is amazing, very well done. 

hey reda_ea are you developing this further or leaving it at this because i have some feature requests, this is something i would really like to help with if only i knew how, my last software programming was vb6 in windows and prehaps some java lol

---

### Post by molgar on 2006-07-18
Thanks for that "save song" version. I also missed it :)

---

### Post by mattisking on 2006-07-18
When I run it after install, I get this:
exec: 5: -a: not found

Any ideas? Thanks!

---

### Post by reda_ea on 2006-07-19
> **OrganicPanda said:**
> wow, just wow, this is amazing, very well done. 

hey reda_ea are you developing this further or leaving it at this because i have some feature requests, this is something i would really like to help with if only i knew how, my last software programming was vb6 in windows and prehaps some java lol

I m not the developer of this program, just a happy user who likes it. I think feature requests should be posted both in the forum and sent to the main developer.
I think someone is working on a libnotify feature. Also, I'll be working on some user interaction improvements when I have time (and I don't have much for the moment :( ).

---

### Post by theturtlemoves on 2006-07-19
> **mattisking said:**
> When I run it after install, I get this:
exec: 5: -a: not found

Any ideas? Thanks!

Try this:

```
gksudo gedit /usr/bin/last-exit
```

and replace "#!/bin/sh" with "#!/bin/bash"

Mono squawks a bit when it is run with non-standard shells, because they don't support the -a option.

---

### Post by MikkelM on 2006-07-20
My player lags :/

Has anyone else experienced this too?

---

### Post by Hairy_Palms on 2006-07-22
does anyone else use the latest official lastfm player? its open source y'know and does kinda pwn :)
[http://static.last.fm/client/Linux/LastFM_Linux_1.0.0b.tar.bz2](http://static.last.fm/client/Linux/LastFM_Linux_1.0.0b.tar.bz2)

---

### Post by Arisna on 2006-07-23
The official client uses QT, IIRC.  Last Exit is probably a more promising option for GNOME and XFCE users because it uses GTK+.

---

### Post by Hairy_Palms on 2006-07-23
ist static qt, the same as opera but it works well and static so doesnt have an immense load time

---

### Post by Arisna on 2006-07-23
0_0

That was fast.

I didn't realize that significance of the static linking.  When I tried the official client out before, though, it still didn't look very nice because of the different toolkit, even if functionality wasn't bad.

---

### Post by Arisna on 2006-07-24
> **MikkelM said:**
> My player lags :/

Has anyone else experienced this too?
Yes, mine is a little laggy with the first song I play after launching the program.  This also happened under the previous version.  People said it had to do with buffering.  Didn't happen with the official client.

---

### Post by Zottan on 2006-07-26
can you say howto activate save feature from source 1.0 for amd64 :? , thanks

---

### Post by reda_ea on 2006-07-28
the lag is caused on the first seconds of playing by the save song patch.
I don't know why it does this, but if you don't want lag, just use the normal version (that is also provided as a .deb)

> can you say howto activate save feature from source 1.0 for amd64  , thanks
ther's a lot of modifications to the source code, it's because you don't just "activate" it, you change the way the player works so you always have a local copy of the current stream in a file in your home.
I'll put a patch for the source code, I was going to do it looong time ago, but I didn't have the time :(

PS: I'll put the patch in the first post.

---

### Post by Buffalo Soldier on 2006-07-28
just curious, which license is the developer use? I can't seem to find that info on the site given [http://www.o-hand.com/~iain/last-exit/about.html](http://www.o-hand.com/~iain/last-exit/about.html)

---

### Post by reda_ea on 2006-07-29
> **Buffalo Soldier said:**
> just curious, which license is the developer use? I can't seem to find that info on the site given [http://www.o-hand.com/~iain/last-exit/about.html](http://www.o-hand.com/~iain/last-exit/about.html)

look in the source files

---

### Post by HAARP on 2006-07-29
Are there any plans to make the app able to create local streams so I can play it with xmms? The official player is capable of that.
That, and less lagging, would be awesome! :)

---

### Post by Zottan on 2006-07-30
thanks for the patch , but new last-exit 2.0 released

---

### Post by topyli on 2006-07-30
> **HAARP said:**
> Are there any plans to make the app able to create local streams so I can play it with xmms?
The best way to use an external player is to run the [Last.fm proxy]("http://vidar.gimp.org/lastfmproxy/") and connect to that with your favorite player.

---

### Post by Buffalo Soldier on 2006-07-31
Nice job reda_ea. Any rough estimates when you'll be releasing ver 2.0?

---

### Post by quickblaine on 2006-08-01
for some reason when i use this program the tracks are really really jumpy, and it doesnt seem to stop. is that just lag or something else, and how do i fix it?

---

### Post by quickblaine on 2006-08-01
never mind, I just installed the version without the save song feature

---

### Post by HAARP on 2006-08-02
> **topyli said:**
> The best way to use an external player is to run the [Last.fm proxy]("http://vidar.gimp.org/lastfmproxy/") and connect to that with your favorite player.

Rocks. Thanks!

---

### Post by stalefries on 2006-08-04
For those who care, i compiled Last Exit version 2.0. No patch, sorry. It's attached.

---

### Post by petervk on 2006-08-04
Just a warning to users, the new last-exit 2.0 package does not upgrade the last-exit 1.0 package previously in this post. You need to uninstall the old package to actually use the new last-exit 2.0.

---

### Post by reda_ea on 2006-08-04
I made a better package (no checkinstall and all) for version 2.0 it's in the first post.

No Save Song Patch for the moment, I will look at it later.

> **HAARP said:**
> Are there any plans to make the app able to create local streams so I can play it with xmms?

I think that could be easy with a little hacking, 
by the way the patched version creates a hidden file in your home dirctory with the current song, may be this could be used somehow ..

EDIT

When I play ~/.lastfm.mp3 with xmms with repeat song on it works :)

---

### Post by hazart on 2006-08-04
I have successfully ported the old v1.0 patch to v2.0 and saved the first pair of songs. The new patch is attached to this message.

Known issues:
[LIST]
[*]The Lag issue still exists
[*]Sometimes it doesn't copy the ~/.lastfm.mp3 to the desired folder, when the song finishes. I'm not certain when and why? This needs further attention.
[/LIST]

NB: If anybody wants i can make a amd64 .deb with save song patch. Just write in this thread an ill look at it. Atm. i don't remember how to make the .deb ;-)

EDIT: O.K. now i think i know why. You have to manullay select save for each song that you want to save. A future feature could be that it saves all complete songs to a dir that you could sort afterwards.

---

### Post by reda_ea on 2006-08-04
> The new patch is attached to this message.

I think you forgot to put the patch file ...

for the package, you can just take my package and replace the 3 liblastexit* files in /usr/lib/last-exit with the ones you got (that's the only binary files there I think).
maybe also the exe file (for the patched version).

---

### Post by hazart on 2006-08-04
Sorry, forgot to post the files
I did some reading and made a new and, according to *lintian*, better .deb package for amd64 containing the save patch.

**Save_song is working great**, thank you for your work. Here is mine :P

---

### Post by reda_ea on 2006-08-05
thanks hazart,

I added your package as well as the i386 package and the corrected patch file (just removed the error messages by diff from the file) to the first post.

---

### Post by raintheory on 2006-08-05
Hey this is great!  Just found this today (been wanting the last.fm player in ubuntu for awhile tho).  Ran the install via a VNC connection, and it seemed to install and start up just fine.  But can't check the audio currently b/c of the remote connection.

Thanks alot though, this is wonderful!

---

### Post by hazart on 2006-08-05
No problem, i had to practice my debian package skills anyways. Now one thing that would be cool, would be to fix the lag issue. I have been looking at what the patch adds to player.c, but even though i'm a modest C programmer, with lots of kernel code on my back, i can't understand the gstreamer stuff :P - So i guess it's up to you :)

---

### Post by OrganicPanda on 2006-08-06
Glad to see things are still comming along nicely, i removed version 1 with dpkg but the newer deb wont install, i get "Error: Cannot Install 'libdbus-1-cil".

I can't find a package with that exact name, any ideas?

---

### Post by reda_ea on 2006-08-09
the package is in the dapper repos ...
I don't know why you don't have it

---

### Post by reda_ea on 2006-08-09
There was a little problem with the lastest package not working with lastfm: urls

Problem corrected with a new package.

---

### Post by JoshHendo on 2006-08-12
Nice! Glad that I found it :)

I installed the official last.fm player, and it exited when I tried to play a song, so I am assuming that im not the only one (hence the name).

Anyway, thanks for this!

---

### Post by OrganicPanda on 2006-08-15
Ok my mistake, I was being silly, I've got 2.0 installed but what do I do with the patch file? lol I'm so bad at this

---

### Post by reda_ea on 2006-08-15
> **OrganicPanda said:**
> Ok my mistake, I was being silly, I've got 2.0 installed but what do I do with the patch file? lol I'm so bad at this

The patch file is to use with the source code if you want to compile it yourself.
Just use the patched .deb (last-exit_2.0-1ubuntu2_i386.deb.tar.bz2) if you want save song option or the other one if not.

---

### Post by Psukez on 2006-08-17
thanks, works flawlessly :D

---

### Post by buddhalover on 2006-08-18
forgive me for my ignorance but what should i do with the patch file?]

by the way, much gratitude for creating last-exit
tis a beautiful thing. \\:D/

---

### Post by reda_ea on 2006-08-19
> **buddhalover said:**
> forgive me for my ignorance but what should i do with the patch file?]

by the way, much gratitude for creating last-exit
tis a beautiful thing. \\:D/

hey I just answered this 2 posts before you :-| 
anyway 

[QUOTE= me]The patch file is to use with the source code if you want to compile it yourself.
Just use the patched .deb (last-exit_2.0-1ubuntu2_i386.deb.tar.bz2) if you want save song option or the other one if not.[/QUOTE]

Oh and I'm not the developper of this beautiful thing :) I just patched and packaged it.

---

### Post by buddhalover on 2006-08-19
i tried compiling from source first. Then it worked flawlessly. Then when I tried to unpack the deb with the save patch running the program just freezes it. any suggestions? I really want the save song feature.

---

### Post by eduff on 2006-08-22
Hi,
New installation of Dapper, if I install last-exit with all required packages described above, installation is successful, but I get this when I try to run:  


Unhandled Exception: System.DllNotFoundException: libc
in (wrapper managed-to-native) LastExit.Driver:prctl (int,byte[],ulong,ulong,ulong)
in <0x0003f> LastExit.Driver:SetProcessName (System.String name)
in <0x0002d> LastExit.Driver:Main (System.String[] args)

Any ideas what this means?

Thnks

---

### Post by Ragdriet on 2006-08-23
What can I do to apply patch to Last Exit v2.0 to download songs ? Anyone knows ?

---

### Post by &#12465;&#12452;&#12488; on 2006-08-24
Thanks for packaging Last-Exit, but I wish you wouldn't apply the song download patch. The Last.fm service shouldn't be abused like that, and there's also a possibility it could make the Last-Exit client banned, which wouldn't be very fun for its devs and us Last.fm-loving GNOME/XFCE users.

---

### Post by Ragdriet on 2006-08-26
As you say, I think that is not the best way to apply patch and abuse the service of Last.FM, I wouldn't like that client would be banned cause I like the client working, and it wouldn't be very funny for its devs.

---

### Post by reda_ea on 2006-08-27
> New installation of Dapper, if I install last-exit with all required packages described above, installation is successful, but I get this when I try to run:
Is your system up to date? I didn't test this with a fresh install, only in my PC.

> What can I do to apply patch to Last Exit v2.0 to download songs ? Anyone knows ?
patch is the command to do that (you'll find help in google).

> but I wish you wouldn't apply the song download patch.
Of course, using the patch to steal illegal music is .. well .. illegal.
But again, reading mp3 at all is illegal in some places (that's why it doesn't come default with ubuntu), and having this in the repos doesn't mean anyone can use it as he wants. The same goes for last-exit.
Anyway last-exit doesn't have that by default, and the patch is not official. But this is open source, anyone can modify the code in any way, and that's what we like about it : freedom.

---

### Post by j_m on 2006-08-30
> **hazart said:**
> I have successfully ported the old v1.0 patch to v2.0 and saved the first pair of songs. The new patch is attached to this message.


Can you attach the patch for 1.0, please? 2.0 needs dbus, not something I want to install... ](*,)

---

### Post by matid on 2006-08-30
Have anyone tried to install it on Edgy? It doesn't seem to play anything. It's silent, even after turning up the volume. Any other player works fine.

---

### Post by macross3003 on 2006-08-31
> **hazart said:**
> Sorry, forgot to post the files
I did some reading and made a new and, according to *lintian*, better .deb package for amd64 containing the save patch.

**Save_song is working great**, thank you for your work. Here is mine :P

the .deb file has an error in the postinst script... it refers to /usr/etc/gconf/schemas/last-exit.schemas which doesn't exists... must say just /etc/gconf/schemas/last-exit.schemas...

thanks for the pack... 
but why always everybody just share the .deb file and no .dsc and tarball?? i really don't undestand this attitude ](*,)

workaround:
sudo ln -s /etc /usr/etc
sudo dpkg -i last-exit-2.0-0ubuntu1_amd64.deb
sudo rm /usr/etc

beside that everything works fine

---

### Post by pangloss on 2006-09-01
> **macross3003 said:**
> 
but why always everybody just share the .deb file and no .dsc and tarball?? i really don't undestand this attitude ](*,)

It's funny, just last week I was thinking the exact same thing about the Ubuntu community in general.

---

### Post by reda_ea on 2006-09-01
> **macross3003 said:**
> but why always everybody just share the .deb file and no .dsc and tarball?? i really don't undestand this attitude ](*,)

I make packages with dpkg -b .. so I don't have them

[QUOTE=j_m]Can you attach the patch for 1.0, please? 2.0 needs dbus, not something I want to install...[/QUOTE]

you can find everything here [http://membres.lycos.fr/bou3ou/packages/last-exit/]("http://membres.lycos.fr/bou3ou/packages/last-exit/")

---

### Post by j_m on 2006-09-10
> you can find everything here 
[http://membres.lycos.fr/bou3ou/packages/last-exit/]("http://membres.lycos.fr/bou3ou/packages/last-exit/")

Wonderful, thanks! :cool:

---

### Post by crazedgremlin on 2006-09-15
Hey.... I love it!
But what is the save song patch and how do I install it?

---

### Post by reda_ea on 2006-09-17
> **crazedgremlin said:**
> Hey.... I love it!
But what is the save song patch and how do I install it?

it's a modification of the program to be able to save the track you're listening to, it adds the save button.

It's already included in the lastest package (on the first post), just instal the .deb and you have it.

---

### Post by macross3003 on 2006-09-21
here is a fixed deb for amd64 made from edgy sources containing save song patch.

edit:
the steps I followed to up this files were:

$ apt-get source last-exit
$ apt-get build-dep last-exit
$ cd last-exit-2.0
$ mkdir debian/patches
$ mv ~/last-exit-2.0-save_song.patch debian/patches
$ dch -i 
$ fakeroot dpkg-buildpackage -d
$ sudo dpkg -i ../last-exit_2.0-1build2_amd64.deb

ok, the thing is that i cannot heard the music nor skip track (no error message at all) :-& 
anybody knows if the patch works with the edgy packed version?

thanks

---

### Post by bdoetsch on 2006-09-22
Same effect here. So I'm back to the edgy repository version. No sound on edgy with the debs here.

---

### Post by recrispi on 2006-09-23
Hi! I'm new here...
I installed the last-exit .deb, so I have 
 last-exit      2.0-1          Last.fm audio player
but I hear no sound... when I run last-exit from command line and select a radio I get the following message:
$ last-exit
&#65279;station: [http://ws.audioscrobbler.com//radio/adjust.php?session=3b4866df8213db3fd584df36887b4f66&url=lastfm://globaltags/japanese&debug=0](http://ws.audioscrobbler.com//radio/adjust.php?session=3b4866df8213db3fd584df36887b4f66&url=lastfm://globaltags/japanese&debug=0)
response=OK
url=lastfm://globaltags/japanese
toggled
[http://streamer2.last.fm:80/last.mp3?Session=3b4866df8213db3fd584df36887b4f66](http://streamer2.last.fm:80/last.mp3?Session=3b4866df8213db3fd584df36887b4f66)
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
Everyday Dream
I think I have last-exit sending its output to another device not to ALSA (which I have installed). Any recomendation? Where should I configure this?
Thanks.

---

### Post by bdoetsch on 2006-09-23
hm. comparing the repository source with the build-src of the package could probably show the differences, so that the patch could be ported.

---

### Post by tuxcantfly on 2006-09-23
modified the amd64 deb, and uploaded a new one that fixes the errors in the control, prerm, and postinst files, and changes the version so that it won't conflict with the one in the ubuntu repos

---

### Post by tuxcantfly on 2006-09-23
by the way, I'm getting this dbus error on edgy:

Unhandled Exception: System.DllNotFoundException: /usr/lib/last-exit/liblastexit.so
  at (wrapper managed-to-native) LastExit.DBus:check_lastexit ()
  at LastExit.DBus.CheckInstance () [0x00000]
  at LastExit.Driver.Main (System.String[] args) [0x00000]

help please?

---

### Post by tuxcantfly on 2006-09-23
never mind, fixed it by installing libdbus-1-2 from dapper repos

---

### Post by tuxcantfly on 2006-09-24
just noticed that someone already made an edgy amd64 version, seems like mine's not needed. just tried it, but it refuses to play anything. starts fine, just doesn't play. same error with mine.

---

### Post by tuxcantfly on 2006-09-24
this is the error message (doesn't play):

```
(last-exit:11893): GStreamer-CRITICAL **: gst_bin_get_by_name: assertion `GST_IS_BIN (bin)' failed

(last-exit:11893): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(last-exit:11893): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(last-exit:11893): GStreamer-CRITICAL **: gst_bin_get_by_name: assertion `GST_IS_BIN (bin)' failed

(last-exit:11893): GStreamer-CRITICAL **: gst_bin_get_by_name: assertion `GST_IS_BIN (bin)' failed

(last-exit:11893): GStreamer-CRITICAL **: gst_bin_get_by_name: assertion `GST_IS_BIN (bin)' failed

(last-exit:11893): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(last-exit:11893): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(last-exit:11893): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(last-exit:11893): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(last-exit:11893): Gtk-WARNING **: Error loading theme icon for stock: Icon 'stock_volume-med' not present in theme

(last-exit:11893): Gtk-WARNING **: Error loading theme icon for stock: Icon 'stock_volume-med' not present in theme
station: http://ws.audioscrobbler.com//radio/adjust.php?session=3e24927c4e37025a83f7913cf6d42376&url=lastfm://artist/Hilary Duff/similarartists&debug=0
response=OK
url=lastfm://artist/Hilary Duff/similarartists
toggled
```

now, I exit from last-exit

```
(last-exit:11893): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed
http://streamer2.last.fm:80/last.mp3?Session=3e24927c4e37025a83f7913cf6d42376
(last-exit:11893): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(last-exit:11893): GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

help please?

---

### Post by FaxeSystem on 2006-09-24
Hi, I`m verry happy with last-exit but I`ve still one problem. When I`m using the version without the save function everything works fine but when I'm using the version with the integrated save function the sound is stuttering as hell? Anyone with similar problems?

---

### Post by reda_ea on 2006-09-25
> **FaxeSystem said:**
> Hi, I`m verry happy with last-exit but I`ve still one problem. When I`m using the version without the save function everything works fine but when I'm using the version with the integrated save function the sound is stuttering as hell? Anyone with similar problems?

EVERYONE has that similar problem.
but it only lasts for the first one or two songs, after that it plays well.

and if you want it to work well from the start, mute the player and open ~/.lastfm.mp3 (not sure about the filename) in xmms or another player.

As for the edgy problems, I don't have edgy yet, and anyway my PC is broken for the moment, I'll take a look at it ASAP.

---

### Post by knatten on 2006-09-26
If you don't get any sound, and get the message "** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int) 3" you don't have all the needed gstreamer-plugins.

Fix:
sudo apt-get install gstreamer0.10-plugins-ugly

---

### Post by recrispi on 2006-09-28
> **knatten said:**
> If you don't get any sound, and get the message "** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int) 3" you don't have all the needed gstreamer-plugins.

Fix:
sudo apt-get install gstreamer0.10-plugins-ugly

Thanks!

That solved my problem! :-)

---

### Post by beamo on 2006-09-29
I absolutely love this, thank you!

---

### Post by ebel_ on 2006-09-30
Another edgy user here who wants to save files. No matter the version of last-exit (1 or 2), the normal client will work fine, but when patched to save files, nothing will play, and I can't switch tracks. I've looked at it through wireshark (the successor of ethereal), a packet sniffer, and aside from a little bit of traffic when it starts up, there is no bandwidth use. The unpatched version makes lots of traffic. A GUI patch shouldn't really affect networking...

---

### Post by tuxcantfly on 2006-10-01
same problem here

---

### Post by tuxcantfly on 2006-10-01
hey, could it be possible that the last.fm folks have banned last-exit? is it still working for anyone?

---

### Post by ebel_ on 2006-10-02
> **tuxcantfly said:**
> hey, could it be possible that the last.fm folks have banned last-exit? is it still working for anyone?

No because the unpatched version still works fine for me. It's only the patched version that doesn't work. It's a very weird problem. I'm going to try the patched version on dapper, and see does it work. I normally use edgy. If that's the problem then that means something changed in edgy that the save file patch relys on.

And it's hard to ban a client, and imposible for them to detect if you are saving the file.

---

### Post by ebel_ on 2006-10-02
I can confirm that the patched save song version linked to in the first post works on Dapper, and not Edgy. However I tested it on i386 Dapper and powerpc Edgy, so I don't know if it's the version or the architecture that matters. Since everyone forgets about non-intel architecure, I downloaded and source and patch for v2.0 from [http://membres.lycos.fr/bou3ou/packages/last-exit/](http://membres.lycos.fr/bou3ou/packages/last-exit/). I compiled it succesfully and this version works fine and I can save the songs.

The save song version is horribly stuttery for the first half of the first song, then it quickly goes normal.

---

### Post by tuxcantfly on 2006-10-02
tried it on amd64 dapper, and it still doesn't work. same error.

---

### Post by reda_ea on 2006-10-03
> **ebel_ said:**
> A GUI patch shouldn't really affect networking...

it's not a gui patch, you can look at it, it changes the whole way the player works. the original player has no way of saving the song .. or playing it with anything else than gstreamer.
yeah it's bad design but I don't think the original programmer meant to go that far when he fist started it...

[QUOTE=ebel_]so I don't know if it's the version or the architecture that matters. Since everyone forgets about non-intel architecure[/QUOTE]

yes the architecture matters, the player itself is in mono, but it contains and uses a C library to get stuff from last-fm, only this lib needs recompiling, the rest is architecture  independant.
as for the version, there shouldn't be any problem except dependencies, since when I first made the packages there may be some dependencies I forgot to include, or packages coming in a default ubuntu install...

ebel_ , are you in edgy? if so could you post your packages here please, since I'm not upgrading to edgy yet .. or maybe (if you didn't make a package) just send me the liblastfm binary files (or a checkinstall package).

---

### Post by ebel_ on 2006-10-03
[quote=reda_ea]it's not a gui patch, you can look at it, it changes the whole way the player works.[/quote]
I thought maybe the gstreamer folk (or mono or someone) had changed something that broke backwards compatibility, but tuxcantfly seems to have ruled that out.

[quote=reda_ea]
ebel_ , are you in edgy? if so could you post your packages here please, since I'm not upgrading to edgy yet .. or maybe (if you didn't make a package) just send me the liblastfm binary files (or a checkinstall package).[/quote]
Do you mean my last-exit packages? I just patched the original 2.0 source file. Would powerpc compiled libraries be much use to you? I've attached the patched and compiled programme. I ./congure-ed it into it's own directory and tared it up.

---

### Post by reda_ea on 2006-10-03
> Would powerpc compiled libraries be much use to you?

not to me since I'm still in dapper and everything is fine for me, but as people have problems in edgy someone should make packages for it (powerpc, amd and intel).

---

### Post by tuxcantfly on 2006-10-03
running in a 32 bit vmware vm, it works fine. it doesn't like amd64; must be an architecture issue

---

### Post by tuxcantfly on 2006-10-03
but then again, I'm also using kubuntu. might that be the issue?

---

### Post by ebel_ on 2006-10-04
[quote=reda_ea  	
]not to me since I'm still in dapper and everything is fine for me, but as people have problems in edgy someone should make packages for it (powerpc, amd and intel).[/quote]
The version I uploaded is broken. I'll be more than happy to share a compiled version *when* I can get it to work.

It's looking like it's an arcitecture issue. Which is a pain cause normally open source software is quite platform neutral.

---

### Post by IbeeX on 2006-10-04
It is working on amd64 but it is wery sensitive starts to skip vhatewer I doo on comp

---

### Post by Binary Jay on 2006-10-04
Okay, Last Exit...  I got it from the Edgy repos...  but I'm confused on what the difference is that Last Exit gives me compared to the lastfm player...  it seems to have reinvented the wheel.

---

### Post by topyli on 2006-10-05
> **Binary Jay said:**
> Okay, Last Exit...  I got it from the Edgy repos...  but I'm confused on what the difference is that Last Exit gives me compared to the lastfm player...  it seems to have reinvented the wheel.
I'ts GTK+, it's a Rebellious Unofficial Hack, and it's got a much cooler website! :cool:

---

### Post by Jonas Reiff on 2006-10-05
It works fine for me

Witch comand do i use too build build with the save song patch? i have build last-exit with dpgk -i last-exit-2.0-0ubuntu1_amd64.deb

---

### Post by ulisse on 2006-10-06
Any chance to have a patched version 3.0 for Edgy 32bit?

---

### Post by brk3 on 2006-10-15
Yo this rocks thanks loads! :) Espially since the normal last.fm client isnt working for me right now

---

### Post by brk3 on 2006-10-15
Cant believe how good it is! :)

---

### Post by gohanUbuntu on 2006-10-18
Maybe my question will sound stupid (and maybe it is), however I prefer you tell me "...that's sooooo easy [-(  ..." rather that don't ask:

I downloaded last-exit-2.0.tar-bz2 and its patch last-exit-2.0-save_song.patch, my question is..how can I patch it? :-k 

I'm using Edgy under Intel. I tried to patch in the classic way:

#cd last-exit-2.0
#patch -p0 < last-exit-2.0-save_song.patch

But it doesn't work ](*,) I know is trivial for some of you guys ;)

---

### Post by Nubbie on 2006-10-20
So Iain released version 3.0... Edgy has packages already.

Question is... will there be version 3.0 packages here for Dapper?
(and will the save song patch still function??)](*,)

---

### Post by ZeBob on 2006-10-22
Discover this great app today on Edgy !

Here are the save patch for 3.0.

[ATTACH]18012[/ATTACH] #patch
[ATTACH]18013[/ATTACH] #source patched

Note : Modif applied for gst10, see the bug report mentionned there : [http://raphael.slinckx.net/blog/2006-03-06/deskbar-and-leaftag-last-exit](http://raphael.slinckx.net/blog/2006-03-06/deskbar-and-leaftag-last-exit)
I've just add "! typefind !" to the "bin" string. It's was hard to find since i'm not a programmer ](*,) 

For deb package don't know how to make it but shouldn't be so hard for anyone to do it.
Have fun :)

---

### Post by ferdy on 2006-10-23
Hallo,
i have build a patched Version of last-exit 3 for dapper.
You can [her download the DEB]("http://rapidshare.com/files/334255/last-exit_3-1_i386.deb.html").

I m not the developer of this program and not the hacker for the patch...

---

### Post by ZeBob on 2006-10-23
Made a mistake, thought this post could solve a bug.

---

### Post by reda_ea on 2006-10-23
thanks all for the good work,
I put the new package in the first post

anyway I like the new ui imporovements, but I have a little problem with this one: sometimes sound stops working and never plays again (the player is normal but nothing is downloaded), anyone got the same ?
I think it's just my PC but I don't know, I'll try again when I reboot.

---

### Post by John.Michael.Kane on 2006-10-23
Also for those running Edgy last-exit 3.0 is in the repo's.

---

### Post by ZeBob on 2006-10-25
@reda-ea:
Got this too : sounds is more and more distorded when i click on next, and when i try to save the file i've got an anormal cpu usage then. But strangely these things don't happen when i lauch last-exit from the directory where i compiled it : no anormal cpu usage, and almost no distorded sound. But I don't understand why !

@SD-Plissken : yes but we try to include the save song patch here.

---

### Post by cumic on 2006-10-28
After install, I needed some additional packages:

```
$ sudo apt-get install libdbus-glib-1-dev
```

Another thing, for the people who hates rapidshare, I've put a mirror:

[http://lapapelera.org/wp-content/lastexit_31_i386.deb](http://lapapelera.org/wp-content/lastexit_31_i386.deb)

And my blog entry, in spanish: [http://lapapelera.org/lastfm-para-gnomegtk/](http://lapapelera.org/lastfm-para-gnomegtk/)

I love this player!

---

### Post by erdu on 2006-10-31
just installed last-exit_3-1_i386.deb on intel...no problems during installation, but when i wanted to launch the program, i waited for 20 seconds or so, and finally it didn't get launched...so now i'd like to uninstall (or fix this)...how???

---

### Post by hulet on 2006-10-31
For people who are experiencing the sound skipping (and generally chocking up) problem with the last-exit 3.0 (patched version), what you can do is (and this has solved the similar problem I was experiencing)to open the patch and find a text that reads "alsasink" and change it with "osssink", "esdsink", or any variation of this, and recompile to see if it gets better. For me esdsink works like a charm although it has a problem playing the first song.

---

### Post by hulet on 2006-10-31
> **erdu said:**
> just installed last-exit_3-1_i386.deb on intel...no problems during installation, but when i wanted to launch the program, i waited for 20 seconds or so, and finally it didn't get launched...so now i'd like to uninstall (or fix this)...how???
What message do you get when you try to run the program from the terminal?

To uninstall, I think it is "dpkg -i last-exit_3.1" without the quote.

---

### Post by erdu on 2006-11-01
> **hulet said:**
> What message do you get when you try to run the program from the terminal?

To uninstall, I think it is "dpkg -i last-exit_3.1" without the quote.

Problem's been solved. Uninstalled with "sudo apt-get remove last-exit" 
Message I got when running last-exit_3-1 from a terminal was of a missing .dll file. Can't recall exactly, got something to do with dbus. Installing last-exit_2.0-1ubuntu2_i386.deb worked like a breeze, so I'm using the older version now. What's the difference with the newest one?

---

### Post by FaxeSystem on 2006-11-01
Are there any debs with the patched version 3 for edgy? Because libdbus-1-2 has been replaced by libdbus-1-3 in edgy and so there is a dependency problem when I try to install the dapper deb.

---

### Post by Polygon on 2006-11-03
EDIT: I fixed this by installing version one, which installed some dependencies and then i upgraded to version three and now it works. here is a ss of the dependencies that it installed if you want to install them manually:

[[IMG]http://img139.imageshack.us/img139/4447/lastexityx3.th.png[/IMG]](http://img139.imageshack.us/my.php?image=lastexityx3.png)


i cant launch this from dapper

i had to first install mono now its giving me even more errors:
```
mark@genesis:~$ last-exit

** (/usr/lib/last-exit/last-exit.exe:25832): WARNING **: The following assembly referenced from /usr/lib/last-exit/last-exit.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=0)
     Version:    2.8.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/last-exit).


** (/usr/lib/last-exit/last-exit.exe:25832): WARNING **: The class Gtk.ActionGroup could not be loaded, used in gtk-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...
Aborted

```


mmm wonderful. it cant find packages when i try to compile it myself becuase the author spelled the package name wrong

```

No package 'gconf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found

```

thats because the package names are gstreamer0.10 gstreamer0.10-plugins-base and so on and so on. back to version one....

---

### Post by Mechanical on 2006-11-08
I am using edgy and I can get the last exit player in the repo working fine but no save song button.  I try to install the one provided here and it tells me lidbus-1-2 is not satisfiable.  Any ideas?

---

### Post by t3chn0b0y on 2006-11-09
Now to bypass the save button and save every song... :)
I don't think it would take much more code... I might
be mistaken..but wouldn't it just be a jump in the code.
I'm new at this.. stilling having problems with my tv tuner
not playing audio.. though there is a kernel fix for it,
its not available yet for ubuntu.. only thing holding back
from removing windows.. :-#

---

### Post by t3chn0b0y on 2006-11-09
> **Mechanical said:**
> I am using edgy and I can get the last exit player in the repo working fine but no save song button.  I try to install the one provided here and it tells me lidbus-1-2 is not satisfiable.  Any ideas?

[http://packages.ubuntulinux.org/dapper/devel/libdbus-1-2](http://packages.ubuntulinux.org/dapper/devel/libdbus-1-2)

---

### Post by Mechanical on 2006-11-09
> **t3chn0b0y said:**
> [http://packages.ubuntulinux.org/dapper/devel/libdbus-1-2](http://packages.ubuntulinux.org/dapper/devel/libdbus-1-2)

I installed this and the last exit player installed as well, but now when I start last-exit it doesn't do anything.  In terminal it says this..

Unhandled Exception: System.DllNotFoundException: dbus-glib-1
  at (wrapper managed-to-native) LastExit.DBus:dbus_g_thread_init ()
  at LastExit.Driver.Main (System.String[] args) [0x00000] 

Any suggestions?  I am still trying to get it to work.

---

### Post by ZeBob on 2006-11-10
@To others : I think the deb posted here was builded on dapper, cause there is libdbus 1.3 on Edgy and 1.2 on Dapper, take the source and build your own package on Edgy.

@Mechanical : I've rewritten  a part of the patch (the gstreamer pipeline), but I ain't a good programmer, so i still have a small bug. 
After that, i'm thinking of adding such option :
- adding  a folder toi save file in the preferences menu
- changing the save button into a toggle button

We will loose the « on-click choose the folder » function, but I don't know if this is a problem or not.

---

### Post by Mechanical on 2006-11-10
Whatever can get this thing working on edgy with the patch would be awesome.  If anyone has got it working please give details.  I have been using the one in synaptic and love it but still would love a patch.  I feel like I have tried everything in my knowledge to get it working but with no success.

---

### Post by Jenda on 2006-11-10
So... why is it that the sound is jumpy at the from the start when you use the patched version? Is there any way to fix that?

---

### Post by deadlydeathcone on 2006-11-10
Okay, I'll bite:

[last-exit.tar.gz]("http://www.lightofcracker.com/ubuntu/last-exit.tar.gz") patched for Edgy.

Thanks for updating the patch for compatibility for version 3.0.

edit: link fixed

---

### Post by Mechanical on 2006-11-10
> **deadlydeathcone said:**
> Okay, I'll bite:

[last-exit_3.0.1-0ubuntu1_i386.deb]("http://www.lightofcracker.com/ubuntu/") patched for Edgy.

Thanks for updating the patch for compatibility for version 3.0.

Ack, can't download.  It says I am crackasized.

---

### Post by deadlydeathcone on 2006-11-10
> **Mechanical said:**
> Ack, can't download.  It says I am crackasized.

It's not my fault you're all crackasized and whatnot!

Eh, give it a shot now, it should work. I just linked to a subdirectory, since my hosting is a little... weird.

---

### Post by Mechanical on 2006-11-10
> **deadlydeathcone said:**
> It's not my fault you're all crackasized and whatnot!

Eh, give it a shot now, it should work. I just linked to a subdirectory, since my hosting is a little... weird.

Yeah, the subdirectory has a few packages for ubuntu but none of them seem to be available for download.  They just lead to the error page.

Thanks for the effort though!  Maybe just upload it elsewhere.

---

### Post by deadlydeathcone on 2006-11-10
Okay, it's finally fixed. Apparently it doesn't like .deb or tar.bz2 files.

---

### Post by Mechanical on 2006-11-10
> **deadlydeathcone said:**
> Okay, it's finally fixed. Apparently it doesn't like .deb or tar.bz2 files.

Hey thanks!  Its working quite well actually.. for some reason it won't save songs to another partition and after the second song has been saved it uses 100 percent of my cpu.  Does that happen with anyone else or just me?

---

### Post by deadlydeathcone on 2006-11-10
> **Mechanical said:**
> Hey thanks!  Its working quite well actually.. for some reason it won't save songs to another partition and after the second song has been saved it uses 100 percent of my cpu.  Does that happen with anyone else or just me?

That happens for me as well, but it seems to happen at random. We've traded it in for the stuttering song bug that was in Dapper, apparently.

Anyone who's gotten my package so far might want to download it again; I messed around in the source and added a handy save song button to the menu on the tray menu.

---

### Post by ZeBob on 2006-11-12
Think i solved the 100% cpu usage problem : the Filechooser dialog does not like to start in the same directory where the temporary dump file is. I really don't know why, but i changed the directory of the dump file : instead of home dir i set it in the tmp dir of the user.

I will post all modifications i've made after further testing.

---

### Post by ZeBob on 2006-11-12
Seems to be ok :) No lag, no 100% usage, pipeline rewritten.

Patch : [ATTACH]19237[/ATTACH]
Patched source : [ATTACH]19238[/ATTACH]
Deb (for EDGY i386) : [ATTACH]19239[/ATTACH]

Notes : 
- if you're on Dapper or other architecture, just compile it from the source or wait for someone to post a deb here :)
- Gst 0.10 is needed.
- if you are a package maker, please give us clean package (other than this checkinstall made deb).

---

### Post by Mechanical on 2006-11-12
> **ZeBob said:**
> Seems to be ok :) No lag, no 100% usage, pipeline rewritten.

Patch : [ATTACH]19237[/ATTACH]
Patched source : [ATTACH]19238[/ATTACH]
Deb (for EDGY i386) : [ATTACH]19239[/ATTACH]

Notes : 
- if you're on Dapper or other architecture, just compile it from the source or wait for someone to post a deb here :)
- Gst 0.10 is needed.
- if you are a package maker, please give us clean package (other than this checkinstall made deb).


I installed the deb package but it won't start up for me.

---

### Post by ZeBob on 2006-11-12
Did you get an error message in a console ?

---

### Post by Mechanical on 2006-11-12
> **ZeBob said:**
> Did you get an error message in a console ?

Here it is, I was just going to include it in my previous reply, hehe..

Unhandled Exception: System.DllNotFoundException: dbus-glib-1
  at (wrapper managed-to-native) LastExit.DBus:dbus_g_thread_init ()
  at LastExit.Driver.Main (System.String[] args) [0x00000]

---

### Post by ZeBob on 2006-11-12
Theorically the original last-exit depends on libdbus-1-3 an libdbus-glib-1-2 Check if you have them installed in synaptic.

---

### Post by Mechanical on 2006-11-12
> **ZeBob said:**
> Theorically the original last-exit depends on libdbus-1-3 an libdbus-glib-1-2 Check if you have them installed in synaptic.

I checked and I have both of those plus libdbus-1-2 which I installed earlier to get the last posted deb of this playing.  When I installed this version it mentioned not finding an icon and I just realized there isn't an icon or entry for it in the applications menu anymore either.  I just had a launcher for it on my toolbar.

---

### Post by ZeBob on 2006-11-12
Did you supress the previous *.deb, it may cause problem. Normally you don't need another libdbus but the one given in Edgy.

---

### Post by Mechanical on 2006-11-12
> **ZeBob said:**
> Did you supress the previous *.deb, it may cause problem. Normally you don't need another libdbus but the one given in Edgy.

I did the complete removal of the previous last-exit before installing.  For some reason I couldn't get last-exit to even install at all until I also installed the previous version of libdbus.  I just removed the older version though along with last-exit and then reinstalled it but am getting the same error.

---

### Post by zegnus on 2006-11-13
Hi!

I have ubuntu edgy and when I try to install version 3, ubuntu says me that I no have libdbus-1-2, the fact es that in edgy, I have libdbus-1-3 installed and I cannot install libdbus-1-2

Thanks !

---

### Post by guix on 2006-11-13
Same as zegnus, I took the .deb in page 14 of this thread and now I have :

Unhandled Exception: System.DllNotFoundException: dbus-glib-1
  at (wrapper managed-to-native) LastExit.DBus:dbus_g_thread_init ()
  at LastExit.Driver.Main (System.String[] args) [0x00000

which is the same as Mechanical. Edgy here.

---

### Post by ZeBob on 2006-11-13
This is strange I ain't have a special config, maybe try to compile it from the source :/

---

### Post by Mechanical on 2006-11-13
> **guix said:**
> Same as zegnus, I took the .deb in page 14 of this thread and now I have :

Unhandled Exception: System.DllNotFoundException: dbus-glib-1
  at (wrapper managed-to-native) LastExit.DBus:dbus_g_thread_init ()
  at LastExit.Driver.Main (System.String[] args) [0x00000

which is the same as Mechanical. Edgy here.

It seems we are all having about the same problem.  Well I hope somehow it gets fixed.

---

### Post by deadlydeathcone on 2006-11-13
> **ZeBob said:**
> 
- if you are a package maker, please give us clean package (other than this checkinstall made deb).

Here you go: [last-exit_3.0.1-0ubuntu2_i386.deb]("http://lightofcracker.com/ubuntu/last-exit-3.02.tar.gz")

Thanks, you seem to have solved it.

I attached the patch for the tray menu:

---

### Post by Mechanical on 2006-11-14
> **deadlydeathcone said:**
> Here you go: [last-exit_3.0.1-0ubuntu2_i386.deb]("http://lightofcracker.com/ubuntu/last-exit-3.02.tar.gz")

Thanks, you seem to have solved it.

I attached the patch for the tray menu:

I have been using it a for a while now and haven't had a single problem.  Thanks!!

---

### Post by wilk on 2006-11-14
Works perfectly, thanks a lot. Just one annoying thing : the last directory chosen for saving tunes is not remembered, and. Is it something that needs to be setup in nautilus ?

---

### Post by lisa on 2006-11-14
Thanks ZeBob. The package is great. the problem with the lag has now been also resolved.

---

### Post by t3chn0b0y on 2006-11-14
> **Mechanical said:**
> I installed the deb package but it won't start up for me.

when i install the deb on my edgy i get no audio, i had to resort
back to the old version requiring the dbus1-2. :( 

when i go to compile the src i get the following

No package 'gdk-pixbuf-2.0' found
No package 'gtk+-2.0' found

checking for LASTEXIT... configure: error: 
Package requirements (
gconf-2.0  gdk-pixbuf-2.0 gtk+-2.0 >= 2.6 gstreamer-0.10 >= 0.10.0                gstreamer-base-0.10                                gstreamer-plugins-base-0.10 >= 0.10.0   dbus-1 >= 0.60                  dbus-glib-1 >= 0.60) were not met:

---

### Post by ZeBob on 2006-11-14
Thanks for the package and the patch.
I've also added a shorcut in the last patch, Alt+S to save the song.

TODO :
 - automatically add the good id3 tag
 - adding an option to auto save the song (technically easy to do but i'm not fan of this option :) )
 - save in gconf the last save folder

---

### Post by t3chn0b0y on 2006-11-14
> **t3chn0b0y said:**
> when i install the deb on my edgy i get no audio, i had to resort
back to the old version requiring the dbus1-2. :( 

when i go to compile the src i get the following

No package 'gdk-pixbuf-2.0' found
No package 'gtk+-2.0' found

checking for LASTEXIT... configure: error: 
Package requirements (
gconf-2.0  gdk-pixbuf-2.0 gtk+-2.0 >= 2.6 gstreamer-0.10 >= 0.10.0                gstreamer-base-0.10                                gstreamer-plugins-base-0.10 >= 0.10.0   dbus-1 >= 0.60                  dbus-glib-1 >= 0.60) were not met:

](*,) ](*,) ](*,)  avoid the above post some how i removed the libgtk2.0-dev package ](*,) ](*,) ](*,)

---

### Post by zegnus on 2006-11-14
Thanks !! it works !

---

### Post by t3chn0b0y on 2006-11-14
Okay I compile the code install problems in the cosole, if i install your deb package same problems with sound..
(/usr/local/lib/last-exit/last-exit.exe:7262): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (dest)' failed

(/usr/local/lib/last-exit/last-exit.exe:7262): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (src)' failed

i still have to resort back before your last patch before the alt+s

---

### Post by guix on 2006-11-15
Strange...
I built the packages after having patched with save_song on my 2 Edgy systems : AMD64 Gnome and Pentium 4 Enlightenment.

Last-exit works fine for the AMD64 system. For the Pentium 4 it starts streaming for 1 second then freezes... Any idea ? (same if I launch a gnome session by the way)

[edit] Maybe it's a problem of network at work (Pentium 4), however the official last.fm client works there...

---

### Post by guix on 2006-11-17
Bump ! Any idea ?

---

### Post by ZeBob on 2006-11-18
Got this bug once recently, but i think it was a gstreamer hang cause totem was not working too.

---

### Post by QuantumSchmantum on 2006-11-20
This player seems excellent, but when I run it it doesn't pick up song info from the station.  The music plays just fine, but the artist and song title don't display in the player window or the Info window.

The terminal output doesn't indicate any errors.

Any idea why this would be happening on an AMD 64 system with Dapper Drake?

---

### Post by glotz on 2006-11-20
Puhleeeze make a wiki page for last-exit. Thanks mucho! [https://help.ubuntu.com/community/last-exit](https://help.ubuntu.com/community/last-exit)

---

### Post by wilk on 2006-11-21
There seems to be a problem at the moment :

This page does not exist yet

---

### Post by ZeBob on 2007-01-03
Hi,
I've rebuilded the packages for edgy and feisty (for i386) :

[LIST]
[*]Edgy deb : [ATTACH]22236[/ATTACH]
[*]Edgy source : [ATTACH]22237[/ATTACH]
[*]Feisty deb [ATTACH]22238[/ATTACH]
[*]Feisty source : [ATTACH]22239[/ATTACH]
[/LIST]

It should not be hard for a packager to build package with this sources, dsc, diff and orig are included.

Note : Edgy package might work on Dapper with backports enabled.

---

### Post by guix on 2007-01-04
Hi ZeBoband, and thanks for this new version.
I still have the same problem though : last-exit starts streaming for 1 second then freezes.
Strange because the last-exit from Ubuntu repository (without save song) works.
Strange because on my AMD64, complied from the sources for AMD64 given in this thread, last-exit with save song works.

---

### Post by videodrome on 2007-01-16
Hello.

Is it normal for this program to work (the .deb above) fine, but NOT properly interface with the last fm website as far as actually doing anything regarding my likes and dislikes???

I mean the whole point is to build up some sort of recommendations of what I like streamed to me right? Because as it stands now, I can veto 4 Foo Fighters songs and it just keeps on sending me Foo Fighters songs, for example.

And I don't see anything on the website to indicate that I have any recommendations or vetos or whatever.

Thanks

---

### Post by Nubbie on 2007-01-22
How's the work on last-exit 4 coming along? Is there a patch available?

---

### Post by lisa on 2007-01-24
Does anyone have a problem connecting to the server? 'cause i guess since 2 weeks last-exit can't connect to any stations.

Problem solved: last-exit couldn't connect through the proxy.

---

### Post by banjobacon on 2007-01-25
Here's a package of Last-Exit 4 for Edgy, if anyone needs it. It was built using Prevu.

---

### Post by wilk on 2007-01-26
Thanks a lot, is there a save patch around for this version, the last one doesn't compile.

---

### Post by videodrome on 2007-01-31
This last one errors out as well after you use it for about 15 minutes.

ANd no matter how many songs I approve of or disapprove of, it still sends me nothing but bands I hate on my "recommendation radio." 

You'd think after listening to 500 songs that it would suggest ONE song that I like.

---

### Post by OrganicPanda on 2007-02-27
I'm having the same 'plays for 1 second then freezes' error on version 3 for edgy, any ideas on how to fix this?

---

### Post by nigra on 2007-03-01
> **OrganicPanda said:**
> I'm having the same 'plays for 1 second then freezes' error on version 3 for edgy, any ideas on how to fix this?
same here for last-exit version from the repos, version 3 and 4.
Intrestingly bmpx,rhythmbox, virtually any application freezes when i try to listen to a last.fm stream. However, the stations stream flawlessly inside firefox (flash player).Serious problem... ](*,)

---

### Post by videodrome on 2007-03-24
Anyone working on this?

I've been using the 3.0 version of Last Exit for awhile now, and it constantly locks up. It'll play fine for about 15 minutes and then just go silent for no reason.

And even though I have now played 3000 songs, the recommendation radio absolutely sucks. It sends everything that I hate, and nothing that I clicked the little smiley face for or listened to all the way through.

---

### Post by Billy McCann on 2007-03-24
Why aren't you all using the lastfm package?  

```
sudo apt-get install lastfm
```

Works brilliantly for me.

---

### Post by theturner on 2007-03-24
Because it's QT, and there's no save patch for it.

---

### Post by videodrome on 2007-04-01
Still no new version?

---

### Post by ZeBob on 2007-04-01
Here is a patch for **feisty**'s last-exit (version 4) : [ATTACH]28732[/ATTACH]
Apply it against last-exit ubuntu source (i.e. apt-get source last-exit)

And this one is the debian binary package for feisty/i386 : [ATTACH]28731[/ATTACH]

Check your local law to see if you can register radio.

---

### Post by wilk on 2007-04-02
I was thinking an option to tag the file saved with style/album=lastm or something like that would be very useful, in order to easily select them in a music library. I very often end up with several versions of a track if I buy the album I first got from lastfm.

---

### Post by lisa on 2007-04-03
@ZeBob: Thanks a lot for the patch. worked wonderfull. But i wanted to ask how you created this patch?

And last-exit crashes when searching  "Music that sounds like".  Also with the "official" feisty package.
This is what the console tells me:
> Unhandled Exception: System.FormatException: Input string was not in the correct format
at System.Int32.Parse (string) <0x0004e>
at LastExit.FindStation.ParseSimilar (string) <0x00305>
at LastExit.FindStation.FindStationCompleted (LastExit.FMRequest) <0x000b2>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_FMRequest (LastExit.FMRequest) <0x0002a>
at LastExit.FMRequest.request_completed_idle () <0x0001a>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x0002c>
at IdleProxy.Handler () <0x0002a>
at (wrapper native-to-managed) IdleProxy.Handler () <0x00036>
in (unmanaged) 0xb7e9f090
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at LastExit.Driver.Main (string[]) <0x00335>

Has anyone an idea?

---

### Post by j_m on 2007-04-06
> **ZeBob said:**
> Here is a patch for **feisty**'s last-exit (version 4) : [ATTACH]28732[/ATTACH]
Apply it against last-exit ubuntu source (i.e. apt-get source last-exit)


This breaks last-exit; you only get ~2 seconds of playback, and nothing else after that. Plus a bunch of assertion failed errors. :(

---

### Post by ZeBob on 2007-04-07
@Lisa : i did not create it, there was a patch for version 0.2 of last-exit that i found here : [http://raphael.slinckx.net/last-exit-save-song.patch](http://raphael.slinckx.net/last-exit-save-song.patch) (This man is a GNOME developper)

But it didn't work with version 3, so i've just adapt it, and i also change the gstreamer pipeline which was used by the patch. Notice that i'm not a programmer I've just used the gstreamer manual and example to write the pipeline.

I've got the same error, but if you want to post the bug at bugzilla, check you're using the original version. ([http://bugzilla.gnome.org/browse.cgi?product=last-exit](http://bugzilla.gnome.org/browse.cgi?product=last-exit) )

j_m : sometimes i've got problem to connect to lastfm streams. check later if it still do that.

---

### Post by lisa on 2007-04-07
@ZeBob: Thanks for the Information. I was just wondering how you managed to "get" the patch, cause i was searching so long for the patch-version 4 and didn't know how to do it myself.

After you mentioned it, i tried it again, with the patched version, the ubuntu-package and the original package on [http://folks.o-hand.com/iain/last-exit/;](http://folks.o-hand.com/iain/last-exit/;) coming with all to the same result resp. problem.
Others are having the same problem with version 4, so there allready exists a bug-report:
[http://bugzilla.gnome.org/show_bug.cgi?id=423667](http://bugzilla.gnome.org/show_bug.cgi?id=423667)
But at least i did comment it.

---

### Post by j_m on 2007-04-07
> **ZeBob said:**
> 
j_m : sometimes i've got problem to connect to lastfm streams. check later if it still do that.

Has nothing to do w/ connection. It plays sound for 2 seconds and then the application freezes. The patch is broken; works perfectly fine without it.

---

### Post by lisa on 2007-04-08
For the search-Bug exists a Patch. And there's a bug-report on [http://bugzilla.gnome.org/show_bug.cgi?id=423667](http://bugzilla.gnome.org/show_bug.cgi?id=423667)

The patch at least works for me.

---

### Post by Nubbie on 2007-04-11
[SIZE="5"]_**[ATTACH]29510[/ATTACH]**_[/SIZE]

I have built a package for Feisty containing the ubuntu, save song, and search patches.

Thank you Iain for making such an amazing program, and thank you ZeBob for fixing up the save song patch, and thank you Lisa for linking up that search patch.

Note: I did not go in depth at all with dependancies in this package, so please remember to run ```
sudo apt-get build-dep last-exit
``` before installing this package.

---

### Post by videodrome on 2007-04-22
on a brand new xubuntu install, that last deb doesn't work at all. it starts, then does nothing.

---

### Post by Nubbie on 2007-04-24
Thats very strange, what did sudo dpkg -i <packagename.deb> output in terminal?

---

### Post by Mechanical on 2007-04-24
> **Nubbie said:**
> [SIZE="5"]_**[ATTACH]29510[/ATTACH]**_[/SIZE]

I have built a package for Feisty containing the ubuntu, save song, and search patches.

Thank you Iain for making such an amazing program, and thank you ZeBob for fixing up the save song patch, and thank you Lisa for linking up that search patch.

Note: I did not go in depth at all with dependancies in this package, so please remember to run ```
sudo apt-get build-dep last-exit
``` before installing this package.

Works great but I don't see the search feature.  I am using feisty.

---

### Post by lisa on 2007-04-24
> **Mechanical said:**
> Works great but I don't see the search feature.  I am using feisty.

It's not a feature it's a patch :-)  The Searching-Tool  should work with it properly.

---

### Post by el mariachi on 2007-04-30
> **lisa said:**
> It's not a feature it's a patch :-)  The Searching-Tool  should work with it properly.

is this still in development? I installed the latest deb available here (last-exit_4-1_i386.deb) and it just plays less than 2 seconds of music. when the "cross" icon is clicked it just shuts down instead of going to tray (or is this supposed to happen?)

---

### Post by erdu on 2007-05-01
> **Nubbie said:**
> [SIZE="5"]_**[ATTACH]29510[/ATTACH]**_[/SIZE]

I have built a package for Feisty containing the ubuntu, save song, and search patches.

Thank you Iain for making such an amazing program, and thank you ZeBob for fixing up the save song patch, and thank you Lisa for linking up that search patch.

Note: I did not go in depth at all with dependancies in this package, so please remember to run ```
sudo apt-get build-dep last-exit
``` before installing this package.
Thanks for the .deb Nubbie. Didn't work the first couple of times on a clean installed Feisty...now it does...except, the "save feature" doesn't save, and "music that sounds like" makes the player disappear (but that's no major problem really, I can launch last-exit from last.fm's website).

---

### Post by erdu on 2007-05-01
Hey Nubbie...save problem is somewhat solved now. Apparently, last-exit manages to save to its own ext3-partition but not to another fat32-partition on the same disk (permissions satisfied)...used to be able to do that when I was still using Edgy. 
Btw, I think in my case it may not have been necessary to do sudo apt-get build-dep last-exit before installing, so I wonder if there's a swift way to get rid of the 30 MB build-dep that I downloaded (wouldn't like that to get that in the way of future installs).
Anyway, thanks a bunch again for providing such a neat package!

---

### Post by lisa on 2007-05-02
@erdu:
> autoconf automake1.7 autotools-dev cdbs cli-common-dev debhelper html2text intltool libatk1.0-dev libcairo2-dev libdbus-1-dev libdbus-glib-1-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev libglib2.0-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgtk2.0-dev libice-dev libidl-dev libmono-accessibility2.0-cil libmono-cairo2.0-cil libmono-data-tds1.0-cil libmono-microsoft-build2.0-cil libmono-peapi1.0-cil libmono-peapi2.0-cil libmono-relaxng1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-system-data1.0-cil libmono-system-runtime1.0-cil libmono-system-web1.0-cil libmono-winforms2.0-cil libmono1.0-cil liborbit2-dev libpango1.0-dev libpng12-dev libpopt-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml-dom-perl libxml-regexp-perl libxml2-dev libxrandr-dev libxrender-dev m4 mono-gmcs mono-mcs mono-utils x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev

These are the packages that have been installed by compiling last-exit (in feisty). so if you want to get rid oft it, ...

but i guess you'l need some of the packages to compile other packages (for example: automake1.7)

---

### Post by el mariachi on 2007-05-02
installing the [older] version from the repos made it work, although it doesn't have the "save" feature, but I can live with that, because it's a great app: small, simple and does it's job:KS

---

### Post by antouane on 2007-05-29
Hey im noob,

How to patch the last-exit version 4 with the text file attached ?

Sorry for that noobish question but i realy don't know how ...

:(

---

### Post by Tom B on 2007-05-29
I have been using last exit happily for a few months now. I installed it using Nubbie's package. However, now whenever I use it, none of the track information is displayed. It says "Playing [blank] by [blank] " etc. This also causes a crash whenever I try to save a song. I tried reinstalling it- same error. I can't figure out why it all of a sudden started acting funny. I really liked it before, and want to make it work again. Any ideas?

---

### Post by Nubbie on 2007-06-03
I'm sorry it's not working out for some people. Like I said, I didn't include any dependencies in this package, as it was really the first I've ever made. I *think* that most problems will be solved by running this before installing..
```
sudo apt-get build-dep last-exit
``` Please let me know if this solves your problems, and by all means, if you are capable/willing to create a better package, please do. Give it a try!

---

### Post by Tom B on 2007-06-03
Don't be sorry- we owe you for making it. I personally have no idea how to make one. I did run that code before installing before, but i gave it another shot and reinstalled it again....and now it works! Who knows what happened.

Another thing that has nothing to do with the package and is just a bug in the program (i think)- it seems like if a track doesn't have an album, the program crashes if you try to save it. It's no big deal, though. Overall, it works great. Thanks again for making the package.

---

### Post by Fonsis on 2007-06-20
Will there be a save patch available for last exit 4.x ?
The player works fine, but I would like to use the save option, if possible... 

Fonsis

---

### Post by Fonsis on 2007-06-20
Ok, now I got it running with save function in it, but I wonder why I have to click manually on the save button every time I hear a new song?
Isn*t there an option to recored all upcoming songs automatically?

[IMG]http://img400.imageshack.us/img400/7527/snapshot1ip8.png[/IMG]

---

### Post by lisa on 2007-06-23
@Fonsis:
Maybe you should try out thelastripper ([http://thelastripper.com](http://thelastripper.com)). This program saves songs automatically. Allthough this software still has bugs and didn't work for me.

---

### Post by introspectif on 2007-06-28
Is anyone working on the save patch for version 5.0?

I've been trying to compile older versions of last-exit with the save patch, but I keep running into errors about ranlib not being able to do something when I reach "make install". And that's preventing me from poking around version 5.0. Anyone has come across this ranlib problem? Btw, I'm using Feisty.

---

### Post by introspectif on 2007-06-28
> **introspectif said:**
> Is anyone working on the save patch for version 5.0?

OK, this might sound freaky, but I think I've just done it myself. To download, and for more details, [read my blog entry]("http://mahalkita.nanogeex.com/2007/06/29/shhh-secret-delivery/").

---

### Post by el mariachi on 2007-06-29
> **introspectif said:**
> OK, this might sound freaky, but I think I've just done it myself. To download, and for more details, [read my blog entry]("http://mahalkita.nanogeex.com/2007/06/29/shhh-secret-delivery/").

I downloaded it but it won't start...

```
Starting new Last Exit server

(/usr/local/lib/last-exit/last-exit.exe:5147): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (dest)' failed

(/usr/local/lib/last-exit/last-exit.exe:5147): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (src)' failed

Unhandled Exception: System.DllNotFoundException: libsexy
  at (wrapper managed-to-native) LastExit.UrlLabel:sexy_url_label_new ()
  at LastExit.UrlLabel..ctor () [0x00000] 
  at LastExit.PlayerWindow.SetupUI () [0x00000] 
  at LastExit.PlayerWindow..ctor () [0x00000] 
  at LastExit.Driver.Main (System.String[] args) [0x00000]
```

it says something about GStreamer.. I've got the ugly set installed *only*

---

### Post by introspectif on 2007-06-29
> **el mariachi said:**
> I downloaded it but it won't start...

```
Unhandled Exception: System.DllNotFoundException: libsexy
  at (wrapper managed-to-native) LastExit.UrlLabel:sexy_url_label_new ()
  at LastExit.UrlLabel..ctor () [0x00000] 
  at LastExit.PlayerWindow.SetupUI () [0x00000] 
  at LastExit.PlayerWindow..ctor () [0x00000] 
  at LastExit.Driver.Main (System.String[] args) [0x00000]
```



Thanks for trying my package :) It seems that you're missing libsexy. Could you try installing libsexy? 

sudo aptitude install libsexy2

---

### Post by el mariachi on 2007-06-29
it didn't work... libsexy2 is installed but the error persists

---

### Post by introspectif on 2007-06-29
Oh no :( I really wanted to share the joy in having the save feature. I hope someone more knowledgeable can show the way.

---

### Post by introspectif on 2007-06-29
Oh yes, perhaps you could try the unpatched version from [http://packages.debian.org/unstable/gnome/last-exit](http://packages.debian.org/unstable/gnome/last-exit) just to see if there are any additional dependencies you need. It says gstreamer0.10-fluendo-mp3, so maybe you need that too. Thing is, I tried installing the unpatched version first, and it worked. However, when installing you need to do

sudo dpkg -i --ignore-depends=libc6 last-exit_5-1_i386.deb

I hope that helps.

---

### Post by Nubbie on 2007-07-03
you need to install libsexy's development package.
```
sudo apt-get install libsexy-dev
```
and that package should run. i haven't tested it out yet as i don't have any speakers right now. i'll let you all know.

---

### Post by introspectif on 2007-07-08
Thanks very much for the tip, Nubbie. How did it turn out?

---

### Post by Nubbie on 2007-07-08
Well after a couple of seconds the audio cuts out. This is because of the save patch, because it would happen to other patched versions of last-exit. the question is now how did i get the audio working correctly last time. lol.

---

### Post by introspectif on 2007-07-09
I have that problem too, sometimes, but it's due to a connection problem --- my Linksys WUSB54G disconnects every once in a while. But when the connection's good, it plays and saves perfectly :)

I'm thinking of tinkering with the buffer size of the player, to improve playback. I wonder if that helps.

---

### Post by Tom B on 2007-07-13
After installing libsexy's development package like Nubbie said, the package works perfectly. Thanks for making it.

---

### Post by el mariachi on 2007-07-14
> **Tom B said:**
> After installing libsexy's development package like Nubbie said, the package works perfectly. Thanks for making it.
for me it plays 1 second of music and then... silence...:confused::confused:

---

### Post by cyber_bushi on 2007-07-16
Hi there,

i have libdbus-1-3 on my sys, but last-exit wants 1-2 - can i just do some ln -l magic to convince it to work, or are there other possibiities?

Thanks in advance for your time,

CB

---

### Post by buzz91 on 2007-08-02
Hello,

i installed the patched last-exit 5 and it works but its very very very slow.

Is this normal? Seems to be a missing package ... i guess?

Maybe someone can help me

Thanks

Greetings

P.S.: Is there any Player (Banshee, BMP, Exail, etc.) playing Last.fm-Streams?
P.S.:P.S.: Anybody running thelastripper under feistay? It des' work for me ...

---

### Post by durand on 2007-08-15
> **buzz91 said:**
> Hello,

i installed the patched last-exit 5 and it works but its very very very slow.

Is this normal? Seems to be a missing package ... i guess?

Maybe someone can help me

Thanks

Greetings

P.S.: Is there any Player (Banshee, BMP, Exail, etc.) playing Last.fm-Streams?
P.S.:P.S.: Anybody running thelastripper under feistay? It des' work for me ...

Try amarok, as for thelastripper, it doesnt seem to work in gutsy either...it downloads the start of the file and thats it...

---

### Post by introspectif on 2007-08-15
> **buzz91 said:**
> 
P.S.: Is there any Player (Banshee, BMP, Exail, etc.) playing Last.fm-Streams?
P.S.:P.S.: Anybody running thelastripper under feistay? It des' work for me ...

Rhythmbox does play last.fm streams too.

---

### Post by durand on 2007-08-16
Heh, the last ripper seems to work for me now, just leave it to download 2 songs, then it should start working properly :)

---

### Post by wilk on 2007-08-17
I tried to adapt introspectif method to get last-exit 5 patched for amd64 on Gutsy. I can build the package, but no streams are played. Did anyone succeed on a 64bit system ?

---

### Post by immigrant on 2007-08-17
I believe LastExit is playing different songs than official last.fm player. The official player plays my favorite groups more often. Does last.fm feed last-exit player more low quality songs:confused:

---

### Post by lisa on 2007-08-22
The package from introspectif works good, but when searching "tagged as" last-exit crashes. i allready noticed that this is documented on bugzilla.

---

### Post by el mariachi on 2007-08-22
> **immigrant said:**
> I believe LastExit is playing different songs than official last.fm player. The official player plays my favorite groups more often. Does last.fm feed last-exit player more low quality songs:confused:
I don't know about low quality but I also noticed that it plays different songs

---

### Post by introspectif on 2007-08-26
Funny I received an email notification that someone replied the following, but I can't find it here:

> Here's another packages for feisty (i386).
I tried the version that was posted by introspectif and i had to install libsexy-dev and all it's dependencies (20 packages).

Anyway: i made a package on my own. it is based on the gutsy-src and i just had to make a change on the dev-dependencies. The package itself has been created by using dh_make and dpkg-buildpackage -rfakeroot.
I didnt add my name and i didn't note the changes. The package contains the save-song-patch.

At least you don't have to install libsexy-dev.

so if anyone wants to try out the package, feel free to use it.

Has anyone tried this one? Care to share the download link again?

---

### Post by introspectif on 2007-08-26
I recompiled the same thing, but this time under Gutsy. [Read my notes and download the package]("http://mahalkita.nanogeex.com/2007/08/27/last-exit-5-patched-for-ubuntu-gutsy/") from my blog.

---

### Post by lisa on 2007-08-28
> **introspectif said:**
> Funny I received an email notification that someone replied the following, but I can't find it here:

Has anyone tried this one? Care to share the download link again?

I deleted the post cause i don't know if it's legal in my country.

---

### Post by reda_ea on 2007-09-16
> **introspectif said:**
> OK, this might sound freaky, but I think I've just done it myself. To download, and for more details, [read my blog entry]("http://mahalkita.nanogeex.com/2007/06/29/shhh-secret-delivery/").

thanks,
I repackaged your deb with correct dependencies and no need for dev packages (if you're not a programmer libsexy-dev will add lots of unwanted packages, from x11 to gtk and gnome libs and so) and with files in more correct locations (same as most other ubuntu debs).

package is in [the first post of this thread ]("http://ubuntuforums.org/showthread.php?p=1239424#post1239424")

---

### Post by hotweiss on 2007-10-02
> **introspectif said:**
> I recompiled the same thing, but this time under Gutsy. [Read my notes and download the package]("http://mahalkita.nanogeex.com/2007/08/27/last-exit-5-patched-for-ubuntu-gutsy/") from my blog.

OK, I've just installed the Feisty version but it does not appear in my menu. I just right-clicked on it and installed it.

---

### Post by introspectif on 2007-10-02
[replied via email]

I've had no problems with that before. I think you have to restart or give Feisty some time for it to update its menu. Is there anyone else facing the same problem?

---

### Post by hotweiss on 2007-10-02
> **introspectif said:**
> [replied via email]

I've had no problems with that before. I think you have to restart or give Feisty some time for it to update its menu. Is there anyone else facing the same problem?

Do you think me having the real Last.FM player installed is causing the trouble?

---

### Post by introspectif on 2007-10-02
I don't think so.. I have both apps and faced no problems :)

---

### Post by hotweiss on 2007-10-03
OK, I've reinstalled it and now it's in the menu, but it won't start up. It says starting Last-Exit at the bottom and then it disappears...

---

### Post by introspectif on 2007-10-03
try starting it from a terminal window and see if there are error messages?

---

### Post by weed-n-linux on 2007-10-03
i don't think last.fm puts some good sounds , but if i ever needed it , amarok can play it .even thou i like some features in this program, very smart keep on rocking :)

---

### Post by meindian523 on 2007-10-03
> **Nubbie said:**
> [SIZE="5"]_**[ATTACH]29510[/ATTACH]**_[/SIZE]

I have built a package for Feisty containing the ubuntu, save song, and search patches.

Thank you Iain for making such an amazing program, and thank you ZeBob for fixing up the save song patch, and thank you Lisa for linking up that search patch.

Note: I did not go in depth at all with dependancies in this package, so please remember to run ```
sudo apt-get build-dep last-exit
``` before installing this package.

Nubbie's package worked for me tho' sudo apt-get build-dep last-exit resulted in E:Could not satisfy build dependencies for last-exit after enabling all repos.:)

Only one problem,it starts with some part of the previous song too.....Also,could we add a previous button,a very-much-missed feature when I jumped across a song I WANTED to save and couldn't go back.:(

But,gimme five,Nubbie!Great Job.

EDIT:I'm sorry,it doesn't start with some part of the previous song....I realized it was the lead :P.But the previous button feature request remains....

---

### Post by hotweiss on 2007-10-03
> **introspectif said:**
> try starting it from a terminal window and see if there are error messages?

This is the error that I got when I started it in terminal:

> 
Unhandled Exception: System.DllNotFoundException: libsexy
  at (wrapper managed-to-native) LastExit.IconEntry:sexy_icon_entry_new ()
  at LastExit.IconEntry..ctor () [0x00000] 
  at LastExit.FirstRunDialog..ctor () [0x00000] 
  at LastExit.Driver.Main (System.String[] args) [0x00000] 


---

### Post by hotweiss on 2007-10-03
OK, according to this post I need the libsexy package:

[http://ubuntuforums.org/showthread.php?t=213185&page=20](http://ubuntuforums.org/showthread.php?t=213185&page=20)

I'm downloading it now.

---

### Post by introspectif on 2007-10-03
ah, the libsexy problem :)

go download the improved version of my package done by reda_ea himself. it's available from the first post of this thread: [http://ubuntuforums.org/showthread.php?p=1239424#post1239424](http://ubuntuforums.org/showthread.php?p=1239424#post1239424)

reda_ea managed to include the libsexy inside the package so you don't have to install it yourself

---

### Post by hotweiss on 2007-10-03
OK, now it works, but the sound disappears after a second.

---

### Post by introspectif on 2007-10-03
That's a chronic problem that has not been solved until now. Some say it's because the original, unpatched program has that problem. I suspect it's also due to poor handling of slow connections (e.g. no notification of buffering status). 

Nowadays I just listen to last.fm using the original client.

---

### Post by buzz91 on 2007-10-15
Hello,

i've just installed the new 5.3savepatch-version of last-exit, but sadly there are probelms:

```
last-exit
Starting new Last Exit server

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (dest)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (src)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (dest)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GStreamer-CRITICAL **: gst_element_link_pads: assertion `GST_IS_ELEMENT (src)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GStreamer-CRITICAL **: gst_bus_add_watch_full: assertion `GST_IS_BUS (bus)' failed

(/usr/lib/last-exit/last-exit.exe:8037): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed
Unknown key: info_message
Unknown key: fingerprint_upload_url
Unknown key: permit_bootstrap

```

Anyone can help me?

Gretz

---

### Post by ZeBob on 2007-10-26
I'm currently working on the SVN version which handle the new lastfm protocol. Good news it seems that this new protocol cut songs perfectly. I'll make further testing but I think we won't have to use audacity anymore.

Here we are :

Full SVN patched source : [ATTACH]47876[/ATTACH]

How to use ?
1. Remove old version of last-exit
```
sudo apt-get remove last-exit
```
2. Get build dependencies
```
sudo apt-get build-dep last-exit
```
3. Unzip the archive
4. Configure and install the package
```
./autogen.sh
make
sudo make install
```

Note : I won't make a deb package here because it's a development version. Wait for the next release and I will make it.

Source of the patch : [ATTACH]47877[/ATTACH] Notice the change made to the change_dump_file function where the GST_STATE are not used anymore, due to the new protocol. Lot of original source code have been simplificated too.

---

### Post by ZeBob on 2007-10-28
Hey hey , new release! I think you'll love this one! :guitar:

New features:
[LIST]
[*]Default save location
[*]Now only saving finished song (that means if you skip or stop the current song, the song won't be saved)
[*]Autosave song mode
[*]Ability to disable the report of song played to last.fm
[/LIST]

Some screenshots:
[ATTACH]48201[/ATTACH][ATTACH]48202[/ATTACH]

The already patched svn source: [ATTACH]48195[/ATTACH]
Install it as described in the previous post.

The full patch (for information purpose): [ATTACH]48196[/ATTACH]

TODO: id3 tagging :confused:

---

### Post by meindian523 on 2007-10-29
TO DO:

Previous button feature...if we skip a song by mistake.......

---

### Post by ZeBob on 2007-10-29
It is not possible, it's streaming like a webradio, lastfm provides song randomly, so you can't get back.

---

### Post by meindian523 on 2007-10-29
Oh,sorry....wish it was possible,I have missed quite a few tracks that way........

---

### Post by introspectif on 2007-11-04
ZeBob, 

Thank you for patching the latest SVN source. I tried compiling it; the install went well, and the program can run, but I only hear the first second of each song :( 

What might be the problem?

---

### Post by el mariachi on 2007-11-04
Could you compile it for 64-Bit Gutsy?

---

### Post by ZeBob on 2007-11-05
> **introspectif said:**
> ZeBob, 

Thank you for patching the latest SVN source. I tried compiling it; the install went well, and the program can run, but I only hear the first second of each song :( 

What might be the problem?

Cause you need libgstlame to be installed (gstreamer0.10-plugins-ugly-multiverse package) or it won't work. If you want to be free you could use vorbis instead of mp3, just change :

```
encoder = gst_element_factory_make ("lame", "encoder");
```
with
```
encoder = gst_element_factory_make ("vorbisenc", "encoder");
```

And change every ".mp3" by ".ogg" in the patch.

---

### Post by introspectif on 2007-11-05
Thanks ZeBob! That worked marvellously! :D

---

### Post by Mr K on 2007-11-11
Ahem! I'm kind a of noob with ubuntu...i'm running feisty and it give's me this when I try to ./autogen.sh:

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.ac
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running aclocal-1.9...
aclocal:configure.ac:44: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
Running autoheader...
Running automake-1.9...
data/Makefile.am:25: GCONF_SCHEMAS_INSTALL does not appear in AM_CONDITIONAL

I've copied those famous *.m4 files but it still keeps throwing up the same message... Please help me :( !! Otherwise i'll throw my pc out the window!! (may hurt someone) :)
Thanks!!

---

### Post by ZeBob on 2007-11-11
No pb.

Copying thoses things was not necessary.
You need to install libgconf-dev to continue.

---

### Post by Mr K on 2007-11-12
That is installed now but it keeps giving me the same message.. what else should i need to do that my noob brain doesn't tell me? Sorry for filling the post with my stupid questions...

---

### Post by lisa on 2007-11-13
> **Mr K said:**
> That is installed now but it keeps giving me the same message.. what else should i need to do that my noob brain doesn't tell me? Sorry for filling the post with my stupid questions...

Did you, before compiling the source, use the following command: sudo apt-get build-dep last-exit

And have you installed gnome-common? That did the trick for me.

---

### Post by Mr K on 2007-11-13
Found out the problem! I had my repos messed up for some weird reason! Now it works perfectly!!
Thanks guys!!!!!

---

### Post by Neo4 on 2007-11-14
I'm having a problem, last exit isnt playing music!
i have 2 soundcards on my pc i've turned one off to see if that is the problem but i guess not!

if i click play it starts playing but i can't listen anything...
btw one question:
this will srobble my played musics in other players to lastfm too?

thanks

---

### Post by ZeBob on 2007-11-14
Do you have gstreamer-plugins-ugly installed ?

---

### Post by marcgenou on 2007-11-18
im running with 5-3 and ugly multiverse plugins on feisty and i cant hear anything...

running it from a terminal i can see logging to the last.fm station but nothing else happens

---

### Post by keibak on 2007-11-19
Great work, ZeBob!

Only one thing:
When connect with a new account and choose neighbours sender (which is empty) following exception occurs:

```
Starting new Last Exit server
Scrobbling enabled
session=<sessionID>
stream_url=http:/<IP>:80/last.mp3?Session=<SessionID>
framehack=0..
base_url=ws.audioscrobbler.com
base_path=/radio
info_message=
fingerprint_upload_url=http://ws.audioscrobbler.com/fingerprint/upload.php
permit_bootstrap=1
Unknown key: fingerprint_upload_url Value:http://ws.audioscrobbler.com/fingerprint/upload.php
Unknown key: permit_bootstrap Value:1
station: http://ws.audioscrobbler.com//radio/adjust.php?session=<SessionID>&url=lastfm://user/<UserName>/neighbours&lang=en&debug=1
Playlist: New playlist requested
Playlist: Got new playlist
PlayerWindow: Playlist ready
PlayerWindow: Player is playing? False
Player: Requesting Song
Playlist: Song Requested
Playlist: Getting Playlist? False
Playlist: GetNextSong (): Returning song number 0
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Index is less than 0 or more than or equal to the list count.
Parameter name: index
0
  at System.Collections.ArrayList.get_Item (Int32 index) [0x00000] 
  at LastExit.Playlist.GetNextSong () [0x00000] 
  at LastExit.Playlist.RequestNextSong () [0x00000] 
  at LastExit.Player.Play () [0x00000] 
  at LastExit.PlayerWindow.OnNewPlaylistReady (LastExit.Playlist playlist) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_Playlist (LastExit.Playlist)
  at LastExit.Playlist.GetNewPlaylistCompleted (LastExit.FMRequest request) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_FMRequest (LastExit.FMRequest)
  at LastExit.FMRequest.request_completed_idle () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
  at GLib.Idle+IdleProxy.Handler () [0x00000] 

   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Idle+IdleProxy.Handler ()
   at GLib.Idle+IdleProxy.Handler ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.Run ()
   at LastExit.Driver.Main ()
```

---

### Post by workage on 2007-11-25
> **ZeBob said:**
> Hey hey , new release! I think you'll love this one! :guitar:

New features:
[LIST]
[*]Default save location
[*]Now only saving finished song (that means if you skip or stop the current song, the song won't be saved)
[*]Autosave song mode
[*]Ability to disable the report of song played to last.fm
[/LIST]

Some screenshots:
[ATTACH]48201[/ATTACH][ATTACH]48202[/ATTACH]

The already patched svn source: [ATTACH]48195[/ATTACH]
Install it as described in the previous post.

The full patch (for information purpose): [ATTACH]48196[/ATTACH]

TODO: id3 tagging :confused:



ZeBob: thanks for a great app.  I followed post #233 instructions on a fresh install and just needed to install gnome-common & automake in order for things to work.

---

### Post by buzz91 on 2007-12-01
Hello out there,

is there a way to youse last-exit with xine?

gretz

---

### Post by Nooreazy on 2007-12-01
I only get to hear like the frist  2 secs of the song :(

---

### Post by immigrant on 2007-12-13
Anybody here with an last-exit playing more than a second?
Do I have wrong configuration or did Last.fm change protocoll again?

---

### Post by regomodo on 2007-12-13
used it about an hour ago in Debian Lenny. Was working fine then.

---

### Post by buzz91 on 2007-12-29
Hi,

anyone using the patched version under debian stable?

i didn't manage to run the patched version under debian, can anyone help me waht to do?

gretz

---

### Post by dicecca112 on 2008-01-11
anyone able to get this to run on x64 gutsy?  I don't get any errors, the program tries to start, but fails

---

### Post by Ruzihm on 2008-01-14
Running x64 Gutsy,  I try to run last-exit in console, I get this:

```

Starting new Last Exit server
Stacktrace:

  at (wrapper managed-to-native) LastExit.Player.player_new () <0x0000b>
  at (wrapper managed-to-native) LastExit.Player.player_new () <0xffffffff>
  at LastExit.Player..ctor (LastExit.Playlist) <0x00077>
  at LastExit.Driver.Main (string[]) <0x00450>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        last-exit [0x565c2b]
        last-exit [0x545811]
        /lib/libpthread.so.0 [0x2b10490b5100]
        /usr/lib/libgstreamer-0.10.so.0(gst_element_link_pads_filtered+0x68) [0x2aaab5175b28]
        /usr/lib/libgstreamer-0.10.so.0(gst_element_link_many+0xc6) [0x2aaab5175f56]
        /usr/local/lib/last-exit/liblastexit.so(player_new+0x1ac) [0x2aaab4cc0f2c]
        [0x402cfaba]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47348953248528 (LWP 15811)]
[New Thread 1080912208 (LWP 15815)]
[New Thread 1078810960 (LWP 15814)]
[New Thread 1075988816 (LWP 15813)]
[New Thread 1073822032 (LWP 15812)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002b10496100a2 in select () from /lib/libc.so.6
  5 Thread 1073822032 (LWP 15812)  0x00002b10490b47b1 in ?? ()
   from /lib/libpthread.so.0
  4 Thread 1075988816 (LWP 15813)  0x00002b10490b17a6 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  3 Thread 1078810960 (LWP 15814)  0x00002b10490b41ab in ?? ()
   from /lib/libpthread.so.0
  2 Thread 1080912208 (LWP 15815)  0x00002b10490b41ab in ?? ()
   from /lib/libpthread.so.0
  1 Thread 47348953248528 (LWP 15811)  0x00002b10496100a2 in select ()
   from /lib/libc.so.6

Thread 5 (Thread 1073822032 (LWP 15812)):
#0  0x00002b10490b47b1 in ?? () from /lib/libpthread.so.0
#1  0x00000000004e70aa in ?? ()
#2  0x00002b10490ad317 in start_thread () from /lib/libpthread.so.0
#3  0x00002b1049616d5d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 4 (Thread 1075988816 (LWP 15813)):
#0  0x00002b10490b17a6 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004ec12f in ?? ()
#2  0x00000000004ec45d in ?? ()
#3  0x00000000004ec223 in ?? ()
#4  0x00000000004fd5b0 in ?? ()
#5  0x000000000049b66d in ?? ()
#6  0x00000000004b65da in ?? ()
#7  0x00000000004fbae6 in ?? ()
#8  0x0000000000517d27 in ?? ()
#9  0x00002b10490ad317 in start_thread () from /lib/libpthread.so.0
#10 0x00002b1049616d5d in clone () from /lib/libc.so.6
#11 0x0000000000000000 in ?? ()

Thread 3 (Thread 1078810960 (LWP 15814)):
#0  0x00002b10490b41ab in ?? () from /lib/libpthread.so.0
#1  0x00000000004f9d79 in ?? ()
#2  0x00000000004bd00c in ?? ()
#3  0x00000000402d2119 in ?? ()
#4  0x0000000000000064 in ?? ()
#5  0x00002aaab4ca13e0 in ?? ()
#6  0x00002aaab4b28f00 in ?? ()
#7  0x00000000009383a0 in ?? ()
#8  0x00002aaab4b0aaf8 in ?? ()
#9  0x00000000404d4ba0 in ?? ()
#10 0x00000000402d20bb in ?? ()
#11 0x00002aaab4b0aaf8 in ?? ()
#12 0x00000000404d4ba0 in ?? ()
#13 0x00000000404d4ab0 in ?? ()
#14 0x00002aaab4b0aaf8 in ?? ()
#15 0x00002aaab4210f48 in ?? ()
#16 0x0000000000000000 in ?? ()

Thread 2 (Thread 1080912208 (LWP 15815)):
#0  0x00002b10490b41ab in ?? () from /lib/libpthread.so.0
#1  0x00000000004f9d79 in ?? ()
#2  0x00000000004bd00c in ?? ()
#3  0x00000000402d2119 in ?? ()
#4  0x00000000406d5b20 in ?? ()
#5  0x00002aaab4210f60 in ?? ()
#6  0x000000000000001f in ?? ()
#7  0x0000000000997600 in ?? ()
#8  0x0000000000002000 in ?? ()
#9  0x000000000000000d in ?? ()
#10 0x00000000402d20bb in ?? ()
#11 0x00002aaab4b0aea0 in ?? ()
#12 0x00000000406d5ba0 in ?? ()
#13 0x00000000406d5ab0 in ?? ()
#14 0x00002aaab4b0aea0 in ?? ()
#15 0x00002aaab4210f60 in ?? ()
#16 0x0000000000000000 in ?? ()

Thread 1 (Thread 47348953248528 (LWP 15811)):
#0  0x00002b10496100a2 in select () from /lib/libc.so.6
#1  0x00002b1048c3516f in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00002b1048c35538 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x0000000000565cf4 in ?? ()
#4  0x0000000000545811 in ?? ()
#5  <signal handler called>
#6  0x00002aaab5175b28 in gst_element_link_pads_filtered ()
   from /usr/lib/libgstreamer-0.10.so.0
#7  0x00002aaab5175f56 in gst_element_link_many ()
   from /usr/lib/libgstreamer-0.10.so.0
#8  0x00002aaab4cc0f2c in player_new () at player.c:256
#9  0x00000000402cfaba in ?? ()
#10 0x00007fff624fc2b0 in ?? ()
#11 0x00002aaab4b2af50 in ?? ()
#12 0x0000000000858b70 in ?? ()
#13 0x00002aaaaaacce68 in ?? ()
#14 0x0000000000000864 in ?? ()
#15 0x00000000402cfa4b in ?? ()
#16 0x00002aaab4b2af50 in ?? ()
#17 0x00007fff624fc430 in ?? ()
#18 0x00007fff624fc240 in ?? ()
#19 0x00000000402cf6a0 in ?? ()
#20 0x00002aaaaaadadc0 in ?? ()
#21 0x00002aaaaaadadc0 in ?? ()
#22 0x00002aaaaaadadc0 in ?? ()
#23 0x0000000000000000 in ?? ()
#0  0x00002b10496100a2 in select () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

```

This is after installing gstreamer-plugins-ugly.  Unfortunately, before that, I only had a split second of music playing each time. 
Thanks for any help! :)

---

### Post by sciurus on 2008-02-01
Does anyone else see their[ last.fm password stored in plain text]("https://bugs.launchpad.net/ubuntu/+source/last-exit/+bug/187958") in the gconf key /apps/lastexit/password ?

---

### Post by ZeBob on 2008-02-20
Note to all users:

It seems that upstream have stopped the development of last-exit, so I think that all current bugs will stay unpatched. I will no longer update my save patch for this program.

I advice you to take a look at Vagalume, a last.fm client written in C by Alberto Garcia: [http://people.igalia.com/berto/](http://people.igalia.com/berto/) This program has a function to save the free song of last.fm.

I have also ported my save patch for Vagalume to save all songs, but I don't know if I'll distribute it because of the eventual legal problems.

Many thanks to all.

---

### Post by mtron on 2008-02-20
can you send me the save song patch for Vagalume please? i'm sure that this IS leagal in my country of residence (in fact i study law ;). I will also try to maintain the patch for further releases.

---

### Post by clasikowski on 2008-03-03
Hi ZeBob!

I have a question regarding the source-code in the quote below, quoting ZeBob from page 24. #234 in this thread:

> The already patched svn source: last-exit-source_v2.tar.gz
Install it as described in the previous post.


Is there a possibility for non-members to get hold of this stuff? I'm in the process of writing a wiki-thing for the german [http://ubuntuusers.de/wiki](http://ubuntuusers.de/wiki) ; I would like to make your source-code available for others, too

Another issue is the bug mentioned here [http://bugzilla.gnome.org/show_bug.cgi?id=465549](http://bugzilla.gnome.org/show_bug.cgi?id=465549)
I have sucessfully added the patch by  Bob Mauchin to the  "TagView.sc" and "FindStation.sc"-files in the last-exit-patchv2/src-directory of your tarball-thing , so the issue is solved - and a newly compiled deb-package works fine.
Would it be possible to add the patched versions of these files to your last-exit-source_v2.tar.gz? I'll try to attach them as .zip-files, I'll also include my last-exit_5.4_i386.deb, which works fine with gutsy. It's compiled from ZeBob's archive, and the added patched files.

so long
clasikowski (aka hank)

---

### Post by ZeBob on 2008-03-04
Brandon Hale commited my patch for the bug [http://bugzilla.gnome.org/show_bug.cgi?id=465549](http://bugzilla.gnome.org/show_bug.cgi?id=465549) . And for other bugs too.
So just get the last svn and add this patch to your debian/patches
[ATTACH]61593[/ATTACH]
Then you should rebuild the package without problems.

As I said before you should take a look at Vagalume. Mtron made a nice package with the save patch I gave him. It's available here*: [http://mtrons.googlepages.com/vagalume](http://mtrons.googlepages.com/vagalume)

Thanks again Mtron :)

---

### Post by mtron on 2008-03-05
all the thanks goes to you for the nice patch :) I'm using vagalume since 2 weeks, and it is very stable and usable already (very much unlike last-exit,which tended to crash quite often.) i tried to announce vagalume with the possibility of integrating the patch during the build, but the ubuntuforums policy seemed to have changed :(

My thread got  instantly deleted by a moderator, whats a bit strange, because this one about the same stuff for last-exit is still in the "Tips & Tricks" section...

So i don't really get the point why the vagalume thread wasn't accepted ? Anyway, i will of course respect the moderators decision and not talk about this Patch here... 

The german ubuntu forums (ubuntuusers.de) has no problem at all with a patched vagalume, so i will support the patched version there. For english speaking people i will announce a place to get support as soon as possible.

PS: if you wanna build your own binary package for debian based distribution xy, i suggest you get the archive vagalume_0.5.1.src.patched.tar.gz, unpack it, cd in the sources and run "fakeroot debain/rules binary"

---

### Post by buzz91 on 2008-03-05
Hello,

thanks for the tip of using the patched Vagalume 0.5.1 ... but i am not able to compile that for me.

What will  I have to do on an Debian/Etch?

I've downloaded the patched.src, unpacked it, installed fakeroot and then typed "fakeroot debian/rules binary" then I got the error message that dh_testdir is a unknown function.

Can anybody help me?

grezt

---

### Post by clasikowski on 2008-03-05
Hi ZeBob!

Thanks for the infos - I've managed to compile the package, even though only by applying your patch in "copy'n'paste" style... 

I've just another question regarding last-exit: the stations I have used are saved somewhere; they appear on the menu-list. Is there a way to remove them? I couldn't find any file with those entries, do you know how to delete the list (or single entries?)

Vagalume is fine, too,the only thing I miss is the volume-control within the player (a mute button would be ok, too...) 

so long
clasikowski (aka hank)

---

### Post by mtron on 2008-03-06
hi buzz! 

i've uploaded a new vagalume source archive , get the archive vagalume-0.5.1-src.tar.gz

you will need a typical build environment for building packages. I recommend reading the well written [ubuntu packaging guide]("https://help.ubuntu.com/ubuntu/packagingguide/C/"). same applies to debian, as we all know ubuntu is a pimp'ed debian sid :)

Concerning your question: you are missing some packages. Check that you have the set from[ here]("https://help.ubuntu.com/ubuntu/packagingguide/C/gs-tools.html") installed 
you'll need: (as root)
```
apt-get install build-essential devscripts debhelper dh-make diff patch gnupg fakeroot
```

when you look in the debian/ subfolder of the vagalume source code you will find some control files You can edit "changelog", and for debian remove the "1gutsy3" part. This stands for:
1           -      current Debian release Version
gutsy3  -      ubuntu gutsy release version number 3

so i suggest you change it to current debian release +1, e.g 
> vagalume (0.5.1-2) unstable; urgency=low

but you don't need to, it will also work on debian without this change. 

in the debian folder is another one named patches. in this folder is the "save-song.patch", which will be applied during build.  So if you don't want to include the patch just delete it from the dir. (this works also the other way round. If you place another patch in the debian/patches subfolder, they will be applied automatically. i've added a very simple patching environment. Have a look in the rules file)

now cd in the root folder of the vagalume sources and run "fakeroot debian/rules binary" to build the package.

---

### Post by mocha on 2008-03-06
With the latest last-exit v5.4 deb I get 

```
trying to overwrite /usr/local/share/icons/hicolor/icon-theme.cache which is also in package gnomebaker
```

---

### Post by clasikowski on 2008-03-08
Hi Mocha!

Sometimes it helps to remove the package in question, and reinstall it later on...

Otherwise try to build the package from the source-code tar.gz by ZeBob; replace the patched files with those from my post, and, using checkinstall, use the optiom --exclude /usr/local/share/icons/hicolor/icon-theme.cache  (or take up  ZeBob's hints further up the thread, and mtrons explanation two posts up; it should work, too)
 Or fetch the already patched source from here: [http://www.box.net/shared/uduh3i05cw](http://www.box.net/shared/uduh3i05cw) and compile it. I have gnomebaker installed on a gutsy 32-bit system, and had no problems...

so long

clasikowski (aka hank)

---

### Post by clasikowski on 2008-03-08
Hi ZeBob!

I'm still musing about Last-Exit-features, even though I think vagalume is the better choice. 
One question concerns the patches for both: Is there a way to save the files in a hierachy,  automatically creating  - or using an already existing - artist-directory, in which an album-directoriy is made (or again an existing one used)  to save all tracks from that album? 

It would save the  time to tag the files and help to keep an order within the tracks otherwise wildly mixed in the download-directory. 

TheLastRipper [http://thelastripper.com/index.html](http://thelastripper.com/index.html)  is able to do that; I think there is some kind of tagging-program included to achieve this , as it adds ID3v2-tags to the saved files automatically.

Another question concerns the radio stations used in Last-exit: they are saved somewhere - do you know where, and how the list could be removed or edited? The dropdown menu becomes somewhat littered after a time...

thanx,
and so long
clasikowski (aka hank)

---

### Post by mocha on 2008-03-09
> **clasikowski said:**
> 
 Or fetch the already patched source from here: [http://www.box.net/shared/uduh3i05cw](http://www.box.net/shared/uduh3i05cw) and compile it.
clasikowski (aka hank)

Thanks.

---

### Post by clasikowski on 2008-04-05
Hi!

A new version last-exit-6 is available in the hardy-universe repos!

Zebob has updated and improved his save-song-patch; and I have added a few small things for convienience...:guitar:

To use last-exit-6 in gutsy, grab the sourcecode with

```
wget https://launchpad.net/ubuntu/hardy/+source/last-exit/6-1/+files/last-exit_6.orig.tar.gz  
wget https://launchpad.net/ubuntu/hardy/+source/last-exit/6-1/+files/last-exit_6-1.diff.gz
wget https://launchpad.net/ubuntu/hardy/+source/last-exit/6-1/+files/last-exit_6-1.dsc
```

If you need, get the build-deps; then build the sourcecode-directory using

```
sudo apt-get build-dep last-exit
dpkg-source -x last-exit_*.dsc 

```

The patches can be found here: 
[http://media.ubuntuusers.de/forum/attachments/1517680/Last-Exit-6-1-pat.gz](http://media.ubuntuusers.de/forum/attachments/1517680/Last-Exit-6-1-pat.gz)

Move the patches you want to use to the /last-exit-6/debian/patches-folder. Read the **README** first to know what they do; you will definitely need the 01-patch, the others are optional, but some depend on each other, while others can't be used together!
Compile the whole thing using

```
dpkg-buildpackage -us -uc
``` 
install and start ripping...

A prepared source-code-tar.gz and ready-made example.debs (gutsy-32-bit-versions, but they work with hardy, too; and new amd64-bit-versions, still untested!) can be found here: [http://www.box.net/shared/cc0v7zpyck# ](http://www.box.net/shared/cc0v7zpyck# )

(more details, at least  if you know german:
[http://wiki.ubuntuusers.de/Last-Exit](http://wiki.ubuntuusers.de/Last-Exit) )

Have fun!  :)
so long
clasikowski AKA hank

**Edit:** Please note that it could be illegal in your country to rip the LastFM-Stream! I know that it's legal for personal use in Germany and Austria.

---

### Post by bensabin on 2008-05-07
Hi! I'm running on Hardy and I have a problem with the patched last-exit, I tried to install the proposed debs and compile it from the sources, but the result is the same. I only hear the first second of the song and nothing else.
Moreover, it is impossible to save the "playing" song.

Thank you for your help.

[SIZE="1"]I apologize for my bad English, I'm French speaker.[/SIZE]

Edit: Well, it's solve now, the gstreamer0.10-plugins-ugly wasn't installed.
Thank for all

---

### Post by benjou on 2008-07-05
Same problem: one second of music then mute.

Unfortunately for me plugins-ugly is already installed and reinstalling it does not change anything to the problem.
Any idea?

---

### Post by clasikowski on 2008-07-07
Hi!

Sorry, I don't know how to solve this; I think there was a solution posted somewhere in this thread further up; so you'll probably find it somewhere...

If the problem persists (sometimes things like that are due to connection problems with last.fm and disappear sooener or later), have a look at
[http://mtrons.googlepages.com/vagalume](http://mtrons.googlepages.com/vagalume)
It's a new player which offers a lot of things for lastfm, including the savepatch.

so long
clasikowski AKA hank

---

### Post by benjou on 2008-07-07
Hi!

Tried vagalume,

Works like a charm after I installed a few gstreamer plugins.
Would be good to know which ones are actually necessary

Thanks a lot anyway!

---

### Post by clasikowski on 2008-07-09
Hi!

mtron suggests the following:
```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
he advised to get rid of those:
```
sudo dpkg -r gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux
```

I'm not sure which ones are actually needed, either...but for me it works that way.
Vagalume will be in the ubuntu-repos for intrepid ibex, so you could try and install the build-dep's for that source-package, if you have problems.

so long
clasikowski AKA hank

---

### Post by clasikowski on 2008-07-13
Hi!

I fixed a bug concerning scrobbling in the patched version; the revised source-code **last-exit-6-1savesong~hardy1.tar.gz** can be found here: [http://www.box.net/shared/cc0v7zpyck#](http://www.box.net/shared/cc0v7zpyck#) ; the patches can be found in the **last-exit-6/debian/patches** and **last-exit-6/debian/contrib** folder.

As to the problem mentioned above
> Same problem: one second of music then mute.
be sure to have the following installed:

```
gstreamer0.10-plugins-good gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly
```

so long
clasikowski AKA hank

---

### Post by nerd23 on 2008-11-02
hi, does the round play button work with firefox?
i really can't figure it out, tried already
this howto
[http://www.lastfm.de/group/Last+Exit/forum/30436/_/177610](http://www.lastfm.de/group/Last+Exit/forum/30436/_/177610)
tix
nerd

---

### Post by thistransition on 2009-07-14
Is this program compatible with 9.04? I am getting the error "Error: Dependency is not satisfiable: libgconf2.0-cil (<= 2.20.0)" when I try to install the *advancedcheck* version of the program (list of other versions [here]("http://www.box.net/shared/cc0v7zpyck#1:16760013")) 

It seems like my version of that file is too new.. how do I revert back? 

Or what do I need to do?

I'm a noob, thanks for coping with me.

---

### Post by durand on 2009-07-14
You could just manually extract the deb file. Its just a normal archive with two other archives in it. The files are in the...files archive.

BTW, since there haven't been any updates since last.fm started charging most countries for radio access, this may not even work anymore...

---

### Post by Invy on 2009-12-07
where can I get last working version of last.fm player? :)
prefareble installation package then sources, but also can be.

---

### Post by mocha on 2009-12-08
> **Invy said:**
> where can I get last working version of last.fm player? :)
prefareble installation package then sources, but also can be.

I don't think any of the old players like last-exit or vagalume work anymore.  Last.fm changed their API becuase they are moving to a paid model.  Better switch over to shoutcast at this point.

---

### Post by clasikowski on 2009-12-09
Hi!

> I don't think any of the old players like last-exit or vagalume work anymore. Last.fm changed their API becuase they are moving to a paid model. Better switch over to shoutcast at this point.

This isn't exactly true. Unfortunatelly, only users from USA, GB and Germany still have free access to Last.fm, some of the features aren't usable for non-subcribers (like using playlists), but for the time being the third-party-applications still work...

Nobody knows for how long, though... "Outsiders" could try to use a proxy from the privileged countries.

so long
clasikowski AKA hank

---

### Post by Liz.nogan on 2009-12-09
If only broadcasting to a portable radio roughly 100 meters or less away, hooking the speaker output of the computer to a part 15 FM broadcaster (these are low power legal FM broadcasters that put out only enough power to get roughly 100 meters in most residential areas or so) and broadcast away. Any furthur than that would require a license in most locations in the world.

---

### Post by clasikowski on 2010-04-17
Hi!

For some time now I can't connect to Last.fm with last-exit anymore - the player starts up, but it is not able to play anything. In the terminal everything looks normal at startup, but after showing a message like

```
station: http://ws.audioscrobbler.com//radio/adjust.php?session=9fe643146867a038c679c0e58280de3f&url=lastfm://artist/Rebekka Bakken/similarartists&lang=en&debug=1
Playlist: New playlist requested
``` 

nothing happens.

When trying to change to another station, it shows

```
Playlist: New playlist requested
Playlist: Already getting playlist
```

When closing the app, this message appears:

```
(/usr/lib/last-exit/last-exit.exe:21521): GStreamer-CRITICAL **: 
Trying to dispose element player, but it is in READY instead of the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
This problem may also be caused by a refcounting bug in the
application or some element.
```

This happens using the standard software as well as the patched player, regardless of the type of account I use (I have a suscribtion, and another account, too); and regardless which ubuntu version I use (I tried intrepid, karmic and lucid).

The whole project seems to be dead; I can't reach the lastexit-website anymore, and one of the developers asked for a new maintainer in June on the Last.fm last exit group , since he's not using linux anymore...[http://www.lastfm.de/group/Last+Exit/forum/30436/_/551786]("http://www.lastfm.de/group/Last+Exit/forum/30436/_/551786")
Any ideas on this?

so long
clasikowski aka hank

---

### Post by durand on 2010-04-17
If you don't live in the UK, US or Germany, you have to pay to use lastfm radio :( That might be the reason why it doesn't work.

---

### Post by clasikowski on 2010-04-17
Hi!

@ durand
No, since I do live in Germany, and even have a suscribtion, this definitely is not the reason.... And other players work (vagalume etc). 

I guess it is because Last-Exit is not compatible with the new API, but I wonder why the package remains in the repos for lucid if it doesn't work anymore.

so long
clasikowski aka hank

---

### Post by durand on 2010-04-17
Hmm, not sure then...Sorry :(

---

