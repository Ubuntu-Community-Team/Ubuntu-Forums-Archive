---
title: "Shell Script for automating WOW launch (Wine 1.4 &amp; .sh)"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by teh603 on 2013-01-29
Since the latest PPA build really borked my framerate, I figured I'd try to reinstall Wine 1.4. That means I have to manually run an applet with --nohttpauth. I can do this manually by copy-pasting a line of code into the terminal.

HOWEVER, this is a pain in the butt compared to just running it in WINE 1.5

I've tried to make a shell script on the desktop to automate launching WOW. One click SHOULD launch Agent.exe and then the WOW launcher.

```
#!/bin/bash
cd /home/(me)/.wine/drive_c/users/Public/Application\ Data/Battle.net/Agent/Agent.1544/
/home/(me)/.wine/drive_c/users/Public/Application\ Data/Battle.net/Agent/Agent.1544/Agent.exe --nohttpauth &
cd /home/(me)/.wine/drive_c/Program Files\ (x86)/World\ of\ Warcraft/
/home/(me)/.wine/drive_c/Program Files\ (x86)/World\ of\ Warcraft/World\ of\ Warcraft\ Launcher.exe

```

I then flagged it as executable. I'm not a total nooblet, y'know. ;)

The problem is, when I click on it and hit "execute" in the dialog that pops, I get the following error message: 

> Failed to execute child process "/home/(me)/Desktop/Wine_FIX.sh" (No such file or directory)

Anyone got an idea of how to get this working?

Edit: This is a shell script thread, not a WINE thread. I've got everything working in WINE. All I need is help with this shell script.

---

### Post by omeomi on 2013-01-29
Does it work if you run it from the terminal?
```
sh ~/Desktop/Wine_FIX.sh
```

---

