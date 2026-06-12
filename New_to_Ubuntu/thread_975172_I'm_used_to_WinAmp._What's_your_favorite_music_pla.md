---
title: "I'm used to WinAmp. What's your favorite music player and why?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by surelock22 on 2008-11-08
Right now, I've been playing my music files in Rhythmbox, a good media player, but I'm curious if I'm missing something better. I read that Amarok is pretty decent, and if I own an ipod that it'll sync with it easily, which is a plus if I have a friend bring his over or if I ever get one. Any suggestions, even if you suggest using these two, that's fine, just let me know that I'm using the most powerful / user friendliest. 

THXINADVANZ

---

### Post by thunk77 on 2008-11-08
Audacious is very close to Winamp, you could give that a try.
Also when installed you should search for plugins in Synaptic if you want extra features than the default install.

---

### Post by shifty_powers on 2008-11-08
Amarok +1

it looks good, does everything i want and is very easy to use :D

---

### Post by Kosimo on 2008-11-08
If you like Winamp, I recommend you to give it a try to Audacious. It is very very similar, you can even install winamp 2.x skins, (download and then drop them into audacious) 
[IMG]http://kosimo.googlepages.com/audacious1.4winampskin.png[/IMG]



It doesn't support iPod sync, but for that matter you can easily use Rythmbox. It is clean and it doesn't use KDE libs

---

### Post by surelock22 on 2008-11-08
wow, that Audacious looks pretty rad. i may check that out. right now, i'm d/ling Amarok and i'll check it out to see where that puts me. if it works well, i'll just stick with that. but props on that desktop!

---

### Post by GrammatonCleric on 2008-11-08
Amarok:  Once you get used to the interface it has everything that you could want in a music player/manager.    Here's what I use it for...

- Managing, organizing and playing my 50,000+ music files.

- Managing, downloading and playing all my podcast shows.

- Listing to online audio streams and last.fm integration.

- Syncing to my ipod. Using the transcode on the fly plugin to convert my ripped ogg files to mp3 for playback on my ipod.

- Love the fact that I can point the backend database for Amarok to MYSQL or PostgreSQL.  


I also like Exaile, which is a GTK version of Amarok, too but it does not yet have all the functionality that Amarok has....yet.

- GC

---

### Post by glotz on 2008-11-08
I use the mpd + mpc + ncmpc packages. It's a music player for the command line. It uses very few resources and is easy to script.

---

### Post by surelock22 on 2008-11-08
> **glotz said:**
> I use the mpd + mpc + ncmpc packages. It's a music player for the command line. It uses very few resources and is easy to script.

I'm not very command line "advanced". I copy and paste commands into the terminal, THAT'S IT. My brother is going to show me how to use Playlist.com to get any single song I want using the terminal, which I think is cool. Otherwise, I need a GUI media player. :)

---

### Post by vishzilla on 2008-11-08
Rhythmbox is my fav. You could use Audacious. Its a good winamp replacement.

---

### Post by Zopiac on 2008-11-08
rhythmbox; i can make it look minimalistic :D

---

### Post by surelock22 on 2008-11-08
Well, I can say this: there are definitely more choices on Linux that are actually worth something than what I've seen on Windows. Literally, WinAmp was the ONLY media player that I would use that wouldn't try to fully integrate itself into every type of media file even when I told it not to (i.e. iTunes and WMP). Rhythmbox and from what I've seen from Amarok, are both pretty good. I like Amarok slightly more-so right now, but I'll test both out quite thoroughly.

---

### Post by Teabicky on 2008-11-08
I like Aamrok, it look great, is easy to navigate large volumes of music.  I started using Rhythmbox but I couldn't get it to archive my files in a way that I liked.

---

### Post by gradysghost on 2008-11-08
If you like WinAmp, as many others have said, Audacious is great.  Personally, I use RhythmBox to browse and listen to my music.  If you want something for an iPod interface, nothing I've found can come close to matching the quality of [Floola]("http://www.floola.com") (not in the repos).  It's not open source, but it is freeware, and none can compare.

Installation is easy.  Download it to your desktop.  It will run by itself straight from there, but if you don't want it on your desktop, taking up space, you can do what I've done.  Save the tar.gz file they provide on the website to your desktop, then follow these commands:

```

sudo -i
[Provide password]
mv /home/username/Desktop/Floolafile.tar.gz /usr/lib/
cd /usr/lib
tar -xvf Floolafile.tar.gz

```

That moves the Floola tarball into your /usr/lib directory, and then unzips it.  The tarball contains a folder, and it will create that folder when you unzip it.  To find out what the folder was called, do this:

```

whereis Floola
 - or -
whereis floola

```

...depending on how the file is capitalized.  At any rate, note the folder that it spits back at you.  Then do this:

```

cd /usr/bin
ln -s /usr/lib/Floola-linux/Floola floola

```

...only make sure that the "/usr/lib/Floola-linux/Floola" is the correct path that the whereis command gave you.  What you've done now is create a symbolic link to the Floola executable.  Type "exit" and press Enter to get out of SuperUser mode.  Now, from anywhere, you can run the command "floola" and launch the program.

