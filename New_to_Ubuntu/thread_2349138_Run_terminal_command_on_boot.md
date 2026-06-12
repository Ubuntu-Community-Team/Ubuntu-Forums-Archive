---
title: "Run terminal command on boot"
date: 2017-01-11
forum: New to Ubuntu
---

### Post by vegarab on 2017-01-11
Hi.
I did my first ever linux install on my MacBook two days ago - everything is working great, and I LOVE the OS. 

One of the first things I wanted to do was get hold of a script that will swap my left-ctrl and cmd button.
I made a file called .Xmodmap in /home/user/ with the following:

```

clear control
clear mod4

keycode 105 =
keycode 206 =

keycode 133 = Control_L NoSymbol Control_L
keycode 134 = Control_R NoSymbol Control_R
keycode 37 = Super_L NoSymbol Super_L

add control = Control_L
add control = Control_R
add mod4 = Super_L

```

I then ran the following commands in terminal:

& chmod +x .Xmodmap
& xmodmap .Xmodmap

The script works perfectly. However, I need to make the script executable AND run it every time I boot up. I have tried to
add this to the Startup Applications program, with the following command:

& chmod +x /home/user/.Xmodmap; xmodmap /home/user/.Xmodmap

However, it doesnt seem to work. I still have to type that into the terminal manually every time I restart (which is every time
I need to close the lid on the computer, because neither suspend nor hibernate works)

Thank you!

---

### Post by TheFu on 2017-01-11
Welcome to the forums.

You can't run X modifying scripts at boot. X/Windows doesn't start that quickly and these settings are X-session specific, which happens AFTER login.  Wait until login of the GUI.  Depending on which WM and/or DE you are running, there is a different way to run programs after login.  Search for "autostart" and the specific flavor of Ubuntu you are running. Found this for ubuntu: [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)  xubuntu, lubuntu, kubuntu, Ubuntu-Gnome/Mate will have different methods.

Lastly, I'm confused by the '&' at the beginning of your lines.  '&' means to put a process into the background and goes at the end of a command, not at the beginning.  Is that really supposed to be a $ (for normal user) or a # (for root)?
```
$ chmod +x .Xmodmap &
$ xmodmap .Xmodmap &

``` would be more correct, IMHO.  I'm not an expert on Xmodmap - would have to look up the commands that are valid. Think you want to use the "clear", not empty set methods, but don't know for sure.

To get suspend working is hardware specific and apple seems to always be special.  Look in the Apple-HW subforum is  my only suggestion.

---

### Post by vegarab on 2017-01-11
Thank you for the welcome!

I am used to & as an indication that you are typing it in terminal from OS X. I simply type the command behind it.

I am running Unity, but havent been able to find any other solutions to running a script like this at boot. As I said i have tried to add it to the Startup Applications, but it doesnt work.

I certainly dont have any understanding of Xmodmap, I just found this guide on the forum: [http://askubuntu.com/questions/317442/how-to-invert-ctrl-and-cmd-on-a-macbook-pro-keyboard](http://askubuntu.com/questions/317442/how-to-invert-ctrl-and-cmd-on-a-macbook-pro-keyboard)

---

### Post by TheFu on 2017-01-11
Sorry - missed the "clear" in your .xmodmap file. Didn't scroll up enough when composing my other reply.

You cannot run any X/Windows stuff at boot. It must wait until login - not just login, but a GUI login. There is a difference.

Can't help with Unity, sorry. Haven't looked at it in almost 6 yrs.

The chmod is only needed once. This is a normal Unix system, so the file and directory permissions work just like we expect on all Unix systems. Nothing new to learn.

I run my keyboard changes using the method openbox uses. The autostart file:   ~/.config/openbox/autostart - that doesn't help with Unity.  It has execute permissions and a list of programs to be run.  Mainly, just setup the touchpad for my preferences, but also do some screensaver stuff.

---

### Post by vegarab on 2017-01-11
The post I first found this Xmodmap fix also mentions a .xinitrc file. Would that be something that could work?

---

### Post by TheFu on 2017-01-11
Depends on the login manager.  Doubtful Unity would pay any attention to it.  I use that, but don't run any DE - I'm a pure WM-only guy.

---

### Post by vegarab on 2017-01-13
Problem solved.

It was not a problem having Unity run the command at boot - gnome was constantly changing the keyboard settings. Deactivating automatic changes to keyboard-settings solved the problem.
```

gsettings set org.gnome.settings-daemon.plugins.keyboard active false

```

---

