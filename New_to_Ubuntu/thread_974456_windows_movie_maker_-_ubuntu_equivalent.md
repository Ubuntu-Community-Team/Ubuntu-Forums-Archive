---
title: "windows movie maker - ubuntu equivalent ?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-07
does anyone know a good free alternative to windows movie maker?

---

### Post by bobnutfield on 2008-11-07
I use Cinelerra, but I don't think I could compare it to Movie Maker.  It is much more powerful, but as such it is much more complicated to run.  It has reached stability now, and is maintained by cinelerra.org, where you can find a tutorial.  But, if you want something just as simple to use, I probably would not recommend Cinelerra.

---

### Post by nhasian on 2008-11-07
some video editing tools for linux include:

Cinelerra, KDenlive, LiVES, Kino, AviDemux 



[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

### Post by iKonaK on 2008-11-07
> **nhasian said:**
> some video editing tools for linux include:

Cinelerra, KDenlive, LiVES, Kino, AviDemux 



[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
+1 
i never use intensively video editing but from what i saw AviDemux & LiVES seemed cool....

---

### Post by B34ST1Y on 2008-11-07
movie maker > cinelerra? or cinelerra > movie maker ? ?

---

### Post by SunnyRabbiera on 2008-11-07
Video editing is a weakness in linux sorry to say, there isnt much out there for it at this time.

---

### Post by bobnutfield on 2008-11-07
> **B34ST1Y said:**
> movie maker > cinelerra? or cinelerra > movie maker ? ?

SunnyRabbiera is correct.  Video editing has a long way to go get to the level of something like Adobe Premier.  Cinelerra is much more powerful than Movie Maker, but as I mentioned it is also much more complicated to use and rendering the final compilation can be iffy.  Take a look at the tutorial:

[http://www.robfisher.net/video/cinelerra1.html]("http://www.robfisher.net/video/cinelerra1.html")

---

### Post by ad_267 on 2008-11-07
> **B34ST1Y said:**
> movie maker > cinelerra? or cinelerra > movie maker ? ?

Depends on what you want to do.

If you're after something like Move Maker then you're probably better off with Kino or Avidemux, Cinelerra would be to complicated.

---

### Post by B34ST1Y on 2008-11-07
I have followed the steps to install Cinelerra...and everything looks like it worked correctly....but how do I start it? ```
cinelerra
``` in terminal does nothing, and I cant see an icon for it anywhere...?

---

### Post by chrisod on 2008-11-07
The only reason I still have a Windows partition is to use Movie Maker. I simply have not found anything in Linux that compares.

---

### Post by stinger30au on 2008-11-07
> **B34ST1Y said:**
> does anyone know a good free alternative to windows movie maker?


why use an alternative???

install virtualbox it is in the repos. install your copy of XP

xp runs fine in VB and you can use movie maker. 

share directorys between xp and ubuntu with "guest aditions"

works like a charm. been doing this for ages

---

### Post by B34ST1Y on 2008-11-07
thats a gimped answer. I hate M$oft. why use them if you dont have to? There's got to be a way to do video editing.

---

### Post by B34ST1Y on 2008-11-07
im content with using cinelerra...I just cant seem to turn it on? How am I supposed to run it?

---

### Post by chrisod on 2008-11-07
Hate MS or not, even the blind squirrel finds a nut once in a while. Movie Maker is their nut. It's probably the best designed, most user friendly app MS has ever put out. I've tried every video app in the repositories, never got one of them to actually complete a project. They all fail in some unique way. Granted, that was a year ago and they could have improved a lot in the last year. However if you have XP or Vista, you've paid for and own Movie Maker...

Or, you can ignore us and beat your head against the wall with the open source video apps that simply aren't there yet. Your choice :)

---

### Post by ugm6hr on 2008-11-08
I used kdenlive v0.5, which I found very simple for editing home video, adding soundtracks and fading scenes.  I haven't used Windows MovieMaker, but I think it was designed in a similar fashion (i.e. for home rather than professional use).

I haven't used it since the 0.7 (KDE4) update, but I think the Ubuntu repos still have 0.5 anyway.

Only problem - it would spontaneously shut itself down from time to time - so just make sure you save your work frequently!

---

### Post by B34ST1Y on 2008-11-08
> **ugm6hr said:**
> I used kdenlive v0.5, which I found very simple for editing home video, adding soundtracks and fading scenes.  I haven't used Windows MovieMaker, but I think it was designed in a similar fashion (i.e. for home rather than professional use).

I haven't used it since the 0.7 (KDE4) update, but I think the Ubuntu repos still have 0.5 anyway.

Only problem - it would spontaneously shut itself down from time to time - so just make sure you save your work frequently!

this may be a stupid question...but if it says its for KDE...will it still work if i'm using a GNOME desktop? o.O

---

### Post by ad_267 on 2008-11-08
> **B34ST1Y said:**
> this may be a stupid question...but if it says its for KDE...will it still work if i'm using a GNOME desktop? o.O

Yes, you just have to install some extra kde libraries. They also have to load when the application runs, which can make it a little bit slower to load. As long as you have plenty of hard drive space there isn't an issue.

---

### Post by Argentino on 2008-11-09
> **B34ST1Y said:**
> im content with using cinelerra...I just cant seem to turn it on? How am I supposed to run it?

Make sure you installed the application. :D

List of commands to add rep to your sources and then install:

```
wget -q http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update 
```

then

```
echo deb http://akirad.cinelerra.org akirad-intrepid main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update 
```

and finally to install:

```
sudo apt-get install cinelerra
```

The second line of code is probably not necessary, but just in case it is there.

To run it, it will be under Applications>Sound & Video>Cinelerra or just cinelerra in yout terminal.

Hope it helps!

---

### Post by B34ST1Y on 2008-11-09
fantastic, thanks guy! :) :) thanks all around!

---

### Post by faintscrawl on 2009-03-19
Has anyone ever successfully edited a video in Cinelerra, rendered it and (using another program) got it on a dvd and have it look half-decent and in sync?

If no one has, I'm going to give up.  :)

---

