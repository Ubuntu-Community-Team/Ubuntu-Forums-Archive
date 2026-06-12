---
title: "Text Torrent Client - kinda specific needs"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Syndacate on 2008-08-25
I found one called rTorrent, but I read that the version in the repos is rather old.

Here's the simple problem:

I need to leave a computer some place and torrent (legally, of course), but I need to be able to operate it via ssh.

So I need to be like, able to log in, check it or whatever, and download whatever.

Also, I need there to be a settings file (up max) as well as a directory path and a port number because I can't store the LiveCD's on the same partition that the distro is on and I have a router.

Anything out there that meets my requirements?

---

### Post by DirtDawg on 2008-08-25
Rtorrent is exactly what you're looking for as far as I can tell. The repo version works fine. In fact, rtorrent is my first choice of torrent clients, GUI or no.

EDIT: Everything you will need to know is well documented on the [rtorrent homepage]("http://libtorrent.rakshasa.no/").

---

### Post by Nepherte on 2008-08-25
The latest (unstable) version of rtorrent is 0.8.2. The version in the repos is 0.8.0. That's not a huge difference if you ask me. It's not always necessary to get the latest cutting edge version of a program.

---

### Post by Syndacate on 2008-08-26
> **Nepherte said:**
> The latest (unstable) version of rtorrent is 0.8.2. The version in the repos is 0.8.0. That's not a huge difference if you ask me. It's not always necessary to get the latest cutting edge version of a program.

Gotcha, thanks for the info guys, I'll check it out 'n see what I think.

I need to operate this computer remotely, so I need it manageable via SSH.

Hope this works.

---

### Post by eightmillion on 2008-08-26
Something you may be interested in is torrentflux. It's in the repositories and it has a feature rich web interface. You can control your torrents through your browser.

---

### Post by Syndacate on 2008-08-26
> **eightmillion said:**
> Something you may be interested in is torrentflux. It's in the repositories and it has a feature rich web interface. You can control your torrents through your browser.

Oh wow, that sounds pretty nifty.

I only need full torrent control via SSH, (directory selection, upload/download caps), and some sort of update-status thing that keeps updating, like top, even if it's only a %, but that still sounds pretty sweet.  I'll check that out.

---

### Post by eightmillion on 2008-08-26
It is really cool. You can set up individual users with their own logins and options. I've even got it running on a 266 MHz ARM system with 32 MB of ram. You might also check out ctorrent and enhanced ctorrent.

---

### Post by Archmage on 2008-08-26
I would use rtorrent combined with screen for that.

E.g. start:

SSH login
screen rtorrent
CTRL-A + D for detaching screen
SSH logout

To watch what is going on

SSH loing
screen -r
CTRL-A + D for detaching screen
SSH logout

---

### Post by Syndacate on 2008-08-27
> **eightmillion said:**
> It is really cool. You can set up individual users with their own logins and options. I've even got it running on a 266 MHz ARM system with 32 MB of ram. You might also check out ctorrent and enhanced ctorrent.

****, I took one look at the manual page for rtorrent and almost offed myself.  I guess there's so much GUI stuff that I take for granted in a torrenting program that I don't even know where to begin with rtorrent.

Another thing which I'm a bit confused by is instances of the program.

Say I ssh into my server and type:
```
rtorrent &
```

Then I do my thing, after adding some torrents I log out by tying:
```
^q
``` then ```
exit
``` and it disconnects from my server.

Right, peachy.

Then 2 hours later I go back - but now how do I "get" the instance of the program?  I realize I can use top or pgrep to find out the process ID - but then how can I look at it again?  Simply typing "*rtorrent &*" will give me another instance of rtorrent with a different PID and everything.  How do I "open" my old instance?  Some kind of "*select <PID>*" option?

Only thing I can think of is killing the old process when I reconnect.

Also, does anybody have a "quick" write-up on using rtorrent?

The options aren't the best, they seem to be command line arguments, which is kind of annoying - I'd much rather have a config notepad file that I could edit with nano or emacs, though I'm sure one don't exist - that would be way too convenient 'n all ;).

