---
title: "Good Music Player"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by fazillatheef on 2008-06-23
Hi
 I do not want the default Music Player in Ubuntu hardy heron. It contains features like library which I dont want.I need a player that can function like winamp player for windows.Which has a simple playlist function. I dont need it to have theming support. I just need it to look like its a part of the ubuntu OS.

I tried using xmms on hardy .The installation required me to download source,compile and install.But after install it doesnt have any text.And when i right click on the player the gui looks very primitive and it also doesnot have any text. It doesnt use gtk theme that ubuntu has.

Second I tried winamp over wine and that had some problems also.The winamp window could not be minimzed to the taskbar.And the window stays always on top of other windows 

Thanks in advance

---

### Post by sharks on 2008-06-23
You can use Real Player 11 for Linux. or u can use amarok but it is best working in KDE.

Real player download [www.real.com/linux](www.real.com/linux)

---

### Post by undertakingyou on 2008-06-23
Amarok is awesome.  Just point it at the music folder and it will watch changes, has excellent cover support, can sync to iPod or other music player.  It has an easy to set up playlist and some cool queing stuff like winamp did.  

AMAROK FTW!!!

---

### Post by undertakingyou on 2008-06-23
> **sharks said:**
> You can use Real Player 11 for Linux. or u can use amarok but it is best working in KDE.

Real player download [www.real.com/linux](www.real.com/linux)

amarok works fine in gnome.  It just installs some of the KDE libraries to work.  But it doesn't matter if you use gnome or xfce.  Haven't tried it with fluxbox though . . .:-k

---

### Post by OutOfReach on 2008-06-23
I personally prefer Amarok, its a great music player. And it does work smoothly with GNOME :)

---

### Post by sharks on 2008-06-23
ok . havent tried Amarok yet.

---

### Post by dizee on 2008-06-23
Audacious is winamp-like, it's a simple player+playlist with no media library stuff so might be what you're looking for. It's in the repos as well.

Its default look might not integrate that well into Ubuntu but it is fully compatible with Winamp classic skins, so there's lots of choices to get it looking the way you want.

---

### Post by kpkeerthi on 2008-06-23
+1 for Audacious if you are looking for winamp clone.

---

### Post by kdcoetzee on 2008-06-23
Amarok.
Exaile is a media player aiming to be similar to Amarok but it equalizer is not so good.

---

### Post by 7raTEYdCql on 2008-06-23
I personally prefer Amarok, and personally think that it is the best out there. Rhythymnbox ain't that bad, but still. That is for managing my collection. Media player i prefer totem(the default one),vlc suffices my needs.

---

### Post by aktiwers on 2008-06-23
You could also have a look at Quod Libet. It has lots of nice plugins.
Edit: its in the repos..

---

### Post by paulderol on 2008-06-23
> **fazillatheef said:**
> Hi
 I do not want the default Music Player in Ubuntu hardy heron. It contains features like library which I dont want.I need a player that can function like winamp player for windows.Which has a simple playlist function. I dont need it to have theming support. I just need it to look like its a part of the ubuntu OS.



Amarok does not sound like what this person wants, nor does exaile. Both of those are more complicated than this request.

The OP wants Audacious. Really.

---

### Post by crackedparadigm on 2008-06-23
I'm just now trying out Banshee 1.0 and I have to say that it rocks some major ***.

---

### Post by rockerphil on 2008-06-23
i didn't see this one mentioned in the thread, so i'll toss it in. i LOVE VLC Media Player, lightweight, very powerfull and skinnable, and it's supported in the repos \m/(  - _ -  )\m/

---

### Post by crackedparadigm on 2008-06-23
> **fazillatheef said:**
> Hi
 Which has a simple playlist function. 

The new Banshee has an "add to play queue" feature

---

