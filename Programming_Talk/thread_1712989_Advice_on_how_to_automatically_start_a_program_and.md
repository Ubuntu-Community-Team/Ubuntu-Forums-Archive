---
title: "Advice on how to automatically start a program and keep it running"
date: 2011-03-23
forum: Programming Talk
---

### Post by GeoMX on 2011-03-23
I have some push buttons connected to the parallel port of my computer, I've created a program that polls the parallel port every X seconds and takes an action if it detects the button is being pressed. This is a console program that executes inside an infinite loop, it reads the status port and sleeps for X seconds.

For testing, I open a terminal and execute the program, it works fine. Now , I want to have this program running always on my system, but I don't know how should I do it, what are the options for having this program start and keep running automatically?

I'm reading about creating a daemon process, but would like to know whether converting my program to a daemon would be a good solution of there are better alternatives.

Thanks in advance for your help.

---

### Post by cavh on 2011-03-23
Suggest writing a small bash script using your favourite text editor.

The bash script would look like this:

```
#! /bin/bash

[insert here the command to start the application]
```

Save the script and then make it executable as follows: in a terminal, navigate to the folder containing the script, then type 

```
chmod u+x [enter script name here]
```

Then set the script to run at system startup by calling it in System, Preferences, Startup Applications (see screenshot attached).

PS: I read your blog and learnt some new things! Cool, thank you.

---

### Post by GeoMX on 2011-03-24
I will try your suggestion, although I forgot to mention I'm planning on using this program on a computer without GDM/Gnome :).

> **cavh said:**
> 
PS: I read your blog and learnt some new things! Cool, thank you.
I'm glad you found something useful :). Thanks for your comments.

---

### Post by Grey on 2011-03-25
You are probably looking for this article in the Debian Administration guide.

[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by GeoMX on 2011-03-25
@Grey, thanks for the info, your suggestion seems "more appropriate". I'm also having a look at upstart jobs, I'll let you know my results.

---

### Post by Cheesehead on 2011-03-25
Well, Ubuntu uses upstart instead of sysvinit...though it maintains compatibility.

Upstart is more flexible in it's start/stop crtieria, can listen for (or emit) emitted events, and can respawn your daemon if it crashes.

---

### Post by GeoMX on 2011-03-26
Thanks for the comments, those are the reasons why I was trying upstart. However, what I'm doing is this:

I converted my program to a daemon process and launch it from the X init script (/etc/X11/xinit/xinitrc) because I'm simulating keyboard events using xdotool, and it seems to work only if it is launched within the same X session that I want to send keyboard events to. It is working fine, but I'd like to know how (if possible) I would start my program using upstart.

---

### Post by hakermania on 2011-03-26
Also, try making a .desktop file at ~/.config/autostart and that links to your application. This works fine for me...

---

### Post by Cheesehead on 2011-03-26
Well, if you really want to use upstart for this...

Add a line to /etc/X11/xinit/xinitrc to emit an event. Let's call the event 'x-server-up'
(Uh, I'm making the assumption here that the script running xinitrc has (root) permission to run initctl. I haven't checked.)
```
initctl emit x-server-up
```


Add an upstart listener to /etc/init. The name of the listener should have a '.conf' suffix, and I name them so I can locate them again, like 'CHEESEHEAD-keyboard-simulator.conf'. When it hears the event, it triggers your script.
```

start on x-server-up

script
/path/to/my_script.sh
end script

```
There's more to the details, like respawning, stopping/restarting criteria, etc. But this gets you started with Upstart events.

---

### Post by GeoMX on 2011-03-28
Actually, I decided to use an upstart job to keep an X session running, if X gets terminated (either killed or by pressing Ctrl+Alt+Backspace) it is restarted by an upstart script in /etc/init. So I think launching my program from the xinit script is a "good" way of doing what I wanted :).

Anyway, I want to try launching the program using upstart so that it can be kept running and restarted if killed (independent from the X respawn), I won't be killing it (intentionally) but just in case, and just for the purpose of learning a bit more about Linux ;).

Thank you so much for all of your comments.

---

