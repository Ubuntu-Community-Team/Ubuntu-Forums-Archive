---
title: "Play avi from command line?"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by vorophobe on 2012-09-02
Hey, I am logged into a terminal (tty1) and am trying to watch an .avi movie from the command line using mpg321

However when I run the movie, the video is displayed as like ASCII art. The sound works fine

Is it possible to watch movies from the terminal? :P

Thanks

---

### Post by Laiquendi on 2012-09-02
You want to watch graphics in terminal? Not possible because it does not support it :P
If you want to run another program like mplayer or something from terminal, to watch on that program then what's the point? But.. you can, simply install program like mplayer and run it from the terminal.

---

### Post by nothingspecial on 2012-09-02
> **Laiquendi said:**
> You want to watch graphics in terminal? Not possible because it does not support it :P


Yes it does. You need to use the framebuffer.

---

### Post by vorophobe on 2012-09-02
> **nothingspecial said:**
> Yes it does. You need to use the framebuffer.

Wow thanks a lot! Really helps me!

---

### Post by angry_johnnie on 2012-09-02
If you have the framebuffer enabled, it's possible.  Vlc will play videos in ascii art.  Mplayer will play the videos in their original format.

I added this alias to my $HOME/.bashrc

```
alias mplay='mplayer -vo fbdev -zoom  -fs -x 1280 -y 1024'
```

So, when in tty, i just cd to the videos directory, and run mplay nameofvideo.  it plays in fullscreen, with a 1280x1024 resolution.

You can adjust that to fit your own monitor.

---

