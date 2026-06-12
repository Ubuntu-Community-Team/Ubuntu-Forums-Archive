---
title: "Newbie game programer"
date: 2008-09-16
forum: Programming Talk
---

### Post by null-cipher on 2008-09-16
Hi there Ubuntu community!

I'm a bit of a wannabe developer, and as a project, I'm looking to create a text-based RPG.
Sort of in the spirit of "Castle of the Winds". [http://en.wikipedia.org/wiki/Castle_of_the_Winds](http://en.wikipedia.org/wiki/Castle_of_the_Winds)
and other rouge-like sorts of games. Perhaps minus the graphical elements, depending on how hard it'll be! :)

I'm a little bit familiar with C++ (firm with the basics, still learning things such as the STL), and I was just wondering if anybody out there might have any advice, or reference material that could help me.

Any libraries/APIs that you could reccomend for something like this would be great!

I can't give you much of a detailed over-view of what I hope to accomplish, as I'm not too sure myself.
And I'm sure you're thinking that this is a bit silly asking about libraries and such when you don't know exactly what your game is going to do...
But I'm just attempting this so I can learn more about programming and development.

Also, I would like to be able to make my little game cross platform so that my friends can test it for me in the future, but it's not a huge priority. I'd rather getting it working on my Ubuntu computer before having it cross-platform.

As always, any help is appreciated.

---

### Post by LaRoza on 2008-09-16
[http://ubuntuforums.org/showthread.php?t=667422](http://ubuntuforums.org/showthread.php?t=667422)

As for the game like the one you linked to, it would be easiest to do in a language that doesn't get in the way. It looks like it would be suitable for PyGame and Python (PyGame is the module, and Python is the language).

My wiki has references for both.

C++ would be...painful (to use for this type of goal)

---

### Post by null-cipher on 2008-09-16
I had considered something like that...

However, I'm only looking to have the more classical text interface for the game.
I would give an example... but as I'm only 16 the text-only games are a bit before my time.

I have however been looking for a good excuse to learn Python, so I shall consider your suggestion.
Thanks!

---

### Post by leg on 2008-09-16
Take a look at the [Ogre]("http://www.ogre3d.org/") site there is a lot of good material there even if you don't want to use Ogre.

---

### Post by pmasiar on 2008-09-16
If you are reasonably competent C(++) programmer, you will earn Python over a weekend. Train your hand on some simpler training tasks (see wiki in my sig), you will be surprised how much more flexible Python data structures (and literals) are - you will be able to cut 75% of code lines, compared with C++.

If you want to go into graphic games, pygames is your best bet, or we will be glad to have you at GameBaker (see my sig again).

---

### Post by Sockerdrickan on 2008-09-16
If you consider using C++ then learn SDL and it's render functions!

---

### Post by null-cipher on 2008-09-17
I'm not *terribly* competent at programming as a whole yet.

Most of my experience has been in PHP code I used for my website. However I think learning Python would be mostly a syntactical exercise.

I have settled on learning Python for this little project, so that if I wish to extend it to a graphical/semi-graphical interface that it wouldn't be a huge thing to do.

I've grabbed eric4 and pygame and a WHOLE lot of relevant documentation! :D

---

### Post by null-cipher on 2008-09-18
Also, for anybody not familiar with Castle of the Winds...
It is available under a freeware (shareware?) license from this link [http://www.exmsft.com/~ricks/castl11a.zip](http://www.exmsft.com/~ricks/castl11a.zip)

I spent a good portion of my childhood playing this game, and I think making my own rendition would not only be great fun, but an interesting challenge for programming.

It's an old Windows 3.x game, but I know it runs fine under Wine.

Naturally, I don't have delusions of grandeur, I know that a newbie programmer can't pull off something as complex as that straight away, but I think I can at least get the text-based side working after awhile.
I just want the option of being able to work it up to that tile based, rogue-like game that CotW was.

I'm currently perusing some of the PyGame documentation at the moment, along with a great deal of Python tutorials and the like.

I must say, I do like the look of Python. I think the higher-level of the language is more suited to my skills (and understanding) than the low-level features I've used in C++.

---

### Post by namegame on 2008-09-18
> **null-cipher said:**
> 
It is available under a freeware (shareware?) license from this link [http://www.exmsft.com/~ricks/castl11a.zip](http://www.exmsft.com/~ricks/castl11a.zip)


A bit off-topic...

I have been searching for this game for the past few months/years. I had it on a CD and the CD broke in half...

I could probably blame Castle of The Winds for my current RPG addiction...

---

### Post by null-cipher on 2008-09-18
Haha! I would have to agree fully there. I used to have the first half on a floppy disk that got damaged many years ago.

A real classic.

Glad I could be of help.

The reason I picked that as an example was partly because it was developed by one man (an ex microsoft employee, back when they were a struggling little company), as a project to learn widgets for windows.
Can't really site any solid references there, but I think I read that off of his personal page there.

---

