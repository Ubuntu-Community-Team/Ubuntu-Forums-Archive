---
title: "Wmv9 on AMD64"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Conq on 2006-06-04
Playing back wmv9 files on AMD64 is tricky. On i386 you can use mplayer with the win32 codecs, or the experimental vc-1 codec. However, using AMD64, things get a bit more difficult. It is possible to use the 32bit mplayer package, but it requires that all the libraries that it depends on are also 32bit. Thats why I made a package for you!

Here is what you do:

1. Install all ia32-libs packages apt-get.
```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 ia32-libs-openoffice.org
```
2. Download the package from:
DAPPER: [http://folk.ntnu.no/grannas/debs/mplayer32_1.0pre7-1_amd64.deb]("http://folk.ntnu.no/grannas/debs/mplayer32_1.0pre7-1_amd64.deb")
EDGY: [http://folk.ntnu.no/grannas/debs/mplayer32_20070130-1_amd64.deb]("http://folk.ntnu.no/grannas/debs/mplayer32_20070130-1_amd64.deb")
3. Install the package:
DAPPER: ```
sudo dpkg -i mplayer32_1.0pre7-1_amd64.deb
```
EDGY: ```
sudo dpkg -i mplayer32_20070130-1_amd64.deb
```
4. Fetch the Win32 codecs from: [http://www.people.virginia.edu/~drf8f/MPlayer/releases/codecs/essential-20060501.tar.bz2]("http://www.people.virginia.edu/~drf8f/MPlayer/releases/codecs/essential-20060501.tar.bz2")
5. Unpack it and install to /usr/lib/win32.
```

tar -jxvf essential-20060501.tar.bz2
sudo mkdir /usr/lib/win32
sudo cp essential-20060501/* /usr/lib/win32/

```

Use mplayer32 to play wmv9 files (but it can also be used for other files as well ;-))

If you want a 32 bit mencoder as well, you can download it from here:
[http://www.stud.ntnu.no/~grannas/debs/mencoder32](http://www.stud.ntnu.no/~grannas/debs/mencoder32) and put
it into /usr/bin/ .

If there is enough people requesting it, I will make a package out of it.

If you want to use the gmplayer gui, rather than the command-line do the following:
```

sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer

```
This operation has to be done manually as the gmplayer file is "owned" by the original mplayer package.


[COLOR="Red"]Edit:[/COLOR] Added more IA32 packages.
[COLOR="Red"]Edit 2:[/COLOR] Added download for mencoder32
[COLOR="Red"]Edit 3:[/COLOR] Added info on the GUI

---

### Post by dpasirst on 2006-06-04
This is just what I was looking for...but there are more packages required for this to work.  The following additional packages were required on my system:

lib32asound2
lib32ncurses5
ia32-libs-sdl

---

### Post by Conq on 2006-06-05
Yes, thank you. I've added it to the howto.

---

### Post by superm1 on 2006-06-05
Awesome!

just you named libsound32 wrong in that first post :)

---

### Post by Gyuszk on 2006-06-05
Thanks, worked well! (ubuntu 6.06 LTS final amd64)

---

### Post by Chareos on 2006-06-05
If this could be extended to dvd playing functionality... would be godly.

---

### Post by Conq on 2006-06-06
[QUOTE=Chareos]If this could be extended to dvd playing functionality... would be godly.[/QUOTE]

I am assuming you want libdvdcss. I don't want to distribute it, but someone else does. This is what you do:
```

wget http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
dpkg -x libdvdcss2_1.2.5-1_i386.deb .
sudo mv usr/lib/libdvdcss.so.2* /usr/lib32/

```

Unfortunately, I can't test this right now, because my DVD drive is broken,
but you might?

---

### Post by Schapie123 on 2006-06-06
If you want gmplayer as graphical frontend, you can do the following after following the first post:

```

sudo apt-get install mplayer
sudo cp /usr/bin/mplayer /usr/bin/mplayer64
sudo cp /usr/bin/mplayer32 /usr/bin/mplayer

```

Is it possible to use the mplayer32 from this guide with a plugin in the [www.getfirefox.com](www.getfirefox.com) firefox version?

---

### Post by superm1 on 2006-06-06
I created my own mozilla-mplayer package that called the appropriate binary.  I also used the newer upstream package for this purpose.  Attached are binary and source.

Note: I created two binaries.  One of them is intended for a 64 bit web browser, and the other and the other a 32 bit web browser.  Also attached is the source package I used to create each.

---

### Post by Conq on 2006-06-06
[QUOTE=Schapie123]If you want gmplayer as graphical frontend, you can do the following after following the first post:

```

sudo apt-get install mplayer
sudo cp /usr/bin/mplayer /usr/bin/mplayer64
sudo cp /usr/bin/mplayer32 /usr/bin/mplayer

```

Is it possible to use the mplayer32 from this guide with a plugin in the [www.getfirefox.com](www.getfirefox.com) firefox version?[/QUOTE]

Actually, if you look at it, gmplayer is just a symbolic link to mplayer. 
If you want gmplayer to use mplayer32 instead of mplayer (64 bit version), a better way would be to do something like this:

```

sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer

```

---

### Post by Schapie123 on 2006-06-06
[QUOTE=superm1]I created my own mozilla-mplayer package that called the appropriate binary.  I also used the newer upstream package for this purpose.  Attached are binary and source.

Note: The binary I made is designed to be used with the 64 bit firefox.  If you are using some sort of 32 bit variant, grab my source here and just build it for 32 bit instead.[/QUOTE]

How do I build it for 32 in stead of 64?

---

### Post by Schapie123 on 2006-06-06
[QUOTE=Conq]Actually, if you look at it, gmplayer is just a symbolic link to mplayer. 
If you want gmplayer to use mplayer32 instead of mplayer (64 bit version), a better way would be to do something like this:

```

sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer

```[/QUOTE]

I see. But why does launching mplayer through this symbolic link have a different effect (the added gui) than launching it directly?

---

### Post by superm1 on 2006-06-06
[quote=Schapie123]How do I build it for 32 in stead of 64?[/quote]
I Just rebuilt again, one for a 32 bit browser, and uploaded both.  I don't have a 32 bit browser installed, so someone will have to verify that the package installs and such okay, but its the same source as the 64, so it should be functionally the same.  See my older post for the binaries.

---

### Post by Conq on 2006-06-06
[QUOTE=Schapie123]I see. But why does launching mplayer through this symbolic link have a different effect (the added gui) than launching it directly?[/QUOTE]

It's one of those unix-tricks =). What happens is that the first argument passed to any program is the name of the program that has been started. Mplayer simply checks this and sees that it is gmplayer that is the first parameter and launches the GUI. If you look at your /usr/bin directory, there are several other just like it (f.ex vim). 

In geek: argv[0] is a string with the name of the command-line utility :-)

---

### Post by Schapie123 on 2006-06-07
[QUOTE=superm1]I Just rebuilt again, one for a 32 bit browser, and uploaded both.  I don't have a 32 bit browser installed, so someone will have to verify that the package installs and such okay, but its the same source as the 64, so it should be functionally the same.  See my older post for the binaries.[/QUOTE]

Thanks. I tried it. Since I got my firefox32 in /usr/lib/mozilla-firefox-32 I copied the plugins from /usr/lib/mozilla/plugins to /usr/lib/mozilla-firefox-32/plugins
Firefox sees the plugins are there (I tried it with the 64 version, it couldn't see those). But as soon as I try to play a video, firefox crashes on me.

---

### Post by Schapie123 on 2006-06-07
[QUOTE=Conq]It's one of those unix-tricks =). What happens is that the first argument passed to any program is the name of the program that has been started. Mplayer simply checks this and sees that it is gmplayer that is the first parameter and launches the GUI. If you look at your /usr/bin directory, there are several other just like it (f.ex vim). 

In geek: argv[0] is a string with the name of the command-line utility :-)[/QUOTE]

As a kid I used to mess around in C on my good old 286 DOS thingy. Should have known ;)

---

