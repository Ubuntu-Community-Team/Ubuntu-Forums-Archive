---
title: "Game implementation question"
date: 2009-12-13
forum: Programming Talk
---

### Post by JDShu on 2009-12-13
Hey everyone!

I have just started writing a game, and I do not know how outside files are usually implemented in games. My problem is that my game will be drawing upon data from some text files, but I do not want players to access the files directly and learn about (or modify) things in the game. What is the usual practice to discourage people from examining files of this type? Thanks in advance!

---

### Post by JDShu on 2009-12-13
I guess its a stupid question? After some pondering, I decided that most people won't be bothered to open up the file anyway so I guess I won't do anything special.

---

### Post by Can+~ on 2009-12-13
If it's a plain text file, someone will modify it. It can break the whole game experience, but if they want to do so, let them, they are the ones who lose. On the other hand, this may lead to people making mods, or other things, it goes both ways.

If someone really wants to edit your files, they will find a way to do so, anything on the client side can and will be hacked one day or another. **Resistance is futile**. The best you can do, is discourage them or have server validation (only works with online games that require to go online, doing server validation on a game that will be played locally, will lead the hacker team to just disable the online check).

Now, if you really want to keep them off your config file, an easy way to discourage most people is using a binary format. Binary format would require a hex editor (ghex for ubuntu), and patience, so it can be discouraging for a non tech-savvy, until someone comes up with a script that does the modification.

Other things involve hashing the file.

---

### Post by JDShu on 2009-12-14
Hey! thanks for the reply. I knew that people who wanted to modify the file would be able to if they wanted badly enough, but I was just wondering if I should make some minor discouragement. I decided that its too annoying though, and its not an important enough issue to bother with.

---

### Post by Logan513 on 2009-12-14
> **JDShu said:**
> Hey everyone!

I have just started writing a game, and I do not know how outside files are usually implemented in games. My problem is that my game will be drawing upon data from some text files, but I do not want players to access the files directly and learn about (or modify) things in the game. What is the usual practice to discourage people from examining files of this type? Thanks in advance!

I would write a whole bunch of worthless code that looks really complicated and important, and if your lucky the user would figure it's not worth it and give up.

But that's just me! :lolflag:

---

### Post by era86 on 2009-12-14
> **Can+~ said:**
> 
Now, if you really want to keep them off your config file, an easy way to discourage most people is using a binary format. Binary format would require a hex editor (ghex for ubuntu), and patience, so it can be discouraging for a non tech-savvy, until someone comes up with a script that does the modification.

Other things involve hashing the file.

Simply writing game data to a binary file is the best way to do this.  Give the file some intimidating extension like *.kill or something :D

---

