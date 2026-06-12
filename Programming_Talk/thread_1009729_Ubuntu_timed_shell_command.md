---
title: "Ubuntu timed shell command?"
date: 2008-12-12
forum: Programming Talk
---

### Post by beavis2008 on 2008-12-12
Hello,
I am trying to record the radio on my computer. I have an audio cable going from the radio to my pc.

I use this command to record the audio: "sox -t ossdsp -w -s -r 44100 -c 2 /dev/dsp -t raw - | lame -x -m s - ./radio.mp3"

Question: How can I run this command to record for 30 minutes and then have it stop?

I can get it to start at a certain time of the day with crontab, but how do I get it to stop? Can I put some thing on the end of the command or do I have to put it into a script? 

Thanks in advance..

---

### Post by fubbleskag on 2008-12-12
there's probably a better way to do this, but I suppose you could setup another crontab to kill the apps at a specific time

---

### Post by mssever on 2008-12-12
> **beavis2008 said:**
> Hello,
I am trying to record the radio on my computer. I have an audio cable going from the radio to my pc.

I use this command to record the audio: "sox -t ossdsp -w -s -r 44100 -c 2 /dev/dsp -t raw - | lame -x -m s - ./radio.mp3"

Question: How can I run this command to record for 30 minutes and then have it stop?

I can get it to start at a certain time of the day with crontab, but how do I get it to stop? Can I put some thing on the end of the command or do I have to put it into a script? 

Thanks in advance..
The easiest thing would be to add another cron job that kills the recorder.

---

### Post by beavis2008 on 2008-12-13
> **mssever said:**
> The easiest thing would be to add another cron job that kills the recorder.

Thanks! 
I made a script to record with "sox -t ossdsp -w -s -r 44100 -c 2 /dev/dsp -t raw - | lame -x -m s - ./radio.mp3" in it.


I then made another script with "pkill sox" in it to stop the process. 

I then put the 2 scripts in the root crontab. It works great!

Thanks for your help!

---

### Post by lensman3 on 2008-12-13
Use the "at" command from a command line:

```
% at "time"
whatever commands
you want
ctl-d
%
```

OR

 ```
"at 3am <file"
```

where file has the commands.

From page 35 "The Unix Programming Envrironment by Kernighan and Pike" 1984

Page 129 has the self perpetuating example.

---

### Post by lensman3 on 2008-12-13
Sorry I miss-read you problem.

You are going to have to do something like:

(sleep 1805; ps ax | grep <for pid and extract pid>; kill -3 pid) &

Your recording command.

The 1805 is 60 seconds * 30 minutes + 5 seconds slack.  The command will pop into background and sleep for 30 minutes and 5 seconds before killing the recording command.  You might see if the recording command looks for kill signals so that it will die gracefully by closing all open files and not hanging the recording interface.

This can all take place in user space and not in superuser space.

Hope this helps.

---

### Post by Sami_Sdata on 2008-12-13
> **beavis2008 said:**
> Hello,
I am trying to record the radio on my computer. I have an audio cable going from the radio to my pc.

I use this command to record the audio: "sox -t ossdsp -w -s -r 44100 -c 2 /dev/dsp -t raw - | lame -x -m s - ./radio.mp3"

Question: How can I run this command to record for 30 minutes and then have it stop?

I can get it to start at a certain time of the day with crontab, but how do I get it to stop? Can I put some thing on the end of the command or do I have to put it into a script? 

Thanks in advance..

 It's been a bit since I used sox but I think it has a "trim" filter.  You can set that to make the recording a certain length.  I'm at work right now so I don't have sox available to check but you can try "man sox" and see if it mentions trim.  Good luck.

---

### Post by Sami_Sdata on 2008-12-13
> **Sami_Sdata said:**
> It's been a bit since I used sox but I think it has a "trim" filter.  You can set that to make the recording a certain length.  I'm at work right now so I don't have sox available to check but you can try "man sox" and see if it mentions trim.  Good luck.

 Ok, I sshed back to the house to test this out.  I used sox's rec option so it would use my default sound input.  This started recording after 0 seconds and stopped after 10.  I'm not home where I can check if it recorded anything usable but hopefully this will get you moving the right direction.

 rec -w -s -r 44100 -c 2  -t wav - trim 0 20  | lame -x -m s - ./radio.mp3

---