Man pages were always hard for me to understand, and that's for basic stuff...I don't even know where to begin to initiate the options for rtorrent.  I mean do those options get entered when you run the program (the ackward ones, not the regular arguments)?  Do they save when you close?  Which ones are considered arguments?

I'm hella confused.  A basic few lines of code on **basic** useage would be greatly appreciated.

Thanks.

If not, I'll have to turn to that GUI web-based torrent thing you mentioned - but I sorta don't like the sound of that...

TIA and thanks so far...

---

### Post by Nythain on 2008-08-27
dont control q out of rtorrent, that will close rtorrent, not what you want
what you want, as mentioned, is screen + rtorrent
basically, as mentioned
ssh into the server you want to run rtorrent on
run screen
once screen loads
run rtorrent
then, to exit it all
control+a+d to disconnect from screen. this will leave the screen session running in the background along with rtorrent wich was running inside of screen.

to get back to rtorrent
ssh into the server
screen -r (i always do RDAa, man screen to find out why)
then rtorrent should show back up, still running, still downloading/uploading those torrents

also, rtorrent has an rc file... .rtorrent.rc for setting most options, well documented, i never run rtorrent with any command line arguments, because everything i need is set in the rc... if you want i cant post *most* of my .rtorrent.rc so you can see how to get things done, and remember, the .rtorrent.rc needs to be located in your home directory
another note, newer version of rtorrent than the one in the repo support encryption wich is becoming more and more popular these days to avoid isp tricks like sandvine

any further questions
man screen
man ssh
man rtorrent
google "screen"
google "ssh"
google "rtorrent"
google "rtorrent + screen"

hope that helps, its an excellent solution for remote ssh administration of torrents

---

### Post by kaivalagi on 2008-08-27
If it's ssh based you want see the attached rtorrent.init.txt file which can be used to run rtorrent as a daemon...good guide to the whole daemon script in Debian/Ubuntu is here: [http://girasoli.org/?p=120](http://girasoli.org/?p=120)

If you are willing to go down a web server based route read on...

What about clutch, it manages the transmission-cli through a webpage which you can be hosted in apache or another more lightweight webserver on you local machine. It runs as a daemon so is started on boot (not on login) and works just fine. Just install it from the repo's...

Although I have nothing downloaded at the moment you get the general idea from the screenshot of the webpage...

Alternatively you can setup rtorrent as a daemon (/etc/init.d/rtorrent start/stop etc..) then setup rtgui (freely downloadable, just search for it) in apache which talks to the rtorrent session via xmlrpc...all much more complicated than clutch/transmission but there are good guides out there and it can be done...I was using this method previously until I found clutch.

Hope that helps

---

### Post by Syndacate on 2008-09-10
Sorry to bump such an old thread - I've been very busy.

So final verdict - thank you very much.  rtorrent wasn't bad to learn once I got the config file created.  Very simple commands, very awesome program.

Started by:
```

*connect*
screen
rtorrent
C-a C-d (careful not to select a torrent, C-d will stop it)
exit

```

Check by:
```

*connect*
screen -r

**shows legally downloaded(ing) and shared live CD's**

C-a C-d
exit

```

Very cool - does exactly what I need it to - thanks a million.

---

### Post by hyper_ch on 2008-09-10
btw, if you want the newest rtorrent version, I wrote a little howto for compiling it from SVN:  [http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

---

### Post by Syndacate on 2008-09-14
> **hyper_ch said:**
> btw, if you want the newest rtorrent version, I wrote a little howto for compiling it from SVN:  [http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

Thanks, I'll look into that.

Question:
If you decide to run this locally as your torrent client - how do you run it, the same way?  Just open up a terminal and screen it?  Or do you run it off tty 2 or 3 or something?

---

### Post by Mornedhel on 2008-09-14
Locally ? As in on your own machine ?

Just run rtorrent on gnome-terminal. Or did I miss something ?

---

### Post by hyper_ch on 2008-09-14
I run it in screen, so I can easily detach and re-attach the session from everywhere.

---

