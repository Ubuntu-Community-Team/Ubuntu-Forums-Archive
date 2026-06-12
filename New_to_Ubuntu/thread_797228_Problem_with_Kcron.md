---
title: "Problem with Kcron"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by darbid on 2008-05-17
I have only just started using Ubuntu in the last couple of months.

I wanted to record some radio shows and used these instructions

[http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/](http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/)

Here is my script

```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
mplayer "mms://66.70.119.243/B105" -ao pcm:file=/media/Music/Internet_Radio/Temp_Files/mystream.wav -vc dummy -vo null
lame -m s /media/Music/Internet_Radio/Temp_Files/mystream.wav -o "/media/Music/Internet_Radio/HamishAndy/Hamish_Andy-$NOW.mp3"
rm /media/Music/Internet_Radio/Temp_Files/mystream.wav

```

As per the instructions i have a second file with

```
pkill mpplayer
```

The idea being that the first script is initiated to start the recording, then the second script is called to stop it.  Then it turns it into a mp3 file.

If I enter this all in terminal it works great.

I then set up Kcron and it also all works if I choose the "Run Now" function of Kcron.

Problem is that it does not run as scheduled.

Could anyone please help.

---

### Post by Monicker on 2008-05-17
Does Kcron keep a log of any errors that may have occurred when the job tried to run?  

You can also add this to the end of your mplayer command

```
> /home/username/cron.txt
```


That way, if there is a specific error, you should see it in the file.

---

### Post by darbid on 2008-05-17
ok Thanks for your reply.

Adding that for some reason makes the mplayer part work.

Now however when lame starts it simply puts a 8kb file into the directory.

Of course it works fine in terminal.

i added your txt suggestion to the lame line and the resulting txt file is empty.

---

### Post by darbid on 2008-05-18
I have been looking at this all day.  The recording with mplayer is ok but this line

```
lame -m s /media/Music/Internet_Radio/Temp_Files/mystream.wav -o "/media/Music/Internet_Radio/HamishAndy/Hamish_Andy-$NOW.mp3"
```

So the same old story applies it runs in terminal.  It even runs when you "test" it in Kcron but as soon as you schedule it you get a 40kb (5sec) mp3 file.

I have tested this on 3 computers now and they all do the same.

Can anyone please give me help or indicate what i could look at.

---

### Post by nyborjare on 2008-07-18
Interesting

I have been testing this too and my experience is the same.
As I am total newby I can only wait and see if anybody can come up with solution to this
Regards

---

### Post by darbid on 2008-07-18
please remember that I am also a beginner.

By chance my now works.

here is my specific code that works, I am sorry I do not want to make it generic in case I write something false.
```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
mplayer "mms://66.70.119.243/B105" -ao pcm:file=/media/General/Radio/Hamish_Andy/mystream_$NOW.wav -vc dummy -vo null > /media/General/Radio/Hamish_Andy/error.log
lame -m s /media/General/Radio/Hamish_Andy/mystream_$NOW.wav -o "/media/General/Radio/Hamish_Andy/Hamish and Andy - $NOW.mp3" >/media/General/Radio/Hamish_Andy/scripterror.log 2>&1
#mplayer "http://resources.b105.com.au/listenfeed/b105.asx" -ao pcm:file=/media/General/Radio/mystream_NOW.wav -vc dummy -vo null > /media/General/Radio/kcron_$NOW.txt
```

I am pretty sure that the two error logs are what made it work for me.  They just overwrite each day.

---

### Post by borgdrone on 2008-07-27
This Kcron thing is wierd. Has it worked for anyone?. I have tried to use Kcron on different versions of Kubuntu, Fedora core, etc . It doesn't seem to work in any case. Is this app actually suppossed to do something.

---

### Post by darbid on 2008-07-30
I got it to work on something small very easily.  I am a total beginner and just wrote some small script and then tested it.

Oh I also started with the GUI.  Once it produced the file I then edited the file myself for little tweaks.

As you question is so general and because I am a beginner I am sorry but I do not think I can help further.

---

### Post by str238 on 2008-08-08
I have the same problem with my Ubuntu HH. KCron seem to do absolutely nothing. No matter what applications or scripts I schedule, it does simply nothing. Cron deamon is running, anacron as well. ;(

---

