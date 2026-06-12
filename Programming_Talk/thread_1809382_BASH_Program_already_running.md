---
title: "BASH: Program already running?"
date: 2011-07-21
forum: Programming Talk
---

### Post by Volens on 2011-07-21
The situations is as follows:
 
I am trying to write some startup scripts for a MineCraft server I've been running. I have some that have been working, but I feel that they are very messy.
 
Basically the script must do these things:
[LIST]
[*]Check if there is already and instance of the server running
[*]Start the MC server if it isn't already started
[*]Check if there is already an instance of Ventrilo running
[*]Start Ventrilo if it isn't already
[/LIST]My current solution uses ps and grep, however, I have recently read that ps | ax, pgrep etc. can occasionally return false values due to PID reassignments etc.. I also read about a half-solution using an "until" loop (this only makes sure it actually started and cannot check if the script is re-run).
 
I considered a different approach that would use the exit code of "screen" (which I am using to manage the server) to determine if the screen the server was running on existed yet. Running "screen -r screenname" will give me a "1" if it doesn't exist, but if it does, it goes to that screen which does me no good.
 
At a loss for other solutions I have turned to the forum to ask:
 
Is there an ideal way to check for the existence of processes, or was I on the right track? I am content with the performance of my current script, but it would put my mind at ease if a more experienced coder could give me some insight because there is a difference between basic functionality and elegant functionality.

---

### Post by mikejonesey on 2011-07-21
ps is fine, you can always generate a lock file in the init dcript for each server, then if ps does not find the process, lauch the init script which generates a lock file...

for example;

script to check and launch init;
```
servCheck=$(ps -ef | grep -i mincraft...)
[CODE]if [ -z "$servCheck" ]; then
/init.d/mine start
fi
```

edit the init.d script to;

if start... launch custom start script...

custom start script:
```

touch /var/lock/minelock
# here would go whatever the launch command was from the init script
functuin serverStopped()
{
rm /var/lock/minelock
}

trap serverStopped EXIT

```

---

### Post by Volens on 2011-07-21
Ok, I had seen some stuff on lock files. I guess I'll try it out.
 
I remember reading that making sure the lock file is removed after the process dies is important. Is there any way to ensure this if for instance I had a power outage?
 
I only ask because what got me started with scripting was the need to back up maps since I had one get corrupted on me when I lost power. I'd rather not purchase a aux power supply for a little hobby server.

---

