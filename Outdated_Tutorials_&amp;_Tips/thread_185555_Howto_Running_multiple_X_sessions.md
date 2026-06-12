---
title: "Howto: Running multiple X sessions"
date: 2006-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by NXArmada on 2006-05-31
**How to start X sessions**

There are two ways to start the first X session: you either start the X Window System manually after logging in, or X starts automatically when your Linux system boots up. If your system is configured to start X automatically, you don't have to worry about the first X session: it's already running.

If you don't have a graphical login, you probably start X with the startx command after logging in:
[COLOR="RoyalBlue"]startx[/COLOR]

The first X session you start runs on screen 0. It does this by default, so when you start an X session, you don't have to specifically tell it to run on screen 0. However, you can run the second X session on screen 1, the third on screen 2, and so on. This is how you tell X to run on screen 1:
[COLOR="RoyalBlue"]startx -- :1[/COLOR]

Of course, to run X on screen 2, you'd use the command [COLOR="RoyalBlue"]startx -- :2[/COLOR], and so on.

**Switching between X sessions**

You probably know you have several virtual terminals. On a default Linux configuration, you have command line sessions running on your first six virtual terminals. Your first X session is running on the seventh virtual terminal (screen 0). If you're running only one X session, all the terminals after terminal seven are empty.

As you probably guessed, the second X session runs in virtual terminal eight, the third session in virtual terminal nine, and so on. You switch between X screens the same way you switch between virtual terminals: Press Ctrl, Alt and the F key with the desired terminal's number.

For example, to switch from screen 0 to screen 1 (from the first X session to the second one), you'd press Ctrl + Alt + F8. To go back to the first X session, you use Ctrl + Alt + F7.

**Useful tips**

When starting multiple X sessions with startx, make sure you have a file called .xinitrc in your home directory. It's the file that controls things like what window manager is started. For more info about .xinitrc, have a look at the Changing the default window manager tuXfile.

Because the default screen is 0, some graphical applications may get a bit confused when using other screens. If you type an application's name at the command line of a terminal emulator, the application may run on screen 0 although you launch it from another screen. This isn't a problem, though. Many applications have a command line option for specifying the screen it runs on. For example, to run Gimp on screen 2, you'd start it with:
[COLOR="RoyalBlue"]gimp --display :2[/COLOR]

This is actually an advantage. You can launch the application from any X session or virtual terminal you want and send it to any X screen you like!

No one is forcing you to use the same window manager or configuration in all the X sessions. This is probably one of the reasons you'd want to run multiple X sessions at the same time: to be able to quickly switch between different window managers, resolutions, or color depths.

To have an X session with another color depth than the default one, you'd use the -depth option. For example, to run a second X session with a really ugly 8 bpp color depth, you'd type:
[COLOR="RoyalBlue"]startx -- :1 -depth 8[/COLOR]

Of course there are much more options than just the -depth option. To get more help with startx, check out the manual page:
[COLOR="RoyalBlue"]man startx[/COLOR]

[COLOR="DarkRed"]This Will Work With All Version of Ubuntu[/COLOR]

Original howto by: Nana Långstedt < nana.langstedt at gmail.com >

---

### Post by steveneddy on 2006-06-03
In my experience, the F8 key is for the "behind the scenes" Ubuntu code that runs under the GUI, and the second screen will be on the F9 key. I have done this many time to show friends and it is very cool. I sue the F1 screen for general command line work and go to Gnome for surfing. I also use centerICQ for my chatting on F2.

Happy Computing!

-SE

---

### Post by Lil_Eagle on 2006-06-06
This is nice, but on my system crashes (total freeze) when I press ctrl-alt-f7 to get back to my first session.

I'm not sure why this happens.  My video is set up fine, using the latest fglrx and it works as it is supposed to according to all of the threads about that stupid proprietary driver.

I have entered several messages about it but nobody seems to have a clue as to why this is happening.  I don't really think my problem belongs in the HOWTO section, but I am sort of desparate.

---

### Post by caldevil on 2006-06-07
[QUOTE=Lil_Eagle]This is nice, but on my system crashes (total freeze) when I press ctrl-alt-f7 to get back to my first session.

I'm not sure why this happens.  My video is set up fine, using the latest fglrx and it works as it is supposed to according to all of the threads about that stupid proprietary driver.

I have entered several messages about it but nobody seems to have a clue as to why this is happening.  I don't really think my problem belongs in the HOWTO section, but I am sort of desparate.[/QUOTE]
As Far as I remember this is related to using fglrx on 686 machine. Try using ati and see if you have the same problem there too.

---

### Post by chphilli on 2006-08-24
> As Far as I remember this is related to using fglrx on 686 machine. Try using ati and see if you have the same problem there too.

Does anyone know what is causing this problem for sure? I would really prefer to use the fglrx driver, for the acceleration ( since Xgl doesn't work well without it ), but I'm plagued by this issue as well. 

The thing that intrigues me is that the **entire system** hangs when you switch back to the Xserver from a virtual terminal. I've shown this by being logged in from another machine via ssh, switched away from X and then back, and then tried to do anything via the ssh connection. Nothing happens - there is no response from the host machine. 

Replies to chphilli (at) Google's mail service.com would be great, but I'll try to check back here as well. 

Thanks!

---

### Post by motin on 2008-01-21
Just a note: Since Feisty (or was it Gutsy?) - all you have to do is to go to Apps -> System tools -> New login to start a new X session.

---