### Post by kuja on 2006-06-07
I decided I'd give this a go, yet it seems it won't even start :(

dustin@terra:~$ mplayer32
mplayer32: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

---

### Post by superm1 on 2006-06-07
[quote=Schapie123]Thanks. I tried it. Since I got my firefox32 in /usr/lib/mozilla-firefox-32 I copied the plugins from /usr/lib/mozilla/plugins to /usr/lib/mozilla-firefox-32/plugins
Firefox sees the plugins are there (I tried it with the 64 version, it couldn't see those). But as soon as I try to play a video, firefox crashes on me.[/quote]

Hmm.... can you try launching FF from a command line and see if it spits anything else back about why things went south?  And have you tried the 64 bit version with the 64 bit plugin, does that work?

---

### Post by Conq on 2006-06-07
[QUOTE=kuja]I decided I'd give this a go, yet it seems it won't even start :(

dustin@terra:~$ mplayer32
mplayer32: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory[/QUOTE]

It seems I forgot another library dependency:
```

sudo apt-get install ia32-libs-gtk

```

It has been added to the howto.

---

### Post by Schapie123 on 2006-06-07
[QUOTE=superm1]Hmm.... can you try launching FF from a command line and see if it spits anything else back about why things went south?  And have you tried the 64 bit version with the 64 bit plugin, does that work?[/QUOTE]

I will try it friday, and post here how it went :)

---

### Post by kuja on 2006-06-07
[QUOTE=Conq]It seems I forgot another library dependency:
```

sudo apt-get install ia32-libs-gtk

```

It has been added to the howto.[/QUOTE]

Thank you ever so much :) It works well now

---

### Post by henriquemaia on 2006-06-07
Thanks a lot for this one! Works flawlessly!

Finally I can see all those little videos people send me through email. :)

---

### Post by Schapie123 on 2006-06-09
[QUOTE=superm1]Hmm.... can you try launching FF from a command line and see if it spits anything else back about why things went south?  And have you tried the 64 bit version with the 64 bit plugin, does that work?[/QUOTE]

Launching firefox from the terminal gives me:

```

/usr/lib/mozilla-firefox-32/run-mozilla.sh: line 131:  6006 Segmentatie fout     "$prog" ${1+"$@"}

```

Which, of course is a segmentation fault in English :)

The 64 bits version of firefox with the 64 bits plugin has the same problem on my system

---

### Post by Garfy on 2006-06-10
hi!

When I launcing mplayer32 I got an error:
```
~$ mplayer32 
mplayer32: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

but, the libstdc++6-0 package already installed.
mplayer32_1.0pre7-1_amd64.deb installed too of course.
(Ubuntu-Dapper, AMD x86_64)

Any idea?
THX

---

### Post by Conq on 2006-06-10
[QUOTE=Garfy]hi!

When I launcing mplayer32 I got an error:
```
~$ mplayer32 
mplayer32: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

but, the libstdc++6-0 package already installed.
mplayer32_1.0pre7-1_amd64.deb installed too of course.
(Ubuntu-Dapper, AMD x86_64)

Any idea?
THX[/QUOTE]

You need the lib32stdc++6 package, just add it with 
```

sudo apt-get install lib32stdc++6

```
I've added it to the howto.

---

### Post by Garfy on 2006-06-10
[QUOTE=Conq]You need the lib32stdc++6 package, just add it with 
```

sudo apt-get install lib32stdc++6

```
I've added it to the howto.[/QUOTE]

lib32stdc++6 is already the newest version.
:-?

---

### Post by Garfy on 2006-06-10
Solved:
I just reinstalled all lib32 packages and its now working.

---

### Post by jairo.serrano on 2006-06-11
Great! works for me!

amd64 3000+

---

### Post by Lonergan on 2006-06-11
This works flawlessly for me running an AMD64 X2 4200+

Thanks!

---

### Post by julipanno on 2006-06-12
[QUOTE=Schapie123]Launching firefox from the terminal gives me:

```

/usr/lib/mozilla-firefox-32/run-mozilla.sh: line 131:  6006 Segmentatie fout     "$prog" ${1+"$@"}

```

Which, of course is a segmentation fault in English :)

The 64 bits version of firefox with the 64 bits plugin has the same problem on my system[/QUOTE]

Same problem here.
I have been using firefox32 on amd64 as described in the wiki (now to be found under "java" I believe). First, to get mplayer-plugin to work, I simply copied the "plugins"-directory from the 32bit mozilla-mplayer deb-file I found at the official repository to /usr/local/firefox32/plugins. This worked, and the plugin was able to play a few formats. I didn't have a clue how to make w32codecs work with the plugin, though, and this thread seems to have a perfect solution. Unfortunately it crashes on me.

Being somewhat a beginner myself, the error don't make much sense to me. I checked up line 131 in /usr/lib/mozilla-firefox-32/run-mozilla.sh and all it says is "{"

If I uninstall the mplayer-plugin from this thread and revert to the standard 32bit package that worked, how can I tell the plugin where to find the w32codecs?


peace,
Stian

---

