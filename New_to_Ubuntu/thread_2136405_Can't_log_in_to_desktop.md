---
title: "Can't log in to desktop"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by neilnoise on 2013-04-17
I've been using Unity on 12.10 for a few months, and tried installing Gnome to try it out and see if I like it. After rebooting, when I get to the log in screen and log in, the screen flashes black, then goes straight back to the log in screen again. This happens regardless of which desktop environment I choose.

Strangely, I can log in as a guest no problem, and I can also log in to a terminal session fine with ctrl+alt+f1.

As I'm still fairly new to Ubuntu, I don't really know where to begin troubleshooting this.

---

### Post by palaau on 2013-04-17
Have you tried removing Gnome and reinstalling?

---

### Post by palaau on 2013-04-17
like *sudo apt-get remove gnome *... ?

---

### Post by neilnoise on 2013-04-17
I was having much bigger problems up until this one, so I purged and reinstalled unity, gnome and ubuntu-desktop. That solved most of the issues, but not this one.

---

### Post by Elephant454 on 2013-04-17
Did you do anything else besides install Gnome? I had something similar happen to me when I installed a bad nVidia driver.

---

### Post by neilnoise on 2013-04-17
When I fist rebooted after installing gnome, it would log in, but only load my desktop background - no launcher of anything. I found a thread with a similar problem, and follwed the instructions there, booting into safe mode and running 
[I]
sudo apt-get purge unity*
sudo apt-get purge gnome-shell
sudo apt-get install unity
sudo apt-get install unity 2d
sudo apt-get install gnome-shell
dpkg-reconfigure -a
[/I]
After rebooting, I was greeted with the error: "The system is running in low graphics mode. Your screen, graphics cards, and input device settings could not be detected correctly. You will need to configure these yourself."

I found advice to do *sudo apt-get install --reinstall ubuntu-desktop*&#8203;. This fixed that error, but now I have the current problem where it keeps just reverting to the log-in screen.

---

### Post by steeldriver on 2013-04-17
If the desktop works fine for guest logins then I think it's unlikely to be anything related to your graphics drivers or basic package configuration - most likely it is something particular about your session or your home directory

First thing I would check is ownership and permissions on your home dir and Xauthority files - from the Ctrl-Alt-F1 virtual terminal (logged in as the 'broken' user)

```

ls -ld $HOME

ls -l $HOME/.{ICE,X}authority

```

---

### Post by neilnoise on 2013-04-17
Ok. Output of ls -ld $HOME is:

drwxr-xr-x 36 neil neil 4096 Apr 17 19:39 /home/neil

Output of ls -l $HOME/.{ICE,X}authority is:

-rw------- 1 neil neil 14314 Apr 17 17:19 /home/neil/.ICEauthority
-rw------- 1 root root 51Apr 17:23 /home/neil/.Xauthority

---

### Post by steeldriver on 2013-04-17
OK yes so you need to either remove that root-owned file or make it owned by you

```
rm /home/neil/.Xauthority
```

OR

```
sudo chown neil:neil /home/neil/.Xauthority
```

Either should work, the 1st one is handy if you don't belong to the sudo group - then Ctrl-Alt-F7 back to the GUI and try again with your login

---

### Post by neilnoise on 2013-04-17
Ok, I made the file owned by me. It's now letting me log in, but not properly. It gets as far as loading my desktop background, then just seems to stop. No launcher or anything. I can move the mouse, and the only keyboard shortcuts that work are ctrl+alt+fn ones.

---

### Post by steeldriver on 2013-04-17
Well I can't vouch for them personally (I'm still on 12.04) but there are some instructions for resetting Unity here:

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

One or other of these methods *may* work for you

---

### Post by neilnoise on 2013-04-17
I tried following those instructions, but it's still not working.

The step "dconf reset -f /org/compiz/" gives this error message:

[I]Error spawning command line `dbus-launch --autolaunch=fcd00e379a4f584eaab0252f51093fa0 --binary-syntax --close-stderr' : Child process exited with code 1

[/I]After this error code, the *setsid unity* command doesn't appear to do anything, and the problem remains.

---

### Post by steeldriver on 2013-04-17
Were you doing that from the Ctrl-Alt-F1 virtual terminal? I think you need to do it from the running X session i.e. you need to be able to at least start an X term (Ctrl-Alt-t) in the GUI

[it *might *work from the virtual terminal if you specify the display # explicitly e.g. 

```
DISPLAY=:0 dconf reset -f /org/compiz/
```

assuming your primary display is :0 ]

---

### Post by neilnoise on 2013-04-18
So I gave up last night and went to bed, then when I booted up this morning it logged in fine first time (albeit with about 70 "Ubuntu has encountered an internal error" messages)!

I didn't change anything else since my last post and it magically fixed itself... Isn't technology wonderful?!

Thanks for your help though :)

---

