---
title: "HowTo: MPlayer1.0pre7try2 with *fully working* gtk2 gui patch"
date: 2005-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Arktis on 2005-10-29
Firstly, this howto is inspired by [this thread]("http://www.ubuntuforums.org/showthread.php?t=78037"), which now links to bored2k's prebuilt cvs .deb, since cvs has gtk2 gui support already.

What I wanted was to have the latest stable release of MPlayer, 1.0pre7try2, with the same support as was originally given by that howto. However, the link to the patch in that thread no longer works, and furthermore has a problem with not displaying the right-click menu in gmplayer.

So, I scoured, and kept at it, until I found another patch for 1.0pre7 which does not have this problem.  [COLOR=blue]So, if you want the fully working gtk gui support for stable mplayer, this howto is for you.[/COLOR]

===========

**Step 1.)**  Download the mplayer1.0pre7try2 source from [the mplayer website]("http://www.mplayerhq.hu/homepage/design7/dload.html"), and extract it somewhere in your home directory.

**Step 2.)**  Next, go [here]("https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/") and right click the mplayer-1.0_pre7-gtk2.patch link and choose "save as". Browse to the folder you extracted the mplayer source code and save it there.

**Step 3.)** Open a terminal and cd into the directory where you extracted the mplayer source and saved the patch. Issue the following command:```
patch -p1 < mplayer-1.0_pre7-gtk2.patch
``` 
 ===========

That's it. Now all you need to do is compile and install mplayer. I won't go through that in this howto because there is plenty of information on the forums here on how to do that. Just make sure that when you run configure, that you use the **--enable-gui** parameter.

Enjoy! :smile:

**Note:** I've also attatched the patch file in case the link goes down. If you use that when following the howto, just rename it from a .txt to .patch after saving it.

---

### Post by Promethe on 2005-10-29
Tested and aproved :]
May we know what is the MPlayer theme on this screenshot?

---

### Post by Arktis on 2005-10-29
Certainly. The gui theme in the screenshot is called "sessene" and is availible from the mplayer website's skin download section.

It is my favorite, but has one annoyance factor. The close button is VERY small and hard to hit, but you don't have to use it. Obvious alternatives are pressing 'q' to quit, or use the close button on the play window, or use 'exit' from the right-click menu.

---

### Post by beeldings on 2005-10-30
Ok, I followed your instructions and when I tried to launch MPlayer with the "gmplayer" command, I would get:

```

spikentm@ubuntu:~$ gmplayer
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Intel Celeron Covington/Pentium II Deschutes,Tonga/Pentium II Xeon (Family: 6, Stepping: 2)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX


vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.


```

And when I attempted to add "echo 1024":

```

spikentm@ubuntu:~$ sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq
bash: /proc/sys/dev/rtc/max-user-freq: Permission denied


```

So, what did I do wrong and how I can correct this problem, without re-compiling MPlayer? I would really like to use the GTK2-enabled MPlayer over the pre-built versions from the repositories.

---

### Post by Technoviking on 2005-10-30
[QUOTE=beeldings]
And when I attempted to add "echo 1024":

```

spikentm@ubuntu:~$ sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq
bash: /proc/sys/dev/rtc/max-user-freq: Permission denied


```
This can not be ran via sudo, you must su and run it as root.

Mike

---

### Post by GTvulse on 2005-10-30
[QUOTE=beeldings]

And when I attempted to add "echo 1024":

```

spikentm@ubuntu:~$ sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq
bash: /proc/sys/dev/rtc/max-user-freq: Permission denied


```

So, what did I do wrong and how I can correct this problem, without re-compiling MPlayer? I would really like to use the GTK2-enabled MPlayer over the pre-built versions from the repositories.[/QUOTE]

Do this with your favorite editor, mine is vim:

```

sudo <your_editor> /etc/sysctl.conf

```

Add the following line at the end of the file:

```

sys/dev/rtc/max-user-freq=1024

```

Then type:

```

sudo /etc/init.d/sysctl restart

```

And you're done. This same setting helps wonders with virtualizing software such as QEMU.

---

### Post by Technoviking on 2005-10-30
[QUOTE=dradul]