Hope this helps.  It really is the best iPod interface I've found yet for Linux.

---

### Post by Gausian on 2008-11-08
[Exaile ]("http://www.exaile.org/") is a pretty good player as well, that integrates nicely with Gnome

---

### Post by gradysghost on 2008-11-08
Floola doesn't come with an icon to use for launchers, and I'm the kind of guy who likes his icons.  So I made [this one]("http://lh4.ggpht.com/_i9Jd9BJ6PRY/SRWwqdGxF-I/AAAAAAAAAV4/C-Zg3Plvd9w/s144/floola.png") by screenshotting their webpage and then doing some basic manipulation.

---

### Post by kaptengu on 2008-11-08
I also like Exaile.

---

### Post by oldos2er on 2008-11-08
Exaile (for Gnome) and vlc.

---

### Post by Sirron on 2008-11-08
If you've got a massive library and prefer a WMP style interface (not that I expect you do, but just in case ^^) try Songbird. Built on the Mozilla platform, but not BY Mozilla, it has a growing extensions and skins community. It's also one of the only media players I've used on linux that can work with the official Last.fm client like WMP on windows.

Incidentally, if you're into Last.fm, try BMPX.

---

### Post by metallicamike on 2008-11-08
amarok, banshee or rythmbox fo me

---

### Post by surelock22 on 2008-11-08
> **Gausian said:**
> [Exaile ]("http://www.exaile.org/") is a pretty good player as well, that integrates nicely with Gnome

My brother is a big fan of Exaile, and I was reading some of the stuff it does, and I'm gonna try it out.

I guess the moral of the story is to try out a couple and see which is best for you. So far Amarok is the winner, but I'm waiting to try Exaile ...

---

### Post by doorknob60 on 2008-11-08
Amarok and Exaile are my favorites, although I'm looking for a replacement as well (not totally satisfied with Exaile, and Amarok looks bad in this setup, at lewast until Amarok 2 comes out)

---

### Post by ad_267 on 2008-11-08
Rhythmbox ftw.

I'd like Banshee if it wasn't so slow on my computer and if I could add .flv files to my video library.

---

### Post by Yashiro on 2008-11-08
If you're an old school Winamp user, get Audacious.

---

### Post by hakimaki on 2008-12-02
MPD, the only player that I found that does random playback right. Just because I have 20 Beatles albums, it doesnt mean I want to hear a Beatles song every 5th song. The big names like Amarok and Rhythmbox were all guilty of this. Sonata provides me a simple GUI to quickly scan my library if I want to hear a certain song.

---

### Post by Locutus_of_Borg on 2008-12-02
im currently using mpd/gmpc 
its good in that it plays music, and is fast to load
i used to use amarok, but prefer gmpc since it loads a lot faster, and has the same usability that i liked without the need for qt/kde bloat

i dont require much beyond a searchable playlist that has buttons i can click on to play music, though

---

### Post by Precipitous on 2008-12-06
I would try BMPX. The Last.fm integration is awesome, it searches/plays Shoutcast streams, has EQ, displays covers, artist info and lyrics - all in all, it is the best Linux audio player/manager I have found.

---

### Post by poetstorm on 2008-12-06
Personally I am happy with the Totem movie player. It loaded my music by default upon my Ubuntu installation and I like the way it works with playlists. Plus the visualization schemes are neat, though I wish it had more choices.

I tried Rhythmbox but I didn't care for the layout.

---

### Post by birddog165 on 2008-12-06
I use Listen. It's worth looking at and has lots of features.

---

### Post by banerjeerupak on 2008-12-06
been using Rhythembox for my music. 
Neat presentation. 
will try some other players now and then comment on which one feels better.

---

### Post by kaptengu on 2008-12-07
The only music player you need from now on is Spotify. I hope they make a linux-version soon, so we don't have to use wine.

---

### Post by mhh91 on 2008-12-07
i use rhythmbox on GNOME and amarok on KDE

---

### Post by surelock22 on 2008-12-07
Lets see... I tried using Amarok, then Exaile perked my ears up with it's Dynamic playlist feature, but then Exaile would just quit on me for no reason, no reason at all, right in the middle of a song and everything, so I went back to Amarok and realized it had a pretty good Dynamic playlist feature and a "random 50" playlist feature that's pretty cool too. I'll just load up the random 50 and then delete some of the songs that I just don't want to hear (or don't belong there, like an entire EDM DJ set, Comedy Audio or Porn Audio Books). That typically suits me fine.

What I'd really like to know now (and I may need to start another thread) is if I can rate all my music by a number (lets say 1 - 5) and make a playlist based on the number, that way I'd kind of get a (hopefully) radio-like experience from my own collection.  Any way to do that with Amarok, or do I need another player for that, if it's possible?

---

### Post by T2manner on 2008-12-07
Exaile because it is simple and very easy to use.

Amarok because it is all around best imo.

They both look way better than all the other ones.

Rhythmbox is good, but i'v had some problems with it.

---

### Post by banerjeerupak on 2008-12-07
Audacious is nice. Esp for those who are familiar or feel comfortable with winamp

But Banshee is not worth the effort of installing it. Didn't prove itself.

---

### Post by MarblePanther on 2008-12-07
Audacious for the minimal look and feel

Exaile for a slightly cleaner version of amarok with ipod support in Gnome

Amarok for full-featuredness and ipod support in Kde

Songbird for web-integration and ipod-sync support!

gtkpod for the best linux-ipod relationship ;)

