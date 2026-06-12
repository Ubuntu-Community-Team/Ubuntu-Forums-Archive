---
title: "Using DosBox and Dune2"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2012-12-09
Can any one tell me how to get the screen format correct after exiting Dune2?

At the moment when I shut down Dune2 the decktop page is in the wrong screen format and unsuable.

Regards Doug.

---

### Post by kostkon on 2012-12-09
The best thing you could do is instead of having dune2 starting full screen in its native resolution (and thus forcing your monitor to change to a very low resolution, and if it is a TFT monitor, apply some kind of scaling of its own, that for one reason or another stays after you leave the game) you could set the resolution of the game to match your screen resolution and then apply scaling to it, i.e. make a custom dosbox.conf file especially for the game, and set
```
fullscreen=true
fullresolution=<width>x<height>
```
where width and height are the dimensions of your monitor's resolution
and the scaler
```
scaler=normal2x
```
to one of these
```
normal2x, normal3x, advmame2x, advmame3x, advinterp2x, advinterp3x, hq2x, hq3x, 2xsai, super2xsai, supereagle, tv2x, tv3x, rgb2x, rgb3x, scan2x, scan3x
```
Check [the wiki page]("http://www.dosbox.com/wiki/Scaler") and decide for youself which filter suits you (or the game) best.
and then in the autoexec section of the file
```
[autoexec]
```
you mount the game's folder and start the game.

Then you can make a custom desktop file that calls the game like this for example
```
dosbox -conf ~/Games/Dune2/dosbox_dune2.conf
```

You can find the conf file that dosbox uses by default in the ~/.dosbox folder and use it as the template for you own custom conf file.

If the above seem a little complicated to you, then you could use a graphical dosbox frontend like [dbgl]("http://members.quicknet.nl/blankendaalr/dbgl/") to setup the game.

Hope that helps.

---

### Post by mastablasta on 2012-12-09
there is also a web broswer version of Dune 2 :-) yeah someone made it multiplayer even...

---