### Post by superm1 on 2006-06-12
I'm still trying to determine what about the way I did that package is causing the breakage.  As soon as I have a conclusion, I'll post up the fix (although I can't reproduce the 64 bit problem here).

---

### Post by DancingSun on 2006-06-14
Thanks for making the 32-bit debs, Conq!

---

### Post by chanman3388 on 2006-06-20
Hello!

[QUOTE=Garfy]

When I launcing mplayer32 I got an error:
```
~$ mplayer32 
mplayer32: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

[/QUOTE]

except the "libstdc++.so.6" is replaced with "libasound.so.2" which I seem to have on the pc. I'm not really sure what's wrong, any help would be very much appreciated.

Thanks

---

### Post by chanman3388 on 2006-06-20
Sorry, the post above is now obsolete, it just seemed that the package hadn't installed. It may be because I'm rather new to this, but the libncurses.so.5 file is now the problem, I sourced out the file and tried to install it, however it said that a newer version was in place. If this file happens to be "libncursesw5", it asks me to remove practically the rest of the software on the pc. Is there a fairly straight-forward solution to this? Thanks for your time.

---

### Post by Conq on 2006-06-21
[QUOTE=chanman3388]Sorry, the post above is now obsolete, it just seemed that the package hadn't installed. It may be because I'm rather new to this, but the libncurses.so.5 file is now the problem, I sourced out the file and tried to install it, however it said that a newer version was in place. If this file happens to be "libncursesw5", it asks me to remove practically the rest of the software on the pc. Is there a fairly straight-forward solution to this? Thanks for your time.[/QUOTE]

No, don't remove that package. Try to install lib32ncurses5 instead.

```

sudo apt-get install lib32ncurses5

```

If it is allready installed, you might want to reinstall it.
```

sudo apt-get install --reinstall  lib32ncurses

```

Are you sure you did step 1 correctly?

---

### Post by chanman3388 on 2006-06-22
Erm, from what I remember lib32ncurses5 is the only one apt-get didn't get as it said it didn't exist. I tried to install/reinstall it but it says I already have it. If it says that the problem is 'libncurses.so.5' isn't that different to lib32ncurses5?? I'll try it from the top again and see what happens. Cheers though.

---

### Post by chanman3388 on 2006-06-22
Right, I don't think I've totally solved it, but I think I may have all the files, but they may not be in the right places? As I found libncurses.so.5 and moved it to the lib32 file which solved that bit. Now it's saying I don't have 'libSDL-1.2.so.0' which I do, but I'm trying to shift it around, so it might be a while before I get this working. At any rate thanks for the help.

---

### Post by chanman3388 on 2006-06-22
I haven't got the mplayer to work as such. But I was faffing with the Add/Remove app and selected 'Show unsupported applications' and like downloaded a load of music apps, and now most of my players can pplay .wma's, which is strange? I dunno, if anyone reads and wonders why, I'm not sure but I downloaded some like gstreamer plugins, xine plugins, er and this audio converter or somin that says it can convert between various formats including .wma so maybe that did it?? At any rate a little exploration never hurt anyone...

---

### Post by Conq on 2006-06-22
[QUOTE=chanman3388]Erm, from what I remember lib32ncurses5 is the only one apt-get didn't get as it said it didn't exist. I tried to install/reinstall it but it says I already have it. If it says that the problem is 'libncurses.so.5' isn't that different to lib32ncurses5?? I'll try it from the top again and see what happens. Cheers though.[/QUOTE]

Yes, there is a difference.
lib32ncurses5 installs "/lib32/libncurses.so.5", while
libncurses5 installs "/lib/libncurses.so.5"

One is for 32-bit apps, while the other is for 64-bit apps. You cannot simply
copy it. If you still have problems please do the following and paste the output into this thread, so I can take a look:
```

ldd /usr/bin/mplayer32

```

---

### Post by Conq on 2006-06-22
[QUOTE=chanman3388]I haven't got the mplayer to work as such. But I was faffing with the Add/Remove app and selected 'Show unsupported applications' and like downloaded a load of music apps, and now most of my players can pplay .wma's, which is strange? I dunno, if anyone reads and wonders why, I'm not sure but I downloaded some like gstreamer plugins, xine plugins, er and this audio converter or somin that says it can convert between various formats including .wma so maybe that did it?? At any rate a little exploration never hurt anyone...[/QUOTE]

You can play most wmv-type files with the 64-bit mplayer, only wmv9 files cannot be played with the 64 bit mplayer.

---

### Post by chanman3388 on 2006-06-23
Yeah, one of the players here says wma v8. Anyways, here be the code:

```

        linux-gate.so.1 =>  (0xffffe000)
        libdvdread.so.3 => /usr/lib32/libdvdread.so.3 (0x5557e000)
        libmad.so.0 => /usr/lib32/libmad.so.0 (0x55597000)
        libvorbis.so.0 => /usr/lib32/libvorbis.so.0 (0x555af000)
        libogg.so.0 => /usr/lib32/libogg.so.0 (0x555d7000)
        libdv.so.4 => /usr/lib32/libdv.so.4 (0x555dc000)
        libtheora.so.0 => /usr/lib32/libtheora.so.0 (0x55604000)
        liblzo.so.1 => /usr/lib32/liblzo.so.1 (0x55621000)
        libmp3lame.so.0 => /usr/lib32/libmp3lame.so.0 (0x4c329000)
        libxvidcore.so.4 => /usr/lib32/libxvidcore.so.4 (0x55641000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0x5575c000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x5577f000)
        libjpeg.so.62 => /usr/lib32/libjpeg.so.62 (0x55793000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0x557b2000)
        libdl.so.2 => /lib32/libdl.so.2 (0x5586e000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x55872000)
        libmpcdec.so.3 => /usr/lib32/libmpcdec.so.3 (0x55884000)
        libspeex.so.1 => /usr/lib32/libspeex.so.1 (0x55893000)
        libfaac.so.0 => /usr/lib32/libfaac.so.0 (0x558b0000)
        libmp4v2.so.0 => /usr/lib32/libmp4v2.so.0 (0x558c1000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0x5595e000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x55a3a000)
        libncurses.so.5 => /lib32/libncurses.so.5 (0x55aa3000)
        libcdda_interface.so.0 => /usr/lib32/libcdda_interface.so.0 (0x4b877000)
        libcdda_paranoia.so.0 => /usr/lib32/libcdda_paranoia.so.0 (0x4bb76000)
        libnsl.so.1 => /lib32/libnsl.so.1 (0x55ae5000)
        libungif.so.4 => /usr/lib32/libungif.so.4 (0x55afa000)
        libsmbclient.so.0 => /usr/lib32/libsmbclient.so.0 (0x55b02000)
        libfribidi.so.0 => /usr/lib32/libfribidi.so.0 (0x55caf000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x55cbd000)
        libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0x55ceb000)
        libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0x55fbf000)
        libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0x5603c000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0x56056000)
        libm.so.6 => /lib32/libm.so.6 (0x5606b000)
        libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0x5608d000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x56095000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x560a2000)
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0x560aa000)
        libXi.so.6 => /usr/lib32/libXi.so.6 (0x560ae000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x560b6000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x560b9000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x560c2000)
        libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0x560c6000)
        libcairo.so.2 => /usr/lib32/libcairo.so.2 (0x560fe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x56145000)
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0x5622b000)
        libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0x56263000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0x56266000)
        libaa.so.1 => /usr/lib32/libaa.so.1 (0x562ea000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x56304000)
        libXxf86dga.so.1 => /usr/lib32/libXxf86dga.so.1 (0x5636b000)
        libXv.so.1 => /usr/lib32/libXv.so.1 (0x56370000)
        libXvMC.so.1 => /usr/lib32/libXvMC.so.1 (0x56374000)
        libXvMCW.so.1 => /usr/lib32/libXvMCW.so.1 (0x56377000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0x5637c000)
        libSDL-1.2.so.0 => not found
        libggi.so.2 => /usr/lib32/libggi.so.2 (0x56382000)
        libslang.so.2 => /usr/lib32/libslang.so.2 (0x5638d000)
        libartsc.so.0 => /usr/lib32/libartsc.so.0 (0x56448000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0x5644e000)
        libesd.so.0 => /usr/lib32/libesd.so.0 (0x56452000)
        libaudiofile.so.0 => /usr/lib32/libaudiofile.so.0 (0x5645a000)
        libaudio.so.2 => /usr/lib32/libaudio.so.2 (0x5647b000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x5648f000)
        liblirc_client.so.0 => /usr/lib32/liblirc_client.so.0 (0x564dd000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x564e2000)
        libc.so.6 => /lib32/libc.so.6 (0x564ed000)
        /lib/ld-linux.so.2 (0x55555000)
        libcrypt.so.1 => /lib32/libcrypt.so.1 (0x5661d000)
        libresolv.so.2 => /lib32/libresolv.so.2 (0x5664a000)
        libgssapi_krb5.so.2 => /usr/lib32/libgssapi_krb5.so.2 (0x5665d000)
        libkrb5.so.3 => /usr/lib32/libkrb5.so.3 (0x56679000)
        libk5crypto.so.3 => /usr/lib32/libk5crypto.so.3 (0x566f2000)
        libkrb5support.so.0 => /usr/lib32/libkrb5support.so.0 (0x56715000)
        libcom_err.so.2 => /lib32/libcom_err.so.2 (0x5671b000)
        libldap_r.so.2 => /usr/lib32/libldap_r.so.2 (0x5671e000)
        liblber.so.2 => /usr/lib32/liblber.so.2 (0x56752000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x5675e000)
        libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0x5677d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x567a2000)
        libgpm.so.1 => /usr/lib32/libgpm.so.1 (0x567a5000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0x567ab000)
        libgii.so.0 => /usr/lib32/libgii.so.0 (0x567b2000)
        libgg.so.0 => /usr/lib32/libgg.so.0 (0x567ba000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x567c3000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x567cb000)
        libsasl2.so.2 => /usr/lib32/libsasl2.so.2 (0x567e3000)
        libgnutls.so.12 => /usr/lib32/libgnutls.so.12 (0x567f7000)
        libtasn1.so.2 => /usr/lib32/libtasn1.so.2 (0x56861000)
        libgcrypt.so.11 => /usr/lib32/libgcrypt.so.11 (0x56871000)
        libgpg-error.so.0 => /usr/lib32/libgpg-error.so.0 (0x568bd000)

```

---

### Post by Conq on 2006-06-23
[QUOTE=chanman3388]Yeah, one of the players here says wma v8. Anyways, here be the code:

```

        libSDL-1.2.so.0 => not found

```[/QUOTE]

Try to do apt-get install ia32-libs-sdl. Are you sure you did step 1 correctly? You are missing a lot of dependencies that would have been installed in that step.

---

### Post by chanman3388 on 2006-06-25
I'm pretty sure I did, but I will redo it to make sure.

---

### Post by chanman3388 on 2006-06-26
Well, it seems I was wrong, I'm sorry. That has solved the problem, thanks alot!

---

### Post by LordOfTheBoards on 2006-06-28
Hello everybody!

I am trying to install wmv9 compatibility on my ubuntu for days now, but I cant believe what a pain in the *** this has become. No matter what problem I solve there is still a shared library that mplayer32 won't find. In this case it's:

mplayer32: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory

Can anybody tell me what package i am missing? 
Thanks for the help so far

LOTB

---

### Post by LordOfTheBoards on 2006-06-28
Hi everybody, the 2nd!

Looks like I made it. I just installed all lib32* packages I found in Synaptic, and removed openoffice temporarily. Then I installed openoffice again and removed the conflicting packages. mplayer32 seems to work. Haven't had the chance to try *.wmv files (now of course I can't find any), but avi works, so I guess thats a good sign.
Thanks again.

LOTB

---

### Post by neev on 2006-07-02
Hello, Ive followed the steps in the 1st page and i got no error, but now i dont know how to run the mplayer32 :oops:. If I write mplayer32 in the terminal i get some sort of command instructions. And under Applications -> Sound & Video, it does not appear (it only appears the one i already had installed, i assume its the 64 one, but cant play wmv9 yet)

Any help?? Thanks!!

---

### Post by maximilian35 on 2006-07-03
amd 3200+, also i succeeded to ran on it. Thanks for sharing.

---

### Post by Simpele on 2006-07-08
> **superm1 said:**
> I created my own mozilla-mplayer package that called the appropriate binary.  I also used the newer upstream package for this purpose.  Attached are binary and source.

Note: I created two binaries.  One of them is intended for a 64 bit web browser, and the other and the other a 32 bit web browser.  Also attached is the source package I used to create each.

Is there any way to create this for Seamonkey as well?

---

### Post by superm1 on 2006-07-08
> **Simpele said:**
> Is there any way to create this for Seamonkey as well?

To follow up, I couldnt reproduce the problems people had before with my plugins on my amd64 box.  I tried a 32 bit and 64 bit browser with both versions of my plugins, but they both work for me.

Seamonkey..... that's the new name for the mozilla suite right?  Well these plugins are compatible with anything using that same netscape plugin format.  They should be able to just be dropped right into the seamonkey's plugin folder and go.

---

### Post by Conq on 2006-07-09
> **neev said:**
> Hello, Ive followed the steps in the 1st page and i got no error, but now i dont know how to run the mplayer32 :oops:. If I write mplayer32 in the terminal i get some sort of command instructions. And under Applications -> Sound & Video, it does not appear (it only appears the one i already had installed, i assume its the 64 one, but cant play wmv9 yet)

Any help?? Thanks!!

Yes, the package only installs the commandline utility. Try to type
mplayer32 <fileyouwanttoplay> in a terminal and it will probably just work =)

---

### Post by Blind Valley on 2006-07-12
> **Conq said:**
> Playing back wmv9 files on AMD64 is tricky. On i386 you can use mplayer with the win32 codecs, or the experimental vc-1 codec. However, using AMD64, things get a bit more difficult. It is possible to use the 32bit mplayer package, but it requires that all the libraries that it depends on are also 32bit. Thats why I made a package for you!

Here is what you do:

1. Install all ia32-libs packages using apt-get.
```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6
```
2. Download the package from:
[http://folk.ntnu.no/grannas/debs/mplayer32_1.0pre7-1_amd64.deb]("http://folk.ntnu.no/grannas/debs/mplayer32_1.0pre7-1_amd64.deb")
3. Install the package:
```
sudo dpkg -i mplayer32_1.0pre7-1_amd64.deb
```
4. Fetch the Win32 codecs from: [http://www.people.virginia.edu/~drf8f/MPlayer/releases/codecs/essential-20060501.tar.bz2]("http://www.people.virginia.edu/~drf8f/MPlayer/releases/codecs/essential-20060501.tar.bz2")
5. Unpack it and install to /usr/lib/win32.
```

