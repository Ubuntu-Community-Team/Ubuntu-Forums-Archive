---
title: "Booting Into a Program"
date: 2012-08-23
forum: Programming Talk
---

### Post by Spirrwell on 2012-08-23
Alright, the question doesn't directly tie into programming, but it's definitely a part of it, and I couldn't find a more suitable forum to post this in.

Let's assume I've written a program using OpenGL to render an image, a quadrilateral, a triangle, or whatever. How would I strip down a Linux distribution to do nothing but run that program? I don't want a user to have to login, or see all of the text or anything printed to the screen, I just want it to boot directly into that program and run it.

How do I do this?

---

### Post by spjackson on 2012-08-23
I haven't done this myself, but the term you want to search for is Kiosk, i.e. google for Linux kiosk or Ubuntu kiosk.

---

### Post by LiamOS on 2012-08-23
I'm really not quite sure what you're asking. 
Do you want to boot and have this program and only this program run, with user input?

If so, I presume you'll need your x server to be running for it, and this complicates things. The way I'd do it would be creating a system where a user is automatically logged in, and this program is spawned fullscreen in xorg without a window manager. You could possibly have a chain to initialize this; *startx* in your .bash_profile or wherever and then something like *program [with-options]* in your .xinitrc.
If you're security conscious though, and don't want access to anything other than your program, this'll be tricky.


Now comes the more fun stuff.
As far as masking the boot process goes, you'll need either a framebuffer theme of some sort or an initramfs. Now I know hardly anything about an initramfs, but I've created a few trivial ones, and this is what I'd look into if I were you. An initramfs allows you to run programs and such out of ram during the boot process, as far as I'm aware, and it may be possible, after a ton of fiddling and tinkering, to get your X and your program working in it. I don't know though, so this mightn't be possible.

---

### Post by Spirrwell on 2012-08-23
> **LiamOS said:**
> I'm really not quite sure what you're asking. 
Do you want to boot and have this program and only this program run, with user input?

Yes, but in my case this program would be a game.

The kiosk idea seems like it would work, but all of the kiosk tutorials I see are for the sole purpose of running a web browser. It doesn't seem that anybody has tried this with a game before.

Is there any tutorial that goes to a specific operating system that shows how to strip the OS so that it will run only a single program\game\whatever?

---

### Post by dwhitney67 on 2012-08-23
> **Spirrwell said:**
> Yes, but in my case this program would be a game.

The kiosk idea seems like it would work, but all of the kiosk tutorials I see are for the sole purpose of running a web browser. It doesn't seem that anybody has tried this with a game before.

Is there any tutorial that goes to a specific operating system that shows how to strip the OS so that it will run only a single program\game\whatever?

You are going to have to go the kiosk route, or the hard route that I took years ago with LFS (Linux from Scratch).

Suffice to say, you are not going to get away with running one mere program.  You will need to run a kernel (the OS), along with an X server.  You will also need to install the necessary libraries for your custom application to function properly.  These libraries will be the OpenGL stuff, but also the standard C library, and a slew of other libraries.

Here's an example list of packages that I had to build just to get the CD installer working so that the operator could install software onto the (medical) device that ran LFS:
```

[LIST]
[*]busybox
[*]e2fsprogs
[*]eject
[*]expat
[*]gcc
[*]glibc
[*]grub
[*]linux
[*]ncurses
[*]qt
[*]tinyxml
[*]X11
[*]xpm
[*]zlib
[/LIST]

```
I'm not stating that you will need all of these, but you will require the majority, and perhaps even more.

---

### Post by Spirrwell on 2012-08-23
I'm aware of that, I just want it to run that program\game at startup so you don't have any access to a terminal, system settings and whatnot, it simply boots the OS to run the designated program with the dependencies of the program. I basically want to make it seem like Linux isn't even there. I want to be able to boot it as Live CD or install it to a flash drive so I could use the hard drive or said flash drive for storing saved data.

