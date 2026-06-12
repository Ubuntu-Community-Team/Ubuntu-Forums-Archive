---
title: "Autorun Commands in Terminal?"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-11-25
Hello there.
Here's what I'm trying to do, but don't know how:
1. Click on a launcher on my desktop
 2. Terminal opens up
  3. runs command *cd ~/Minecraft/server*
  4. runs command *java -Xms1504M -Xmx1504M -jar minecraft_server.jar nogui*

Basically: I'm trying to create a launcher that will launch terminal, change directories in the terminal, and then run a java program in the terminal (minecraft server).

Is there a way to do this?

---

### Post by lechien73 on 2011-11-25
Hi,

Yes, you can do this. Firstly, create a shell script that will launch the Minecraft server. Open a text editor and create a file with the contents:

```
#!/bin/bash

java -Xms1504M -Xmx1504M -jar ~/Minecraft/server/minecraft_server.jar nogui
```

Save this to your home directory as minecraft.sh

Open a terminal window and type:

```
chmod +x minecraft.sh
```

Now create a launcher on your desktop. To do this you need the gnome-desktop-item-edit app.

```
sudo apt-get install --no-install-recommends gnome-panel
gnome-desktop-item-edit ~/Desktop/ --create-new
```

Give the launcher a name, and browse to minecraft.sh as the command. I've tested this and it works fine on my machine :)

---

### Post by mastablasta on 2011-11-25
Instructions are reasonable but here is a little explanation:
 
This is a script that you will make:
```
#!/bin/bash
 
java -Xms1504M -Xmx1504M -jar ~/Minecraft/server/minecraft_server.jar nogui
```
 
This will make the script executable: 
```
chmod +x minecraft.sh
```
 
 
> 
Now create a launcher on your desktop. To do this you need the gnome-desktop-item-edit app.
 
```
sudo apt-get install --no-install-recommends gnome-panel
gnome-desktop-item-edit ~/Desktop/ --create-new
```
 
Give the launcher a name, and browse to minecraft.sh as the command. I've tested this and it works fine on my machine :)
this one i don't think is necessary in Xubuntu. Also you can just move the script to your /home/desktop folder and it should appear on your dektop. or you can simply create launcher with right click and just point to it.

---

### Post by DaimyoKirby on 2011-11-25
Ok, that works! I just moved the file to the desktop, and it runs all right!
But it seems to create new server files (server.properties, whitelist.txt, etc.) whenever I run it from that script, either in my home directory or my desktop. 

Is there a way I can redirect it to where the real server files are (~/Minecraft/server)?

Also, something else I noticed, although it's not such a big deal: the default for clicking on it just tells it to execute, which doesn't open up any terminal or anything, so I can't do server commands (or stop the server...). Is there a way to change it to open in terminal by default?

Lechien73, your method works great too. Except I run into the same problems - I moved minecraft.sh to my server folder, and created the launcher successfully, and when I clicked it, and logged into minecraft, the server ran great. But once again, it created new server files in my home directory, much like mastablasta's method did. I did, however, figure out how to have it open up in terminal - I edited the launcher in notepad. My first question above stands.

---

### Post by lechien73 on 2011-11-25
> **DaimyoKirby said:**
> Ok, that works! I just moved the file to the desktop, and it runs all right!
But it seems to create new server files (server.properties, whitelist.txt, etc.) whenever I run it from that script, either in my home directory or my desktop. Is there a way I can redirect it to where the real server files are (~/Minecraft/server)?

Also, something else I noticed, although it's not such a big deal: the default for clicking on it just tells it to execute, which doesn't open up any terminal or anything, so I can't do server commands (or stop the server...). Is there a way to change it to open in terminal by default?

Edit: I'm gonna try using lechien73's way, just in case that solves the above issues.

If you put the minecraft.sh file in the ~/Minecraft/server folder, and create a launcher using the method I gave above, then the config files will be created in the correct folder.

Also, when you create the launcher, select "Application in Terminal" as the type. That will allow you to enter server commands in the terminal window.

---

### Post by mastablasta on 2011-11-25
> **DaimyoKirby said:**
> Ok, that works! I just moved the file to the desktop, and it runs all right!
But it seems to create new server files (server.properties, whitelist.txt, etc.) whenever I run it from that script, either in my home directory or my desktop. Is there a way I can redirect it to where the real server files are (~/Minecraft/server)?

move it to minecraft server and then put just the launcher (i.e. shortcut) in desktop.

> 
Also, something else I noticed, although it's not such a big deal: the default for clicking on it just tells it to execute, which doesn't open up any terminal or anything, so I can't do server commands (or stop the server...). Is there a way to change it to open in terminal by default?

this one i don't know i am kind of new in commands... but i found this: 
[http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)

should work if you replaced it with xterminal or xterm or what is called in XFCE. i forgot. LOL, just started using XFCE myself.

and this: [http://ubuntuforums.org/showthread.php?t=1015654](http://ubuntuforums.org/showthread.php?t=1015654)

---
lechien73's advice might solve the issues, however i believe (not sure) that this will also install some other stuff that doesn't need to be installed. I think his commands makes a lot of sense if you were using regular Ubuntu.

---

### Post by DaimyoKirby on 2011-11-25
Lechien73 -
Sorry, there's been a little miscommunication. It edited my post, and you hadn't refreshed afterwards; that isn't your fault. Anyway, yes, I already tried moving it to ~/Minecraft/server, and it still created new files in home directory. I did, however, open up the launcher in Leafpad, and edited it to open in terminal.

Mastablasta -
I don't really understand much of what they were talking about:oops:...
I did try the first suggestion in the [ubuntu forums post]("http://ubuntuforums.org/showthread.php?t=1015654") you linked, although I don't know the command to open a terminal - I'm using Terminal Emulator, which is xubuntu's default.
I did, however, successfully create a launcher, and it runs all right, and I checked the box to have it run in terminal, so now I'm able to control it, but it still creates new files in the home directory. I made sure the "working directory" was set to ~/Minecraft/server, too, although I don't know what the working directory is supposed to do/be.

---

### Post by DaimyoKirby on 2011-11-25
AMAZING!!!
I don't know why, I don't know how, but I got it to work.
Remember that problem I was having with the .sh file not using my server files in ~/Minecraft/server, and instead created its own?
I decided to place the launcher on my panel/dock thing, where I keep all my other programs that I regularly use, and when I clicked on it, and it opened up terminal, I noticed it said it loaded a map that was being used by my original server files. So I went and checked, and voila! It's running my original server!

Thanks to both of you for all you help - I couldn't have done it without you!:D:D:D

---

### Post by lechien73 on 2011-11-25
Great stuff...delighted we could help :D

---