tar -jxvf essential-20060501.tar.bz2
sudo mkdir /usr/lib/win32
sudo cp essential-20060501/* /usr/lib/win32/

```

Use mplayer32 to play wmv9 files (but it can also be used for other files as well ;-))

[COLOR="Red"]Edit:[/COLOR] Added more IA32 packages.


It gives me something like that..

mplayer32: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

any suggestion?:-k

---

### Post by wazzie on 2006-07-13
how do i get a graphical front end? none of the posts are clear. like a program i can just load or application to click on. i successfully used mplayer32, i dano if i can play wmv yet though.

---

### Post by Conq on 2006-07-13
> **Blind Valley said:**
> It gives me something like that..

mplayer32: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

any suggestion?:-k

It seems you haven't done step 1 correctly. Try to reinstall lib32asound2 (or
redo step 1).

---

### Post by Conq on 2006-07-13
> **wazzie said:**
> how do i get a graphical front end? none of the posts are clear. like a program i can just load or application to click on. i successfully used mplayer32, i dano if i can play wmv yet though.

You need to make the symbolic link /usr/bin/gmplayer point at /usr/bin/mplayer32. 

```

cd /usr/bin
sudo rm gmplayer
sudo ln -s mplayer32 gmplayer

```

---

### Post by dimis on 2006-07-14
Hi guys,
I installed yesterday Ubuntu and so far most things work. Anyway, I tried to install via automatix the various codecs, but I ended up not being able to play wmv files. Seeking for a solution I came here. I followed all the steps (twice) in copy-paste fashion. Yet, I am still not able to view wmv files. When I try to open a wmv file with mplayer I can hear the sound of the video, but NO image at all. I get the following error message:
Cannot find codec matching selected -vo and video format 0x33564D57.

Any idea for a solution?
Thank you in advance for your time.

---

### Post by dimis on 2006-07-14
Quoting myself:
> **dimis said:**
> Cannot find codec matching selected -vo and video format 0x33564D57.
I don't know how this was fixed, I can now view the image and hear the sound as well. All I did was making again the soft link on gmplayer from mplayer32 ...
Anyway, mplayer seems to play perfectly all wmv videos I tried so far. On the other hand, it now has problems with some avis ... I mean, I can hear the sound and view the image but these two are not synchronized! :p  However, I can perfectly see (synchronization is perfect) exactly the same mplayer-problematic-up-to-now-video with Totem (Movie Player)! :o On the other hand, Totem is not able to open all wmv files ... :confused: 
Can someone explain me what is actually happening with the codecs. A reference would be extremely welcome as well, because so far I thought that codecs were universal and players retrieved them at will from a directory.

Thank you in advance,
My best regards from my lovely Ubuntu64! :)

---

### Post by Conq on 2006-07-14
Hi, this is usually caused by bad sound-card setups. You might want to try different -vo and -ao options in mplayer. Just type mplayer -vo help and you'll see a list of your options (same goes for -ao). Additionally, the mplayer homepage [mplayerhq.hu](mplayerhq.hu) has a lot of information regarding similar problems.

---

### Post by joakim2 on 2006-07-15
> **superm1 said:**
> I created my own mozilla-mplayer package that called the appropriate binary.  I also used the newer upstream package for this purpose.  Attached are binary and source.

Note: I created two binaries.  One of them is intended for a 64 bit web browser, and the other and the other a 32 bit web browser.  Also attached is the source package I used to create each.

I can see the plugin(s) in about:config, I can play fine from the command line using mplayer, but trying to watch a video in the browser crashes it with a no more useful error than seg fault. I'm using the 32 bit version you provided together with Swiftfox

---

### Post by profjohn on 2006-07-18
> **LordOfTheBoards said:**
> Hello everybody!

I am trying to install wmv9 compatibility on my ubuntu for days now, but I cant believe what a pain in the *** this has become. No matter what problem I solve there is still a shared library that mplayer32 won't find. In this case it's:

mplayer32: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory

Can anybody tell me what package i am missing? 
Thanks for the help so far

LOTB

You need to do
**sudo ia32-libs-openoffice.org**

That fixed mine

---

### Post by julipanno on 2006-07-18
> mplayer32: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory
 
 Can anybody tell me what package i am missing?

You can search for contents of packages at [http://packages.ubuntu.com](http://packages.ubuntu.com)

In your case, libgssapi_krb5.so.2 is included in "libkrb53"


peace,
Stian

---

### Post by fabertawe on 2006-07-20
**HUGE** thanks to Conq and superm1 :D 

I didn't see it mentioned, so for clarification... I removed standard mplayer thinking I'd do a clean install but couldn't view certain video clips in Swiftfox until I'd reinstalled mplayer from Synaptic **as well as this version** (plus fonts and skins). I had to remake the symlink for gmplayer to mplayer32 as well, obviously.

Cheers ... Paul

---

### Post by futureman on 2006-07-23
I cannot get this to work, no video will play for me, here's an example of what i get.

[HTML]MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/mike/video.wmv.
ASF file format detected.
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: FileCabi.net - Where you Provide the Entainment!
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
tdfxfb: This driver is only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5
Couldn't open /dev/3dfx
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 320 x 240 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 320 x 240 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Video: no video
Starting playback...
A: 110.8 (01:50.8) of 113.0 (01:53.0)  0.3%

Exiting... (End of file)
[/HTML]

Any ideas?

---

### Post by Conq on 2006-07-24
> **futureman said:**
> I cannot get this to work, no video will play for me, here's an example of what i get.

Any ideas?

Have you tried selecting another video output driver with the vo-option, like it says in the output? Try mplayer32 -vo help for a list of options and mplayer32 -vo <outputdriver> <filetoplay> to actually try it.

---

### Post by MilesTEG1 on 2006-07-25
Thanks for this HowTo, it work greatfully for my Dapper Kubuntu 64 bits ;)

But it is only in command line.
Does mplayer32 have a gui (for kde or gnome) ??

Thanks
++
Miles

---

### Post by Conq on 2006-07-27
> 
But it is only in command line.
Does mplayer32 have a gui (for kde or gnome) ??


Yes, It's one of the previous posts. Basically what you do is make a
symbolic link from gmplayer to mplayer32 like this:
[CODE]
sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer
[CODE]

Then you can use gmplayer to get a graphical frontend. Maybe I should make
it a part of the package? The problem is that the original 64 bit package "owns" that file. Perhaps just I'll just update the howto. Opinions or suggestions anyone?

---

### Post by Theja on 2006-07-29
Hi all,
me been watching a lot of threads....
Have been using dapper 64bit for my turion notebook.
I am getting the same message....as the one posted before..for eg:
/////////////////////////////////////////////////////////////

theja@kitchencomp:~$ mplayer32 -vo 1 Shinobi-Heart\ under\ Blade\ 2005.avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer; Athlon 64 X2 Toledo; Turion Newark,Lancaster (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Shinobi-Heart under Blade 2005.avi.
AVI file format detected.
AVI: ODML: Building odml index (2 superindexchunks)
VIDEO:  [XVID]  672x288  12bpp  23.976 fps  783.4 kbps (95.6 kbyte/s)
Clip info:
 Software: AVI-Mux GUI 1.16.11, Dec 15 2004  14:51:34
SUB: Detected subtitle file format: subviewer
SUB: Read 491 subtitles.
SUB: added subtitle file (1): ./Shinobi-Heart under Blade 2005.srt
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)



////////////////////////////////////////////////////////////////

and when I do mplayer32 -vo I get this message....

theja@kitchencomp:~$ mplayer32 -vo
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer; Athlon 64 X2 Toledo; Turion Newark,Lancaster (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
////////////////////////////////////////////////////////////////

I have followed everything what was given in the thread....gmplayer opens mplayer but it is hung with no buttons to click on.......

Can someone help me in this regard......

Theja

---

### Post by LinuxConvertJune2006 on 2006-08-04
Hi thanks for yur guide, mplayer32 laucnhes foir me, however cnn.com free video provides sounds but no video, just the "loading mplayers" logo , qwhich seems to connect to their URI fine (I see connected and get sound from the clip) but no video. any suggestions?

---

### Post by DonVla on 2006-08-05
does it also work with xine?

vlad

---

### Post by a_l_a_n on 2006-08-05
Dude ... what about mencoder32?!? :confused: Thats why I followed your howto ... I figured you were goung to give me both. :(  If we could have that then we wouldnt have need to use 32 bit and crappy windows codecs, we could just recode to a sensible format. :cool: 

Any chance?

(I sound rather ungrateful, sorry. Thanks for the info./deb =D> )

---

### Post by a_l_a_n on 2006-08-05
Or if you could post a few details about the 64 to 32 bit compilation process Id be happy to try myself.

---

### Post by Conq on 2006-08-06
Try this binary:

[http://www.stud.ntnu.no/~grannas/debs/mencoder32](http://www.stud.ntnu.no/~grannas/debs/mencoder32)

Put it in /usr/bin and let me know if it works. I'll make a package
later (when I have the time).

---

### Post by LinuxConvertJune2006 on 2006-08-06
> **LinuxConvertJune2006 said:**
> Hi thanks for yur guide, mplayer32 laucnhes foir me, however cnn.com free video provides sounds but no video, just the "loading mplayers" logo , qwhich seems to connect to their URI fine (I see connected and get sound from the clip) but no video. any suggestions?

FYI, if this happens to you overwrite mplayer with mplayer32 binary, mentioned on like the first page, I forgot that step now it works fine.

---

### Post by a_l_a_n on 2006-08-06
> **Conq said:**
> Try this binary:

[http://www.stud.ntnu.no/~grannas/debs/mencoder32](http://www.stud.ntnu.no/~grannas/debs/mencoder32)

Put it in /usr/bin and let me know if it works. I'll make a package
later (when I have the time).

Hey, thanks for getting on this, but its just seg faulting for me:
```

$ strace mencoder32
execve("/usr/bin/mencoder32", ["mencoder32"], [/* 34 vars */]) = 4294967282
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