Let's start small, let's assume I have a Linux distribution with the application and its dependencies installed. How do I remove all of the unnecessary things and make it load my program\game automatically? I've looked up the kiosk stuff, and all of the tutorials I could find were either outdated or for the purpose running a web browser only. Does someone know how to do this or know of any tutorial suited for what I want?

---

### Post by trent.josephsen on 2012-08-23
What is the fundamental difference between booting into a web browser and booting into a game? Can't you learn from a tutorial even if the end result isn't exactly what your goal is?

---

### Post by Spirrwell on 2012-08-23
The main focus of the tutorials was the web browser and running privoxy so one could only browse specific websites. The tutorials I found were showing how setup the browser and not necessarily showing how to strip down the OS for the browser, it's like they missed a step.

---

### Post by dwhitney67 on 2012-08-24
> **Spirrwell said:**
> The main focus of the tutorials was the web browser and running privoxy so one could only browse specific websites. The tutorials I found were showing how setup the browser and not necessarily showing how to strip down the OS for the browser, it's like they missed a step.

There are probably hundreds of tutorials that are available for you to peruse.  Just because you found one that doesn't quite fit your needs should not indicate that the end of the world is near.  You just need to persevere and continue your search.

In a snap, here's a tutorial that I found with a simple Google search:  [http://ianatkinson.net/computing/operakiosk.htm](http://ianatkinson.net/computing/operakiosk.htm)

All you have to do is skip the sections following the one with a heading of "Setting Up Opera" (and of course, the one that asks to install Opera/Java/etc; you would need to install OpenGL).

As for your application, it can be launched with the help of the script /etc/rc.local.

Now, if you are looking for a way to create a bootable CD or thumb-drive, then a full-blown OS is not what you need (it will not fit).  For this you will need to create a pruned-down OS.  I indicated earlier the minimum set of packages that would be needed to build a bootable CD (and to launch a Qt, not OpenGL, application).

