---
title: "HOW TO: Author a simple DVD form video file"
date: 2005-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by endy on 2005-07-18
Today we'll learn how to download a film, transcode it ready for DVD, create the file structure of a DVD, make a DVD ISO and burn the damn thing :) Yep, you heard me, *download a film*, but not just any film, the worst film ever! Why? -- Why not!

You may have heard the other day that Edward Wood's film flop 'Plan 9 from Outer Space' was [released to the public domain](http://www.archive.org/details/Plan9FromOuterSpace) so that means you can download it absolutely free. Now just before we start you may want to read this review from the [IMDB](http://imdb.com) if you don't know the film:

> Poor poor Plan 9: So bad people just watch it to laugh about how bad it is, yet this fundamental flaw pushes it above bad movies, and so it's stuck in between the bottom 100, and well, no where near the top 250...

Anyway, back to the movie. It is as bad as you've no doubt heard. The scene changes from night to day to night, the spaceship is a hubcap (you can see the string it hangs from catch on fire at one point), I could do a better job acting, etc. ad nauseum. But it takes a hell of a lot to be almost universally considered the worst movie of all time, and here is Plan 9's true strength. There are many horrible of movies, but most of them are so bad because they are too bad to be truly bad, and therefore sink into mediocrity. Plan 9, however, has no redeeming quality's, and so it stands out. Few will recognise a movie such as "The Medallion," but every movie-goer knows Plan 9.

As I said before, it takes a hell of a lot to be the worst. Because of this, Plan 9 is some of the most fun you'll EVER have watching a movie. Almost every scene is so bad I broke out laughing. Few other movies achieve that kind of humor, whether intentional or not. For that I give it a very intentional 10/10.


Prerequisites: Just before we start you may want to check you have all of the following:

1.  The 'dvdauthor' and 'ffmpeg' programs, first follow [this link](http://www.ubuntuguide.org/#extrarepositories) to add the extra repositories if you haven't already then:

```

sudo apt-get install dvdauthor
sudo apt-get install ffmpeg

```
2.  A DVD burner as we will be burning a DVD, also a DVD+/- R/W disc could be useful ;)

3. Broadband connection, may god help anyone downloading a 1.8G file on 56k :S

4.  A love of films.


Still interested? Ok then, lets begin.


1.  Download the film from the link on the page below and let bittorrent do the rest. Remember to share the file back (at least 100%) when you're done too, thats very important. I did it so you can too :) This is a 1.8G file so it could take a while to download.

```

[http://torrents.pdmdb.org/details.php?info_hash=686368294eb5b9226a60534a442b497351c8b7c5](http://torrents.pdmdb.org/details.php?info_hash=686368294eb5b9226a60534a442b497351c8b7c5) 

```


2. Open up a terminal and change directory to where you downloaded the film. Now lets use ffmpeg to transcode the file ready for a dvd:

```

ffmpeg -i ./Plan_9_From_Outer_Space.mpeg -target dvd -hq -aspect 4:3 ./plan9.mpeg

```

Right, go do something for a few hours, this will take a while. Take in some TV, sports or go for a drink with friends.


3.  That's the donkey work out the way now lets use dvdauthor to create the DVD filesystem:

```

dvdauthor ./plan9.mpeg -o plan9

```


4.  Now we need to create the titles in that filesystem. Nothing fancy, AFAIK these are just techincal titles as you wont actually see anything when you run this DVD in your DVD player:

```

dvdauthor -T -o ./plan9

```


5.  Now it's time to master the dvd iso:

```

mkisofs -dvd-video -o plan9.iso ./plan9

```


6.  Lets check the iso and make sure it looks good as DVD's are quite specific:

```

isoinfo -i plan9.iso -l

```

You should get output similar to what I got below:

