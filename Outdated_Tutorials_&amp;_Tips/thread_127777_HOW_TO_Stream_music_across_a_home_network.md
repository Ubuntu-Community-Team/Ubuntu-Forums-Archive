---
title: "HOW TO: Stream music across a home network"
date: 2006-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by jonny on 2006-02-09
The problem: you have hundreds of music files stored on a PC somewhere.  You want to play these on various computers across the house.  You don't want to teach your IT illiterate partner to use a command line.  And you have a vague feeling that MythTV might be overkill.

The solution: use Beep Media Player with Gnome VFS enabled.

This problem has two parts: first, the PC with the music must be able to share the  music files.  Second, the PC that's going to play the music must be able to play them.  I'm not going to tell you how to solve the first problem, as there are plenty of how-to's in these forums and in the Ubuntu Wiki.  Just search for Samba, and you'll find the solution.  If you don't like Samba, just set up an FTP server - again, there are plenty of how-tos out there.

So now you have a client PC that can see your music on the Places menu if you connect to a server through the Places menu.  But how do you get your music player to see them?  None of the most common music players - Rhythmbox, Muine, Quod Libet, Banshee, XMMS - can cope unless you mount a network drive using the command line.  You don't want to have to teach your kids how to mount drives, and you don't want to mount network drives automatically on startup because laptops get rather stroppy if you try to mount your home drives when you're in the office.

You might not know this, but what you actually need is a music player that's Gnome-VFS aware.  None of the music players in Synaptic are, so we'll build our own version of Beep Media Player with Gnome-VFS enabled.

Open a terminal session and enter the code below.  Substitute your own user name for jonny, and type your password when prompted.  Use your initiative or accept the defaults for any other questions.

```
cd ~/Desktop
sudo apt-get remove beep-media-player
sudo apt-get build-dep beep-media-player
sudo apt-get source beep-media-player
sudo apt-get install checkinstall libgnomevfs2-dev build-essential
sudo chown -R jonny:jonny beep-media-player*
cd beep-media-player-0.9.7.1+cvs20050803/
./configure --enable-gnome-vfs
make
sudo checkinstall
cd ..
sudo rm -rf beep-media-player*

```
To play your network music, first connect to the music server using the 'Places --> Connect to server' option on your desktop. Note that you only have to do this once - Gnome remembers the connection, even if you turn off your PC. Now start up Beep Media Player - it sould be in your Applications menu - and you'll be able to access your remote files through the normal Open File dialogue box.

Have fun.

---

### Post by potrick on 2006-03-05
Hey, thanks for the howto. Only one problem: when I do this, my beep plugins are gone, and I can't seem to recompile them for the program. Any idea why this would be?

---

### Post by djgenesis on 2006-05-12
Great! Works line a charm ... well basically the line:
```
cd beep-media-player-0.9.7.1+cvs20050803/
```
has to be substituted with ```
cd beep-media-player-0.9.7
``` cause this is the version downloaded :) 12/05/2006
Other than that i am really happy !! Thank you :D:D:D:D

---