There are a lot of details that are missing from my previous post; these details were painfully learned by going through the LFS (Linux From Scratch) tutorial.  You can find the details/tutorial of LFS here: [http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

If you are unwilling to even try going through the motions of creating a customized version of Linux for your needs, you can bet that no sane person will do it either... at least not for free.

In conclusion, now that you have been shown the path, the next step to take is yours.  Google incessantly for a solution, or just get your hands dirty.

---

### Post by spjackson on 2012-08-24
I don't know how you prevent any text appearing before you see your game, especially any text that the Bios may produce. There's kiosk info about this, but I haven't tried to digest it. In Ubuntu, plymouth displays a blank screen or image, but you can still press Esc and get a display of what's happening. You will need to research that some more.

In terms of running your game and nothing else, I can't see why you don't just put something in /etc/rc.local along the lines of

run_my_game # or maybe su some_safe_user -c run_my_game
halt # or reboot, or a loop to run the game again

I have tested this with a non-interactive OpenGL display program on my Raspberry Pi (debian wheezy based raspian distro) - easy to test because I can simply take out the SD card and stick it in my laptop to amend rc.local.

In terms of cutting down the installed packages, I think that if I was doing it, I'd probably start with something as small as I could find, maybe Arch, and build up, rather than starting with something large and stripping down.

Think about how you are going to trouble-shoot the system that you've made impossible to login to. I guess that if you can boot from removable media, then you're OK.

---

### Post by Spirrwell on 2012-08-24
> **dwhitney67 said:**
> There are probably hundreds of tutorials that are available for you to peruse.  Just because you found one that doesn't quite fit your needs should not indicate that the end of the world is near.  You just need to persevere and continue your search.


I never said I discontinued my search, but I am working on several things at once such as this, learning how to create a proper makefile, and etc. 

I actually found something that was very helpful that someone posted right here on these forums. It gave me an understanding of how running the game at boot is supposed to work by modifying the .xsession or .xinitrc.
> **lykwydchykyn said:**
> 
```

xset -dpms
xset s off
matchbox-window-manager &

while true;do
	rsync -qr --delete --exclude='.Xauthority' /etc/profiles.d/kiosk/ $HOME/

	wcgbrowser -f	
done

```


While I couldn't get it to work, it was still very helpful. I'll look over the tutorial you supplied and I'll probably get another distribution to test with, as I've been working with Slackware.

As for no text and whatnot showing, I was simply talking about text produced by the operating system, nothing to do with the bios. Basically all of the things the operating system checks before it fully boots such as Checking state of something... [OK]

Thank you, I'll look into everything I can now.

---

### Post by Spirrwell on 2012-08-24
Alright, I switched over to Linux Mint since I am familiar with it and I wrote a small program that uses SDL, I tested it, it ran fine. I copied the program named "SimpleSDL" to /usr/local/bin and modified the rc.local file from:

```
exit 0
```

to

```

SimpleSDL
exit 0

```

I did this to simply see if the program would run, and I assume it wouldn't run that exit code until the program is closed. It didn't work.

The file did have some comments that said to use this file you need to change the bit order, of course I don't know what it was talking about, but I assume I'm missing something.

So in short, what am I doing wrong?

---

### Post by spjackson on 2012-08-24
> **Spirrwell said:**
> 
```

SimpleSDL
exit 0

```I did this to simply see if the program would run, and I assume it wouldn't run that exit code until the program is closed. It didn't work.

The file did have some comments that said to use this file you need to change the bit order, of course I don't know what it was talking about, but I assume I'm missing something.

So in short, what am I doing wrong?
I would be very surprised if /usr/local/bin is in PATH when rc.local is executing. On Ubuntu it is /sbin:/usr/sbin:/bin:/usr/bin

So
```

/usr/local/bin/SimpleSDL
exit 0

```However I suggest you run the application from a console session first, rather than rebooting to test it, in light of your remark about bit order.

---

### Post by Spirrwell on 2012-08-24
Alright I got it to sort of work. My program starts and displays a bitmap image of the earth.

The problem is the program loads slowly, and it doesn't respond to my keyboard input. It also won't load in my monitor's native resolution of 1680x1050. It loads as if I were running it from the console without a window manager, which I didn't even know that was possible. I'll work on it some more.

Edit: Okay I realized that the program does respond to my input until I press the escape key to try and quit. It will just hang there.

Edit2: As for that bit order thing, it actually says that by default the rc.local script does nothing, and in order to enable it you have to change the execution bits

Also, it seems as though it will only boot into my program every couple of reboots.

---

### Post by Spirrwell on 2012-08-25
Alright, I've only be doing this through VirtualBox, but Windows 8 crashed and somehow GRUB re-installed itself on my computer when I know for a fact I had overwritten it installing Windows 8. So I had access to Linux Mint on real hardware, and I did a little more playing around.

I re-wrote the same program and was able to launch it directly from the CLI fullscreen, although if I tried to quit the program, it would crash. I couldn't run a program I wrote that used OpenGL with the error "OpenGL is not available."

Before I tried launching the matchbox desktop environment directly from the rc.local file, it didn't seem to do anything. I don't currently have matchbox installed and I'm in Windows 7 at the moment, but what file\command should I use for initializing X with one of the desktop environments so I could load up a program that does use OpenGL and whatnot?

This has actually been a fun learning experience so far, I'll keep messing with it.

---

### Post by conradin on 2012-08-26
Koisk is one direction, tough it would seem to come with a lot of extra overhead. whats this 1 program running on? Is embedded linux an option?

theres lots of striped down versions of linux, stuff like DSL, and tinycore, or compile only what you need with gentoo. I would consider booting in to single user mode, or possibly, multiusermode (2) w/o networking. 

something like this might be of interest.
[http://www.linuxchix.org/content/courses/kernel_hacking/lesson2](http://www.linuxchix.org/content/courses/kernel_hacking/lesson2)

---

