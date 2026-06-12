---
title: "Bash script (Newbie)"
date: 2011-09-08
forum: Programming Talk
---

### Post by Fenlig on 2011-09-08
Hey Guys,

Hope this is in the write section. Im trying to write a start/stop script for my Minecraft server running on ubuntu server 11.04. I fairly new to scripting as well and Linux. 

I'm using a more complex script that does what I want as a reference, but I would like to write this on myself as a learning project.

Reference script: [http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

And heres mine: 
> 
#!/bin/bash
# Minecraft startup script
# Made by Simon
DIR="/home/minecraft/game/"
JAVA="java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui"
GREP="ps -ef | grep minecraft | grep SCREEN"

if [ "$1" = start ] ; then[INDENT]         if [ "$GREP" = -eq 1 ] ; then 
echo "Minecraft is already running"
else
echo "Starting!"
cd $DIR screen -dmS minecraft $JAVA
echo "Still starting :)"
fi
[/INDENT]fi 
Now Line 10 is giving me a error

> 
[EMAIL="minecraft@Servertron:%7E/.bin"]minecraft@Servertron:~/.bin[/EMAIL]$ minecraft start
/home/minecraft/.bin/minecraft: line 10: [: too many arguments
Starting!
Still starting
[EMAIL="minecraft@Servertron:%7E/.bin"]minecraft@Servertron:~/.bin[/EMAIL]$ 
Now line 10 is the " if [ "$GREP" = -eq 1 ] ; then" is it that I cannot use an If statment right after another if?

Much appreciation for any help offered.

---

### Post by Arndt on 2011-09-08
> **Fenlig said:**
> Hey Guys,

Hope this is in the write section. Im trying to write a start/stop script for my Minecraft server running on ubuntu server 11.04. I fairly new to scripting as well and Linux. 

I'm using a more complex script that does what I want as a reference, but I would like to write this on myself as a learning project.

Reference script: [http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

And heres mine: 
Now Line 10 is giving me a error

Now line 10 is the " if [ "$GREP" = -eq 1 ] ; then" is it that I cannot use an If statment right after another if?

Much appreciation for any help offered.

You have both = and -eq, that's what's too many.

---

### Post by Fenlig on 2011-09-08
Awesome, thanks.

Okay so now what i need to happen is when I run the script the runs the minecraft server in a seperate screen named minecraft_server

Now the command I got is not near working :(

Ive been looking at tutorials for screen but it boggles the mind.

Could someone shed some light please :)

My line of script

cd $DIR screen -dmS minecraft_server $JAVA

---

### Post by sisco311 on 2011-09-08
> **Fenlig said:**
> Awesome, thanks.

Okay so now what i need to happen is when I run the script the runs the minecraft server in a seperate screen named minecraft_server

Now the command I got is not near working :(

Ive been looking at tutorials for screen but it boggles the mind.

Could someone shed some light please :)

My line of script

cd $DIR screen -dmS minecraft_server $JAVA

cd and screen are two commands. You may also want to quit the script if the directory doesn't exist. Oh, and use quotes, they are vital:
```
cd "$DIR" || exit 1
screen -dmS minecraft_server "$JAVA"
```

---

### Post by papibe on 2011-09-08
> **Fenlig said:**
> Now the command I got is not near working :(
There's a problem with the test you are doing to know if minecraft is already running.

You are not actually executing the ps command with this:
```
...
GREP="ps -ef | grep minecraft | grep SCREEN"
...
    if [ "$GREP" =  1 ] ; then
... 
```
What your are doing is comparing the string "ps -ef..." to 1. Which always is going to be false!

Although there are several approaches to solve that, here's a very simple one:
```

....
    ps -ef | grep minecraft | grep -q SCREEN
    if [ $? = 0 ]; then
        echo "Minecraft is already running"
....

```
The last grep has a -q option so it doesn't print the results. The $? variable is the exit code of the last command.

Another way would be test directly the execution of the pipe:
```

...
    if ps -ef | grep minecraft | grep -q SCREEN; then
        echo "Minecraft is already running"
...

```
Hope it helps,
Regards.

---

### Post by sisco311 on 2011-09-08
Since Ubuntu uses Upstart I would probably try to write an Upstart job, instead of a System V style init script.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

### Post by Fenlig on 2011-09-08
Okay the script now can tell if the minecraft process is running (thanks [papibe]("http://ubuntuforums.org/member.php?u=774785") for explaining what was happening)

But now it doesnt seem to be launching the program.

The line "screen -dmS minecraft_server "$JAVA" Doesnt work
but the line "screen -dmS minecraft_server java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui"  does, any one have an idea why the variable isn't working :(

> 
DIR="/home/minecraft/game/"
JAVA="java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui"
GREP="ps -ef | grep minecraft_server.jar | grep -v grep"

if [ "$1" = start ] ; then
        if ps -ef | grep minecraft_server.jar | grep -v -q grep ; then 
        echo "Minecraft is already running"
        else
        echo "Starting!"
        cd "$DIR"
        screen -dmS minecraft_server "$JAVA"
        echo "Still starting"
        fi
fi 


---

### Post by CharlesA on 2011-09-08
I was going to suggest using:

```
GREP=$(ps -ef | grep minecraft_server.jar | grep -v grep)
```

instead of the way you were using it how it is.

Like it is:

```
#!/bin/bash

DIR="/home/minecraft/game/"
JAVA="java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui"
GREP=$(ps -ef | grep minecraft_server.jar | grep -v grep)

if [ "$1" = start ] ; then
	if [[ -n $GREP ]]; then
		echo "Minecraft is already running"; else
		echo "Starting!" && cd "$DIR"&& screen -dmS minecraft_server "$JAVA" && echo "Still starting"
	fi
fi
```

EDIT: So the problem is that the java process isn't starting?

Why don't you just use the full path to minecraft_server.jar instead of cding to the game directory?

---

### Post by Fenlig on 2011-09-08
Okay guys after using some awesome suggestions my script is looking a lot cleaner...

> 
#!/bin/bash
# Minecraft startup script
# Made by Simon

# DIR="/home/minecraft/game/"
JAVA="java -Xmx1024M -Xms1024M -jar /home/minecraft/game/minecraft_server.jar nogui"
GREP=$(ps -ef | grep minecraft_server.jar | grep -v grep)

if [ "$1" = start ] ; then
        if [[ -n $GREP ]] ; then 
        echo "Minecraft is already running"; else
        echo "Starting!" && screen -dmS "$JAVA"
        sleep 7
                if [[ -n $GREP ]] ; then 
                echo "Minecraft server started successfully" ; else
                echo "Minecraft server failed to start"
                fi
        fi
fi 
Only problems is we are getting a new error :(

> 
[EMAIL="minecraft@Servertron:%7E/.bin"]minecraft@Servertron:~/.bin[/EMAIL]$ minecraft start
Starting!
Must run suid root for multiuser support.
Minecraft server failed to start
Any ideas?

---

### Post by CharlesA on 2011-09-08
Do you need to use sudo to start minescraft?

---

### Post by Fenlig on 2011-09-08
I never had to before

---

### Post by rolandrock on 2011-09-08
You need to re-evalute $GREP before the second test.  Repeat the GREP=... line after the "sleep 7" line.

---

### Post by CharlesA on 2011-09-08
> **rolandrock said:**
> You need to re-evalute $GREP before the second test.  Repeat the GREP=... line after the "sleep 7" line.

Agreed.

I'd replace $GREP with just $(ps -ef | grep minecraft_server.jar | grep -v grep) in both instances.

---

### Post by Fenlig on 2011-09-08
So the variable has got only one use? Can you explain why?

Is this what  you mean?
> 
# DIR="/home/minecraft/game/"
JAVA="java -Xmx1024M -Xms1024M -jar /home/minecraft/game/minecraft_server.jar nogui"
GREP=$(ps -ef | grep minecraft_server.jar | grep -v grep)

if [ "$1" = start ] ; then
        if [[ -n $GREP ]] ; then 
        echo "Minecraft is already running"; else
        echo "Starting!" && screen -dmS "$JAVA"
        sleep 7
GREP=$(ps -ef | grep minecraft_server.jar | grep -v grep)
        if [[ -n $GREP ]] ; then 
        echo "Minecraft server started successfully" ; else
        echo "Minecraft server failed to start"
        fi
        fi
fi


Thanks,

---

### Post by rolandrock on 2011-09-08
When you assign a value to a variable, it stays at that value unless you change it.  You assigned GREP to the output of the ps command not to a dynamic formula that is updated on invoking the value of GREP.  

You can re-write your code to do this by changing GREP to a function call.  That is probably too much work for what you want to achieve unless you want to do it for fun.

Also, you should take CharlesA's advice and get rid of the GREP variable.  It is not pretty.

---

### Post by Fenlig on 2011-09-08
Okay guys thanks I remove the $GREP and just put in the actuall code, but I have found that the "&&" symbols is giving me the "Must run suid root for multiuser support." error anyway around this?

Thanks

---

### Post by CharlesA on 2011-09-08
Try running each command individually, to see which one is showing that message - the && is just chaining commands together. I think it's coming from screen.

---

### Post by rolandrock on 2011-09-08
CharlesA is right.  Try providing a session name with screen command:

> screen -dmS **MINECRAFT** "$JAVA"

---

### Post by Fenlig on 2011-09-08
Well Minecraft should never require root to run the server I had it successfully running earlier without it.

I checked for other screens but couldn't find any but I rebooted the server just in case but im still getting the issue :(

I just ran "java -Xmx1024M -Xms1024M -jar /home/minecraft/game/minecraft_server.jar nogui"(which is $JAVA) and it worked fine.

Confused :S

---

### Post by Fenlig on 2011-09-08
[B]Brilliant you guys are right its cos I didnt assign a name to the screen :)

Thanks
[/B]

---

### Post by rolandrock on 2011-09-08
Hi Fenlig,

I might have contributed by completely changing my last reply.  Please see amended 'screen' command in my previous post.  That should fix this error.

---

### Post by rolandrock on 2011-09-08
You're welcome.

---

### Post by Fenlig on 2011-09-08
Okay the multiuser issue is gone but now its failing to start.

Been looking around to see what, but I know its one small tiny character thats breaking it.

What i type 
> 
[EMAIL="minecraft@Servertron:%7E/.bin"]minecraft@Servertron:~/.bin[/EMAIL]$ minecraft start
Starting!
Minecraft server failed to start 
The script so far
> 
#!/bin/bash
# Minecraft startup script
# Made by Simon

JAVA="java -Xmx1024M -Xms1024M -jar /home/minecraft/game/minecraft_server.jar nogui"

if [ "$1" = start ] ; then
        if ps -ef | grep minecraft_server.jar | grep -v -q grep ; then 
        echo "Minecraft is already running"; else
        echo "Starting!" && screen -dmS minecraft "$JAVA"
        sleep 7
                if ps -ef | grep minecraft_server.jar | grep -v -q grep ; then 
                echo "Minecraft server started successfully" ; else
                echo "Minecraft server failed to start"
                fi
        fi
fi 


So 
"echo "Starting!" && screen -dmS minecraft java -Xmx1024M -Xms1024M -jar /home/minecraft/game/minecraft_server.jar nogui"
works but
echo "Starting!" && screen -dmS minecraft "$JAVA"
doesnt 
:(

---

### Post by Vaphell on 2011-09-08
what happens when you unquote $JAVA in that troublesome line? as it stands quoted JAVA variable is treated as a single continuous string not as a collection of many parameters

---

### Post by papibe on 2011-09-08
> **Vaphell said:**
> unquote $JAVA
+1
I was testing that, it works:
```
screen -dmS minecraft $JAVA
```
Regards.

---

### Post by Fenlig on 2011-09-09
Hey Guys,

Just want to thank you all for helping me out. Now that the "Start" section is done ill move on to the "Stop" section. Really nice support here on this forum.

> 
JAVA="java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui"
DIR="/home/minecraft/game/"

if [ "$1" = start ] ; then
        if ps -ef | grep minecraft_server.jar | grep -v -q grep ; then 
        echo "Minecraft is already running"; else
        echo "Starting!" && cd $DIR && screen -dmS mine_server $JAVA
        sleep 7
                if ps -ef | grep minecraft_server.jar | grep -v -q grep ; then 
                echo "Minecraft server started successfully" ; else
                echo "Minecraft server failed to start"
                fi
        fi
fi 


---