```

Directory listing of /
d---------   0    0    0            2048 Jul 18 2005 [    276 02]  . 
d---------   0    0    0            2048 Jul 18 2005 [    276 02]  .. 
d---------   0    0    0            2048 Jul 18 2005 [    278 02]  AUDIO_TS 
d---------   0    0    0            2048 Jul 18 2005 [    277 02]  VIDEO_TS 

Directory listing of /AUDIO_TS/
d---------   0    0    0            2048 Jul 18 2005 [    278 02]  . 
d---------   0    0    0            2048 Jul 18 2005 [    276 02]  .. 

Directory listing of /VIDEO_TS/
d---------   0    0    0            2048 Jul 18 2005 [    277 02]  . 
d---------   0    0    0            2048 Jul 18 2005 [    276 02]  .. 
----------   0    0    0            6144 Jul 18 2005 [    282 00]  VIDEO_TS.BUP;1 
----------   0    0    0            6144 Jul 18 2005 **[    279 00]  VIDEO_TS.IFO**;1 
----------   0    0    0           49152 Jul 18 2005 [1159328 00]  VTS_01_0.BUP;1 
----------   0    0    0           49152 Jul 18 2005 [    285 00]  VTS_01_0.IFO;1 
----------   0    0    0      1073709056 Jul 18 2005 [    309 00]  VTS_01_1.VOB;1 
----------   0    0    0      1073709056 Jul 18 2005 [ 524581 00]  VTS_01_2.VOB;1 
----------   0    0    0       226252800 Jul 18 2005 [1048853 00]  VTS_01_3.VOB;1 

```

Don't worry if some of the number are slightly different, the line in bold is the important bit, It has to contain the lowest number after the "." and ".." entries above it. All *should* be Ok though.


7.  Next is the burning:

```

growisofs -dvd-compat -Z /dev/dvd=plan9.iso

```

Now sit back, wait for it to burn, eject it and go watch it with your friends and family with some pop corn :D

---

### Post by endy on 2005-07-18
Ahhh crap, I just realised I posted this in the wrong forum. Perhaps a friendly mod could help me out here... :D

---

### Post by kirillrdy on 2005-11-07
[QUOTE=endy]Ahhh crap, I just realised I posted this in the wrong forum. Perhaps a friendly mod could help me out here... :D[/QUOTE]

I dont think thats gonna happen, i think u'd have to PM someone,

---

### Post by [D-Tail] on 2006-04-16
Is there actually a way to add more 'movies' to one DVD? I am a complete DVD video mastering-noob, really... Let's say I've downloaded this TV-series, consisting of 9 episodes. Every three of 'em fit exactly on one 4.7GB DVD. So basically, what I want to do, is converting the AVIs to MPEG (some quality loss is acceptable). I have achieved this already by doing the 'ffmpeg' line, first step in the process. But then, how to make all MPEGs appear on a single DVD ISO? Thanks in advance!

Yours,

[D-Tail]

---

### Post by kirillrdy on 2006-04-16
[http://dvdauthor.sourceforge.net/doc/ex-title.html#AEN41](http://dvdauthor.sourceforge.net/doc/ex-title.html#AEN41)

I hope this will help.
Actually, i could answer more detailed, but i just woke up, need to be awake.
Look at that link, if that doest help you, let me know i'll explain some more :-)

---

### Post by [D-Tail] on 2006-04-17
This seems quite doable -- I'll try it ASAP (and when I've converted my AVIs to MPEG; still in progress). So on this page, I saw several XML elements, like <titleset> and <title>. My next question may be a bit off-topic, but what difference is there between titles and chapters? I mean, I could easily add three episodes as three chapters in one title. I could also add three titles, with one chapter in them, containing an episode. Which is the preferred way?

---

### Post by kirillrdy on 2006-04-17
The difference as far as i can think of is.
If you create 3 epd in 1 title 3 chapters. On stand alone DVD player it will play one ep after an other , like they are ONE thing, if you keep them as sepparate titles, After each ep it will come back to main menu. I hope i get what i mean.

What i suggest you, is, If epesodes follow each other, i mean 1 ep is continuation of story of previouse ep, you should put them in 1 title and 3 chapters.
If story is unrelated, ( like Simpsons for example,) u can keep them sepparate titles.

But in reality its up to you :)

---

### Post by [D-Tail] on 2006-04-17
You're a real good help, thanks so far already ^_^. So if I'd go for the 3 eps in 3 titles, I'd need a menu, right? Should I read another HOWTO for that? Or is it generated automagically?

I'm really showing my noob-ness, aren't I? ;-)

---

### Post by kirillrdy on 2006-04-17
For making menu, you either use some program eg dvdstyler qdvdauthor, or make it by hand. Actually I never done it, simply because i think its too much of troubles just for 1 dvd, ( and i burn tons of those :P )
if u are interested [http://fixounet.free.fr/avidemux/doc/en/DVD/index.html](http://fixounet.free.fr/avidemux/doc/en/DVD/index.html)



Actually since I dont make menus ( I am lazy) , so in my case if i have 2 titles, my DVD player stops after first title, and I need to press Play to keep playing the second title or press " >| "

---

