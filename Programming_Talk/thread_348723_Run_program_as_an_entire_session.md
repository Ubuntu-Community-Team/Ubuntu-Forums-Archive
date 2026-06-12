---
title: "Run program as an entire session"
date: 2007-01-29
forum: Programming Talk
---

### Post by kripkenstein on 2007-01-29
Is there a way to run a program as a session? What I want is to choose between "GNOME", "KDE" and some FPS game, at the graphical login screen. This way, the FPS game will run (fullscreen), without the overhead of an entire GUI and desktop environment.

Then when I exit the game, I want to get back to the graphical login screen, so I can get back to my GUI (and perhaps do some work).

Any ideas on how to do this? I know that the directory "/usr/share/xsessions" has files for the sessions that are offered at the graphical login screen. So if I create a file there for the FPS game, would that work? I guess I don't understand enough about the 'bootstrap' process in Linux - would the FPS be able to access the screen, audio, etc., at all?

---

### Post by LotsOfPhil on 2007-01-29
That's a pretty neat idea. I am mostly replying just to subscribe to the thread.

Could you just boot to a command-line only, or just X? It isn't quite as automated as what you describe, but should lose you some of the overhead.

---

### Post by jblebrun on 2007-01-29
> **kripkenstein said:**
> Is there a way to run a program as a session? What I want is to choose between "GNOME", "KDE" and some FPS game, at the graphical login screen. This way, the FPS game will run (fullscreen), without the overhead of an entire GUI and desktop environment.

Then when I exit the game, I want to get back to the graphical login screen, so I can get back to my GUI (and perhaps do some work).

Any ideas on how to do this? I know that the directory "/usr/share/xsessions" has files for the sessions that are offered at the graphical login screen. So if I create a file there for the FPS game, would that work? I guess I don't understand enough about the 'bootstrap' process in Linux - would the FPS be able to access the screen, audio, etc., at all?

Yes. An "Xsession" is a xsession for the Xserver, which is loaded last in the LInux bootstrap process. If your game was, for example, tuxracer, you should be able to create an xsession like:

(EDIT: My original response used xdm xsession format)
```

[Desktop Entry]
Encoding=UTF-8
Name=My Really Fun Game
Comment=Just the game!
Exec=/usr/bin/myreallyfungame --fullscreen
Terminal=False
TryExec=/usr/bin/myreallyfungame --fullscreen
Type=Application

[Window Manager]
SessionManaged=false


```


And when you login with this session, it will play the game, and when you exit the game, it will go back to login.

Caveat: I haven't tried this myself, but it *should* work...

---

### Post by featherking on 2007-01-29
I had the same idea a while back, got it to work exactly as you describe see my original thread [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=184953"). I built a mame arcade machine and used ubuntu as my OS and had a mame emulator right after login. It works sweet, because if i need to use gnome for any reason i can just quit the emulator and im back at the login screen..

---

### Post by kripkenstein on 2007-01-30
Thanks for the advice, guys. I'll get to hacking and see if it works...

---

