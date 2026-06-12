---
title: "HOWTO: Create video clips for the Play-Yan micro"
date: 2007-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Trisa on 2007-06-03
I recently got myself a [PLAY-YAN micro]("http://www.nintendo.co.jp/n08/play_yan_micro/index.html") for my new hand-held gaming system, the [Game Boy micro]("http://micro.gameboy.com/"). It's quite a neat accessory with the ability to play MP3 files on the go and view movie clips. While the sample movie was cool to watch on the GBm, I wanted to put my own movie clips on it.

However, there was a problem. I didn't buy the MediaStage CD. That program converts the movies into a file that is compatible with the PLAY-YAN micro. It's also a Windows program and is in Japanese. Thankfully, I realized that I already had the tools at my disposal thanks to Ubuntu. With many experimentations, I was able to create movie clips without the need to buy a program.

Owners of the PLAY-YAN micro are probably wondering how to make these files on Ubuntu. This tutorial was tested on the latest version on Ubuntu.

1 - Before starting, add the [Medibuntu]("http://medibuntu.sos-sts.com/") repository on your system, so that you can have the most up-to-date version of ffmpeg. This version has the faac/faad2 encoder and codec compiled, which you'll need in order to make your movie clips work. Make sure that the universe repositories are enabled as well. The instructions are provided in the web site.

2 - If you don't have the program already, type this in the terminal and press enter:

```
sudo apt-get install ffmpeg 
```3 - There are three settings that you can choose from depending on the clip.

**Normal Settings (Works with most video clips, recommended):**

```
ffmpeg -i 'Input.avi' -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 300 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 Output.mp4
```** Special Settings (For video clips with fast movement or difficult scenes):**

```
ffmpeg -i 'Input.avi' -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 300 -mbd 2 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 Output.mp4
```** Extreme Settings (Only use this setting if the second option still gives you problems):**

```
ffmpeg -i 'Input.avi' -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 500 -mbd 2 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 Output.mp4
```All of these settings give out the highest quality video you can have without limiting the PLAY-YAN micro's power.

UPDATE - If you wish to make the process easier, you can create a script that will allow you to right-click on a movie file and convert it right away without using the terminal.

Credits goes to [COLOR=Black]**kevinlyfellow** and **codypump****er**[/COLOR] for this method. (Original thread can be found [here]("http://ubuntuforums.org/showthread.php?p=2974704")).

1 - Go to Applications --> Accessories --> Text Editor.

2 - Type the following in:

```
#!/bin/bash

cd $NAUTILUS_SCRIPT_CURRENT_URI
ffmpeg -i $1 -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 300 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 "$1".mp4
```3 - Save this file as "Play-yan" and store it at "~/.gnome2/nautilus-scripts" (~ means your username).

4 - Right click on a movie clip and go to Scripts --> Play-yan.

5 - Wait until you see a new file. The file is now ready to be playable in the PLAY-YAN micro.

Once the file is created, put the movie in the SD card, put it in the PLAY-YAN micro, and enjoy the show. Feel free to experiment with the settings, though the default settings are good enough if you have a GBm.

With the normal settings, a typical half-hour episode or show will be about 50-80 megabytes.

This HOWTO is still a work in progress. Expect more from this thread soon.

Here are some shots of my GBm playing some clips I made on Ubuntu:

_[U][[IMG]http://xs216.xs.to/xs216/07230/PYm01.jpg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs216&d=07230&f=PYm01.jpg") _[/U]_[[IMG]http://xs216.xs.to/xs216/07230/PYm02.jpg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs216&d=07230&f=PYm02.jpg") [[IMG]http://xs216.xs.to/xs216/07230/PYm03.jpg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs216&d=07230&f=PYm03.jpg")_

I hope this is helpful for those who own a PLAY-YAN micro. :D

---

### Post by hraposo on 2007-06-06
My output: **Unknown codec 'aac'**

---

### Post by Trisa on 2007-06-06
> **hraposo said:**
> My output: **Unknown codec 'aac'**

Did you make sure to enable the Medibuntu repository (it's been said that the Medibuntu version of ffmpeg has the faac/faad2 codecs compiled)?

---

### Post by codypumper on 2007-07-05
Thank you so much!! I had one slip up, solved by downloading the libavcodec0d package from the medibuntu repository.

---

### Post by codypumper on 2007-07-05
> Could this be turned into a Nautilus Script? I've tried and failed miserably...

Solved this at [http://ubuntuforums.org/showthread.php?p=2974704#post2974704](http://ubuntuforums.org/showthread.php?p=2974704#post2974704)
This makes this process so much simpler. I right click on video ---> Scripts ----> Play-Yan
Then I wait a while for it to encode. Then I can just copy it onto the sd card. 
No opening a terminal.

---

### Post by Trisa on 2007-07-06
> **codypumper said:**
> Thank you so much!! I had one slip up, solved by downloading the libavcodec0d package from the medibuntu repository.

You're welcome. I'm glad to hear this worked for you. :)

>  This makes this process so much simpler. I right click on video ---> Scripts ----> Play-Yan
Then I wait a while for it to encode. Then I can just copy it onto the sd card. 
No opening a terminal.

That's pretty cool. Tried this myself and works great. If you don't mind, I'll add this to the HOWTO since it will make conversion much easier for the user.

---

### Post by codypumper on 2007-07-07
> If you don't mind, I'll add this to the HOWTO since it will make conversion much easier for the user.
That's great. Not sure why I would mind. ;)

---

### Post by thanius on 2008-03-05
I've written a WIKI for converting and using Play-Yan under Linux, check it out:

[http://play-yan.thanius.com](http://play-yan.thanius.com)

---