$ nm /usr/bin/mencoder32
nm: /usr/bin/mencoder32: File format not recognized

```

Is it difficult to cross-compile like this?

Just had what is probably a very naive thought. Could linux32 be of any use in this case?

---

### Post by xep007 on 2006-08-07
how to build the package mplayer32 for debian-amd64/sid?

---

### Post by a_l_a_n on 2006-08-07
:confused: 

> **xep007 said:**
> how to build the package mplayer32 for debian-amd64/sid?

Are you asking for clarification on my question (in which case the answer is yes) or are you asking another question of your own?

---

### Post by Conq on 2006-08-07
Hi, try to download the binary again, for some reason I only got a
partial upload the last time.

Actually, what I did is quite simple. I ripped out the mplayer binary from
a i386 install, along with all the debendencies (libraries and such) and made a package out of it using checkinstall.

---

### Post by a_l_a_n on 2006-08-07
SWEET! :D 

Thanks conq!!!! It works beautifully. Now I can get rid of all these stupid wmv and rm files.

Thanks again.

---

### Post by Zyith on 2006-08-07
> **Conq said:**
> 

Here is what you do:

1. Install all ia32-libs packages using apt-get.
```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6
```

I feel like a moron, I've tried this, and I get the following errors:

```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6
Reading package lists... Done
Building dependency tree... Done
lib32asound2 is already the newest version.
lib32stdc++6 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not installable
             Depends: libc6-i386 but it is not going to be installed
  ia32-libs-sdl: Depends: lib32gcc1 but it is not going to be installed
                 Depends: lib32z1 but it is not installable
  lib32asound2: Depends: libc6-i386 (>= 2.4-1) but it is not going to be installed
  lib32ncurses5: Depends: libc6-i386 (>= 2.3.4-1) but it is not going to be installed
  lib32stdc++6: Depends: lib32gcc1 but it is not going to be installed
E: Broken packages
```

Am I missing a repository or something? I've been at this for a while, even tried getting a few dependencies one by one, but it isn't helping. I'm on Dapper Drake with the default 2.6.15 AMD64 Generic kernel. Any help will be greatly appreciated. Everything else has set up fine. :-|

Thanks in advance to anyone who can help me figure this out. I think I've been trying to long and I'm missing the obvious.

---

### Post by mr.f on 2006-08-11
> **Conq said:**
> Yes, It's one of the previous posts. Basically what you do is make a
symbolic link from gmplayer to mplayer32 like this:
[CODE]
sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer
[CODE]

Then you can use gmplayer to get a graphical frontend. Maybe I should make
it a part of the package? The problem is that the original 64 bit package "owns" that file. Perhaps just I'll just update the howto. Opinions or suggestions anyone?

I tried that but apparently I have no skins. I get the error:

[INDENT][skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).[/INDENT]

Am I missing some packge?

---

### Post by Conq on 2006-08-11
Yes, you need the mplayer-skins package as well

```

sudo apt-get install mplayer-skins

```

---

### Post by mr.f on 2006-08-11
> **Conq said:**
> Yes, you need the mplayer-skins package as well

```

sudo apt-get install mplayer-skins

