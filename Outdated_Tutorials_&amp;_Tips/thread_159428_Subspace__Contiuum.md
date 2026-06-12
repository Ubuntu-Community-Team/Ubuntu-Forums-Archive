---
title: "Subspace / Contiuum"
date: 2006-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by b3nw on 2006-04-12
This is my first guide so hopefully things work as smoothly for you as they did for me.

What is subspace / contiuum?

Continuum is a two-dimensional space shooter computer game. This freeware game incorporates quasi-realistic zero-gravity into a massively multiplayer online game. The action is viewed from above (aerial view), which presents challenges very different from those of a three-dimensional game. The game has no built-in story or set of goals; players may enter a variety of servers, each of which have differing objectives, levels, sounds, and graphics.
[source]("http://http://www.ssdownloads.com/index.php?act=what_is")

Pic:

[IMG]http://www.ssdownloads.com/images/snapplayc.gif[/IMG]



Looks interesting? Here's how to do it:

1st, you'll need to install wine
```
sudo apt-get install wine
```

2nd, you'll need to have wine generate config files
```
winecfg
```

3rd, get our updated wine for contiuum:
```
 wget [http://www.network3d.net/continuum-wine/Continuum-wine.0.1.a.i686.tar.bz2]("http://www.network3d.net/continuum-wine/Continuum-wine.0.1.a.i686.tar.bz2") 
```

4th, extract:
```
tar -jxvf ~/Continuum-wine.0.1.a.i686.tar.bz2
```

5th, play!
```
~/Continuum-wine/continuum.sh
```

---

### Post by rvergara on 2006-04-14
Hi there.

I have been waiting for Subspace to run under Linux for ages, so this is great news.

I followed your steps and I was able to get the initial screen where I defined the name and password, selected a zone name and hit play. However I only got a blank screen.

I am running 5.10 on a P4 3.0MZ HT PC.

I hope you can help me to debug the problem to get this great game going.

Thanks

Ramiro

---

### Post by b3nw on 2006-04-15
sorry forgot to mention, you can only play in windows mode :(


shameless plug: try redstar! :D

---

### Post by rvergara on 2006-04-15
Yes, In SS I clicked on Resolution-->Windowed, and it works!!

Great. This is the first time ever that this is avaliable for Linux!

Thanks

Ramiro

---

### Post by Kethinov on 2006-04-15
[QUOTE=b3nw]sorry forgot to mention, you can only play in windows mode :(


shameless plug: try redstar! :D[/QUOTE]

Um, not true. Been playing Continuum fullscreen at 1600x1200 for a couple months now. And redstar sucks. Play the 17th Parallel. :p

Also, seriously, give credit where credit is due! [this guy](http://wiki.minegoboom.com/index.php/Running_Continuum_under_Wine) deserves serious kudos and his guide is much simpler anyway. Get WINE's source, apply the patch, compile, done. Easy.

It's also worth noting [WineHQ](http://appdb.winehq.org/appview.php?versionId=3703)'s entry on the topic, which is good to have.

And here's another screenshot I took back in January: 
[[img]http://eric.halo43.com/images/screenshots/2006-01-29-desktop-thumb.png[/img]](http://eric.halo43.com/images/screenshots/2006-01-24-continuum-linux1.png)

---

### Post by seth3d on 2006-05-23
[QUOTE=Kethinov]
Also, seriously, give credit where credit is due! [this guy](http://wiki.minegoboom.com/index.php/Running_Continuum_under_Wine) deserves serious kudos and his guide is much simpler anyway. Get WINE's source, apply the patch, compile, done. Easy.[/QUOTE]

Actually, I put this binary together and I have a [page dedicated to it.]("http://www.network3d.net/portal/content/view/12/1/")  I made it for the people who don't know how, don't want to take the time to compile the wine source, or would rather not have an extra 1.5 GB of wine libraries sitting on their hard drive.

MineGoBoom didn't author this patch, however he has done a good job of distributing it and explaining it.  The original hacker is unknown.  As far as his how-to being easier... I don't think any green Linux user is going to have the slightest idea how to connect to a CVS. ](*,) 

Shameless plug: Chaos Zone Ownz You

--
Seth
[http://www.network3d.net](http://www.network3d.net)

---

### Post by Starlight on 2006-09-17
I have a problem... when I try to run Continuum. it says:

wine: failed to initialize: /usr/local/lib/wine/ntdll.dll.so: cannot open shared object file: No such file or directory

That file is right there in the ~/Continuum-wine/bin directory... why is it trying to look for it in the wrong directory?

---

### Post by stalefries on 2006-09-17
Because it's only looking in your Windows path, which (as far as i know) is only located in your wine "C: drive", located at ~/.wine/drive_c/

---

### Post by Starlight on 2006-09-18
So should I copy the files to the wine C drive directory? It's looking for them in the /usr/local/lib/wine/ directory, which doesn't even exist...

---

### Post by seth3d on 2006-10-07
The development version of Continuum-wine now works with ubuntu :D 
[http://wine.getcontinuum.com/development.php](http://wine.getcontinuum.com/development.php)

---

### Post by seth3d on 2006-10-07
> **Starlight said:**
> So should I copy the files to the wine C drive directory? It's looking for them in the /usr/local/lib/wine/ directory, which doesn't even exist...

This problem should be addressed in the new version.

---

### Post by xphelanx on 2006-10-28
I just installed Ubuntu 6.10 and un-tar'ed Continuum-wine 0.2 and I get nothing, just an error saying: /home/xphelanx/Continuum-wine/wine: could not locate Wine source tree
This sucks :mad: I just ditched windoze and was under the impression that Continuum-wine would work under Ubuntu for me. Can anybody help? :???:

---

### Post by zenrox on 2006-10-29
do a gedit ~/Continuum-wine/wine
find these lines
```

else
  echo "$0: could not locate Wine source tree"
  exit 1

```

and make them look like
```

#else
#  echo "$0: could not locate Wine source tree"
#  exit 1

```
then re run the .2 ver of the game agine
and enjoy

---

### Post by xphelanx on 2006-10-29
You are my god. You may have my first born if you so please!!! :mrgreen:

---

