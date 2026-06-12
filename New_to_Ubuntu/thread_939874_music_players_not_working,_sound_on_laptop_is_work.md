---
title: "music players not working, sound on laptop is working"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-10-06
for some reason my dell inspiron E1505 laptop is having sound troubles.  Sound works in browsers- i tested it out in youtube, and the hardware testing program.  The problem only happens when i try to play mp3 files on amarok or rhythmbox.  When i try to do that, the songs don't play.  On amarok, it just freezes up and i have to force quit.  On rhythmbox, they just don't play.  If i try to skip to the middle of the song, the progress bar doesn't move.  Any ideas why this is happening?

---

### Post by tjwoosta on 2008-10-06
it sounds like you need to install the right codecs


first do 

```
sudo apt-get install ubuntu-restricted-extras
```

this will install most of the codecs you will need for alot of music and video formats

then if it still doesn't work you might need to install the w32codecs

(im not sure if w32codecs are included in the restricte-extras package or not but it cant hurt to  install them anyway)

so first you would need to add the medibuntu repository

here is a good guide
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after adding the repository you will need to update

```
sudo apt-get update
```

after all of this you can install the w32codecs   (substitute w64codecs if you are using 64bit ubuntu)

```
sudo apt-get install w32codecs
```

---

### Post by shortridge11 on 2008-10-06
hmm that seems to have worked.  I thought i had the medibuntu repo added, but i guess not.  Thanks for your help!

---

