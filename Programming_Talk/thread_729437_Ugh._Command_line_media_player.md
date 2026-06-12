---
title: "Ugh. Command line media player"
date: 2008-03-19
forum: Programming Talk
---

### Post by t3hi3x on 2008-03-19
Ok. This is driving me nuts

In VB there is an ActiveX control from M$ that is essentially an API for windows media player.

Well, I'm trying to make a program that would use the same info provided by the API. You can essentially control any form of the player.

Of course Linux doesn't use OCXs, and I wouldn't half way want it to, but I'm looking for something that I can use to make the program in.

The program is to be completely command line, and I'm programming in C++. I would be perfectly fine with a program that is command line, and just do it that way.

I've tried mplayer, and VLC, but neither seem to support robust command line control.

Any ideas?

---

### Post by sowelie on 2008-03-19
I know you can control Rhythmbox and XMMS via the command line.  Here's an article I ran into today:

[http://http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Rhythmbox]("http://http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Rhythmbox")

---

### Post by t3hi3x on 2008-03-19
There are several good players on there, but will any of them support command line only operation? I'm wanting to run this on a box without an X session.

---

### Post by LaRoza on 2008-03-19
> **t3hi3x said:**
> There are several good players on there, but will any of them support command line only operation? I'm wanting to run this on a box without an X session.

mplayer by default has no GUI.

---

### Post by t3hi3x on 2008-03-19
> mplayer by default has no GUI

I've looked into that, but I can't seem to manage to control it via command line - specifically within a C++ program.

Have you had any luck doing this?

---

### Post by sowelie on 2008-03-19
Ah, I see what you're going for.  You should just use some sort of MP3 library instead of a media player, that way you can have complete control.

---

### Post by LaRoza on 2008-03-19
> **t3hi3x said:**
> I've looked into that, but I can't seem to manage to control it via command line - specifically within a C++ program.

Have you had any luck doing this?

That would not be the way to do it. To use the command line, try shell scripting, Perl, Python, or Ruby.

How about xine-lib? It would be suitable for that.

---

### Post by t3hi3x on 2008-03-19
Thanks for the direction. I'm looking into xine-lib, they don't like c++, but tough patoot :)

lol. I'm going to try to find an example for this, but it looks pretty promising.

---

### Post by t3hi3x on 2008-03-19
> **t3hi3x said:**
> Thanks for the direction. I'm looking into xine-lib, they don't like c++, but tough patoot :)

lol. I'm going to try to find an example for this, but it looks pretty promising.

Well maybe, does xine support streaming audio?

---

### Post by t3hi3x on 2008-03-19
> **t3hi3x said:**
> Well maybe, does xine support streaming audio?

Yup. It does.

---

### Post by stylishpants on 2008-03-20
mpd is nice for this sort of thing, it provides a very scriptable interface and no need for X.

---

