---
title: "Audio Stutter"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Charbo00 on 2008-05-27
I am having an issue with my audio stuttering or not even playing. I can play songs and videos in movie player but both stutter like crazy and pause for at least a few seconds when they stutter. In amarok I cannot even play songs, it acts like it plays fine and the progress bar moves but no sound. I switched all the sound settings over to ALSA to even get amarok to try to play the files and I downloaded the restricted extras also.

---

### Post by alienexplorers on 2008-05-27
I heard that the new 17-xx kernel was suppose to fix this.  I loaded 17-xx and I still have crackling and stuttering when playing mp3's or streaming audio.  not sure where to go from here.  I also enabled ALSA in sounds for all options.

---

### Post by Charbo00 on 2008-05-27
Yeah I have the 17 kernal too I dont know what else to do =/

---

### Post by Charbo00 on 2008-05-27
Anyone been able to resolve this? :(

---

### Post by Charbo00 on 2008-05-31
bump :confused:

---

### Post by brucewagner on 2009-03-09
Same problem here....  on all our Ubuntu machines (also, they are all NVidia)...

Any news?

---

### Post by Hobbez on 2009-04-28
TLDR version starts at "Solution:"

I have Nvidia as well as an issue with stuttering sound. My problem might be a little different from the ones previously described, however I did come across this topic on my search for a fix so it seems like a good spot to share my findings. 

What happened to me is that I would be playing something with firefox, or vlc, and maybe I opened up too many instances of VLC or caused firefox to crash somehow, but the sound would be sent into repeating the most annoyingly loud loop of whatever was playing at that moment. It was like a skipping CD, except it would not stop. Restarting X did not seem to work. 

I then came across a [potential fix from tigerstripedcat]("http://ubuntuforums.org/showthread.php?t=452448") that suggested using ```

lsof | grep pcm       //to find the process that is getting caught
kill -9 16883         //to kill the open sound processes. 
sudo /etc/init.d/alsa-utils restart     //to reset everything. 
```
Well that didn't actually work for me, but it seemed to be on the right track. I was sick of restarting the computer every time this problem arose, so I liked the idea of just shutting down processes.

Recently I have also been looking for ways to become more command line literate, so I found [this]("http://www.ibm.com/developerworks/aix/library/au-speakingunix3.html"). 
```

ps -Aeww    //"To see the complete command line 
            //and environment of every process on the system."
```
I figured I would just get into a terminal and start killing processes until the sound stopped or my system crashes. Well the first one I killed was pulseaudio. This worked. I finally was able to figure out how to stop the stuttering sound without restarting the computer. Then, I also had the command to start running it again. 

Solution:

```
jack@sony:~$ ps -aeww | grep pulseaudio
21451 ?        00:00:02 pulseaudio
jack@sony:~$ sudo kill -9 21451
[sudo] password for jack:
jack@sony:~$ pulseaudio &
[1] 21622
jack@sony:~$

```

There you have it. Kill the pluseaudio, and then run it again using alt+f2 or in the background using ```
pulseaudio&
```
That is the solution I found. 

Hope I could help
-Hobbez

---

### Post by yoasif on 2009-04-28
if you are still seeing this issue, you may want to run alsa-utils.sh and report your findings to this bug report. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

For getting the alsa.sh do the following
wget [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) -O alsa.sh && bash alsa.sh

---

### Post by lemmingrebel on 2010-06-28
> **Hobbez said:**
> TLDR version starts at "Solution:"

I have Nvidia as well as an issue with stuttering sound. My problem might be a little different from the ones previously described, however I did come across this topic on my search for a fix so it seems like a good spot to share my findings. 

What happened to me is that I would be playing something with firefox, or vlc, and maybe I opened up too many instances of VLC or caused firefox to crash somehow, but the sound would be sent into repeating the most annoyingly loud loop of whatever was playing at that moment. It was like a skipping CD, except it would not stop. Restarting X did not seem to work. 

I then came across a [potential fix from tigerstripedcat]("http://ubuntuforums.org/showthread.php?t=452448") that suggested using ```

lsof | grep pcm       //to find the process that is getting caught
kill -9 16883         //to kill the open sound processes. 
sudo /etc/init.d/alsa-utils restart     //to reset everything. 
```Well that didn't actually work for me, but it seemed to be on the right track. I was sick of restarting the computer every time this problem arose, so I liked the idea of just shutting down processes.

Recently I have also been looking for ways to become more command line literate, so I found [this]("http://www.ibm.com/developerworks/aix/library/au-speakingunix3.html"). 
```

ps -Aeww    //"To see the complete command line 
            //and environment of every process on the system."
```I figured I would just get into a terminal and start killing processes until the sound stopped or my system crashes. Well the first one I killed was pulseaudio. This worked. I finally was able to figure out how to stop the stuttering sound without restarting the computer. Then, I also had the command to start running it again. 

Solution:

```
jack@sony:~$ ps -aeww | grep pulseaudio
21451 ?        00:00:02 pulseaudio
jack@sony:~$ sudo kill -9 21451
[sudo] password for jack:
jack@sony:~$ pulseaudio &
[1] 21622
jack@sony:~$

```There you have it. Kill the pluseaudio, and then run it again using alt+f2 or in the background using ```
pulseaudio&
```That is the solution I found. 

Hope I could help
-Hobbez



Hey, sorry if this is a complete noob question, but that's exactly what I am: a noob.

But I'm having this same issue, and when I try to run this kill command, it says that the daemon is still running.

What do I do?

---