---

### Post by justutkarsh on 2009-02-20
I ve been searching for equivalent to winamp in ubuntu  for long time
and i ve tried most of them (banshee amarak rhythmbox xine..)
but exaile is GOD after you install all the plugins
faster algo for searching a track in collection
far more customizable. supports tray control uses 
gstreamer for audio playback and very fast for gnome.

---

### Post by MrWES on 2009-02-20
I run Rhythmbox, mainly becuase it supports mt-daap shares. I would have to admit, Amarok seems to have the most features. With mt-daap (Firefly) I can share my complete audio library with everyone in the household from one place.

Bill

---

### Post by baizon on 2009-02-20
I've like it simply (like Winamp under Windows), so i'm using **Audacious**.

---

### Post by konqueror7 on 2009-02-20
rhythmbox, just lazy to install others, and it meets all my needs...:o

---

### Post by Vorian Grey on 2009-02-20
My two favorite is Amarok and Banshee. I probably use Amarok 95% of the time.

---

### Post by _noob_ on 2009-02-20
VLC And Amarok For me. The VLC because it plays all formats no problem and the Amarok because it has useful things built in.

---

### Post by Dougie187 on 2009-02-20
I enjoy command line mplayer. It's really simple, and I can play music that I mount with sshfs. It's lightweight enough to not have much overhead too.

---

### Post by Ivo Moelans on 2009-03-09
I was used to WinAmp too.

Now I use [**gmusicbrowser**]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html") because it has the functions I used under WinAmp and then some. It is also very stable and configurable.

It is not the most pretty and it takes some getting used to.

---

### Post by MrWES on 2009-03-09
> **surelock22 said:**
> Right now, I've been playing my music files in Rhythmbox, a good media player, but I'm curious if I'm missing something better. I read that Amarok is pretty decent, and if I own an ipod that it'll sync with it easily, which is a plus if I have a friend bring his over or if I ever get one. Any suggestions, even if you suggest using these two, that's fine, just let me know that I'm using the most powerful / user friendliest. 

THXINADVANZ

+1 For Rhythmbox -- it supports mt-daap; network music shares.

Bill

---

### Post by pitje on 2009-03-09
I use [mocp](http://moc.daper.net/)

all from the cli. Simple and it does what I want it to do (play music)

---

### Post by jocheem67 on 2009-03-09
Rhythmbox +1
Nice library-handling.

Songbird +1
Because it looks slick

Foobar2000 with wine
Because it's tagging capabilities

- it's converting possibilities

- "file operations" deleting, copying, renaming, great little feature

- it's extensive info on files

- it's replay gain capabilities

and more.....:D

Foobar was the reason for me to stick to windows as main os, however it now runs decently with wine.

Won't be ported btw, and that's a great shame:(

---

### Post by sideaway on 2009-09-01
Foobar on windows, rhythmbox for Linux. I think Rhythmbox is underrated sometimes. I used Amarok for a long time. But Rhythm handles my library much nicer. I think you really need KDE to run Amarok in a stable environment.

---

### Post by bug67 on 2009-09-01
Well, I'm using WinAmp via Wine!  

Actually, I use Rhythmbox but, WinAmp through Wine has been the *only* way I have been able to get the MilkDrop visualizer to play.  Works awesomely!  I have not been able to get ProjectM to work in *any* of the native Linux players so, WinAmp via Wine it is!

:popcorn:

---

### Post by Ichtyandr on 2009-09-01
one more +1 for Exaile

Rhythmbox does not have equalizer for some reason
I also used Banshee but Exaile beats them both
Amarok is great but consider it is a KDE app, so Exaile will integrate better on Gnome desktop
Audacious is different though, it is more like good old Winamp, but cannot use it after Exaile

---

### Post by theozzlives on 2009-09-01
I like Amarok14 (available in the PPAs). I'm a karaoke singer and can follow along with the lyrics when practicing a new song.

---

### Post by colau on 2009-09-01
Audacious.
Lighter.

---

### Post by mvalviar on 2009-09-01
Try amarok 2.1.1. Amarok2 is now as good as 1.4.

---

### Post by NikoC on 2009-09-01
+1 vlc
Very basic player which is very easy to use!

---

### Post by dez93_2000 on 2010-05-26
defo +1 for songbird. tried audacious, exaile, rhythmbox, already have rhythmbox and vlc. Didn#'t like the first 3 - too unintuitive but possibly rewarding later, or too simple. Singbird is intuitive and looks and acts like winamp, PLUS has tons of plugins to hopefully do everything WA did for you.

---

