---
title: "How to install?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by ReeyferMadness on 2008-07-09
Hey, I was trying to d/l a game (dofus) and when I installed it it just opened in the file manager.  A bunch of random files.  Am I missing the right kind of installer or do I need to install it manually (and if so wtf how?  :O )

thx

---

### Post by chalewa on 2008-07-09
is there a readme in there with some instructions?

do you see a file called 'configure'?

---

### Post by ReeyferMadness on 2008-07-09
config.xml is in there

no readme or anything like that

---

### Post by pofigster on 2008-07-09
It could be that you just need  to run one of the files in the folder from the CL
```
~/home/user/folder-where-installed/.game
```
That's how a lot of games work.

---

### Post by damis648 on 2008-07-09
Can you give us the download link? We can help more this way.

---

### Post by overdrank on 2008-07-09
> **ReeyferMadness said:**
> Hey, I was trying to d/l a game (dofus) and when I installed it it just opened in the file manager.  A bunch of random files.  Am I missing the right kind of installer or do I need to install it manually (and if so wtf how?  :O )

thx

Hi and what type of file, deb, tar? 
And this link may help
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by AOZ on 2008-07-09
FYI the easiest way to download/install anythin is via Add remove programs, apt-get, and synaptic. I'm assuming this game isn't in any of those though.

Are u sure this game is compatible wiht linux? if not r u plannign on using wine?

---

### Post by ReeyferMadness on 2008-07-09
Yeah.  And thanks, you guys always answer questions within like seconds :D  Best.  Community.  Ever :D !

Errr actually you have to have a subscription to d/l.  It's a game called dofus, a mmo.  I can give you the link to the webpage tho.  

[http://www.dofus.com/en/mmorpg/play.html](http://www.dofus.com/en/mmorpg/play.html)

and I don't see anything that'll run.  It basically looks like what a windows game looks like in its folder after you install, minus the .exe

---

### Post by Tatty on 2008-07-09
It might be best if you post a screenshot of all the files in that folder.

Or you could cd to it in a terminal and then list all the files, then copy and paste that output to here:

```
cd *folder*
ls
```

You can download it without a subscription, I started to but then realised it was 159Mb and cancelled ;)

---

### Post by ReeyferMadness on 2008-07-09
yeh, it's a multiplatform mmo, I got the linux version.  

and it was a zip file with what looks like all of the games files already installed in it.

---

### Post by damis648 on 2008-07-09
Can you give us the list of files? (Can you do an ls in terminal?)
```
ls /home/[user]/the/game/directory/
```

---

### Post by ReeyferMadness on 2008-07-09
just a sec, I didn't save file and closed downloads and it disappeared :D  Reloading it now then i'll do that.  btw you can d/l w/o subscribing, thought you couldn't, here's the link, [http://www.dofus.com/en/mmorpg/download/full.html](http://www.dofus.com/en/mmorpg/download/full.html)

---

### Post by ReeyferMadness on 2008-07-09
it just spits the same command back in red.  It's not reading the zip file b/c I did the same thing for the whole desktop and it showed the two files up there.  SO I'm at a loss :D

---

### Post by damis648 on 2008-07-09
Downloading now 1.1Mb/sec wow... I hardly ever have that fast... It will just be a minute. :popcorn:

---

### Post by ReeyferMadness on 2008-07-09
err sorry.  First time i tried to extract the file i got a permission error.  Second time it let me do it (perhaps since i saved rather than just opening?  I really know dip **** about ubu :D) here's the list.  

reeyfermadness@compy-386:~$ ls /home/reeyfermadness/Desktop/Dofus_v1_24_0
audio       data        LICENSE-DE.txt  LICENSE-FR.txt  LICENSE-PT.txt  styles
clips       Dofus.html  LICENSE-EN.txt  LICENSE-IT.txt  loader.swf
config.xml  games.xml   LICENSE-ES.txt  LICENSE-NL.txt  modules

EDIT:  ANd I got the impression linux somehow downloads quicker :D  I've been getting huge download speeds since putting up linux, seen a few 2/3MB (and my connections supposed to be only 8mb) and regularly getting 1MB on a lot of stuff.  Even torrents seem to be going faster :D  Coulda just had my windows install loaded with junk, but I swept it out regularly.

---

### Post by damis648 on 2008-07-09
Ok, after unzipping it, right click "loader.swf" and click "open with other application. In the list that pops up, click firefox. There you go! IF it gives you an error at the bottom, just right click the game and click settings, then allow.:popcorn:

---

### Post by Tatty on 2008-07-09
Lol i think we have all been a bit dopey on this one... yet again google saves the day

[http://www.dofus.com/en/mmorpg-game/guide/1-3-for-a-good-start-how-to-install.html](http://www.dofus.com/en/mmorpg-game/guide/1-3-for-a-good-start-how-to-install.html)

> In order to be compatible with the different operating systems, the DOFUS installation was simplified. Just unzip the archive containing the game and you can play straight away. You can therefore put your DOFUS installation file wherever you wish on your computer.

---

### Post by ReeyferMadness on 2008-07-09
thanks, I got it working.  Much appreciated.

---

