---
title: "Starting Scripts"
date: 2006-11-26
forum: Programming Talk
---

### Post by Twigg on 2006-11-26
So i've just installed Ubuntu a couple of days ago, and i'm a novice when it comes to Linux. I've managed to install Wine and get a copy of Starcraft going, and to my surprise it doesn't run to bad. The problem is i'm used to icons that I can just click and run a game... All this shell command stuff is getting annoying.

So how would I go about making a script that I can just click on to open up starcraft, or any other program I want instead of having to go through a bunch of shell commands?

---

### Post by 23meg on 2006-11-26
You don't need a script; just create a launcher on your desktop, entering the command you use to launch the game into the *Command* box in the *Create Launcher* window.

---

### Post by po0f on 2006-11-26
Twigg,

For the command, make sure to enclose the directory with quotes.  Something like the following should do the trick:
```
[FONT="Courier New"]wine "~/.wine/drive_c/Program Files/Starcraft/starcraft.exe"[/FONT]
```

---

### Post by Twigg on 2006-11-26
Awesome that'll work for my games, but i've got other programs I like to run that take up a wad of command lines.

I use hamachi to play lan games of starcraft, warcraft 3 and so on via VPN. To run it I need to enter a bunch of command lines, and i'd like to automate that as well.

Plus I use Xlink Kai to play Xbox games via System link. So I've got to run ./kaid from the bin, and then jKaiUI.jar from my home directory. I figured having a few scripts on my desktop would make this a load easier. I'm just not sure how to go about making the scripts.

Thanks again for the help.

---

### Post by Engnome on 2006-11-26
You could create a launcher that executes a bash script. Just enter the path to the bash file and don't forget to set it to be executable.

Bash script tutorials can be found through Google.

---

### Post by Twigg on 2006-11-26
Right on. Thanks for the info. :)

---

