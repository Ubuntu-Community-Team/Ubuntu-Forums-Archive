---
title: "[SOLVED] Alternate to Sessions?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-27
Is there a way to have a program start at login using the command line?

---

### Post by artir on 2008-05-27
Create a file wherever you want called Whateveryouwant.sh Write the command(s) you want to execute there, save it, give it executions rights and go to sessions and add that file.

---

### Post by slughappy1 on 2008-05-27
Using the command line, not Sessions in any way. I do not want to use Sessions. Isn't Sessions a front end gui for something using the command line?

---

### Post by drs305 on 2008-05-27
> **slughappy1 said:**
> Using the command line, not Sessions in any way. I do not want to use Sessions. Isn't Sessions a front end gui for something using the command line?

Sessions is merely a place to put a command, script etc to run at startup. Whatever you would type on a command line you could put in a Sessions entry. It is by bar the safest and easiest place to put something you want to run at startup.

If you really don't want to put it there, look into scripts linked to one of the /etc/rcX.d folders.

---

### Post by slughappy1 on 2008-05-27
Is there no way of doing it on the command line? For example gnome-session-properties-add /path/to/program/or/script?

drs305, you say to look into the /etc/rcX.d files. But there isn't a /etc/rc7.d file. And since the graphical login is on the 7th... I don't see how to implement what you suggest. Can you clarify please?

---

### Post by drs305 on 2008-05-27
> **slughappy1 said:**
> Is there no way of doing it on the command line? For example gnome-session-properties-add /path/to/program/or/script?

drs305, you say to look into the /etc/rcX.d files. But there isn't a /etc/rc7.d file. And since the graphical login is on the 7th... I don't see how to implement what you suggest. Can you clarify please?

The /etc/rcX.d files are not based on dates, but on 'runlevels'. In simple terms, at boot linux executes the scripts in the rcX.d folders. Scripts beginning with S start processes, scripts beginning with K end processes. So the number doesn't have anything to do with dates, just the order they run - starting with 0. In ubuntu, I believe most of the user processes are in the 2-5 runlevels (but don't quote me).

I am about to go to work, but I think you may need to describe what exactly you want to do on the command line. I assume you want to start running a command as the computer starts up. Is that correct? 

And I assume you don't want to actually want to type something in the command line but would like the command to run automatically. Correct?

Here is what I have in a Sessions command, as an example so that a particular keyboard key runs as a tab:
```
xmodmap -e "keycode 112 = Tab"
```

Session is for a particular user, and the /etc/init.d files are used for everyone. Is that why you don't want to use Sessions?

The beauty of linux is that there are many ways to do things and I am not trying to force you into using the Sessions feature. Just explain what you want to do and people will help you.

Time to go.  Good luck to you.

---

### Post by d.kusummmanth@gmail.com on 2008-05-28
plz provide  a link to a good tutorial on sessions. i'm a n00b.

---

### Post by 7raTEYdCql on 2008-05-28
I discovered this method myself of transferring yourself from the GUI to command line

When somewhere on the GUI type "ctrl+alt+F5"
this will shift you to the command line.

So when your Ubuntu starts up(the loading progress bar comes) then pressinf "ctrl+alt+F5" will shift you to the command line indicating what is happening with the kernel at that instant.

Simalarly when your normal login screen comes pressing this combination will shift you directly to the command line.

---

### Post by drs305 on 2008-05-28
> **d.kusummmanth@gmail.com said:**
> plz provide  a link to a good tutorial on sessions. i'm a n00b.

Sessions is ubuntu's graphical interface for letting users add programs/commands to be run at start up. They are specific to that user; for commands that will affect all users the scripts are placed in the /etc/init.d folders.

To use Sessions, go to the Systems menu, then Preferences, Sessions. Select the Startup Programs tab. If you see the command or application in the window to the left, just tick it and it will start the next time you boot or YOU return to ubuntu.

To add a new command or application to begin at start up, select Add and enter a name. 

In the 'command' window, you must enter the command which launches the script or application. You can also enter terminal commands such as one I quoted earlier in this thread for xmodmap. 

If you don't know the command for an application it get a little tricky - but only a little!. 

There are several ways to find out what command runs an application:
1. If you have an icon of the program in a menu or panel, you can right click, select Properties, and see the command to start the app.

2. In a browser, you can look in the /usr/bin folder to see if you recognize a program. The files in this folder launch applicaitons and the start name is just what you see here. Example: /usr/bin/gedit = start command 'gedit'. Some are more difficult but still discernable, such as Open Office Writer is 'oowriter'. There is a 'whereis' command you can try in terminal, but you would really need the app name to use it (e.g 'whereis gedit').

3. You could also search the Properties > Installed Files of packages listed in synaptic to look for a /usr/bin entry.

4. If you don't see or recognize anything in this folder that might be the start program, do a google search. I would include the general name of the program, 'terminal', 'command' and 'linux' or 'ubuntu'. You will be able to find the start up command somewhere.

5. If all else fails, ask on the forum ;-)

---