### Post by mc4man on 2008-06-23
Amarok is a great, flexible player.
If you want you can take a minimalist approach to using it with no playlists, collections, importing ect. by running it off right click actions. (actually never see the gui). I kept the music organized in home and desktop in folders (some folders inside folders) with some loose files spread about and it works great for me. 
The  3 most useful actions are
load|play - loads whatever you r. click on and starts playing, removes any existing playlist, if any
queue - adds whatever you  r.click on to top of playlist, play starts right after current track
append - adds whatever you r. click on to bottom of current playlist
If you want to try install nautilus actions and create any or all of the three actions
Any r. click on a folder will add/play everything inside in the order listed including sub folders

Additional way to append and or open
If amarok is open a left click/spacebar will append any file to current list if Amarok was set as default for that filetype
If it's not open it will open and start playing

Here's a somewhat scattered thread on how to write the actions, the parameters of the three I use are in last post
[http://ubuntuforums.org/showthread.php?t=830427](http://ubuntuforums.org/showthread.php?t=830427)

---

### Post by overlord.gaurav on 2008-06-23
You might want to install VLC.
Insatlling VLC is simple. Open a terminal and type:
```
sudo apt-get install vlc
```
and press enter. OR install it using Synapic Package manager through GUI.

---

### Post by Tuleele on 2008-06-23
> **rockerphil said:**
> i didn't see this one mentioned in the thread, so i'll toss it in. i LOVE VLC Media Player, lightweight, very powerfull and skinnable, and it's supported in the repos \m/(  - _ -  )\m/

I definately have to agree here! I have been using vlc for years now mainly b/c its so simple to use, and its hard to find a media file that it DOESNT support.

---

### Post by Troll_the_Great on 2008-06-23
Hello all

I see that many of you use Amarok?Do you have any problem with the lyric scripts?Mine broke for no reason.The default one gives me an error (I posted a thread called "Script error" if you want to look at it) and wiki lyrics say I must install some programs:
```
Sorry...
You need one of QtRuby, RubyGTK or TkRuby to run this program
```

I don't know where to find them. Can someone help please?

---

### Post by adityakavoor on 2008-06-23
its Exaile all the way

---

### Post by fazillatheef on 2008-06-23
I have to look audicious and have to check the options with amarok too...
Thanks for the replies.

---

### Post by ans5685 on 2008-06-23
Depends on what you want to do with it!
If it is just for playing music and nothing else then you can't do better than MPD+NCMPC(or Sonata/GUIMUP if u want a gui and/or are not that comfortable with the terminal)
It takes almost no RAM  in comparison to any of the aforementioned music players (640Kb vs 40+ Mb in my case!!!!).
 Visit [http://www.musicpd.org/](http://www.musicpd.org/) if you want to give it a try.
Otherwise i.e. you want it to do more than just play music Amarok is/was the best experience I had before.
You can also visit getdeb.net to and have a look at Beep Media Player
or if are familiar with the iTunes interface try Songbird. :guitar:

---

### Post by Nepherte on 2008-06-23
Most of the recommended music players like amarok, exaile, banshee etc... are not really what the topic starter looks for I believe. They are more alternatives for Windows Media Player, Itunes and Real Player. I think he's more looking for programs like audacious and xmms.

---

### Post by T-Virus on 2008-06-23
I just wanted to say that if all you need is listen to music - XMMS must be the best choice. It does not require a lot of resources and it plays music well.

As for myself - I use Amarok but I have huge collection and I like having sorted library with ID3 tags and everything. Anyway you said you don't need this so go for XMMS.

---

### Post by buzzz on 2008-06-23
> **Troll_the_Great said:**
> Hello all

I see that many of you use Amarok?Do you have any problem with the lyric scripts?Mine broke for no reason.The default one gives me an error (I posted a thread called "Script error" if you want to look at it) and wiki lyrics say I must install some programs:
```
Sorry...
You need one of QtRuby, RubyGTK or TkRuby to run this program
```

I don't know where to find them. Can someone help please?

For Kubuntu
apt-get install libqt0-ruby1.8

For ubuntu
apt-get install libgtk2-ruby1.8

---

### Post by sujoy on 2008-06-23
bmp might be another viable option besides xmms and audacious. but audacious takes up more memory than xmms.

---

