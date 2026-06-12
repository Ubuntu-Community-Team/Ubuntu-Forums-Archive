---
title: "[SOLVED] Nautilus script audio converter...?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by sdim on 2008-08-13
Hi,everyone.
I tried to find through Synaptic a program that can convert from/into all kinds of music formats,and among others I found the _Nautilus script audio converter_.However,I can't find it anywhere(after the installation).
Can someone help?
Thank you.

---

### Post by sdim on 2008-08-13
Here's a screenshot

---

### Post by nicedude on 2008-08-13
It will be in the folder located -> /usr/share/nautilus-scripts/ConvertAudioFile but if you want to use it easier I would recommend installing nautilus scripts manager & then copying and placing it in your home/yourname/.gnome2/nautilus-scripts/ folder so you can right click on a file and access it via the new shortcut "scripts" that the scripts manager will give you :-)

Hope this helps

---

### Post by sdim on 2008-08-13
Just installed SoundConverter,but I'll give it a shot as you suggested.
Many thanks.

---

### Post by sdim on 2008-08-13
> **nicedude said:**
> It will be in the folder located -> /usr/share/nautilus-scripts/ConvertAudioFile but if you want to use it easier I would recommend installing nautilus scripts manager & then copying and placing it in your>  home/yourname/.gnome2/nautilus-scripts/ folder so you can right click on a file and access it via the new shortcut "scripts" that the scripts manager will give you :-)

Hope this helps

Where is that? I found Gnome2,but not Nautilus Scripts...

---

### Post by nicedude on 2008-08-13
You have to install nautilus script manager first as it will create the directory I mentioned then every script you put in there will be available from a right click on the desktop, you will see a new entry called "scripts"

install the script manager with this command

sudo apt-get install nautilus-script-manager

---

### Post by sdim on 2008-08-13
I figured it out.
The _.gnome2_ file is hidden in the Home directory,and you have to tick _show hidden files_ in _View_.Copied and pasted the _Convert Audio File_ in the .gnome2 file,and it's OK.
Thanks for the help.

---

### Post by opakedragon on 2008-08-26
I did the same but when I right click on an audio file (m4a) and click Scripts > ConvertAudioFile I get a warning saying "audio convert 0.3.1 converts audio files please select at least one file. What should I do?

---

### Post by nicedude on 2008-08-26
I am not sure dragon but I think it may just not support m4a as that is a Apple Quicktime based MPEG-4 audio stream and I don't think it would be supported. So if I am right then it is because it doesn't see the file you select as being a music file and therefore is asking you to choose a valid music file. Try using it to convert an MP3 or something really common and if that works then I am right about it not supporting the m4a format.

---

### Post by Piro ko on 2011-11-28
The thread is old, however I just followed it's advice and have not had the same KIND of success and figured I'd post how I got past an error script.
I downloaded the nautilus script audio converter and the scripts manager package as suggested as well. Found the proper folder to place the file. Did so, and now I have the option to convert audio files when I left click on them.
However when I first tried this it told me that there was an error, stating: "you don't have the right codec to decode the selected file. missin' codec: mplayer"

This makes sense to me, however it may not make sense to the next person down the line at 2am when they have a video project due soon and can't get their program to read the music file they want to use.
SO,
if you have this problem or one that has all the same words but replaces the word "mplayer" with something else, try opening up the Synaptic Package Manager, searching for "nautilus-script-audio-converter" (the one you've downloaded/installed) right click on the package.
You'll notice that at the bottom of the dialogue you have the "Mark suggested for installation" option.
In that drop down list will be the package you need. The one described by your error message "mplayer" or "lame" or some such. Click it.
Apply changes.
Viola! Now it works.

Hope this helps at least one person some day. :)

---

