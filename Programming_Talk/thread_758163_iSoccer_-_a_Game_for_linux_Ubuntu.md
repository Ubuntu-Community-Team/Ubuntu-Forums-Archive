---
title: "iSoccer - a Game for linux/ Ubuntu"
date: 2008-04-17
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-04-17
Hey Guys

Myself and Jorge Rosa are proud to announce a new open source game project provisionally called 'iSoccer'.

its a clone of the world renowned 'Sensible Soccer' and the source is available from source forge at:

  [https://isoccer.svn.sourceforge.net/svnroot/isoccer](https://isoccer.svn.sourceforge.net/svnroot/isoccer)

Welcome the communities input/suggestions & help, so if you want to get involved you will be most welcome!

Thanks to slavik for his instructions and also wybiral for reminding me to tell how to compile it.

There is also a code::blocks project ile in there so i you have the libraries included you could just compile using that.

EDIT: you need sdl, mesagl and glut dev libraries installed (if you have troubles, post or pm me if the errors) for the compile to succeed.

Build instructions:
```

svn co 'https://isoccer.svn.sourceforge.net/svnroot/isoccer/' iSoccer
make linux64 #if you have 32bit linux then use linux32
./iSoccer 

```Mike

---

### Post by Glaxed on 2008-04-17
what are the files you need to download to get up and running?
I din't see an install instructions file, sorry, bit newbie.

---

### Post by Wybiral on 2008-04-17
Mickey, you should put up some screenshots and instructions to help draw some attention.

---

### Post by slavik on 2008-04-18
how to get the code, compile and run it

EDIT: you need sdl, mesagl and glut dev libraries installed (if you have troubles, post or pm me if the errors) for the compile to succeed.

```

svn co 'https://isoccer.svn.sourceforge.net/svnroot/isoccer/' iSoccer
make linux64 #if you have 32bit linux then use linux32
./iSoccer

```

played around in it, looks nice :)
the only thing is that the number on the shirt is reversed, I have attached the modified PNG :)
I have also noticed some graphical corruption as I moved around the field, as if there was space between 2 quads. image also attached.

---

### Post by Mickeysofine1972 on 2008-04-18
> **slavik said:**
> how to get the code, compile and run it

EDIT: you need sdl, mesagl and glut dev libraries installed (if you have troubles, post or pm me if the errors) for the compile to succeed.

```

svn co 'https://isoccer.svn.sourceforge.net/svnroot/isoccer/' iSoccer
make linux64 #if you have 32bit linux then use linux32
./iSoccer

```played around in it, looks nice :)
the only thing is that the number on the shirt is reversed, I have attached the modified PNG :)
I have also noticed some graphical corruption as I moved around the field, as if there was space between 2 quads. image also attached.

Yeah i did the shirt reverse as I was playing around, but the tearing in the pitch is probably gonna go away once we have a better model.

Although if anyone has a suggestion about how to handle this kind of artifact i would love to hear from them.

Mike

---

### Post by jorgerosa on 2008-04-18
[URL="http://isoccer.googlecode.com/files/PITCH_Preview_02.jpg"]> **Wybiral said:**
> Mickey, you should put up some screenshots and instructions to help draw some attention.[/URL]
[IMG]http://isoccer.googlecode.com/files/PITCH_Preview_02.jpg[/IMG]
He did... ;)

---

### Post by Mickeysofine1972 on 2008-04-20
Ok so heres an update

iSoccer now features md2 support including GL command list rendering, which has given a much needed boost to the gfx

The ball and goals are now models instead of glu primitives.

I have attached a screen shot fo you to have a look and updated the SVN

Mike

---

### Post by Tomosaur on 2008-04-20
This looks pretty cool, I'll give it a go when I've got some time :) Nice work!

---

### Post by ZylGadis on 2008-04-20
Do you have an IRC channel, folks? I went to #iteam on freenode, but it does not seem it has anything to do with isoccer, and I don't see either of you (jorgerosa and Mickey) there.

---

### Post by Mickeysofine1972 on 2008-04-20
> **ZylGadis said:**
> Do you have an IRC channel, folks? I went to #iteam on freenode, but it does not seem it has anything to do with isoccer, and I don't see either of you (jorgerosa and Mickey) there.

Well although jorge and I are involved with iteam we haven yet planned for a IRC channel for isoccer as its just two atm, but if we get any other developers later its a possibility

Mike

---

