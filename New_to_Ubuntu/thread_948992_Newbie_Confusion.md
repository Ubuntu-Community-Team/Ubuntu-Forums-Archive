---
title: "Newbie Confusion"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Fratien on 2008-10-15
I finally cast off the chains of Microsoft this morning and got myself the newest stable version of Ubuntu, this is (as you'll soon notice from my problems) my first foray into anything to do with linux. 

I read through a few of the links in the Stickied thread, and read how to use the terminal and what not, but I'm still really confused about a few things.

I installed a program from a .deb(Mercury Messenger, if its any kind of important) and I've used the terminal search to make sure it was properly installed, yet I have no idea how to run the actual program. Similarly I ran the updates and got firefox 3.0 but it the beta that came with ubuntu is still running.

I'm really sorry if this has all been mentioned before but most threads I read didn't say anything about file locations after the installations. Thanks in advance

---

### Post by simtaalo on 2008-10-15
for the updates goto update manager in the administration section of the menu, that should take care of firefox etc...

if you cant find the program in any of the menu sections you can press alt+F2 to bring up "run application" if you start to type in the application name it should autocomplete so you can just hit return.

if its an application you use regularly you could make a launcher in your taskbar, simply right click on it add to panel ---> custom application launcher

these links might help
doing things on GUI [http://ubuntuforums.org/showthread.php?t=898328](http://ubuntuforums.org/showthread.php?t=898328)

but i would definitely recommend getting to know the terminal, will make your life quicker , this will help [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

quick note - in future please try to use a more descriptive thread title, something like "installed app and cant find it" it will make sure you get help a lot quicker.

---

### Post by Zzl1xndd on 2008-10-15
If I reacall Mercury adds itself to the Internet section of your application menu.

---

### Post by jbrown96 on 2008-10-15
Some programs do not create icons when they are installed. You will have to find where it is. Open a terminal and try things like mercury, mm and such. A very nice trick is to type something like mer and then hit the tab key twice quickly and it will show all commands and files that match that. Here's an example. > justin@venus:~$ net
net              netkit-ftp       net-snmp-config  
netcat           netscsid         netstat     I typed net and used tab-completion and it showed me the following commands. If you can find Mercury Manager, then try ```
whereis MERCURY-MANAGEr
``` change MERCURY-MANAGER to whatever you found. This will give you the location. I assume that you will want to create a shortcut, which you can do with System-->Preferences-->Main Menu. Move to the folder you want and create a new item. Post the entire path for the command here. Probably something like /usr/bin/mercury... And you will have a menu item for it.

---

### Post by OutOfReach on 2008-10-15
Usually programs do add themselves to the panels, but the panels may need refreshing one way I do that is logging out and back in.

---

### Post by D3M0L1$H3® on 2008-10-15
i assume that instead of the Terminal, you also
sudo check-menu-bar-under: Applications-(all)
and went through to find it.

---

### Post by brian_p on 2008-10-15
> **Fratien said:**
> 

I'm really sorry if this has all been mentioned before but most threads I read didn't say anything about file locations after the installations. Thanks in advance

```
dpkg -L package_name
```

for locations of files installed from package.

---

### Post by Fratien on 2008-10-15
Thanks for all the help everyone, I think I've cracked it now.

- Simtaalo: I'll keep that in mind, but hopefully I won't be making too many threads in here :p

---

### Post by simtaalo on 2008-10-15
> **Fratien said:**
> 
- Simtaalo: I'll keep that in mind, but hopefully I won't be making too many threads in here :p

its one of the best ways to learn, 

screw something up
trawl through forum pages trying to find an answer 
give up 
make a thread
find out its pretty easily sorted = you just learnt something new. 

usually more than one because other things whilst trawling for the answer catch your eye too so you read up on them all the while amassing knowledge :)

i enjoy it anyway :lolflag:

---

