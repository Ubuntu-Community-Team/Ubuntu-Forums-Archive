---
title: "Bash script for launching Minecraft to optimum settings"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by mitwilsch on 2013-06-21
This page: [http://www.minecraftforum.net/topic/579934-how-to-make-minecraft-run-faster-windows-linux-mac/](http://www.minecraftforum.net/topic/579934-how-to-make-minecraft-run-faster-windows-linux-mac/)give instructions on how to launch Minecraft to run faster than its default. The script it gives for launching is here:
```
#!/bin/bash# Minecraft Launcher Script
clear
# Launch Parameters
java -Xmx1024M -Xms1024M -XX:+UseFastAccessorMethods -XX:+AggressiveOpts -XX:+DisableExplicitGC -XX:+UseAdaptiveGCBoundary -XX:MaxGCPauseMillis=500 -XX:SurvivorRatio=16 -XX:+UseParallelGC -XX:UseSSE=3 -XX:ParallelGCThreads=2 -jar ~/Downloads/minecraft.jar
```
Saving as an executable .sh file. Then it says to open a terminal and enter ```
sudo pidof java
sudo renice -20 -p B
```(B being replaced by the output of pidof java)
to give it (java) a high priority. 
I want to do both of these things in one script, but I don't know how. I've tried using !! to use the previous output, and saving output to a variable (v=`foo`; $v) but they don't seem to work. The command !! works in the terminal when typed in, but it doesn't when running the script (!!: command not found).
The main problem I am having though, is getting it to work right. When the minecraft.jar is started, it doesn't do anything else until Minecraft quits. And the changing priority command needs a password for sudo.
So, what I need is for the script to run Minecraft.jar first, to start the Java process. Then the 'sudo pidof java' to run, fetching the pid of java running Minecraft. Then 'sudo renice' to run, using the output of 'sudo pidof' in the appropriate place. 
Can anyone help with this please? It sounds very easy to do, but I can't get it to work at all. Thanks very much.

---

### Post by MidnightGrey on 2013-06-21
I'm not on ubuntu right now so i cant quite test these out, if you just call your script as root ie: sudo sh ./MinecraftLoader.sh it should work.  for the script you can try (again not tested):  
```
  
#!/bin/bash  
clear  
java -blah blah blah -jar Minecraft.jar&  
pidof java | renice -21 -p $1  

```   
the **&** should let you continue without it pausing after executing java. 
the last line pipes the output of pidof into renice.   Hopefully everything works okay, i'll be back on ubuntu later and i can verify the commands.

---

### Post by mitwilsch on 2013-06-21
> **MidnightGrey said:**
> I'm not on ubuntu right now so i cant quite test these out, if you just call your script as root ie: sudo sh ./MinecraftLoader.sh it should work.  for the script you can try (again not tested):  
```
  
#!/bin/bash  
clear  
java -blah blah blah -jar Minecraft.jar&  
pidof java | renice -21 -p $1  

```   
the **&** should let you continue without it pausing after executing java. 
the last line pipes the output of pidof into renice.   Hopefully everything works okay, i'll be back on ubuntu later and i can verify the commands.
That starts Minecraft under /root directory. I could do with that, but when I manually do renice it says the previous value was 0 (1234 (process ID) old priority 0, new priority -20).
I can't find any command to just list what priority java has without changing it using renice and showing what the previous one was, but I'd think it was the same.
Anyways, right now I'm just using 2 scripts: the minecraft.sh (java -blah -jar minecraft.jar) and the priority one (pidof java | renice -20 -p $1). 
It's not exactly what I want, but at least I don't have to open a terminal and memorize a command.

---

