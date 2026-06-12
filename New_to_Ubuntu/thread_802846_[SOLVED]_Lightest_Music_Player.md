---
title: "[SOLVED] Lightest Music Player"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Inxsible on 2008-05-21
I just installed Xubuntu 8.04 on an old laptop (P3, 1.1GHz, 256MB RAM). Xubuntu runs, but is quite slow. When I open up synaptic, it takes quite some time to bring up my password window and then even more time to actually opening Synaptic. 

That is just an example. It takes time in almost all the apps. So anyway, which music player would be best for such a system?

Amarok is definitely out. What are the memory footprints of Exaile, Banshee, Audacious or do you have any other player to suggest ?

---

### Post by jrusso2 on 2008-05-21
xmms is pretty light.  mplayer is run from command line.  And there are many other non-gui players.

---

### Post by aktiwers on 2008-05-21
Xmms or Audacious?

Or without GUI
mpd 

You can install light GUI's for mpd actually.

---

### Post by Inxsible on 2008-05-21
Is there a way to maintain playlists in mplayer or mpd?

mpd sounds good ...since its command line. I haven't tried it. Do you have some links to the user guide for it or something?

I don't want a player with all the bells and whistles, but basic playlist manipulation and folder watching.

---

### Post by HotShotDJ on 2008-05-21
MPlayer.  Can be run from the command line, for example:```
mplayer nuestro\ himno\ national\ anthem\ in\ spanish.mp3 
```No bloated gui... just musical goodness.  For playlists (txt, pls, m3u):```
 mplayer -playlist Playlist.pls
```
EDIT: Use cursor keys on keyboard to fast-forward or skip-back

---

### Post by Helgiks on 2008-05-21
I think mpd is great, and VERY lightweight, and yes you can manipulate playlists, and I think even with the graphical clients like sonata it's still very easy on you're computer.

---

### Post by aktiwers on 2008-05-21
Hmm..  I can't test mpd right now because I set my system to up to use only PulseAudio, and Mpd dont like that.

But it seams very easy to use, keys on the keyboard are shortcuts. I actually think that the key "h" takes you to help menu, that explains all the other keys, if I remember correctly. :)

---

### Post by NightwishFan on 2008-05-21
Install a fluxbox session. It might speed things up for you.

---

### Post by Helgiks on 2008-05-21
> **NightwishFan said:**
> Install a fluxbox session. It might speed things up for you.

I second that idea, it'll make you're old computer look faster than a 3000$ brand new one ;)

---

### Post by Inxsible on 2008-05-21
> **NightwishFan said:**
> Install a fluxbox session. It might speed things up for you.
I do plan to. I actually have left 15GB of space for exactly that purpose. Will be building a minimal system and then installing Fluxbox or IceWM.

I installed Xubuntu because the specs were just sufficient and I wanted to see how fast it would be.

Since we are on that topic, will Fluxbuntu be a better option than a minimal with Fluxbox? How do they differ - if any

---

### Post by NightwishFan on 2008-05-21
Xubuntu felt slow to me, only slightly faster than Gnome on a similar system. Kubuntu seems to run better than both of them on that machine. I do like the look of XFCE4 more than Gnome though.

---

### Post by Inxsible on 2008-05-21
> **aktiwers said:**
> Hmm..  I can't test mpd right now because I set my system to up to use only PulseAudio, and Mpd dont like that.

But it seams very easy to use, keys on the keyboard are shortcuts. I actually think that the key "h" takes you to help menu, that explains all the other keys, if I remember correctly. :)Doesn't Hardy come with PulseAudio as default??

I have Xubuntu 8.04 and so I think mpd might not play well for me either. But I can always try. The other thing I could do is install a server version of Xubuntu and then use everything via CLI - music player and all :)

---

### Post by NightwishFan on 2008-05-21
Use the minimal cd and install a CLI, then sudo aptitude update sudo aptitude install what you want.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Generally, xorg wdm fluxbox and xterm are enough for a base system then just add what you need.

---

### Post by Inxsible on 2008-05-21
> **NightwishFan said:**
> Xubuntu felt slow to me, [COLOR=Red]only slightly faster than Gnome on a similar system. [/COLOR]Kubuntu seems to run better than both of them on that machine. I do like the look of XFCE4 more than Gnome though.I tend to agree with your comparison between Gnome and Xfce (after all the default for Xfce is to use Gnome services)

But I am not too sure about Kubuntu running better than them. I like Xfce more because it installs a lot less junk than Gnome does. I dont use half the apps that a default Ubuntu install gives and I find myself un-installing them all.

Xubuntu has a lot less junk...but it still has a few. I guess a minimal install would be the best way to go. Although I really like Thunar. I hope it doesn't depend too much on other xfce packages.

---

### Post by aktiwers on 2008-05-21
> **Inxsible said:**
> Doesn't Hardy come with PulseAudio as default??

I have Xubuntu 8.04 and so I think mpd might not play well for me either. But I can always try. The other thing I could do is install a server version of Xubuntu and then use everything via CLI - music player and all :)

Yeah but it still seams to use Alsa for a lot of things. I followed some howto here (cant find it right now) that made it more default and fixed some bugs. Since then I lost sound in Wine and mpd does not want to open anymore. 

It even wants me to open it with sudo to get a useful error message:
> aktiwers@HAL:~$ mpd
unable to bind port 6600: Address already in use
maybe MPD is still running?
aktiwers@HAL:~$ sudo killall mpd
[sudo] password for aktiwers: 
aktiwers@HAL:~$ mpd
cannot setgid for user "mpd" at line 35: Operation not permitted
aktiwers@HAL:~$ sudo mpd
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
*** PULSEAUDIO: Unable to connect: Connection refused
aktiwers@HAL:~$ 

But I am pretty sure you could use it fine. I think it worked fine before I did this pulseaudio howto. But I use Audacious mostly.. very light IMO.

---

### Post by NightwishFan on 2008-05-21
Most people do not see kde as light. A fluxbox minimal install on 64bit uses about 70mb of ram. A similarly installed kde-core uses about 110mb.

---

### Post by cariboo on 2008-05-21
Mpg321 probably is one of the lightest mp3 players around. I use to use a program called **play** on a 66Mhz P1 with 64MB ram with a very minimal Debian installation. It ran 24/7 for 4 years and if I hadn't shut it down it probably would still be running. I can't find play in the repositories so i guess it isn't available any more.

Jim

---

### Post by aktiwers on 2008-05-21
> **cariboo907 said:**
> Mpg321 probably is one of the lightest mp3 players around. I use to use a program called **play** on a 66Mhz P1 with 64MB ram with a very minimal Debian installation. It ran 24/7 for 4 years and if I hadn't shut it down it probably would still be running. I can't find play in the repositories so i guess it isn't available any more.

Jim

You are not talking about **cplay **are you?

It's in the repo's too:
```
sudo apt-get install cplay
```
```
cplay
```

---

### Post by Inxsible on 2008-05-21
> **NightwishFan said:**
> Use the minimal cd and install a CLI, then sudo aptitude update sudo aptitude install what you want.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Generally, xorg wdm fluxbox and xterm are enough for a base system then just add what you need.Is the wdm same as Wings Display Manager or something else?

---

### Post by NightwishFan on 2008-05-21
It is indeed Wing's Display Manager.

---

### Post by Inxsible on 2008-05-21
I was planning on not having any DM as such - neither wdm nor gdm nor kdm. A simple login at the CLI and then issuing startx would suffice and save space too.

---

