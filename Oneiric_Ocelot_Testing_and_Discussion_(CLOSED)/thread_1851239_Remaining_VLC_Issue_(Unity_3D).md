---
title: "Remaining VLC Issue (Unity 3D)"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lidex on 2011-09-27
With the help of the many vlc threads in this forum, I have been able to fix/workaround all of my problems excepting one. When opening a video file from nautilus, the video displays, then freezes for about 20 seconds. The desktop is unresponsive during this time as well and cpu usage spikes. Unity-panel-service and unity-window-decorator both hit about 25 during the freeze then compiz momentarily hits 100 then drops quickly. At that point video plays normally and desktop unfreezes. Audio is unaffected throughout.

The funny part is if vlc is running and a file is opened through media -> open file, it functions normally. Has anyone else seen this issue or can reproduce it? What might be causing it?

---

### Post by mc4man on 2011-09-27
Vlc is working fine here though I will not use the 1.11 version except to occasionally test. (currently not installed.

If you can't resolve & inclined to try a 1.2-git, it can or built or - 
The videolan master ppa has atm  resolved it's  packaging issues of the last couple of months & has good builds for 11.10
(the 1.2 version has no problem currently with using the default gtk+ qt gui if that had been a problem for you

IF so i'd remove ~/config/vlc & 
```
sudo add-apt-repository ppa:videolan/master-daily
```

Being a dev version & updated every 3 days or so on the ppa I tend to make sure I have the previous package available before updating just in case. Generally see no issues at this point as 1.2 is nearing a release (maybe

1.2 has some remedial sound indicator support though it remains more a curiosity

---

### Post by lidex on 2011-09-27
Thanks for that, mc4man. I'll follow your suggestion and move to 1.2 but still curious as to why there would be a difference based on how file is opened.

---

### Post by mc4man on 2011-09-27
(un)fortunately I can't get that to happen - from nautilus works the same here
Is this something that started out of the blue or always has been for however old your install is?

Does the same happen in unity-2d or Gs if installed

---

### Post by lidex on 2011-09-28
It's been going on for awhile. I do not have gnome-shell installed and cannot reproduce in unity2D. There are other instances of the same behavior opening files in gedit. I'm thinking compiz has a hand in this.

---

### Post by mc4man on 2011-09-28
Maybe you need a fresh install?, I have a beta 2 but am going to do a new one with either todays or tommrows daily - beta 2 is so -so

If you want to ck. something - 
You could create a .desktop in ~/local/share/applications that would start vlc in verbose mode, probably also in a terminal
(could also enable logging & create a log file that would save the terminal output.

Then it could be called from the nautilus context menu - maybe vlc would report something different than started in verbose from a terminal > open vlc >  open file.

If you want i'll post you a .desktop. ect.

---

### Post by lidex on 2011-09-28
> **mc4man said:**
> Maybe you need a fresh install?, I have a beta 2 but am going to do a new one with either todays or tommrows daily - beta 2 is so -so

If you want to ck. something - 
You could create a .desktop in ~/local/share/applications that would start vlc in verbose mode, probably also in a terminal
(could also enable logging & create a log file that would save the terminal output.

Then it could be called from the nautilus context menu - maybe vlc would report something different than started in verbose from a terminal > open vlc >  open file.

If you want i'll post you a .desktop. ect.
If you would, I would most appreciate.

---

### Post by mc4man on 2011-09-28
While the new little .desktop is interesting actually don't need if you can get logging going.
This is with 1.2, should be the same or similar if still using 1.11

Open your Documents folder & create an empty file named vlctest, save & exit text editor

Open vlc > tools > preferences > bottom left corner - Show Settings > All
Then click directly on Interface & enable " Log to file" - screen 1

After that expand Advanced & click on logging. In the log filename box type in path to vlctest - screen 2
Then click 'Save' & exit vlc

run this in term
```
gksudo gedit /usr/share/applications/vlc.desktop
```
You can close out that annoying untitled document 1 

Scroll down to the Exec= line and insert -vv spaced after vlc as in 
```
Exec=vlc -vv %U
```
screen 3
Save & exit
Then just pick VLC media player as normal from your context menu, play your video(s)
All verbose output (messages) will be appended to the vlctest file

To revert just disable logging as in screen 1 & remove the -vv from vlc.desktop

Edit 
in screen 2 you'll notice there is a verbosity box - you can probably use that if desired rather than adding -vv to vlc.desktop, forgot all about that
experiment if you wish to see..

---

### Post by P-I H on 2011-09-28
I installed the master-daily ppa.
I have no problems with cpu load, when I start  from a directory in the file manager. The problem I had, with audio-video out of sync, is fixed.

However I get this error message when I start a bluray container, but both video and audio is OK.
 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not open the file "(null)". (No such file or directory)[/COLOR]
 [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not open the file "(null)". (No such file or directory)[/COLOR]
 [COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/COLOR]
 [COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/COLOR]

---

### Post by P-I H on 2011-09-29
Got problems to play bluray media after today's updates and had to reinstall the 1.1.11 version of VLC.

---

