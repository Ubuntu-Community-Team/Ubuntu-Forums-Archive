---
title: "How to run firefox from command line on server"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by SumYunGy on 2008-06-16
Was a casual user of Unix 10 years ago. Have forgotten most everything. Today installed 8.04 server on a virgin disk. Then installed firefox. Tried to run firefox from command line but get error message about no display. What is correct command?

---

### Post by rraj.be on 2008-06-16
```
gksudo firefox
```

---

### Post by RomeReactor on 2008-06-16
Hi. Which graphical environment are you running? I would advise against running Firefox as root, though.

---

### Post by ibutho on 2008-06-16
What was the exact error message? Were you logged into an X session when you tried to run Firefox?

---

### Post by rraj.be on 2008-06-16
i am too sorry for providing root privilege for firefox.

You can remove it by just typing firefox without any gksudo in front of that.

---

### Post by cariboo on 2008-06-16
If you installed the server version with out adding a gui, your best bet would be links:)

Jim

---

### Post by Sinkingships7 on 2008-06-16
If you're running a server install, then you probably don't have a graphical shell to run your applications on. This code will install the standard X11 graphical shell, used for all Linux desktops. Don't worry, this won't give you a desktop to play with and ruin your beautiful command line shell, just give you an interface for whenever you need to run a graphical application:
```
sudo aptitude install xorg
```
EDIT: Of course, you can then proceed to run Firefox by typing the command **firefox** into the shell.

Also, I'm not sure if it will launch X11 for you by default. If it doesn't, type the command **startx** into the shell, upon which you will be presented with X11 and a small terminal window. Then you can type **firefox** into that terminal, and you should be good to go.

---

### Post by st33med on 2008-06-16
Yes, as a few other posters above me have said, Ubuntu does not use a GUI in it's servers. Best to learn the ways around the terminal, eh? :)

Firefox does not run in the terminal without an X11 display, but, there is other text web browsers. The best one to use, IMO, is links2:
```
sudo apt-get install links2
```

---

### Post by omstaal on 2009-08-05
Hi guys. I am trying to do something like the original poster. I have installed ubuntu 9.04 server (command line only) on a somewhat old laptop that I want to run Firefox and only that, just to surf the net. I installed xorg and firefox. Doing xstart gives me a terminal window in the top left of the screen, but it only uses about 1/3 of the available screen. Typing firefox in this window gives me firefox in the top left corner, still only using 1/3 of the screen. Typing firefox -width 1024 -height 768 gives the same. I also tried xinit firefox from the command line shell, same result.

I have fiddled about with /etc/X11/xorg.conf to add the highest resolution I know the screen can take (1024x768) under the Display section. Does anyone have any other tips for me as to what I can try to get the X environment to use the full screen?

The laptop has a 1024x768 screen, is a Pentium III with 256Megs of ram (thus the need for the bare bones setup). I have tried xubuntu, it is still too heavy. I also had a go at fluxbuntu and crunchbang, the former did not install correctly, and the latter was way to slow too.

---

### Post by ugm6hr on 2009-08-05
> **omstaal said:**
> The laptop has a 1024x768 screen, is a Pentium III with 256Megs of ram (thus the need for the bare bones setup). 

Have you considered just adding a WM/DE?  A barebones setup with LXDE will run very nicely on 256mb ram.  Although I used Opera rather than FF, I don't see that should limit you.

See the LXDE link below for details (details relate to 8.04/8.10, but should apply to 9.04 too).

Other option is PuupyLinux, which works flawlessly on 256MB.

---

### Post by halitech on 2009-08-05
I have a Celeron 1.0gig with 256meg of ram and I used the instructions here to do a minimal install of Debian with XFCE4 which runs nicely

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

You could also do the first few steps and change xfce for lxde

---

### Post by Terl on 2009-08-05
Just to chime in quickly, I have found dillo to be a nice fast little browser as well.  Still needs X but it is very lightweight.  

I second the suggestion of Puppy Linux - excellent on lower spec boxes.  Damn Small Linux is good as well.

---

### Post by omstaal on 2009-08-06
Thanks guys!

I tried lxde, it worked like a charm. Since I was on a server install I could skip a lot of the instructions.

Thank you for the tips!

---