```

sudo /etc/init.d/sysctl restart

```
[/QUOTE]
I do not have an /etc/init.d/sysctl file, but the following did work for me.

```
 sudo gedit /etc/sysctl.conf
```
Add the following
```
dev.rtc.max-user-freq=1024
```
and save the file

Then reboot or
```
sudo /etc/init.d/procps.sh restart
```
Mike

---

### Post by i3dmaster on 2005-10-30
[QUOTE=Mike Basinger]I do not have an /etc/init.d/sysctl file, but the following did work for me.

```
 sudo gedit /etc/sysctl.conf
```
Add the following
```
dev.rtc.max-user-freq=1024
```
and save the file

Then reboot or
```
sudo /etc/init.d/procps.sh restart
```
Mike[/QUOTE]
```
sysctl -w dev.rtc.max-user-freq=1024
``` no need reboot or anything

---

### Post by beeldings on 2005-10-30
I followed everyone's advice and was able to correct the problem, however when I run the gmplayer command or select MPlayer from the Applications > Sound & Video menu, it appears as if the program is loaded but I am unable to see a GUI. I believe that I might have incorrectly installed the two skins I downloaded. Is there anything else I can do to correct this problem?

---

### Post by GTvulse on 2005-10-30
[QUOTE=Mike Basinger]I do not have an /etc/init.d/sysctl file, but the following did work for me.

```
 sudo gedit /etc/sysctl.conf
```
Add the following
```
dev.rtc.max-user-freq=1024
```
and save the file

Then reboot or
```
sudo /etc/init.d/procps.sh restart
```
Mike[/QUOTE]

Sorry about that. In fact that's the syntax for NetBSD (the init.d/rc.d script, that is), been working on that one more than linux lately. :-) Do notice that for the value to take up, under Linux, you can't do a "restart", but a "reload".

---

### Post by beeldings on 2005-10-30
My problem with the GUI not being displayed turned out to be a simple naming problem with the skin. I have MPlayer up and running, however it appears to not be using GTK2. Does this mean I will have to compile MPlayer again?

---

### Post by Arktis on 2005-10-31
If you patched it properly as per the instructions before compile, your mplayer should look like the screenshot (not the skin, of course).

---

### Post by eraclito on 2005-10-31
it works great, but what about the fonts?

i had istalled .deb pakage, but it seem to not work...

any help?

eraclito

[edit]
sorry  for the wrong place...

---

