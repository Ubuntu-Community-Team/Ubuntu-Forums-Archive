---
title: "I Need Help Installing Something..."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Swenghk on 2008-10-05
I've tried to install this game [http://www.asciisector.net/download.html]("http://www.asciisector.net/download.html"). But I don't know how...

I though I would un-tar it, then use "make", but it said no make-file was found?

```
seth@SETH-LAPTOP:~$ cd ~/Desktop
seth@SETH-LAPTOP:~/Desktop$ tar xvf asciisec0.4.4-linux.tar.gz
asciisec/asciisec
asciisec/history.txt
asciisec/readme.txt
asciisec/icon.bmp
asciisec/manual.pdf
asciisec/sounds/throw.wav
asciisec/sounds/handgun.wav
asciisec/sounds/gun1.wav
asciisec/sounds/gun3.wav
asciisec/sounds/missile.wav
asciisec/sounds/gun7.wav
asciisec/sounds/kick.wav
asciisec/sounds/dscream.wav
asciisec/sounds/fexplode.wav
asciisec/sounds/mexplode.wav
asciisec/sounds/gun8.wav
asciisec/sounds/laser.wav
asciisec/sounds/punch.wav
asciisec/sounds/jumpexp.wav
asciisec/sounds/gun4.wav
asciisec/sounds/armor.wav
asciisec/sounds/rifle.wav
asciisec/sounds/pulse.wav
asciisec/sounds/scooped.wav
asciisec/sounds/gun2.wav
asciisec/sounds/gun9.wav
asciisec/sounds/spray.wav
asciisec/sounds/clip.wav
asciisec/sounds/gun6.wav
asciisec/sounds/gun5.wav
asciisec/sounds/aburn.wav
asciisec/sounds/zap.wav
asciisec/sounds/cexplode.wav
asciisec/sounds/static.wav
asciisec/sounds/gexplode.wav
asciisec/sounds/asthit.wav
asciisec/sounds/shield.wav
asciisec/sounds/stab.wav
asciisec/data/nouns.txt
asciisec/data/rus1.txt
asciisec/data/11.bas
asciisec/data/ame3.txt
asciisec/data/12.bas
asciisec/data/16.bas
asciisec/data/chi1.txt
asciisec/data/10.bas
asciisec/data/bases.txt
asciisec/data/fre3.txt
asciisec/data/chi3.txt
asciisec/data/ame1.txt
asciisec/data/fre2.txt
asciisec/data/ger2.txt
asciisec/data/14.bas
asciisec/data/ita1.txt
asciisec/data/ger1.txt
asciisec/data/17.bas
asciisec/data/8.bas
asciisec/data/23.bas
asciisec/data/18.bas
asciisec/data/21.bas
asciisec/data/5.bas
asciisec/data/fre1.txt
asciisec/data/3.bas
asciisec/data/adjects.txt
asciisec/data/ame2.txt
asciisec/data/9.bas
asciisec/data/25.bas
asciisec/data/6.bas
asciisec/data/15.bas
asciisec/data/rus2.txt
asciisec/data/24.bas
asciisec/data/7.bas
asciisec/data/ita3.txt
asciisec/data/comps.txt
asciisec/data/2.bas
asciisec/data/26.bas
asciisec/data/13.bas
asciisec/data/ita2.txt
asciisec/data/animals.txt
asciisec/data/suffix.txt
asciisec/data/ger3.txt
asciisec/data/19.bas
asciisec/data/chi2.txt
asciisec/data/4.bas
asciisec/data/22.bas
asciisec/data/rus3.txt
asciisec/data/1.bas
asciisec/data/colors.txt
asciisec/data/20.bas
asciisec/graphics/ascmap3.bmp
asciisec/graphics/ascmap5.bmp
asciisec/graphics/ascmap14.bmp
asciisec/graphics/ascmap6.bmp
asciisec/graphics/ascmap2.bmp
asciisec/graphics/ascmap9.bmp
asciisec/graphics/ascmap0.bmp
asciisec/graphics/ascmap15.bmp
asciisec/graphics/ascmap12.bmp
asciisec/graphics/ascmap1.bmp
asciisec/graphics/ascmap13.bmp
asciisec/graphics/ascmap11.bmp
asciisec/graphics/ascmap10.bmp
asciisec/graphics/ascmap7.bmp
asciisec/graphics/ascmap4.bmp
asciisec/graphics/ascmap8.bmp
asciisec/graphics/large/ascmap3.bmp
asciisec/graphics/large/ascmap5.bmp
asciisec/graphics/large/ascmap14.bmp
asciisec/graphics/large/ascmap6.bmp
asciisec/graphics/large/ascmap2.bmp
asciisec/graphics/large/ascmap9.bmp
asciisec/graphics/large/ascmap0.bmp
asciisec/graphics/large/ascmap15.bmp
asciisec/graphics/large/ascmap12.bmp
asciisec/graphics/large/ascmap1.bmp
asciisec/graphics/large/ascmap13.bmp
asciisec/graphics/large/ascmap11.bmp
asciisec/graphics/large/ascmap10.bmp
asciisec/graphics/large/ascmap7.bmp
asciisec/graphics/large/ascmap4.bmp
asciisec/graphics/large/ascmap8.bmp
seth@SETH-LAPTOP:~/Desktop$ cd asciisec
seth@SETH-LAPTOP:~/Desktop/asciisec$ make
make: *** No targets specified and no makefile found.  Stop.
seth@SETH-LAPTOP:~/Desktop/asciisec$ 

```

And I do have build-essential installed...

---

### Post by Swenghk on 2008-10-05
bump...

---

### Post by shifty_powers on 2008-10-05
can you do

```
ls
```

and post the output?

---

### Post by Sef on 2008-10-05
Do not bump unless 24 hours have gone by.  Thank you.

---

### Post by Swenghk on 2008-10-05
Results of "ls"...


```
seth@SETH-LAPTOP:~$ ls
Desktop    Firefox_wallpaper.png  Music     Public  Templates
Documents  FrostWire              Photos    Saves   Videos
Examples   GNUstep                Pictures  School
seth@SETH-LAPTOP:~$ 

```

---

### Post by shifty_powers on 2008-10-05
heh ok

```
cd Desktop/asciisec && ls
```

please ;)

---

### Post by taladan on 2008-10-05
after dl'ing and looking at this, this is a pre-compiled binary.

You need to type the following:

```
sudo apt-get install libsmpeg0
```

Then run ./asciisec

Enjoy.

Tal

---

### Post by Swenghk on 2008-10-05
```
seth@SETH-LAPTOP:~$ cd ~/Desktop/asciisec && ls
asciisec  data  graphics  history.txt  icon.bmp  manual.pdf  readme.txt  sounds
seth@SETH-LAPTOP:~/Desktop/asciisec$ 

```

---

### Post by Swenghk on 2008-10-05
> **taladan said:**
> after dl'ing and looking at this, this is a pre-compiled binary.

You need to type the following:

```
sudo apt-get install libsmpeg0
```

Then run ./asciisec

Enjoy.

Tal


It says I already have the latest version installed...

---

### Post by Swenghk on 2008-10-05
How do I make a shortcut of this in my Game folder, under Applications?

---

### Post by shifty_powers on 2008-10-05
right click on applications menu and go to edit menu's iirc

---

