---
title: "HowTo: view your buddy's Terminal Session from Remote...no X"
date: 2006-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-09-01
[i]
Originally Posted at:
[http://howtoforums.net/viewtopic.php?t=61](http://howtoforums.net/viewtopic.php?t=61)
[/i]

**Overview**
In this HowTo I will explain how two users connected to a Linux Terminal via any xterm terminal emulator, can view each others Shell while cooperating...no X server nor VNC is required...this is all based on a "headless" server with only Secure Shell (SSH) on it.


**The Scenario**
*User 1* is connected to some Mail server in the world over SSH, using his favorite xterm terminal emulator, PuTTY. (you can use any Terminal Emulator)
*User 1* will be conducting a mission critical update on this server, and would like his buddy *User 2* to be his overseeing eye as he goes about his important task...
*User 2* logs into the Mail server via SSH and his favorite term emulator, Konsole. (...again it can be any Term)...
*They are ready to begin...*

**The Magic...**
*User 1* kicks off the commands:
```

echo "I am about to run the script so you can watch me..." | wall
echo "In 5 seconds, do: cat /tmp/watchme" | wall
mkfifo /tmp/watchme
script -f /tmp/watchme

```

*User 2* receives the message via Broadcast and kicks off the command:
```

cat /tmp/watchme

```

[b]
*User 2* is now viewing *User 1's* Terminal Session !!!
[/b]

*User 2* opens up an additional session to the Mail Server and:
```

echo "dude, very cool, I can see what you are typing..." | wall

```

I hope you enjoy this tip, and for more info on the tools we used here you can:
```

man mkfifo
man script
man wall

```


[i]
Big Thanks to my good friend & Guru colleague Zoran Naskov for teaching me this Old School & VERY use full trick!!!
[/i]


-- 
Jacob
Linux -- Breaking All Boundries
"you may say I am a dreamer, but i'm not the only one"
[http://howtoforums.net](http://howtoforums.net)

---

