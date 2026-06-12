---
title: "Play app"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by jronc on 2013-03-03
I typed on the Command line  of terminal: sudo apt-get install play. The loading process started and then stopped saying it could not find play.
I am using Ubuntu 12.10 with all the updates installed. I wanted to use play to play music from the Terminal. How do I secure this app. What repository do I download?
The terminal gave me the actual command line so I was confused as to why it didn't work. :confused:

---

### Post by oldos2er on 2013-03-03
```
sudo apt-get install sox
```

---

### Post by tgalati4 on 2013-03-03
aplay or mocp (sudo apt-get install moc).  I'm not familiar with play.

tgalati4@Mint14-Extensa ~ $ apt-cache policy play
N: Unable to locate package play

D'Oh!  Yes, sox contains the program* play*.

```
sudo apt-get install sox
```

---

### Post by jronc on 2013-03-07
Thank you for the assistance. I entered that at the command line and I am now able to use play. Unfortunately, it only seems to work with ogg. I have tried it with mp3 and m4a and it tells me that it won't work with those file extenders. But, it works great for ogg music files.

---

### Post by oldos2er on 2013-03-07
If you install libsox-fmt-mp3 it should work. ```
sudo apt-get install libsox-fmt-mp3
```

Edit: Or you could use mplayer in CLI too.

---

### Post by jronc on 2013-03-08
I entered the command line you suggested to secure the mp3 but after it read the package list said that the value 'mp3' is invalid for APT::Default - Release as such a release is not 
available in the sources.


Any more Ideas?

Thank you again for your assistance!

---

### Post by oldos2er on 2013-03-08
Try ```
sudo apt-get update && sudo apt-get install libsox-fmt-mp3
``` If there are errors please copy and paste all the terminal output here.

---

### Post by jronc on 2013-03-08
I will give this a shot. However, I tried using mplayer with an tune with an mp3 extension and it worked just fine. However, mplayer would not play the tunes with the m4a extension. Will try it after I update the library and let you know my failure or success.

---

### Post by oldos2er on 2013-03-08
Sounds like you're missing codecs. Try ```
sudo apt-get install [COLOR=#000000]gstreamer0.10-ffmpeg
```[/COLOR]

---

### Post by jronc on 2013-03-08
I entered the command sudo apt-get install gstreamer0.10-ffmpeg and it came back saying that i had the latest version installed so it made not updates. Oh, well mplayer works with mp3 files so I can create a directory of files with those extensions to play around with.

One more question, I have tried to Ctrl-C the terminal screen and when I ctrl-V the forum screen, I only get the command line but not the rest of the output in response to the command. I tried to dump using the word processor to see if it was the terminal. All that wa copied to the word procesor screen was what was copied to the forum screen. So, how do you copy the output of a command if you don't use Ctrl-C?

Thanks for you assistance. This was a good experience and I actually learned some new stuff so I thank you again.

---

### Post by Cheesemill on 2013-03-08
To copy and paste in the terminal you need to use CTRL+SHIFT+c and CTRL+SHIFT+v.

CTRL+c in the terminal means cancel.

The usual method to copy and paste in the terminal is highlight for copy and middle-click for paste.

---

### Post by oldos2er on 2013-03-08
> **jronc said:**
>  So, how do you copy the output of a command if you don't use Ctrl-C?


I just swipe the text with my mouse, then single-click with the middle button to paste. If the command output is more than one page (and it frequently is), enclose it in [code tags]("http://ubuntuforums.org/misc.php?do=bbcode").

I'd still like to see the output from ```
sudo apt-get update && sudo apt-get install libsox-fmt-mp3
``` I suspect there's a problem with a missing repository or mis-configured APT.

---

### Post by andrew.46 on 2013-03-08
Are you really keen to run from the commandline in this way? If you are after an *easier* life either SMPlayer or vlc might help out. For extra codec use with MPlayer from the commandline you can juice up MPlayer a little by upgrading the shared libavcodec package, the name of which depends on which version of Ubuntu you are running. For Quantal:

```

sudo apt-get install  libavcodec-extra-53

```

---

### Post by jronc on 2013-03-09
First thank you both for your assistance. I tried using mplayer Rhymbox with the *m4a music files and the computer played the all the songs in the album. It also worked with mp3 files. I just used mplayer without Rhymbox it would not play the m4a files.

I will give the command line install libracodec-extra-53 a shot and let you know my result. Now that I know how to copy and paste the terminal screen, I can give a better picture of what is and is not working. Take care and thanks again.[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

