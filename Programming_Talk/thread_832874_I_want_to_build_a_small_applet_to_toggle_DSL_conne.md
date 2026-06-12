---
title: "I want to build a small applet to toggle DSL connection, help!"
date: 2008-06-18
forum: Programming Talk
---

### Post by rivalslayer on 2008-06-18
I want to build a applet using PyGTK, that will help users to toggle the DSL connection on and off, without the terminal. For that, I need help, as this is my first ever OSS work, I am a novice in computer programming, with limited experience in C++ and Python. I am 18, and been programming for only four years. Can you help me with these queries...

1. How to check if the DSL connection is On of Off from within Ubuntu?
2. How to run terminal commands using from a Python script?
3. Can I enter the Sudo password from a Python or bash script?

Thanks in advance!!!:)

---

### Post by Mickeysofine1972 on 2008-06-18
> 
1. How to check if the DSL connection is On of Off from within Ubuntu?
not sure maybe you could check /var/logs/messages for the login success message? (might be log instead of logs)

to do this from the terminal I used to do tail -f /var/logs/messages and you can see the output in the terminal

> 
2. How to run terminal commands using from a Python script?
look at the 'os.spawnlp' python function that should do it and you can spawn the xterm command with the '-e command' i think

> 
3. Can I enter the Sudo password from a Python or bash script?
not sure I think so as i saw tseliot ( the guy who does the envy-ng nvidia driver installer program) do something like this in earlier versions of envy.

however, you could just put gksudo infront of the xterm command when you spawn it.

Hope this give you some starting points.

Mike

---

