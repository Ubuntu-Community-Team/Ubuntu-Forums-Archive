---
title: "Beginning Ubuntu 11.10 &quot;Am I Right?&quot;"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Maese909 on 2012-01-20
Hello all. I am new to the world of Linux and so far am loving what I am seeing! I am studying the Terminal and have a few questions... Below is what I have comprehended so far. Obviously, I don't know the hardcore details, so let me know if this is on the right track). Anyway, here's my 2-sense..

So basically there is whats called a 'shell.' This shell is a wrapper around Linux so to speak that gives you access to folders, files and so on. The shell comes in two flavors.. the GUI and the CLI.
The CLI shell can be accessed via the Terminal, whereas the GUI shell is accessed by default when the user logs in. The CLI shell, when used via the Terminal, is called a BASH shell.

p.s. Don't go too crazy with the details, I am still very new at this stuff :D

---

### Post by grahammechanical on 2012-01-20
Oh, it gets more complicated than that! To start with BASH = Born Again Shell, which Wikipedia tells me is a free software replacement for the Bourne Shell, which in turn replaced ... No. No. Enough is enough!

Lets us just say that from the beginning Linux has always had a command line interface = CLI.

Later some clever and hard working people developed ways of giving Linux a Graphical User Interface. Others liked this idea but wanted to do things differently. And so we have a couple of desktop environments and several window managers. And so on. And so on.

There are two things you will learn when you start going on Linux forums. There is more than one way of doing things and everybody has an opinion.

Regards.

---

### Post by Double.J on 2012-01-20
Hi there!

Glad you're taking an interest!

Just to clarify, a "shell" should not be confused with gnome shell - the GRAPHICAL user interface. Bash is the shell used in ubuntu, and is the open sourced shell used by the gnu project. A Shell is a comand line interface for the OS.

A couple of things - first as stated, a shell is a command line interface for users to "operate" the OS without having to engage with it's inner workings - you just type commands to do the things you want it to do, a CLI with no GUI.

Second is that Linux is really GNU/Linux - the linux kernel with the GNU project's tools, combined together to make the basis of the operating system we love! The GNU project's initial goal was to make an open source version of the unix OS - the most important part of this to the end user is the shell - UNIX's shell was called the Bourne Shell. BASH is as I say the open source version of the UNIX Bourne Shell - designed to work in the same way but without using any of UNIX's closed source code - a command on BASH is identical to a command on SH to the end user, but what's going on underneath is different ;)

BASH = Bourne Again SHell ;)


As for the GUI that you mentioned. Whether it be Gnome, KDE or whatever, at present it's all using the X server from The X window system (X11) that makes up the GUI experience on all Linux distros. As the name suggests, X is a server, running on a higher level than the CLI - basically a cli running xserver running gnome. It is not a shell in the same sense that BASH is :)

Did you know that you always have 6 shells available not using X?

press CTRL+ALT+F1 and log in :)... F1 to 6 are different CLI shells, and as linux is a multi user OS, different users can be signed into different shells at the same time ;) **Press ALT+F7 to get back to the GUI land!**

Also try restarting ubuntu in recovery mode - at the CLI, log in then use the command "startx" to run the Xserver on top of the CLI shell.

To get a better definition, I'd look up some of the terms mentioned on a site such as Wikipedia

Hope it helps!

---

### Post by Maese909 on 2012-01-20
Holy @$@$. I pressed Ctr+Alt+F1 and my whole monitor went black with a login like you said. It was the same experience as I had with the terminal as far as the commands are concerned. I see what you mean when you say there are 6 shells to be used. I couldn't figure out how to get back to the GUI until I hit F7 lol.
Now thats what I call a life-changing experience!

Real quick question... so there IS a shell in GUI form.. this is called Gnome shell for Ubuntu? The shell in CLI form (for Ubuntu) is called bash, correct?
Man, this stuff is incredible...

---

### Post by Double.J on 2012-01-20
HaHa sorry about that.. adding the F7 escape route to my previous post.....

Oh btw, whilst in the CLI (F1 to 6) you only need to press ALT and the Function number to switch windows - CTRL+ALT is only necessary in the GUI because of keyboard shortcuts... you'll probably use ALT+F4 to close a window, or ALT+F2 to  run programs more often than you want to use the second and fourth shells!

---

### Post by Maese909 on 2012-01-20
Ok. So what you are saying is the fourth shell is used to close windows, and the second shell (Alt+F2) is used mainly to run programs? Also, is there a way to browse the Internet when in the CLI shell?

P.S. I editied my post where I said holy @$@$ in case you didn't see

---

### Post by Double.J on 2012-01-20
> **Maese909 said:**
> Real quick question... so there IS a shell in GUI form.. this is called Gnome shell for Ubuntu? The shell in CLI form (for Ubuntu) is called bash, correct?
Man, this stuff is incredible...

Hi there, No, gnome shell is different - it's a bit complicated; In the context of your original post, it isn't a shell at all. No GUI can be a shell in that sense. 

