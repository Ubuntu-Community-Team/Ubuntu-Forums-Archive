---
title: "Music ripper"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by loseby on 2008-10-23
I used Cdex in Windows and want something simialr in Ubuntu that will not only rip the music to MP3's but get all the details ie album/song titlt/artist etc

---

### Post by swisscow on 2008-10-23
Doesn't rhythmbox (when it's extracting a new cd) get this information from an online database when you rip a cd?

---

### Post by loseby on 2008-10-24
Have been looking at it but it doesnt appear to encode MP3's

I really dont want something that plays music, just want a program that will rip to MP3's and let me save just the song title and artist name.

---

### Post by swisscow on 2008-10-24
This it will do, without playing the cd. It just uses the **audio cd extractor** software - you can load this seperately (if it's not installed already do so through add/remove software).

You will also need to do 2 more things. The first is to go into edit..preferences in audio cd extractor and set the format to mp3. If mp3 is not an option, then it means you need some codecs.

If so then in add/remove again install the **ubuntu restricted extras** package and that should give you the codecs you need.

Then back to audio cd extractor, edit..preferences and so on

---

### Post by loseby on 2008-10-24
ok, needed the restricted extras and now can rip to MP3 but the problem is I want to rip at 256 or 192 and not 128.

Cant see any option for changing this


btw: thanks

---

### Post by Piraja on 2008-10-24
> **losbey said:**
> Cant see any option for changing this
It seems to me too that Rhythmbox can handle only 128 kbps MP3. Too bad. By the way, I installed **[Grip]("http://www.nostatic.org/grip/")** yesterday and I would recommend that. More advanced IMO. I got the Beta version (3.3.1) available in the Intrepid repos.

Just try: sudo apt-get install grip

---

### Post by loseby on 2008-10-24
I tried Grip and had problems but will try the latest beta version

---

### Post by indytim on 2008-10-24
Sound Juicer (it's in the repositories).

IndyTim

---

### Post by starcannon on 2008-10-24
ripperx(i think it looks and feels a lot like cdex) its in the repositories, its plenty fast, has all the required features, is easy to use, and works nicely with lame mp3 encoder/decoder(which you should also grab from the repositories), you can use {System}>{Administration}{Synaptic Package Manager} then search for "ripperx", then search for "lame" and click install it; or, you can type ```
sudo apt-get install ripperx lame
```GL and have fun.

---

### Post by fatphilthethird on 2008-10-24
I second ripperx. 

Tried sound juicer but it produced huge mp3 files (~50mb per track) and never could work out how to get them smaller. Ripperx just got them to a small size, at the samre bitrate, without any addtional tinkering

Fat

---

### Post by kpkeerthi on 2008-10-24
I vote for [rubyripper]("http://www.google.com/search?q=ubuntu%2C+rubyripper")

---

### Post by andrew.46 on 2008-10-24
Hi,

You could do worse than try abcde:

[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

The big brother of this guide is here:

[http://andrews-corner.org/abcde.html](http://andrews-corner.org/abcde.html)

  Andrew

---

### Post by Piraja on 2008-10-24
Just ripped some Ornette Coleman with **abcde** and I must say it's darn good. Thanks Andrew!

---

### Post by andrew.46 on 2008-10-24
Hi Piraja:

> **Piraja said:**
> Just ripped some Ornette Coleman with **abcde** and I must say it's darn good. Thanks Andrew!

It is a great little script. I am not sure what place this site has in the continuing development of abcde:

[http://code.google.com/p/abcde/](http://code.google.com/p/abcde/)

but it certainly seems to have an svn repository with faily recent work on the code. Hopefully abcde will continue to develop.

  Andrew

---

### Post by Piraja on 2008-10-25
Now that I got the hang of it, I'm exploring the world of GUI-less audio programs: first **mp3blaster** for listening, then **abcde** for ripping, and now **dir2ogg** for converting. I'm absolutely impressed!

I tried to convert some wma files to mp3 and ogg, but both SoundConverter and OggConvert failed. I searched the repos and found dir2ogg, a text-only audio file converter, and tried it: smooth and fast, no problem at all. 

Upon this couple of days' experience, I highly recommend all these three GUI-less, powerful and easy-to-use apps for any audio enthusiast.

---

### Post by Piraja on 2008-10-25
... and take a look at **Orpheus** too:

[[IMG]http://www.aijaa.com/img/t/00822/2974598.t.png[/IMG]](http://www.aijaa.com/v.php?i=2974598.png)

As you can see in the screenshot, Orpheus is very slick in e.g. Ubuntu's graphical environment, since unlike mp3blaster, it appears to respect the custom Gnome Terminal settings, such as transparency.

Nice!

---

### Post by andrew.46 on 2008-10-26
Hi Piraja,

There are some amazing cli media players around and available for Ubuntu. You might be interested in the biggest of them: the svn MPlayer. Some fellow has written a guide for this:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

The gui that comes with this is a little poor but the command-line player is a very, very powerful beast.

  Andrew

---

### Post by Piraja on 2008-10-26
Cheers Andrew,

an impressive tutorial, I will try it later.

As an addition to my previous postings, while Orpheus has a great name and looks very nice in a customized X terminal, I'm afraid I still prefer mp3blaster &#8212; in spite of its name which, in my opinion, just does not make sense. Mp3 is not a generic name for all audio formats, in spite of all the hype. *EDIT*: But luckily, I don't have to choose between them. I can have both! 

Too bad not many portable players support Ogg Vorbis...

---

### Post by Piraja on 2008-11-01
Andrew, I followed your tutorial and installed **Mplayer** on my laptop accordingly. It is indeed a feature-rich, impressive tool. You were right about the GUI, though, and I don't really care for it — I confess I'm an aesthete and put off by skins that I find unattractive or clumsy.

I also realized that **mplayer-nogui** is available via Synaptic at least in the Intrepid repos, so I installed it that way on my desktop machine. It provides a nice minimal player setup.

There are indeed quite a few good choices available in the Ubuntu repos.

To name one more, I searched for a gapless, GUI-less player, and found **Music On Console**. To install it or to read a few words of information about it, you can search with Synaptic for **moc**. Or just type **sudo apt-get install moc**. Remarkably enough, MOC has a namesake, and you must launch the program in terminal by typing "mocp". Typing "moc" returns a message telling that "The program 'moc' can be found in the following packages: *libqt4-dev * qt3-dev-tools" etc. — but it's a different application.

Since MOC is gapless (like Aqualung on the GUI side), I think it's my personal favourite CLI music player at the moment.

---

### Post by andrew.46 on 2008-11-01
Hi Piraja:

> **Piraja said:**
> Andrew, I followed your tutorial and installed **Mplayer** on my laptop accordingly. It is indeed a feature-rich, impressive tool. You were right about the GUI, though, and I don't really care for it — I confess I'm an aesthete and put off by skins that I find unattractive or clumsy.

The MPlayer developers are *very* unenthusiastic about the gui :-). Many people are in fact installing MPlayer without the gui and using smplayer, this might be worth a try particularly as the developer is quite active on these forums.

> There are indeed quite a few good choices available in the Ubuntu repos.

To name one more, I searched for a gapless, GUI-less player, and found **Music On Console**. To install it or to read a few words of information about it, you can search with Synaptic for **moc**. Or just type **sudo apt-get install moc**. personal favourite CLI music player at the moment.

Looks good and I shall certainly try it out.

  Andrew

---

### Post by Piraja on 2008-11-05
I posted a question concerning abcde in another thread: [**[HowTo] abcde**]("http://ubuntuforums.org/showthread.php?t=109429"), post [#30]("http://ubuntuforums.org/showpost.php?p=6109169&postcount=30"). Thanks in advance for taking a look at it!

---

### Post by Jozza The Wick on 2008-11-07
Thanks for this. Wanted something quick & simple to rip to mp3 - not bothered about bit-rate or anything like that - 'CD quality' is good enough for me. Had tried Sound Juicer before but didn't see an option for mp3s. Now I know why - needed to install the restricted-extras package...thanks!

---

### Post by Piraja on 2008-12-30
I would like to add one hint that I find very useful. Andrew mentioned Easytag somewhere as a fine addition to abcde and other audio applications as well. In addition to that, Thunar (the default file manager for XFCE) contains a tool that is very handy also in GNOME: **Bulk Rename**. With this you can e.g. remove all "messy" characters from a whole album's track titles, replace spaces, and do lots of other things with a few clicks. This is indispensable for many CLI music applications. For example, abcde does not clean up the messy characters from its output, at least by default, MPD does not add files and folders while creating a new database if they contain parentheses and other problematic punctuation marks, etc.

---

