---
title: "How to use gui on server"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by ajax4 on 2014-11-25
Hi
Absolute beginner here. I have a **server** (HP Prolient DL360G6) with a Gui on it. I now need a tutorial on how to use it. I want to install, uninstall. Check what's already installed, read logs. I will be using it as a web server, file server,  streamer and so on. 
I don't even know how to look at system information. I just can't find any tutorial on how to do things with the gui. I have issues with typing (bad knuckles) so need the least amount of command line control. 
Any pointers would be appreciated.
Many thanks :?
AJ

---

### Post by The Cog on 2014-11-25
For a start, before anyone can give GUI instructions, they need to know which GUI you are using. 
Open a terminal and enter the command:
```
cat /etc/lsb-release
```
and post the result here. That will at least tell us which GUI is the default.

If you can't work out how to open a terminal, Hold the Ctrl and Alt keys down while you tap the F1 key to get to a a text console. When finished, you can return to the GUI with Ctrl-Alt-F7.

It is normal to install servers with no GUI at all, because servers live in racks with no screens attached anyway - all the normal admin is done remotely.
Can we assume that in this case, you are at the server with a keyboard and mouse attached?

---

### Post by ajax4 on 2014-11-25
First of all, thanks for the assist. Its appreciated.

Eventual the server will be re-attached to the domain with remote log-in. Currently, its not attached to the internet (although I can run a RJ45 to it),  its a new project and a steep learning curve.
DISTRIB_ID=Ubunto
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

---

### Post by nerdtron on 2014-11-25
My never ending question on these topoics: why need GUI?
Do you have a program that needs you to use a GUI? 
What  would you like to do? Maybe we can help you.

---

### Post by ajax4 on 2014-11-26
> **nerdtron said:**
> My never ending question on these topoics: why need GUI?
Do you have a program that needs you to use a GUI? 
What  would you like to do? Maybe we can help you.

Never ending question? If you read my post you wouldn't have to keep asking! :D

---

### Post by lisati on 2014-11-26
> **ajax4 said:**
> Never ending question? If you read my post you wouldn't have to keep asking! :D
Please forgive us if we ask about the need for a GUI on a server, it's not commonly done as it can be a hog of resources and it's easy for many of us to forget that typing can be a problem for some. 

Would a web-based management system that runs in a browser, e.g. webmin, be an option for you?

---

### Post by ajax4 on 2014-11-26
I have a keyboard and mouse plugged into the server. I have the GUI installed and it loads when I turn the Server on. For the time being I can plug it into the internet should i need to download something. Eventually It will be mounted in a rack and will have connectivity for web based access/management. Initially It will be for web hosting and roaming file access.
What I'm aiming for is to have a similar set up to windows where a simple log-in will tell me if any services have stopped running or there are errors. 
I'm not a begginner with windows and can find my way arround a PC. Network and Servers are new to me, Linux might as well be Greek (appologies to any Greeks out there).
I would just like the oportunity to learn how to use a Gui'd system. I have difficulty typing.

---

