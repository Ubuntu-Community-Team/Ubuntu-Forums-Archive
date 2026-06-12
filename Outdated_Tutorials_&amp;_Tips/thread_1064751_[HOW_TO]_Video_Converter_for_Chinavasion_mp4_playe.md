---
title: "[HOW TO] Video Converter for Chinavasion mp4 players"
date: 2009-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Hakimio on 2009-02-09
[SIZE="4"]_HOWTO: Video Converter for Chinavasion mp4 players_[/SIZE]
[SIZE="2"]_[COLOR="Red"]Updated 2011-04[/COLOR]_[/SIZE]

[SIZE="3"]**Intro**[/SIZE]
An acquaintance of mine needed a way to convert video for his [Chinavasion](http://www.chinavasion.com) Touch Screen MP4 Player (aka chinese ipod touch clone) so I wrote him a bash script for that. The script is based on crmanski's [_video-convertor_](http://ubuntuforums.org/showthread.php?t=62625) script. Changes I made to the original script are described in the Changelog section.

_**Features:**_
[LIST=1]
[*]Batch conversion;
[*]Linux, Mac OS & BSD compatible (here I will only describe how to get it working with Ubuntu/Debian systems);
[*]Supports many Chinavasion MP4 player screens and support for more can be easilly added (contact me by posting in this thread or by sending private message if your Chinavasion mp4 player is not supported).
Supported resolutions:
[LIST]
[*]320x240
[*]220x176 
[*]160x128 
[*]128x96
[/LIST]
[*]Video quality can be selected;
[*]Aspect ratio is automatically detected
[*]settings are saved;
[*]Can be easily translated (current translations include: english & lithuanian);
[*]Appropriate video FPS are selected depending on selected resolution;
[/LIST]

[SIZE="3"]**Installation**[/SIZE]
[LIST=1]
[*]Download one of the scripts attached to this post (english and lithuanian versions available)
[*]Place the script in the Nautilus scripts folder (/home/_YourUserName_/.gnome2/nautilus-scripts)
[*]Make sure the file is executable
```
chmod +x ~/.gnome2/nautilus-scripts/MP4-Player-Video
```
[*]Install mencoder:
```
sudo apt-get install mencoder
```
[*]Select some video files. Right-click, Choose Scripts->MP4-Player-Video.
Here is a video showing script in action:
[mirror #1](http://www.binaryworld.skynet.lt/Converter.avi)
[mirror #2](http://binaryworld.xz.lt/Converter.avi)
[mirror #3](http://www.mediafire.com/?sharekey=ab1d4f3024a2b33fd2db6fb9a8902bda)
[/LIST]

[SIZE="3"]**Change log**[/SIZE]
0.1 Beta, April 2011
[LIST]
[*]Easier translation
[*]Automatic aspect ratio detection
[*]awk expression bug fix (shows up with newer awk)
[*]use xterm to tell about missing zenity
[*]major code cleanup
[*]don't show file path and extension in zenity progress dialog
[/LIST]
Initial release (0.01 Alpha; Jan 2009); changes made to crmanski's script:
[LIST]
[*]Settings are saved
[*]All selected files are checked - not only the first
[*]Cancel works correctly when pressed during conversion
[*]MPEG file is correctly identified now
[*]Newlines work when echoed
[*]The checking if the file is video file ends instantly when any match is found
[/LIST]

[SIZE="3"]**To do**[/SIZE]
[LIST]
[*]test & fix the bugs (if present)
[/LIST]

[SIZE="3"]**About Touch Screen Chinavasion MP4 Player**[/SIZE]

I don't own [the player](http://www.chinavasion.com/product_info.php/pName/touch-screen-mp4-player-8gb-28-inch-tft-display/) myself, but anyway hare are few things you might want to know about it:
[COLOR="SeaGreen"]The Good[/COLOR]
[LIST]
[*]Really cheap, like 50$ for 8GB model without camera
[*]Radio built-in
[*]Doesn't require special software to copy files to the device (acts as ordinary flash drive)
[*]Smaller than ipod touch (3.70x2.17x0.59 compared with 4.3x2.4x0.31)
[*]miniSD slot (unlike ipod touch)
[*]Built-in speaker
[*]Optional camera
[*]Up to 8GB memory
[*]Radio 
[*]Picture viewer (JPEG)
[*]Built in MIC
[*]Pretty good screen
[/LIST]
[COLOR="Red"]The Bad[/COLOR]
[LIST]
[*]No wi-fi
[*]Touch screen is not really sensitive (should be ok when using stylus pencil though)
[*]No firmware upgrades will be provided
[*]Play/pause buttons are reversed
[/LIST]
[_Video review_](http://www.youtube.com/watch?v=_xxpDBjkPlY&watch_response) by Citiclown

---

### Post by tippyaloishes on 2009-03-29
I am not only new to ubuntu, I'm new to PCs all together. I have a chinavision mp4 player and I can't convert videos. The convert disc I was given with it doesn't work. I want to do what you put on here but I don't know what you're saying exactly. Can you please explain how I can find a script? Or a file? Or a script folder? Also what and how would I use the codes you put up, like where do they go? Also what is nautilus and how can I find it? I found something that said nautilus on my pc but it didn't say what it is. Please help if you can Thank you..

---

### Post by Hakimio on 2009-03-29
> **tippyaloishes said:**
> I am not only new to ubuntu, I'm new to PCs all together. I have a chinavision mp4 player and I can't convert videos. The convert disc I was given with it doesn't work. I want to do what you put on here but I don't know what you're saying exactly. Can you please explain how I can find a script? Or a file? Or a script folder? Also what and how would I use the codes you put up, like where do they go? Also what is nautilus and how can I find it? I found something that said nautilus on my pc but it didn't say what it is. Please help if you can Thank you..
The script you need is in the archive which is attached to my guide. Download the archive. Then:
[LIST=1]
[*]Open the terminal, which can be found in Applications -> Accessories -> Terminal
[*]Enter:
```
nautilus ~/.gnome2/nautilus-scripts
```
to go to the folder, where all nautilus scripts are located.
[*]Extract the script from the archive you downloaded to the folder you just opened in the previous step.
[*]Close nautilus and execute in the terminal (If you renamed the script you downloaded, change MP4-Player-Video to the new file name):
```
chmod +x ~/.gnome2/nautilus-scripts/**MP4-Player-Video**
```
[*]Find a link to the video tutorial, I posted in the guide.
[/LIST]

---

### Post by tippyaloishes on 2009-03-29
Oh wow thank you.... I've been trying for weeks now. Thank you so much for the extra detail :)

---

### Post by Hakimio on 2011-04-22
Updated the script.

---

