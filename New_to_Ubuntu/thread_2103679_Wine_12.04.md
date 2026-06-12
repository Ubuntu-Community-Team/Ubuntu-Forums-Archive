---
title: "Wine 12.04"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by misswham on 2013-01-10
HI there.  I just installed WINE.  I was doing this because I assumed that I can put software that was meant for windows on linux thru wine.  Is that the case?  I have a pinnacle video editing software thats in windows but I have to always shut down and bootup in windows 7 to do so.  Can I install it on linux thru wine?

---

### Post by bogustrumper on 2013-01-10
Wine can be a timesaver, but it isn't always a miracle worker, and it doesn't run every piece of Windows software all that well.

If you're curious about whether an application will run, there's a compatibility page over at winehq that you should look at. The page is: [http://appdb.winehq.org](http://appdb.winehq.org)

You can search for any windows program you like, and it will list reports of other users who tried to get it running under wine. There's a rating system, where Platinum is best, Gold is great, Silver is OK, Bronze is buggy but functional, and then Garbage is... well... garbage. :)

According to winehq, unfortunately the only version of Pinnacle that seems usable under wine is version 9. Every later version is rated as "garbage." Seems installation appears to work fine, but nobody can run the software.

If you're interested in Linux, I might encourage you to check out a couple native video editing programs, like Kino, Cinelerra, or PiTiVi. There are probably some great threads on this site about which work best, or you can use Google to find some information on which are most similar to Pinnacle.

Sorry to give you the bad news. Best of luck.

---

### Post by houseworkshy on 2013-01-10
I've found that native linux video editing/rendering software is faster than either windows native software in windows or via wine run in linux.  I don't know why but that was my experiance, when duel booting I'd do identical tasks on both sides of the machine and linux seemed to do it better.  Cinelerra is the best video editor I've ever used.  That said I only used the expensive windows stuff at college and in a windows which I hadn't set up and which had multiple users shareing the resources.
You could test this on your own machine as you duel boot.  One quickie is with the gimp, which exists for both systems;-  make a small fractal, make it tileable, wrap it round a sphere and spin it.  Try a similar gif animation on both sides, on my machine the differance in rendering time is fairly dramatic.
One thing about wine and the way it is set up by default.  I'd recomend removeing the / from the list of what it can access.  Allowing it to access root is intended to make it easy to run programs from anywhere in your system, the danger is that it could run malware too.  I've had problems with it several times, on one occasion it "inherited" root powers because I hadn't waited 15 minets after using sudo to install it and ran something in it too soon.  I've had many other problems with wine, getting out of full screen is a common one especailly when something crashes, now I always remove / from the list of drives it can access immediately.   If you do remove it then you will also need to bung whatever you wish to play with on wines virtual drive which is a hidden file in your home directory; that can be found in ".wine" after you choose "show hidden files".
Wine is a very useful program but it is not the only choise, virtual box with windows in it, for example, can usually run anything that whatever version of windows you bung in it can.
Better to use native linux anyway, whilst windows is king for choice especially with respect to games, IMHO for applications ( with a few exceptions like .swf editing ) linux is the better system though mac's are pretty good at graphics too.

---

### Post by misswham on 2013-01-10
I just typed Cinelerra in synaptic and the ubuntu software center and it doesnt show up.

---

### Post by zombifier25 on 2013-01-10
You need to add the Cinelerra PPA first.
Simply copy and paste these commands into the terminal to install cinelerra:
```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra-cv
```

Or if you want to it graphically, open Update Manager > Software Sources > Other > Add, and copy and paste ppa:cinelerra-ppa/ppa into the box.

---

### Post by Mark Phelps on 2013-01-11
Sorry,but lots of Window SW does not run well in Wine.

The page linked below shows that every version of pinnacle newer than version 9 is rated garbage -- meaning, it's not going to work no matter what you do:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2114]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2114")

---

### Post by houseworkshy on 2013-01-12
As cinelerra is proffesional standard and works slighly differantly from some others, it uses the floating window system,  a brief tutorial may be helpful, this one from youtube is pretty good and done with some humour.
[http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
This looks good too.
[http://www.youtube.com/watch?v=jBs-biS8-y4](http://www.youtube.com/watch?v=jBs-biS8-y4)
Actually searching for "cinelerra tutorial" in youtube or "+cinelerra +tutorial" in a search engine brings up a lot.  I find using it as a basic video editor is just as easy as using a basic video editor so one can just add bits of knowlage about the high end features as you need them.

---

