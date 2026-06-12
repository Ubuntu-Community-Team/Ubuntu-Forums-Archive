---
title: "[SOLVED] VLC crashes when i open .avi"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by wrtpeeps on 2008-07-11
I am trying to play an avi file in vlc. It opens for a second and then just closes.

I have the xvid codec installed. Anyone any ideas what else it could be?

---

### Post by mriedel on 2008-07-11
Had that problem on hardy a few weeks back. Have you updated recently?

---

### Post by ChameleonDave on 2008-07-11
> **wrtpeeps said:**
> I am trying to play an avi file in vlc. It opens for a second and then just closes.

I have the xvid codec installed. Anyone any ideas what else it could be?

Make sure you are running the latest version of everything.

Consider enabling the Medibuntu repositories and installing the "non-free-codecs" package.

Then, try running VLC from the terminal.  For example, if you have a file called *LesbianSpankInferno.avi* on your desktop, type "*vlc ~/Desktop/LesbianSpankInferno.avi*".  If it fails, error messages will be spat out onto the terminal.  Paste them here.

---

### Post by wrtpeeps on 2008-07-11
I got this when ran at terminal:

```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.

```

---

### Post by ChameleonDave on 2008-07-11
> **wrtpeeps said:**
> I got this when ran at terminal:

```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.

```

Open up your repo list with **one** of the following commands:

```

sudo nano /etc/apt/sources.list
gksudo gedit /etc/apt/sources.list
kdesudo kwrite /etc/apt/sources.list

```

Add the following line to the file:

```

deb http://packages.medibuntu.org/ hardy free non-free

```

Save and close.

Do the following commands at the terminal:

```

sudo apt-get update && sudo apt-get install libdvdcss2 non-free-codecs

```

---

### Post by wrtpeeps on 2008-07-11
OK, now i get:

```
[00000339] pulse audio output error: Failed to connect to server: Connection refused
[00000339] pulse audio output error: Pulse initialization failed
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 85 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by ChameleonDave on 2008-07-11
> **wrtpeeps said:**
> OK, now i get:

```
[00000339] pulse audio output error: Failed to connect to server: Connection refused
[00000339] pulse audio output error: Pulse initialization failed
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 85 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

OK, that's a totally different problem.

Try playing a different file and/or using a different program.  What happens?

---

### Post by wrtpeeps on 2008-07-11
> **ChameleonDave said:**
> OK, that's a totally different problem.

Try playing a different file and/or using a different program.  What happens?

I tried totem, and got the exact same error

---

### Post by wrtpeeps on 2008-07-11
WHen i tried mplayer, I got a lot of:

X11 error: BadValue (integer parameter out of range for operation)

---

### Post by ChameleonDave on 2008-07-11
> **wrtpeeps said:**
> WHen i tried mplayer, I got a lot of:

X11 error: BadValue (integer parameter out of range for operation)

Log out and log back in again.

Try a different file.

---

### Post by wrtpeeps on 2008-07-11
Thanks it plays now

---

### Post by ChameleonDave on 2008-07-11
> **wrtpeeps said:**
> Thanks it plays now
Great!

When messing around with sound on Linux, the sound server sometimes gets confused.  You can always fix it by logging out.  On Windows you'd probably have to actually reboot after installing new drivers like that.

Perhaps you could use the "Thread Tools" menu to mark this as solved.

---

### Post by avam323 on 2008-07-11
i have erratic problems with vlc as well; sometimes after updates my .mp3 playback will be broken or a video will play, but no sound. removing vlc w/ synaptic, then doing ```
$ sudo apt-get -y install vlc
``` usually fixes the problem. if banshee quits working for whatever reason, that usually fixes that also.

---

### Post by wrtpeeps on 2008-07-11
Done and thanks again!

---

### Post by ChameleonDave on 2008-07-11
> **avam323 said:**
> i have erratic problems with vlc as well; sometimes after updates my .mp3 playback will be broken or a video will play, but no sound. removing vlc w/ synaptic, then doing ```
$ sudo apt-get -y install vlc
``` usually fixes the problem. if banshee quits working for whatever reason, that usually fixes that also.
You don't need to use Synaptic to remove it then come back to the command line to reinstall it.  You can do both from Synaptic, or both from the command line, thus:

```

sudo apt-get install --reinstall **vlc**

```

Or if you wish to remove its configuration files too:

```

sudo apt-get purge **vlc** && sudo apt-get install **vlc**

```

---

### Post by avam323 on 2008-07-11
so purge takes care of the pkg and its dependencies _only_? one time i used autoremove to get rid of rhythmbox and it removed my gnome-desktop (which i thought was an empty metapkg) and i couldn't log in to my desktop after that. i don't really care for synaptic, but i've found it works better for me than the command line. i'll try that next time i need to reinstall something.

---

### Post by ChameleonDave on 2008-07-11
> **avam323 said:**
> so purge takes care of the pkg and its dependencies _only_? one time i used autoremove to get rid of rhythmbox and it removed my gnome-desktop (which i thought was an empty metapkg) and i couldn't log in to my desktop after that. i don't really care for synaptic, but i've found it works better for me than the command line. i'll try that next time i need to reinstall something.
The "purge" thing is the same as "remove', except that it deletes user config files for that package too.  It does not override dependencies, so it will want to uninstall any software that depends on that package.  The subsequent "install" will not automatically restore those deleted packages.  That's why I made sure I didn't put "-y" ("automatically say yes to all questions") in the command.  It will ask you what you want to do.

If you want to force the removal of a package without worrying about dependency issues, you have to go deeper into the system than APT.  The following command will remove VLC, ignoring dependencies:

```

sudo dpkg --force-depends --purge **vlc**

```After running that, you should make sure that you reinstall it, because forcing dependencies can leave the system in a broken state.

---

### Post by chalewa on 2008-07-14
im getting the same error, tried to restart and reinstall vlc, issue persists.


any other ideas?

---

### Post by ChameleonDave on 2008-07-14
> **chalewa said:**
> im getting the same error, tried to restart and reinstall vlc, issue persists.


any other ideas?
And this is with a range of different files, right?

You might just have to report it as a bug on launchpad.

---

### Post by chalewa on 2008-07-15
yea this was the strangest thing. 

it was with a range of different files, across different media players, same basic problem. 

i did some searching, and added a couple of things to my xorg and got it to work. what is weird is that it really just started happening, the only thing that i did to my computer is screw with some samba configuration files, nothing to do with xorg. but it is in fact fixed now. 

for those who have the same problem... (using an ati card with fglrx 8.6)

in the Device Section

```
Option "Textured2D" "On"
Option "TexturedXrender" "On"
```


run 

```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

---

### Post by Robor on 2008-08-21
> **chalewa said:**
> yea this was the strangest thing. 

it was with a range of different files, across different media players, same basic problem. 

i did some searching, and added a couple of things to my xorg and got it to work. what is weird is that it really just started happening, the only thing that i did to my computer is screw with some samba configuration files, nothing to do with xorg. but it is in fact fixed now. 

for those who have the same problem... (using an ati card with fglrx 8.6)

in the Device Section

```
Option "Textured2D" "On"
Option "TexturedXrender" "On"
```


run 

```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

Thanks, chalewa.  That got the movies playing but I have severe flickering with Compiz.  If I 'metacity --replace' the video display normally.  Further searching points at the flickering in Compiz being an ATI driver bug.

---

### Post by chalewa on 2008-08-22
yea flickering with compiz has always been a problem for me. nothing you can really do other than shut down compiz while watching the movie

---

