---
title: "Automatically kill long time processes"
date: 2013-01-09
forum: Programming Talk
---

### Post by icaka92 on 2013-01-09
Hello,

I use my ubuntu 12.01 desktop for converting videos to mp3. I have a problem. On htop stats i have processes that is active from more than 30 minutes. How can i automatically kill processes that is active from more than 30 minutes. My ideas is to run bash script every 30 minutes and with check to kill the process id, but i don't know how to write the bash script.

Thanks !

---

### Post by ofnuts on 2013-01-09
There are plenty of process that are active more than 30 minutes in a Linux computer (your desktop, for instance). So, how do you identify potential victims? And how can you tell when they started?

---

### Post by icaka92 on 2013-01-09
Hello again. I mean ffmpeg proccess that run more than 30 minutes. This is what i need. I don't know how to get the time in ubuntu. In htop i see how much time 1 proccess continious.

---

### Post by TheFu on 2013-01-09
> **icaka92 said:**
> Hello,

I use my ubuntu 12.01 desktop for converting videos to mp3. I have a problem. On htop stats i have processes that is active from more than 30 minutes. How can i automatically kill processes that is active from more than 30 minutes. My ideas is to run bash script every 30 minutes and with check to kill the process id, but i don't know how to write the bash script.

Thanks !

30 minutes is nothing for a video transcoding process. I've had some that take 4+ hours.

If you want to kill a process for any reason, then you want to use the "kill" or "killall" commands.  Definitely look those up before you use them. There are important options to understand.

To get the time, run the "date" command. I think there's a built-in way for bash too.  Every process has information stored inside the process table like start time, user CPU, system CPU, wait states, nice level, etc. I do not know how to access that data from bash, but from other scripting languages, it is easy. Python or perl can easily. Those also have date manipulation routines.

Another way would be to dump the process table every hour and see which processes with a specific command have been running between those two runs. I'd use top, egrep, and cut to parse everything if I wanted to avoid using python or perl for some reason.  Perl is my normal hammer for this sort of stuff.

It sounds like you are doing lots of batch processing.  Be certain to check out **task spooler**. I think you will like it.

If I wasn't clear, these are all CLI/shell commands - no point-n-click. When you want to automate things, that is the best way.

---

### Post by icaka92 on 2013-01-12
Hello. Thanks for the answers. I just kill all ffmpeg proccess on every 30 minutes and now it is okay.

---