The Shell is the CLI, whether it's called BASH, or SH or whatever - that's the *nix shell. Best to think of it in the terms of a shell covering a snail - the snail is the OS, the shell goes on top and is the only way you'd want to touch the snail.

The GUI runs on top of the shell - our snail is now wearing a jumper that's bright and colourful and nicer to touch than the snail's shell (this is one damn fast powerful snail btw) This Jumper is our GUI - the top level. The GUI needs the CLI level to exist - its always snail->shell->jumper. This is different to Windows that is slug-Jumper (no underlying shell on slugs)

The Gnome shell I mentioned (Sorry for confusing you - I though this is what you were referring to) is best though of as a brand name in this context. Gnome is a desktop environment. As of 2011, we're now at Gnome version 3 - the project is massive and complex, and gnome "shell" is the core user interface of the gnome 3 user experience. It's called the "shell" in reference to the CLI shell that you mentioned, because it forms the basic level at which users can interact with the gnome 3 environment. the plan is to have many many features, and adaptions of gnome 3 - shell will be the core of them. For example the Unity interface of your Ubuntu install is an example of this. However it always runs above the CLI if that makes sense?

(If you wanted to try gnome shell desktop environment the command is ```
sudo apt-get install gnome-shell
``` - to try it out, log out and click the cog next to your login box and select it, then log in as usual. To get back log out and select "Ubuntu" from the cog :) - it's the "shell" under unity's "jumper" ;)

So all in all... no, no shell in GUI form - in the GUI you enter commands in the terminals; these are merely terminal emulators - recreating the terminal experience of the shells at F1-6 inside the GUI. In linux there is only BASH, but each desktop environment comes with it's own terminal emulator - gnome terminal, Xterm, Konsole, LXTerminal, to name a few.

Hope that's a bit clearer! :D

---

### Post by Double.J on 2012-01-20
> **Maese909 said:**
> Ok. So what you are saying is the fourth shell is used to close windows, and the second shell (Alt+F2) is used mainly to run programs? Also, is there a way to browse the Internet when in the CLI shell?

P.S. I editied my post where I said holy @$@$ in case you didn't see

No sorry, I'm being confusing, those are keyboard shortcuts in the GUI.. in the CLI those key combinations will just keep switching shells.... Sorry :oops:

---

### Post by collisionystm on 2012-01-20
> **Maese909 said:**
> Hello all. I am new to the world of Linux and so far am loving what I am seeing! I am studying the Terminal and have a few questions... Below is what I have comprehended so far. Obviously, I don't know the hardcore details, so let me know if this is on the right track). Anyway, here's my 2-sense..

So basically there is whats called a 'shell.' This shell is a wrapper around Linux so to speak that gives you access to folders, files and so on. The shell comes in two flavors.. the GUI and the CLI.
The CLI shell can be accessed via the Terminal, whereas the GUI shell is accessed by default when the user logs in. The CLI shell, when used via the Terminal, is called a BASH shell.

p.s. Don't go too crazy with the details, I am still very new at this stuff :D


The command line is access via the TTY shortcuts ( CTRL + ALT + Fkey ) or by Terminal, or SSH, Telnet..etc.

There are many ways to access the command line on your box. Just depends on what you want.

GUI is a GUI. Just a window manager. It creates pretty pictures to interface with the software running.

You pretty much have the linux kernel at the heart. Somebody like Debian or Red Hat writes their software to interface with it, essentially bringing Frankenstein to life. The GUI such as Gnome, KDE and XFCE interface with the software provided by Debian / Red Hat / Ubuntu. Everyone has their own way of manipulating the kernel, but at the heart of the system its all the same. Thats why Linux will work on Linux. Except package managers. Thank god you can compile from source.

There are 1000 ways to skin a penguin. I'd say you have the general idea.

Oh and BASH is just a program written to interface with the Kernel. There are many others, such as KSH, CSH..etc.

---

### Post by Maese909 on 2012-01-20
Wow, you totally made it much clearer for me! That reference to snails make so much sense!!! THANK YOU!!!!

P.S. atm I am readying [http://linuxcommand.org/lts0030.php](http://linuxcommand.org/lts0030.php)

---

### Post by VraiChevalier on 2012-01-20
> **Maese909 said:**
> ...Also, is there a way to browse the Internet when in the CLI shell?

Links or Lynx. Both are available in the repositories. Install either and run it from a console terminal. It's a trip! Blazing fast! Hang onto your seat though because you will get there before you even realize you've left.

I like using Lynx.

---

### Post by Double.J on 2012-01-20
+1 for lynx.. I just like having different colours (even if it's just words) CLI browsers such as those mentioned by VraiChevalier can be really useful when learning the terminal as you can have one open in the next terminal and keep switching back and forth. 

They can be a trip, best read the manual first - 
```
man lynx[COLOR="Green"] or[/COLOR] man links
```
The one your really want for either is press 'G' to enter a web a address ;)

All the best!

---

### Post by Maese909 on 2012-01-20
Lol yeah I downloaded Lynx and used it. Crazy stuff I must say. Took me awhile to figure out the G command :)

---

