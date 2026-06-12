---
title: "HOWTO: Open videos from rar files &quot;without&quot; packing them up"
date: 2007-09-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Meroigo on 2007-09-22
Maybe a stupid thread title, but nevermind.

If you download your movies and tv series only as scene releases, then you'll have to extract the release's video file from its multiple rar files. That can take some time... Not a horrible long time. You can live with it... But I learned a cool thing and thought I could share it just because I have nothing better to do.

A friend (Thank you alias Rövhög) gave me a cool command to "open a rar file" in a video player making the video start playing directly. No need to extract the video before it starts playing.

So this is only for you people who doesn't mind using the terminal and know how to navigate in your file system using commands...

This was tested on Ubuntu 7.04 Feisty Fawn, 32-bit. Use this HOWTO on your own risk.

You'll need the packages "unrar" and "vlc" (or "mplayer" or any other video player you may prefer).

Write this in a terminal if you haven't got the required packages:
```
sudo apt-get install unrar vlc
```

The command to use:
```
unrar p -inul /example/path/to/Some.Scene.Release/some.sr.r00 | vlc -
```

*What the command does:*
unrar = starts unrar
p = outputs the extraction data of the file
-inul = disables error messages
/example/path/to/Some.Scene.Release/some.sr.r00 = path to one of the scene release's rar files
| vlc - = pipes the output of the extraction into vlc that starts to play the output, and therefore plays the video file that is within the rar files. Don't forget the ending "-", or it won't work. You can use another video player if you want, just replace "vlc" with what you want. I have only tested this with vlc and mplayer.

One bad thing with this trick is that you can only pause and play the file, but not rewind or fast forward.


I only write "rarvideo somerarfile.r00". How to do that:

Open ~/.bashrc in a text edior, using for example this command:
```
gedit ~/.bashrc
```

Paste this somewhere in the file, I did it in the top of the file:
```
PATH=$PATH:$HOME/bin
```
Close and save the file.
(This makes your Bash looking in the ~/bin folder for executeable files.)

Make a folder in your home folder called "bin":
```
mkdir ~/bin
```

Make and open in a text editor a file called "rarvideo" in ~/bin:
```
gedit ~/bin/rarvideo
```

and paste this into it:
```
#! /bin/sh
unrar p -inul $1 | vlc -
```
Close and save the file.

Make the file executeable with this command:
```
chmod u+x ~/bin/rarvideo
```

You probably have to restart Bash, so in the terminal, type:
```
bash
```

...and now you can use the command "rarvideo somerarfile.r00"! :)


I hope someone out there likes it. =D

---

### Post by Drittponken on 2008-01-30
The making of the command didn't work for me :/ i followed you steps...

---

### Post by 565Customz on 2008-01-31
did you copy and paste?

---

### Post by Gfy on 2008-08-09
You could also use Dziobas Rar Player with Wine.
Download it here:
[http://ds6.ovh.org/drp.html](http://ds6.ovh.org/drp.html)

Choose Move -> PanScren -> 100% (OpenGL)
to make it possible to view it fullscreen.

And disable your screensaver.

---