```

Ah, that easy. Thanks :D

---

### Post by xep007 on 2006-08-12
> **mr.f said:**
> I tried that but apparently I have no skins. I get the error:

[INDENT][skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).[/INDENT]

Am I missing some packge?

1&#12289;sudo mkdir -p /usr/share/mplayer/Skin
2&#12289;get a skins package from [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
3&#12289;tar jxvf Blue-1.6.tar.bz2 (eg Blue skin)
4&#12289;mv Blue-1.6 default
5&#12289;sudo cp -r default /usr/share/mplayer/Skin

---

### Post by azmrb on 2006-08-13
Thanks Conq!  I was able to get this to work.  I had to rename mplayer to mplayer64 and mplayer32 to mplayer in order to see wmv9 video at sites like CNN but it works.  Can't thank you enough.

---

### Post by Triptol on 2006-08-19
If you got problems with libasound.so.2 being unable to load, it is prety easy to fix it.

The package installs the libraries in /usr/lib32. Mplayer32 expects them in /lib32. Two symlinks will fix your problem:
```
ln -s /usr/lib32/libasound.so.2 /lib32/
ln -s /usr/lib32/libasound.so.2.0.0 /lib32/
```

---

### Post by neighborlee on 2006-08-19
> **azmrb said:**
> Thanks Conq!  I was able to get this to work.  I had to rename mplayer to mplayer64 and mplayer32 to mplayer in order to see wmv9 video at sites like CNN but it works.  Can't thank you enough.

This renaming part should be added as I had to do the same thing on my amd64 system.

I can also see cnn.com videos/sound , BUT it takes quite a while to load it all is it doing that for you as well ?

would you mind trying to view the videos at:

EDIT EDIT: I closed firefox , restarted and gamespot videos are working great !!...wow to have 64 bit OS and working videos  ;00

[http://www.gamespot.com](http://www.gamespot.com) , and see if yours stops like mine ?

thx
g.leej(nl)

---

### Post by kiikkuja on 2006-08-21
Been using 64-bit Dapper for sometime and tackling problems one by one. With 
this guide the i didn't have any problems!!! THANK YOU!!

---

### Post by Theja on 2006-08-30
Hi,
This is theja again....
man..I don't know whats the prob...but this is the error I get..
mplayer32: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


what should I do...
can someone clarify me somethings: will this hack play wmv32 coded files stramed from a site....

could someone build a neat package which we could use....

have been uing ubuntu for 6 moths now...and this is the the only thing which makes me switch OSes....

---

### Post by Conq on 2006-08-30
> **Theja said:**
> Hi,
This is theja again....
man..I don't know whats the prob...but this is the error I get..
mplayer32: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


This file is either provided by the 3d driver, or by mesa, in my case
it's xorg-driver-fglrx, since I have a ATI card. You probably would want
to install 3d drivers in your system anyhow, other howto's will explain
how to do this.

As for the other question, yes, you can use this player. It has been discussed in this thread previously, and a package has been made for it as well.

---

### Post by Theja on 2006-09-08
Mine is ATI Mobility Radeon x300 . I have installed the 3rd party drivers... I mean the above package. 

Is it that having both the versions of mplayer (32 and 64) causing a problem?

---

### Post by qinhengsi on 2006-09-15
hi, i installed ubuntu64 yesterday. I have some problems in Wmv9 on AMD64 . 

I followed the instruction in the thread exactly. But when I tried to install mplayer32_1.0pre7-1_amd64.deb package, i said this package is not compatible with the ia32-libs-openoffice.org package. So I removed the ia32-libs-openoffice.org package and installed mplayer32_1.0pre7-1_amd64.deb.

When I finished the rest step and type mplayer32, it said "mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory". 

I found the missing file libaudio.so.2 is in the ia32-libs-openoffice.org package. But when I tried to re-install it, it said it is not compatible with  mplayer32 package. 

oh, how can I do now?
thanks

---

### Post by quordandis on 2006-09-18
I seem to be having a strange situation. I followed the instructions in the beginning of this post, and now when I play a WMV file in mplayer (which doesn't open at all in totem) it plays the sound, but not the video and I get the error "cannot find codec matching selected -vo and video format 0x33564D57"

Any ideas?

thanks,
Q

---

### Post by Conq on 2006-09-19
Theja: Installing both mplayer and mplayer32 is actually recommended, so that is not where your problem lies. The missing lib should have been installed when you installed the drivers for you graphics card.

Qinhengsi: Thats strange, what version of Ubuntu are you using, and specifically, are you using a different repository for openoffice?

Quordanis: are you using "mplayer" or the "mplayer32" binary? To play wmv9, you need to use "mplayer32 <videofile>"

---

### Post by enopepsoo on 2006-09-19
Thanks a lot.  That worked great.

I found that I had to open files from the terminal, but that is fine by me.  Thanks! :KS

---

### Post by moles on 2006-09-20
> **Conq said:**
> Playing back wmv9 files on AMD64 is tricky. On i386 you can use mplayer with the win32 codecs, or the experimental vc-1 codec. However, using AMD64, things get a bit more difficult. It is possible to use the 32bit mplayer package, but it requires that all the libraries that it depends on are also 32bit. Thats why I made a package for you!

Note that wmv9 works without problems on amd64 using mplayer/ffmpeg from cvs, so there is really no need for all the hassle with 32-bit dependencies (unless there are other 32-bit-only codecs you want to play).

---

### Post by fatsheep on 2006-09-20
It didn't work for me, I'm still getting some crap about no codecs in mplayer.  First off, when I got to the section where I had to make a directory here's what I got:

> fatsheep@fatsheep:~$ sudo mkdir /usr/lib/win32
mkdir: cannot create directory `/usr/lib/win32': File exists
fatsheep@fatsheep:~$ sudo cp essential-20060501/* /usr/lib/win32/


I took a look in nautilus and there is a shortcut named "win32" pointed at /usr/lib/codecs.  Is this a problem?

Second off, do I need 32-bit mplayer for this to work?  If so how do I tell if my mplayer is 64-bit or 32-bit?  And how would I install 32-bit mplayer?

---

### Post by SlCKB0Y on 2006-09-22
Any way to get a GUI for this?

---

### Post by Conq on 2006-09-25
moles: Yes, I know, and it's great! Unfortunately, ffmpeg still isn't as good as the win32 dll's as far as I can gather from the ffmpeg lists. However I excpect this to change quickly. Perhaps in the next release? In addition, a 32 bit version is useful for f.ex realplayer and other win32-only codecs.

fatsheep: Could you post your entire output from "mplayer32 <somewmv9>" ?

SICKBOY: This has been discussed previously, look back in the thread history and you will find your answer there.

---

### Post by fatsheep on 2006-09-25
Nevermind I got it working.  Thanks for the How To, would have been lost without it. :)

---

### Post by mathieujohnson on 2006-10-02
Hi,
Installed Xubuntu Dapper for 64bit.
Tried this howto to get wmv9 files to load on mplayer but get this message while trying
mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

I followed every step carefully, actually tried it twice (by reinstalling xubuntu completly!)

edit:got it working, needed the ia32-libs-openoffice.org (11.0.1) I guess.
maby adding it to the list would be good, that way, even if you don't have openoffice installed you can still get it working! though thanx for the how to, this seems like its working pretty good!

---

### Post by Conq on 2006-10-02
Yes, I seem to have missed that one. I'm adding it to the howto now.

---

### Post by Tolchi on 2006-10-02
i got this msg

mplayer: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory

how i can fix this?

i have installed all packages mentioned in this howto

but still get this msg....

---

### Post by Conq on 2006-10-02
> **Tolchi said:**
> i got this msg

mplayer: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory


You need to install ia32-libs-openoffice.org.
```

sudo apt-get install ia32-libs-openoffice.org

```

---

### Post by Tolchi on 2006-10-02
i did install that packages


however the package just installed libgnutls.so.12 not libgnutls.so.13

---

### Post by Tolchi on 2006-10-02
> **Tolchi said:**
> i did install that packages


however the package just installed libgnutls.so.12 not libgnutls.so.13

dpkg -S libgnutls.so.12
libgnutls12: /usr/lib/libgnutls.so.12.3.8
libgnutls12: /usr/lib/libgnutls.so.12
ia32-libs-openoffice.org: /usr/lib32/libgnutls.so.12
ia32-libs-openoffice.org: /usr/lib32/libgnutls.so.12.3.8

---

### Post by Conq on 2006-10-02
This is a bit strange. The package doesn't depende on gnutls.so.13, but gnutls.so.12. Do you have anything installed that might cause this? It seems that on my system, it's libldap that brings this dependency. Have you upgraded libldap lately?

---

### Post by Tolchi on 2006-10-02
> **Conq said:**
> This is a bit strange. The package doesn't depende on gnutls.so.13, but gnutls.so.12. Do you have anything installed that might cause this? It seems that on my system, it's libldap that brings this dependency. Have you upgraded libldap lately?

as far as i know, i didn't install or upgrade libldap package lately....

---

### Post by holy_bazooka on 2006-10-03
hi.
i am running edgy.
i tried to install mplayer32 but it gave the following error:

```
(Reading database ... 118205 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```

so i backed up that file (lilzo) and after taking the package from /tmp/ did a force-overwrite.

now it gives the error :

```

mplayer32: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory
```

so then i uninstall ia32-libs-openoffice and reinstall mplayer32, it gives this error:

```

mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

```

so uninstalled mplayer32 and reinstalled ia32-libs-openoffice.org
my question is whats going on here?

==>also posted this on simple64 thread

---

### Post by Conq on 2006-10-04
This package was never meant for Edgy. When it is released I will probably make a new package. Edgy has newer libraries, and some of the libraries I have packaged with the mplayer32 binary is now in other packages as well.

---

### Post by coosa on 2006-10-14
I have followed all those steps until the end of "mencoder", but how can i run then the mplayer?

---

### Post by Conq on 2006-10-17
Hust type "mplayer32 <somevideo>" into a console, or if you prefer the gui (and have followed the appropriate steps), then you can either type "gmplayer" or press the corresponding icon in the menu.

---

### Post by sYs^ on 2006-10-20
> **holy_bazooka said:**
> hi.
i am running edgy.
i tried to install mplayer32 but it gave the following error:

```
(Reading database ... 118205 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```so i backed up that file (lilzo) and after taking the package from /tmp/ did a force-overwrite.

now it gives the error :

```

mplayer32: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory
```so then i uninstall ia32-libs-openoffice and reinstall mplayer32, it gives this error:

```

mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

```so uninstalled mplayer32 and reinstalled ia32-libs-openoffice.org
my question is whats going on here?

==>also posted this on simple64 thread

Same problem, really annoying, any ideas?

---

### Post by Conq on 2006-10-20
Simple - It doesn't work on Edgy. I'll make a new package when it is officially released. 

Long answer: Get the dapper openoffice-lib-package and extract the 32 bit libraries from that one, and use them instead. If you don't know what I'm talking about, just wait the until the official release =)

---

### Post by superm1 on 2006-10-20
Conq, have you assembled a debian source package for this?

If not, were you planning on assembling one and submitting it to universe?

---

### Post by Conq on 2006-10-20
No, sorry, I might though, but, wmv9 works in svn ffmpeg, so it might not be needed in the future =). Although this way works for realplayer and such as well. We'll see =)

---

### Post by superm1 on 2006-10-20
> **Conq said:**
> No, sorry, I might though, but, wmv9 works in svn ffmpeg, so it might not be needed in the future =). Although this way works for realplayer and such as well. We'll see =)

Conq, 
WMV9 in ffmpeg svn sounds very sexy to me.  Something i'm looking forward to the day that comes.   I haven't looked very closely at how you do everything in regard to assembling this package.  Depending on how soon wmv9 hits ffmpeg and thus mplayer and mythtv and all the apps using ffmpeg, I might do a deb for this in universe for Feisty.

---

### Post by sYs^ on 2006-10-21
> **Conq said:**
> Simple - It doesn't work on Edgy. I'll make a new package when it is officially released. 

Long answer: Get the dapper openoffice-lib-package and extract the 32 bit libraries from that one, and use them instead. If you don't know what I'm talking about, just wait the until the official release =)

You mean this package:
[http://packages.ubuntu.com/dapper/libs/ia32-libs-openoffice.org](http://packages.ubuntu.com/dapper/libs/ia32-libs-openoffice.org)
?

---

### Post by Conq on 2006-10-21
Yes, exactly, extract the ones you are missing. Although you might need to extract other files from other packages as well. Good luck to you =)

---

### Post by alesdoc on 2006-10-23
> Originally Posted by sYs^
You mean this package:[http://packages.ubuntu.com/dapper/li...openoffice.org?](http://packages.ubuntu.com/dapper/li...openoffice.org?)

Have you tried to get it working?

---

### Post by Conq on 2006-10-23
No, but I'm very sure it will work. Either way, when Edgy is released, I will make a new one, and it is due this week, so just be patient.

---

### Post by sYs^ on 2006-10-23
I think, I'll wait for that :p

---

### Post by jaboua on 2006-10-23
Thanks a lot, exactly what I was looking for.

---

### Post by claud10 on 2006-10-26
The last VLC in Edgy plays WMV9 natively. Tested today when installing it with apt-get :)

---

### Post by superm1 on 2006-10-26
Yup, VLC 0.8.6 is pulled from SVN (since it's not officially released yet).  If we get a nice debian package of mplayer 1.0rc now (it also has the FFMPEG wmv9 support) , we won't even need mplayer32 :)

---

### Post by claud10 on 2006-10-26
Installed Mplayer 1.0rc1 from source and WMV9 works! :)

---

### Post by Conq on 2006-10-27
Yep, it works wonders =)

Although, now the problem becomes realmedia files =(, I'd still like to
play these with mplayer as well.

---

### Post by FedeXX on 2006-11-06
Hello! I've installed that ia32blabla package and forced its version, and now mplayer32 works pretty good... BUT... In firefox32, with the mplayer32 plugin, i still can't see wmv9 :| Why? I'm sure that there's no more mplayer64 plugin, so firefox it's using the 32 bit one. If I download the same video and open it with mplayer32 it works fine, of course. Any ideas about that?

EDIT:

Ups, sorry... i've solved by myself! :D The mplayer plugin calls "mplayer" binary, not the gmplayer link (wich was replaced by me to point to mplayer32). So, the right way is keep gmplayer pointing to "mplayer", rename mplayer as mplayer64 and mplayer 32 as mplayer.

Now I can watch some wmv9 videos while waiting for a perfect 64-bit solution B)

---

### Post by Tyl3r on 2006-11-06
I installed all the ia32 stuff and the mplayer32 package, but when I try to launch it I get this error:
```
tyler@ubuntu:~$ mplayer32
mplayer32: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory
```
Btw libgnu-tls13 is installed. I also tried to reinstall the whole ia32 packages, but mplayer keeps failing ](*,)

---

### Post by ayurchen on 2006-11-06
> **FedeXX said:**
> Hello! I've installed that ia32blabla package and forced its version, and now mplayer32 works pretty good... 

Could you please share with us what was the exact package name as the one that is referenced in this thread only has libgnutls.12, not libgnutls.13 which mplayer32 requires on my machine.

---

### Post by FedeXX on 2006-11-07
> **ayurchen said:**
> Could you please share with us what was the exact package name as the one that is referenced in this thread only has libgnutls.12, not libgnutls.13 which mplayer32 requires on my machine.

...i've used the one linked at page 12...

[http://packages.ubuntu.com/dapper/libs/ia32-libs-openoffice.org](http://packages.ubuntu.com/dapper/libs/ia32-libs-openoffice.org)

It's a good idea to force its version in synaptic (package, force version or lock version) to the one installed, to make it not to be overwritten by the newest version (yes, yours) wich has not the right libgnutls.

---

### Post by peacekpr on 2006-12-11
Qualifying Info:  Ubuntu Edgy 6.10 for AMD64

I attempted to install "mplayer32_1.0pre7-1_amd64.deb" to no avail.  I attempted to preempt the problem through backing files up in a manner such that the installer would not "see" the files.  This did not work.  I am rather reluctant at this point to force the package to install.

Conq, have you come up with a new package to correct the following problem?  I read in an earlier post that you had plans to do so.  Just following up.  Thanks in advance.

```
peacekpr@peacekpr-laptop:~/Downloads$ sudo dpkg -i mplayer32_1.0pre7-1_amd64.deb 
(Reading database ... 106373 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```

---

### Post by adearaujo on 2006-12-12
I followed the steps in page 1 and they worked fine for me first try.
THANK YOU. I have one question though. I am running firefox32 from the wiki tutorial with java and flash, They run perfect. I cant watch wmv within the browser, is there a way to make these plugins I just installed in this tutorial to make it work on firefox32? Thank you in advance

---

### Post by davidgro on 2006-12-14
I just installed mplayer 1.0rc1 on my 64-bit system and sure enough the WMV3 *Video* plays just fine, but in some of my wmvs the Audio does not: it is codec 0x162 which is only supported by a win32codec.  Same with VLC.  So there is still a need for mplayer32.  

Somebody please release a new version for Edgy (with gmplayer32 as well if possible) Or at least instructions for cross-compiling it myself

---

### Post by donizildo on 2006-12-14
I have the same problem.
Is there any alternative to solve this problem yet ?
I've tried a lot of things, but none of them have worked ...

> **peacekpr said:**
> Qualifying Info:  Ubuntu Edgy 6.10 for AMD64

I attempted to install "mplayer32_1.0pre7-1_amd64.deb" to no avail.  I attempted to preempt the problem through backing files up in a manner such that the installer would not "see" the files.  This did not work.  I am rather reluctant at this point to force the package to install.

Conq, have you come up with a new package to correct the following problem?  I read in an earlier post that you had plans to do so.  Just following up.  Thanks in advance.

```
peacekpr@peacekpr-laptop:~/Downloads$ sudo dpkg -i mplayer32_1.0pre7-1_amd64.deb 
(Reading database ... 106373 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```

---

### Post by William Pickett on 2006-12-16
Hello- I am a new Linux user and still do not "get it"- when I unpacked the essential file it said save it to temp file- didn't allow me to create a win32 dir- (from package mgr)- so 4. Fetch the Win32 codecs from: [http://www.people.virginia.edu/~drf8...060501.tar.bz2](http://www.people.virginia.edu/~drf8...060501.tar.bz2)
5. Unpack it and install to /usr/lib/win32.
Code:

tar -jxvf essential-20060501.tar.bz2 sudo mkdir /usr/lib/win32 sudo cp essential-20060501/* /usr/lib/win32/

Since I was not able to use this sequence to get it going- what do I do now? apparently when I unpacked it- saved to tmp- that was unecessary- but then it didnt-(It being the system) see the file on my desktop unpacked- suggestions- and then- how do I set M-Player- not totem mplayer- as the preferred 1st item to go to when I play a vid file?
Thanks Ubuntu folks (amd Ath 64 w/generic -amd64 running.) William....

---

### Post by Zargoon on 2007-01-05
It didn't work for me..... I get this wierd error when I try to open the file:

Error opening/initializing the selected video_out (-vo) device.

Any ideas?

---

### Post by Zargoon on 2007-01-05
Never mind, I get this error everytime I try to use Mplayer.  Any ideas?

---

### Post by amp_man on 2007-01-11
I'm getting the same error (liblzo), a new package would be awesome :D Also, as far as the video output error goes (for one of the users who posted just before me), are you running beryl or compiz? If so, change mplayer to opengl output, that worked for me. xv might work also, dunno.

---

### Post by henriquemaia on 2007-01-15
I'm on Edgy amd64 and I get this error when running it:

mplayer32: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory

This library is installed, I have checked that.

---

### Post by pickarooney on 2007-01-18
Is everybody still stuck trying to install 32-bit mplayer on 64 bit Edgy then?
No workarounds for streaming video or playing WMV or RM(vb) files?

---

### Post by superm1 on 2007-01-18
> **pickarooney said:**
> Is everybody still stuck trying to install 32-bit mplayer on 64 bit Edgy then?
No workarounds for streaming video or playing WMV or RM(vb) files?
VLC 0.8.6 is able to do wmv, and a snapshot from a month or two before release is included in edgy.  This should be able to handle some of the streaming content and such.

---

### Post by henriquemaia on 2007-01-19
> **superm1 said:**
> VLC 0.8.6 is able to do wmv, and a snapshot from a month or two before release is included in edgy.  This should be able to handle some of the streaming content and such.

You're right. VLC works indeed. Thanks for pointing this out.

---

### Post by mbradlcu on 2007-01-23
try and run 'mplayer -vo x11' if that works you can edit /etc/mplayer/mplayer.conf,,, I commented (in) vo=xv and it resolved the problem for me.


> **futureman said:**
> I cannot get this to work, no video will play for me, here's an example of what i get.

[HTML]MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/mike/video.wmv.
ASF file format detected.
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: FileCabi.net - Where you Provide the Entainment!
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
tdfxfb: This driver is only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5
Couldn't open /dev/3dfx
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 320 x 240 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 320 x 240 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Video: no video
Starting playback...
A: 110.8 (01:50.8) of 113.0 (01:53.0)  0.3%

Exiting... (End of file)
[/HTML]

Any ideas?

---

### Post by CanadianMan on 2007-01-26
Has anyone found a sure way to install w32codecs for mplayer on Edgy.  I realize VLC is working but i would like to use mplayer.

Thanks.

---

### Post by ryan76 on 2007-01-26
Yep, I'm stuck too:
```

ryan@ubuntu:~/packages/mplayer$ sudo dpkg -i mplayer32_1.0pre7-1_amd64.deb
(Reading database ... 111995 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```

What can we do about this? I can't watch .mov files.

---

### Post by CanadianMan on 2007-01-27
deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) edgy misc multimedia 

Thank you Superm1 for giving me this link.  I got my video working nicely.

---

### Post by Conq on 2007-01-31
I have now (finally!) made a package that works for Edgy. 
It can be found here: [http://folk.ntnu.no/grannas/debs/mplayer32_20070130-1_amd64.deb]("http://folk.ntnu.no/grannas/debs/mplayer32_20070130-1_amd64.deb")

Please try it out and see if it works for you! I have also updated the howto on the first page.

In addition, this package includes mencoder32 by popular demand.

I look forward to hearing about your experiences.

---

### Post by kuja on 2007-01-31
Awesome, it installed for me flawlessly. Thanks Conq!

---

### Post by gnudoc on 2007-02-17
First off, thanks for putting in the work, Conq. It's much appreciated. =D> 

Are you planning on doing a feisty package? If you are, I thought you might be interested to know that when I tried installing the edgy package on a freshly installed up-to-date 64bit feisty, it threw up the following error:

```
mplayer32: error while loading shared libraries: liblzo.so.1: cannot open shared object file: No such file or directory
```

This was confirmed by a friend with a similar installation of feisty.

also, earlier in the process, I found that there was no ia32-libs-openoffice.org in the feisty repo's.

Keep up the great work!

---

### Post by kuja on 2007-02-18
> **gnudoc said:**
> First off, thanks for putting in the work, Conq. It's much appreciated. =D> 

Are you planning on doing a feisty package? If you are, I thought you might be interested to know that when I tried installing the edgy package on a freshly installed up-to-date 64bit feisty, it threw up the following error:

```
mplayer32: error while loading shared libraries: liblzo.so.1: cannot open shared object file: No such file or directory
```

This was confirmed by a friend with a similar installation of feisty.

also, earlier in the process, I found that there was no ia32-libs-openoffice.org in the feisty repo's.

Keep up the great work!
Well, you found the problem all by yourself ... that file is included in ia32-libs-openoffice.org .... that's one of several libs needed by other programs that got grouped into that package (the only other one I can think of offhand is libaudio). Bah.

---

### Post by gnudoc on 2007-02-18
> that's one of several libs needed by other programs that got grouped into that package (the only other one I can think of offhand is libaudio). Bah.

Bah indeed. perhaps it's still to be added to the repository?

---

### Post by Conq on 2007-02-19
You could problably just take the deb from Edgy, extract the contents and copy the file from there:
(something like this:
```

mkdir tmp
cd tmp
wget http://no.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs-openoffice.org/ia32-libs-openoffice.org_17_amd64.deb
dpkg -x ia32-libs-openoffice.org_17_amd64.deb .

```

and then simply copy the files you need from usr/lib32/ to /usr/lib32 .

As for your second question; if I'm going to make one for Feisty. I will make one if it makes sense, right now it seems like the 64bit version of mplayer in svn can read 64 bit windows dll's, so there won't be any need.

---

### Post by Egils on 2007-04-07
I was searching desperately for some method of getting Real Media/Real Video rmvb files to play in AMD64 fiesty (other than installing realplayer), and decided to test the method suggested above for getting mplayer32 to work. It's tedious to copy the files over manually from ia32-libs-openoffice.org deb to the appropriate directories but it works, and now mplayer32 is functional [-o<  If only these codecs would be released for 64-bit mplayer as well...

---

### Post by muncrief on 2007-04-09
Here's what you need to do to get the needed ia32-libs-openoffice.org libraries so mplayer32 will run under Feisty. Thanks to everyone from above for the info. I've just added the exact files needed.



mkdir tmp
cd tmp
wget [http://no.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs-openoffice.org/ia32-libs-openoffice.org_17_amd64.deb](http://no.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs-openoffice.org/ia32-libs-openoffice.org_17_amd64.deb)
dpkg -x ia32-libs-openoffice.org_17_amd64.deb .

sudo cp usr/lib32/liblzo.so.1* /usr/lib32/
sudo cp usr/lib32/libgssapi_krb5.so.2* /usr/lib32
sudo cp usr/lib32/libkrb5.so.3* /usr/lib32
sudo cp usr/lib32/libk5crypto.so.3* /usr/lib32
sudo cp usr/lib32/libkrb5support.so.0* /usr/lib32
sudo cp usr/lib32/libldap_r.so.2* /usr/lib32
sudo cp usr/lib32/liblber.so.2* /usr/lib32
sudo cp usr/lib32/libsasl2.so.2* /usr/lib32
sudo cp usr/lib32/libtasn1.so.3* /usr/lib32
sudo cp usr/lib32/libgcrypt.so.11* /usr/lib32
sudo cp usr/lib32/libgpg-error.so.0* /usr/lib32
sudo cp lib32/libcom_err.so.2* /lib32

I hope I got it right ... :)

---

### Post by thyazide on 2007-06-05
ive managed to get mplayer32 installed.... i think ive installed the codec's correctly... i attempted to copy what i need into the directory's for all of the openoffice libs... and i get errors when attempting to start any media in the 32bit mplayer, and its still broken. im starting to regret moving to feisty, i had all of this working under 6.10 and its breaking my brain trying to get it running now, the player has no problems recognizing the video codec, but errors on audio, and in most cases crashes out just very annoyed at this point, any suggestions?

---

### Post by DancingSun on 2007-06-05
> **thyazide said:**
> ive managed to get mplayer32 installed.... i think ive installed the codec's correctly... i attempted to copy what i need into the directory's for all of the openoffice libs... and i get errors when attempting to start any media in the 32bit mplayer, and its still broken. im starting to regret moving to feisty, i had all of this working under 6.10 and its breaking my brain trying to get it running now, the player has no problems recognizing the video codec, but errors on audio, and in most cases crashes out just very annoyed at this point, any suggestions?

WMV9 works out-of-the-box after upgrading to Feisty.  The 64-bit MPlayer and Totem-gstreamer both play WMV9 files smoothly in most cases.  I'd gather this is because the open source WM9 codec has matured with this release.  Try installing the gstreamer plugins for WMV9 playback in Totem.

---

