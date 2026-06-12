---
title: "Reaccessing started processs when logging in via ssh"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by ads2996 on 2014-06-27
Hi, 

I run a few different minecraft servers depending on what we feel like playing. I am heading away, but will have Internet, I plan to leave the laptop on and login via ssh to start and stop the servers, but I was wondering if I start the server then close my ssh session is the anyway to get back to the minecraft console to stop it properly? 

Thanks in advance

---

### Post by donkyhotay on 2014-06-27
by default if you log out of ssh any services you started will end when you log out of ssh. You will need to use screen so that you can not only view your session when you log back in but so that the services/programs you are running won't quit when you log out. Do a google search for screen tutorial and you'll find some good ones that will give you the basics.

edit: I would also play around with your server through SSH at home before you leave. Last thing you want to do is find you set something up wrong and can't make the changes that you need while you're gone.

---

### Post by ads2996 on 2014-06-27
is screen kind of like vnc? yeah once i get packed im gona sort out all the kinks and make sure it works :)
thanks for the quick reply

---

### Post by donkyhotay on 2014-06-27
No, screen is nothing like VNC. VNC is a system for viewing a GUI system on a remote system. SSH is used to connect to a remote system in a CLI (Command Line Interfaces / Terminal). Screen allows you to have multiple CLI sessions running at the same time. It isn't something you run from the client but something you run on the host/server after you log into it. It has to be installed on your server but it's in the repos so that's easy to do "sudo apt-get install screen". I'd really recommend reading the tutorials but probably the simplest way I can think of explaining it is like having multiple tabs on a browser. When screen is running by default you have your standard prompts but you can detach the current session (or tabs if you're thinking GUI terms) so that you're not looking at it anymore and instead are looking at a new session with a new prompt. The old session is still running, it's still doing whatever it was when you detached it and if you want you can reattach the session and look at it again. Similar to having multiple tabs open on a browser. It takes some getting used to though because unlike tabbed browsing there is nothing to click on or even tell you what session you're in or how many you have open. Remember, this is for CLI so everything uses keyboard shortcuts. Now you might not need all this other stuff like running multiple session at once (but once you get used to it's really nice, especially if you use SSH alot) but the main thing is that if you SSH into your server, launch screen, start minecraft, detach the screen, then log out of SSH your minecraft server will happily run away and next time you log in you can reattach the screen and see everything it would show you if you had stayed connected the whole time. However if you SSH into your server, start minecraft and then log out of SSH, minecraft will shut down because it is considered a child of your SSH session and when you end that everything you were doing (including minecraft) shuts down too. So you need to read a screen tutorial to learn at least enough to keep your server running while you administer it remotely by SSH.

---

### Post by sandyd on 2014-06-27
Screen allows you to keep "Screens" in the background - which will run even if your not connected to the computer.

Check this out

1. Stop all your minecraft servers.
2. Make sure screen is installed
3.
```

screen -S minecraft1
```
4.
Start minecraft
5. Press Control A+D to detach the screen
6. Repeat the process for the other servers, incrementing the screen name (i.e. minecraft1, minecraft2, and so on)
7. Type ```

screen -R
```

You will find that all the screen sessions you started earlier... are all running!

You can attach the screen sessions using a command such as
```

screen -R minecraft1
```

---

### Post by donkyhotay on 2014-06-27
> **sandyd said:**
> Screen allows you to keep "Screens" in the background - which will run even if your not connected to the computer.

Check this out

1. Stop all your minecraft servers.
2. Make sure screen is installed
3.
```

screen -S minecraft1
```
4.
Start minecraft
5. Press Control+D to detach the screen
6. Repeat the process for the other servers, incrementing the screen name (i.e. minecraft1, minecraft2, and so on)
7. Type ```

screen -R
```

You will find that all the screen sessions you started earlier... are all running!

You can attach the screen sessions using a command such as
```

screen -R minecraft1
```

Default screen hotkey on Ubuntu server is Ctrl-a and then then the shortcut key. This is actually the official default though I believe it can be changed but I don't know since although I use screen often when administering my own personal server with SSH quite often I've never bothered to try to reconfigure it. Which means to detach you need to press Ctrl and A at the same time, let go, then press d (for detach) and it will detach the screen. Ctrl-d by itself does nothing since screen assumes any command that doesn't start with it's own specific hotkey combo is meant for whatever program you're running inside of it like minecraft but also vi, nano, lynx, etc. Again do a google search for "linux screen tutorial" and you'll find lots of stuff to get you going.

edit: also if you're going to specify custom sessionnames make certain they're all unique (I.E. minecraft1, minecraft2, etc.).

---

### Post by sandyd on 2014-06-27
> **donkyhotay said:**
> Default screen hotkey on Ubuntu server is Ctrl-a and then then the shortcut key. This is actually the official default though I believe it can be changed but I don't know since although I use screen often when administering my own personal server with SSH quite often I've never bothered to try to reconfigure it. Which means to detach you need to press Ctrl and A at the same time, let go, then press d (for detach) and it will detach the screen. Ctrl-d by itself does nothing since screen assumes any command that doesn't start with it's own specific hotkey combo is meant for whatever program you're running inside of it like minecraft but also vi, nano, lynx, etc. Again do a google search for "linux screen tutorial" and you'll find lots of stuff to get you going.

edit: also if you're going to specify custom sessionnames make certain they're all unique (I.E. minecraft1, minecraft2, etc.).

Thanks for catching my typo - fixed :D

---

### Post by nerdtron on 2014-06-27
SCREEN!!!! One of the best utilities ever :)
Here's a very quick and concise tutorial on what it is and what it does [http://www.howtoforge.com/linux_screen](http://www.howtoforge.com/linux_screen)

EDIT: Don't press CTRL+D on the screen process or even on the terminal. If you have a blank prompt, pressing it means "exit".

EDIT: I think the title of this thread needs to be "Reaccessing" instead of "Reassessing".

---

### Post by ads2996 on 2014-06-28
i have managed to set up and screen is exactly what i am looking for and works wonderfully. I have a problem cause when i reboot via ssh with the lid closed on the laptop it goes to sleep once my user is logged out, ( well i think that is where it sleeps). I have disabled sleep in the power options menu. I have no idea why it is doing this.

---

### Post by ads2996 on 2014-06-28
> **nerdtron said:**
> SCREEN!!!! One of the best utilities ever :)
Here's a very quick and concise tutorial on what it is and what it does [http://www.howtoforge.com/linux_screen](http://www.howtoforge.com/linux_screen)

EDIT: Don't press CTRL+D on the screen process or even on the terminal. If you have a blank prompt, pressing it means "exit".

EDIT: I think the title of this thread needs to be "Reaccessing" instead of "Reassessing".

I realised after that the title was wrong I was typing on my phone so predictive text got in the way. I can find out how to change it.

---

