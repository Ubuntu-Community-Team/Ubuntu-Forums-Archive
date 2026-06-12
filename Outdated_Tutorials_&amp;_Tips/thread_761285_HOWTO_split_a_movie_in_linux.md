---
title: "HOWTO split a movie in linux"
date: 2008-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Sjovan on 2008-04-21
Okay, Today I missed windows for the first time, but after a lot of googling and struggling I took the matters in my own hand. I don't know if this is a problem that everyone has, but when I tried to split an *.avi with avidemux the sound got messed up (both video and sound on direct copy). I tried a lot of progs, like Lives, Kino and Kdenlive, but those programs weren't what I was looking for. I read up on the forum about mencoder and first i tried to find a GUI frontend that worked, without any luck. So I tried the command: 
mencoder -ovc copy -oac copy -ss TIME -endpos TIME -o "outputname" "inputname"

But what happened? Yes, because of i wanted to start at 00:00:16 in the movie the stop got pushed fwd 16 seconds. Okay, you can calculate this in the head, but if you (like me) have around 50 files that need to be split at many locations, then that isn't a option. 

I talked about my problem on irc.freenode.net #lindox (really helpful people there) and asked for a scripter. Firewing1 came to the rescue :D I explained the problem i depth and talked about that we needed to convert both times to seconds and do an (endtime - starttime) = to get the real endpos time. Firewing1 got it to work :D

So with out any more BS, here is the howto (be nice, it's my first).

```

sudo apt-get install mencoder
cd /usr/local/bin
sudo wget http://home.no.net/sjovan01/scripts/splitvideo
sudo chmod o+x splitmovie

```

Explanation:
Mencoder is a simple movie encoder, designed to encode MPlayer-playable movies. You need that pack cause this script tweeks one of the commands in mencoder.
The reason we go to /usr/local/bin is because scripts in that folder can be executed from any dir.
Wget downloads the script,
Chmod is for making the script executable.

To get the show on the run... taken from the script file:
```

cd /dir/to/the/file/you/want/to/split
splitmovie "outputfilename" "inputfile" <start time> <stop time>

```
start and stop time should be in this format. HH MM SS
NB! don't set the time up like this --> 00 08 17. Do it like this --> 0 8 17

Edit:
Can a admin pleas fix the topic titel? HOWTO split

---