### Post by Arktis on 2005-10-31
[http://www.ubuntuforums.org/showthread.php?t=66863]("http://www.ubuntuforums.org/showthread.php?t=66863")

*ahem*

Check out the excellent documentation on MPlayer's website.

**Edit:** Since their docs appear to be down, here's a [mirror]("http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/#install_osd") of sorts.

---

### Post by Arktis on 2005-11-01
[quote=beeldings]My problem with the GUI not being displayed turned out to be a simple naming problem with the skin. I have MPlayer up and running, however it appears to not be using GTK2. Does this mean I will have to compile MPlayer again?[/quote]

Hmm, after further thought, try installing the package libgtk2.0-dev, remove libgtk1.2-dev, and repatch from a freshly extracted source and recompile.

---

### Post by vendetta red on 2005-11-09
I followed the advice here, but I am still getting this:

```
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[skin] file ( /usr/local/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

```

On a side note should I have uninstalled the original mplayer before this process?

---

### Post by GTvulse on 2005-11-09
[QUOTE=vendetta red]I followed the advice here, but I am still getting this:

```
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[skin] file ( /usr/local/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

```

On a side note should I have uninstalled the original mplayer before this process?[/QUOTE]
Nope, just download the default skin and move it to that location.

---

### Post by vendetta red on 2005-11-09
woops, decided to go ahead and try removing mplayer and then saw your post. It was probably for the best though because I just saw somehting I evidentally missed last time.

```
Checking for GTK version ...
Error: The GUI requires GTK devel packages (which were not found).
```

I searched Synaptic for the gtk-devel package, but didn't find anything. I mean ./configure is asking for gtk-devel, so where would I find this?

EDIT: Found the package libgtk2.0-dev, but Synaptic says it's installed already...

EDIT2: I just deleted the source tree and started again, the configure went fine, compiling now...

EDIT3: When I run gmplayer from console, I get nothing, hitting ctrl+c yields:

```
MPlayer interrupted by signal 2 in module: unknown
```

Any ideas?

FINAL EDIT: Found another HOWTO that worked perfect first time through: [http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100](http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100)

---

### Post by Arktis on 2005-11-14
[QUOTE=vendetta red]On a side note should I have uninstalled the original mplayer before this process?[/quote]

YES.

[QUOTE=vendetta red]EDIT3: When I run gmplayer from console, I get nothing, hitting ctrl+c yields:

FINAL EDIT: Found another HOWTO that worked perfect first time through: [http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100](http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100)[/QUOTE]

Cool.  Glad you got things sorted.

---

### Post by rune on 2005-11-23
I think the patch has been either incorporated into mplayer now, or it's not needed. My mplayer was build using only apt-get packages and cvs mplayer source, and it has the nice menus.

I'd advise people to try build cvs mplayer with debian/rules first and see if it looks ok.

---

### Post by Arktis on 2005-11-23
Yes, cvs has gtk2 support already.  This howto is if you want gtk2 support in the *stable* release.  Once another stable build come out of cvs, this howto is no longer necessary.

---

### Post by j0rd on 2006-02-11
Ubuntu uses gcc4 by default in breezy.  mplayer-1.0_pre7 wants a gcc3.x version to compile.  Here is a gentoo patch for gcc4 if you don't want to install gcc3.

[http://dev.gentoo.org/~halcy0n/mplayer-1.0_pre7-gcc4.patch](http://dev.gentoo.org/~halcy0n/mplayer-1.0_pre7-gcc4.patch)

---

### Post by Arktis on 2006-02-15
Thanks, j0rd, but your patch just doesn't seem to work.  I actually found three different patches for this same issue and they all fail.  Maybe I'm doing something wrong.

---

### Post by Mishal on 2006-02-16
[https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/](https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/)

This does not work.

And can I do this howto without reinstalling MPlayer? I just don't want to go through compiling. Something WILL GO WRONG. I positively HATE compiling. :(

---

### Post by j0rd on 2006-02-16
[QUOTE=Mishal][https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/](https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/)

This does not work.

And can I do this howto without reinstalling MPlayer? I just don't want to go through compiling. Something WILL GO WRONG. I positively HATE compiling. :([/QUOTE]
Just don't do a `make install` and you'll have the binaries in the src/ folder usually.  Most programs will work with out a make install.

---

### Post by Whoopie on 2006-02-17
Hi,

do you also have a skewed icon in the left corner of the window bar?

There should be shown the icon /usr/share/pixelmaps/mplayer-desktop.xpm.

Attached is a screenshot with the skewed icon.

Regards,
Whoopie

---

### Post by Arktis on 2006-02-19
Yeah, but apparently it only happens with gmplayer (gui version).  I have yet to see this bug when running regular mplayer.  I have also seen this bug in the cvs version that is in dapper's extra repos.

---

### Post by Arktis on 2006-02-19
[QUOTE=Mishal][https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/](https://svn.uludag.org.tr/paketler/trunk/media-video/mplayer/files/)

This does not work.

And can I do this howto without reinstalling MPlayer? I just don't want to go through compiling. Something WILL GO WRONG. I positively HATE compiling. :([/QUOTE]
I anticipated the link to the patch going down and so there is a copy of it already attatched to the first post in this thread.  Next time, read please read a person's entire howto before asking questions.  ;)

There's no way to avoid compiling if you want gtk2 support in stable mplayer, unless someone else compiles it for you.  I don't know of any repos or sites that have prebuilt patched gtk2 stable mplayer debs.  I would put one up except that I have no website yet because I'm still waiting for my hosting application to be processed.  It's been a week already since I submitted it too...

---

### Post by magomimmo on 2006-04-13
Hi all, I tried to follow the instructions but:
[COLOR="Lime"]root@*****/MPlayer-1.0pre7try2$ patch -p1 < mplayer-1.0_pre7-gtk2.patch
patching file configure
Hunk #1 FAILED at 150.
Hunk #2 FAILED at 1374.

but I have the same error:
[COLOR="Red"][/COLOR]Error: the GUI requires GTK+ (which was not found)

---

