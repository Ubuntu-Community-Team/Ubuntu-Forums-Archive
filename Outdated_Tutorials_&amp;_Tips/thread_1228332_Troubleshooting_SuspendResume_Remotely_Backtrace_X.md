---
title: "Troubleshooting Suspend/Resume: Remotely Backtrace X"
date: 2009-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Rocket2DMn on 2009-07-31
[COLOR="Sienna"]_**[SIZE="4"]About this Guide[/SIZE]**_[/COLOR]

This guide is geared toward troubleshooting the suspend/resume function on a computer that fails to resume from suspend (i.e. you only get a black screen).  The procedure outlined below may not work on all systems for all problems, depending on the source of the problem.  I have attempted to write it so that beginners can use it, but in reality this is a process usually reserved for those who have at least a comfortable understanding of  Ubuntu packages, video cards, networking, and using the terminal.  Please feel free to ask questions.

[COLOR="DarkSlateBlue"]_**[SIZE="4"]Prerequisites[/SIZE]**_[/COLOR]

[COLOR="Green"]_**[SIZE="3"]Install openssh-server[/SIZE]**_[/COLOR]

Of course, to do remote actions, you must be able to connect to the computer, so we install a SSH daemon:
```
sudo apt-get install openssh-server
```
Test your ability to SSH to the box from another machine, and configure your firewall and router accordingly (on LAN, no extra work should be needed).  Note that SSH may be more reliable when attempting to resume if you are using a wired connection rather than wireless.

Write down the IP of this computer, which you can check with
```
ifconfig
```

[COLOR="Green"]_**[SIZE="3"]Install Debug Packages[/SIZE]**_[/COLOR]

In order to debug, we need gdb and the debug packages for X and for your video driver.  My video card uses the open source radeon drivers, so I will use the debug packages for the package xserver-xorg-video-radeon.  Substitute your own.
```
sudo apt-get install gdb xserver-xorg-core-dbg libgl1-mesa-dri-dbg *xserver-xorg-video-radeon-dbg*
```

[COLOR="DarkSlateBlue"]_**[SIZE="4"]Starting the Debug Procedure[/SIZE]**_[/COLOR]

Switch to TTY1 (CTRL+ALT+F1), login, and start a screen session with a name (e.g. xcrash):
```
screen -S xcrash
```
Now that you are inside of screen, get the pid (process ID) of Xorg.  Write it down, or remember it for just a few seconds:
```
pgrep Xorg
```
Now we start gdb:
```
sudo gdb /usr/bin/Xorg
```
Now you are in the gdb prompt - we will attach to the existing X, handle a couple of signals, and tell X to continue:
```

(gdb) attach <the process ID you found above>
(gdb) handle SIGUSR1 nostop
(gdb) handle SIGPIPE nostop
(gdb) cont

```
Now you can disconnect from the screen session with CTRL+A+D.

Switch back to X (CTRL+ALT+F7, or sometimes CTRL+ALT+F9).  Suspend the computer, wait 10 seconds or so, then attempt to resume it.

[COLOR="DarkSlateBlue"]_**[SIZE="4"]Handling the Failed Resume-From-Suspend[/SIZE]**_[/COLOR]

If the screen fails to come back up, then we need to check gdb to see if a backtrace was obtained.  Of course, if X is frozen up, you probably won't be able to switch back to TTY1, which is why we are using SSH here.  Connect to the computer from another machine:
```
ssh <username>@<IP>
```
e.g.:
```
ssh rocket2dmn@192.168.1.100
```
Now you can attach to the screen session we started earlier:
```
screen -x xcrash
```
NOTE: If you see messages about SIGUSR1 or SIGPIPE, you can probably ignore them, we specifically handled them earlier.
```
Program received signal SIGUSR1, User defined signal 1.
Program received signal SIGPIPE, Broken pipe.
```
Such messages as these should be OK.

Moving on. Now we have the gdb prompt again, so let's grab the backtrace and send it to a file:
```

(gdb) set logging on
(gdb) backtrace full

```
Enter your way through the backtrace until you are back at the gdb prompt.

Open another terminal from the computer you are using to SSH to the broken computer, and grab the backtrace.  The easiest way is to use scp:
```
scp <username>@<ip>:gdb.txt .
```
e.g.:
```
scp rocket2dmn@192.168.1.100:gdb.txt .
```
Don't forget that final period, that places the file you are downloading into the working directory (usually your home directory).

You can now use the backtrace in this file in a bug report.  For help with that, see [Improving Ubuntu: A Beginners Guide to Filing Bug Reports]("http://ubuntuforums.org/showthread.php?t=1011078").  You will most likely want to file your bug against the [xorg-server package]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/").

To resume the X session (may be possible, depending on the problem), at the gdb prompt, run:
```

(gdb) cont

```
Alternatively you can just detach the gdb session from X and use the computer normally.
```

(gdb) detach
(gdb) quit

```

[COLOR="Red"]_**[SIZE="4"]Troubleshooting[/SIZE]**_[/COLOR]
If you are unable to connect over SSH at all, try installing landscape-common:
```
sudo apt-get install landscape-common
```
I used this workaround in Karmic, as explained in [this thread]("http://ubuntuforums.org/showthread.php?t=1221910").

If you are having problems getting the backtrace, see [uwiki]X/Backtracing[/uwiki].

[COLOR="DimGray"]_**[SIZE="4"]Resources[/SIZE]**_[/COLOR]
[LIST]
[*][uwiki]DebuggingProcedures[/uwiki]
[*][uwiki]X/Backtracing[/uwiki]
[*][uwiki]Backtrace[/uwiki]
[*][Bug #313567 - Comment #13]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313567/comments/13") (my own work)
[*][Improving Ubuntu: A Beginners Guide to Filing Bug Reports]("http://ubuntuforums.org/showthread.php?t=1011078")
[/LIST]

---

### Post by stells on 2010-08-27
I was unable to connect over SSH at all, I tried to install landscape-common as you suggested and my trouble was solved instantly!Thanks for the suggestion!

---

