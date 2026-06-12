---
title: "Compiling, installing and configuring wbar"
date: 2010-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Spice Weasel on 2010-10-13
**NOTE: **This tutorial is written from my own experience. Remember, your mileage may vary. Please post any errors.

The .deb package available on the interwebs was built for Debian Etch, so probably isn't the best thing to try on Ubuntu (and especially on RPM distributions, which I originally wrote this tutorial for).

[SIZE=6]Introduction[/SIZE]

wbar is a fairly unknown application, a few of you might know it from the BB/Linux distribution Tiny Core Linux. Yep, it's the dock in TC at the top of the screen. However, it is very lightweight despite having a lot of eye candy. I wouldn't really call it a dock, it's more of a quicklaunch bar with dock-like effects.

Basically, it's a dock for people that hate docks.

I recommend using this with a lightweight window manager (such as Openbox or IceWM) rather than a full blown desktop like GNOME or KDE (the defaults in Kubuntu and Ubuntu), I have also tested it in XFCE (the default in Xubuntu) and it was a nightmare to get working.

_Why would you want wbar?_


[LIST=1]
[*]You like the look of docks, but find them annoying to use.
[*]You use a lightweight window manager like *box, JWM, IceWM or Awesome.
[*]You are comfortable with editing configuration files.
[/LIST]
Here is a custom configuration of wbar doin' it's thing:

[IMG]http://imgur.com/iH9r3.png[/IMG]

[SIZE=6]Getting down to business[/SIZE]

First of all, I have a modified wbar source code where I have fixed a couple of problems I had when compiling it. I have also precompiled it, so you can go ahead
and install it if you do not have any problems.

You can download it [here]("http://www.mediafire.com/?ifvz9nwr8j9d0za"). 

Notice the size of it, and that's with including the source and executables!

Now, let's get on with installing. First, you will need to navigate using your favourite File Manager to where you have downloaded it. In Firefox, the default location is ~/Downloads.

Open it up with the Archive Manager, Xarchiver or Ark. Extract it.

A new folder should have appeared. Open it up, and you should see something like this:

[IMG]http://imgur.com/2iLIw.png[/IMG]

[U][B]PLEASE BE SURE YOU REALLY WANT THIS PROGRAM BEFORE INSTALLING, SINCE IT IS
VERY HARD TO REMOVE AFTERWARDS.[/B][/U]
[SIZE=5]
[/SIZE][SIZE=6]On with the installing already![/SIZE]

Next you will need to open up a terminal. I know, scary. Please bare with me. :P

Type in these commands, be sure to read everything in between them so you are sure of what you are doing.

```
cd /path/to/wbar
```Let the shell know what files you are talking about when it tells you to install. Remember the location we talked about earlier? CD is short for change directory, and you will need to change directory to the place you extracted the source to.

```
sudo make install
```This is self explanatory. I have included the executables, so chances are you won't need to compile. [B]

If you get errors, try this:[/B]

```
make
```To compile the source code again, and then:

**Only if you got errors with the make install command:**

```
sudo make install
``` again.

**You will need to do this no matter what:**

```
make config (NO SUDO!!!)
```Yep. This makes the configuration. Be sure to not be sudoing when you do this, since you will want to configure wbar for your current user.

Now, to make sure everything is okay, try this:

```
wbar --help
```To make srue it is installed properly.

[SIZE=6]Autostarting wbar
[SIZE=1]
If you have installed wbar, then chances are you will want it to run when you log in to your computer. This is the command you will need to enter into your autostart list (I will not tell you where this is or how to edit it, because it is different for every desktop. What am I talking about? Open up GNOME and go to System and then Startup Applications. This is what I need you to do in your desktop, but as we all know wbar doesn't play nice in GNOME. You can try it if you want to.

Here is the command:

```
wbar -nofont -pos top &
```Self explanatory. Start wbar, with no text when you hover over the program at the top of the screen.

[SIZE=6]The configuration file
[SIZE=1]
There are currently no graphical configuration tools for wbar, so you will need to configure it by hand. Type this command into your terminal:

```
sudo nano /usr/share/wbar/dot.wbar
```I will only explain the basics of adding new programs to the bar:

```


```[/SIZE][/SIZE][/SIZE][/SIZE]```
**i: /path/to/the/icon/you/want/to/show/on/the/bar.png** (128x128 or bigger is recommended. SVG icons are not supported. You can find icons for your system in the /usr/share/icons or /usr/share/pixmaps folders.)
**c: command-to-run (for example, firefox would open Firefox.)**
**t: Text to show when you hover over the icon!** Only appears if text is enabled.

```

---

