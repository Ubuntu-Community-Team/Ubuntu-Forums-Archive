---
title: "A Linux Talking Clock"
date: 2011-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Rodney9 on 2011-05-12
Thanks to [http://charlessocci.com/2009/05/27/a-linux-talking-clock/](http://charlessocci.com/2009/05/27/a-linux-talking-clock/)

I thought it would be a fun project to make my own speaking clock for Linux. Here is a very simple project that will get you started with some basic shell scripting and using the crontab.

My first version of the clock used espeak – which is a synthesized voice. It isn’t very appealing. For my second version I went to the AT&T Labs site and used their form to create .wav files of human speech for the numbers one through twelve. I created a .wav for “AM” and another for “PM”. Then I created a .wav that says, “Hello, the time is now: ”

I used the command line application aplay, and output from the date function. It is very simple.

Since I’m kind of lazy, I didn’t bother creating all the minutes. I only want my announcements on the hour and half hour anyway.

I call the script from two crontab jobs, one that runs on the hour and one that runs on the half hour.

You can download my scripts and audio here – check it out and then make your own, but don’t forget to share your success and send me your result!

The basic steps are as follows:

1. Create .wav files of the spoken numbers 1 through 12, the number 30, “AM”, “PM” and “The time is: ”

2. Create a script to run on the hour similar to this example (change the paths to where you saved your files):

#!/bin/bash

aplay -q /home/charleys/time_voice/hellothetimeisnow.wav

HOUR=$(date +%-l)

AMPM=$(date +%p)

EXT=”.wav”

aplay -q  “/home/charleys/time_voice/$HOUR$EXT”

aplay -q “/home/charleys/time_voice/$AMPM$EXT”

#end script

3. Save as hour.sh Make the script executable

chmod +x hour.sh

4. Create a schedule to run the script using crontab

crontab -e

0 * * * * /home/charleys/time_voice/hour_human.sh

5. Repeat the steps above, except you are going to add the “30&#8243; .wav file, like this:

aplay -q  "/home/charleys/time_voice/$HOUR$EXT"
aplay -q "/home/charleys/time_voice/30.wav"
aplay -q "/home/charleys/time_voice/$AMPM$EXT"

NOTE: You MUST use upper case PM and AM for your file name. You MUST use 1.wav, 2.wav, etc for your file names. This is because the file is chosen based on the ouput from the date command. date +%-l outputs only the numbers 1-12 for the hour. Likewise, date +%p outputs either AM or PM. The – just removes the space from in front of the digits 1-9. Aplay only works with ALSA audio I’m told, however there are many other choices in command line audio players you can try.

Enjoy!

---

