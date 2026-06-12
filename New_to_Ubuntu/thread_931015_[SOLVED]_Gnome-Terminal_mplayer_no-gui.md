---
title: "[SOLVED] Gnome-Terminal mplayer no-gui"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by whitethorn on 2008-09-26
Hi, I was wondering if there's a way to get a command to open a new terminal and run the mplayer command in it?

I want to create a launcher on my Desktop that when I drag a media file on it, it'll open mplayer in a terminal window (preferably gnome-terminal but I wouldn't mind using xterm), which will then show the output of the command.  

My problem at the moment is if I drag something onto the launcher mplayer will run in the background and the only way to stop it is to get it's PID number and then kill it.  Anyone have an idea how to do this?

---

### Post by phidia on 2008-09-26
I don't understand what you mean by > if there's a way to get a command
"xterm" is the command and so is "mplayer" you probably want to write a script that will do what you want. Take a look at the scripting wiki [here]("https://help.ubuntu.com/community/Beginners/BashScripting").

---

### Post by whitethorn on 2008-09-26
Well at the moment I've gotten it to work with xterm.  I found a script earlier today and changed it a bit to get xterm to show the output of mplayer

> #!/bin/bash
killall gnome-screensaver
xterm -e mplayer "$1"
gnome-screensaver

I disabled the screensaver option in /etc/mplayer/mplayer.conf because I noticed it took a long time to finish whenever starting a video, this starts a lot faster.
Is there a way to get it run using gnome-terminal?

---

### Post by mc4man on 2008-09-26
> Is there a way to get it run using gnome-terminal? 

here's example for music files (no screensaver stuff 

```
#!/bin/bash
gnome-terminal -e "mplayer "$1""
```

Just set your launcher command as path to script
ex.-  script in home dir.
./<script name>

---

