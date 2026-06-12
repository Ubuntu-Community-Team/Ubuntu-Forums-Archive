---
title: "OpenGL outside Desktop Environment"
date: 2008-10-22
forum: Programming Talk
---

### Post by ChurroLoco on 2008-10-22
I would like to try to create a box that starts directly into an OpenGL program and does not start the desktop.  Does anybody have any ideas how to do this.  I'm used to getting the rendering context of a window.  I really don't know how to grab one from the command line.

---

### Post by snova on 2008-10-22
If you're trying to render OpenGL from a command line (without X running), there's no way to do that. You don't have to start the entire desktop environment, but X is necessary.

Fortunately, I think the command used to start X can take a parameter, the program to run as the root window. Something along the lines of "xinit my-program", I think.

---

### Post by rnodal on 2008-10-22
Linux from scratch may be what you are looking for. Just build what you need in order to have a X Server running then instead of launching any gnome, kde etc just launch your custom application. I'm assuming that by "box" you mean a computer you own so you do need drivers so things like the keyboard, mouse, video card, hard drive etc work. Unless you have your own custom hardware then you will need to code our own drivers etc etc.

-r

---

### Post by snova on 2008-10-22
LFS is overkill. He doesn't need to make a custom Linux distribution, he just needs X to start something other than the default session.

Just install a minimal distribution with the necessary packages to run X, then tweak whatever is necessary to have it automatically start X with your program on boot.

---

### Post by slavik on 2008-10-22
look into kernel framebuffers and see if you can use that. this is how mplayer can play a video file without X running. this is also the same way that knoppix displays the tux logo when it is booting.

---

### Post by mike_g on 2008-10-22
I made an app that runs on a startup script. Basically, it loads before the Window Manager, so its effectivly full screen w/o a WM. When you quit wth WM loads tho. Probably not exactly what you're looking for, but anyway.

I'm sure its possible.

---

### Post by snova on 2008-10-22
I have doubts as to whether framebuffers have an OpenGL implementation.

---

### Post by ChurroLoco on 2008-10-24
I was planning on still using X, but I wasn't sure how difficult it would be to jump right into an OpenGL program.  As I said I'm so used to getting a rendering context through a window.  

The reason I'm asking is because I am making an arcade game, and I don't want the overhead of a window manager... nor do I ever want the player to see a desktop.  

I will be using my own hardware which I'll need to make some drivers for, but that is covered.

Thanks for all your help though. You guys fueled my thought-sickles.

---

### Post by a_guerere on 2008-11-25
ChurroLoco, what did you do at the end? Used LFS or used a normal distro w/o a window manager? Or neither of that?

I am exploring those same options and am looking into LFS...
I have a very similar project, just launch an OpenGL app after boot.


> **ChurroLoco said:**
> I was planning on still using X, but I wasn't sure how difficult it would be to jump right into an OpenGL program.  As I said I'm so used to getting a rendering context through a window.  

The reason I'm asking is because I am making an arcade game, and I don't want the overhead of a window manager... nor do I ever want the player to see a desktop.  

I will be using my own hardware which I'll need to make some drivers for, but that is covered.

Thanks for all your help though. You guys fueled my thought-sickles.

---

