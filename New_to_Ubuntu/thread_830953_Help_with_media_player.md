---
title: "Help with media player"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Zenze on 2008-06-16
I am still very new to Ubuntu and was interested in learning about making scripts and different commands. I have been reading a lot and thought that making a little alarm program that would play music at a specific time would be fun.

But heres the problem... I have been using Rhythmbox as my media player, but I don't think that you can make it play files or playlists from the terminal. I checked the man page and the --help page and didn't see anything that that looked like what I wanted.

Does anyone know if Rhythmbox can be used from the terminal? If not, what music player could I use to do this?

---

### Post by aktiwers on 2008-06-16
mpd or cplay are both terminal based players and can be installed with:
```
sudo apt-get install <appname>
```

where appname is cplay or mpd without braces..

---

### Post by Zenze on 2008-06-16
Ok cool, I will give those a try.

So there are no graphical players that can also be run from a terminal?

---

### Post by pedro_orange on 2008-06-16
You can invoke RB from the terminal. Just type in rhythmbox.

Check out it's manual for opening options.

```
man rhythmbox
```

I don't know if it will do what you want to do. But perhaps with some cheeky piping you might be able to get it to work through RB.

Good luck.

---

