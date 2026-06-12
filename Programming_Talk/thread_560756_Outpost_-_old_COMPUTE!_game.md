---
title: "Outpost - old COMPUTE! game"
date: 2007-09-26
forum: Programming Talk
---

### Post by mutenewt on 2007-09-26
When I was a kid, I used to type in BASIC games from COMPUTE! and other magazines (Atari 800 was my preferred box at the time - ahh the memories).  One of the games was called Outpost.  I would like to update/code Outpost in python.  I'm wondering if anyone else remembers the game and still has access to the code?  I have searched for it but haven't had any luck.

The game was simple - enemy ships approached a space station.  You could only fire your weapons at one target per round.  If you ran out of energy or an enemy reached the station, you died.

I could just write it from scratch but I'd really like to see the old code to make sure I don't forget anything.

Thx for the help

---

### Post by Compyx on 2007-09-27
I found the VIC-20 version here: [ftp://ftp.zimmers.net/pub/cbm/vic20/games.basic/unexpanded/Outpost.prg]("ftp://ftp.zimmers.net/pub/cbm/vic20/games.basic/unexpanded/Outpost.prg")

What you need to run it is the VICE emulator suite. It's in synaptic but that version is missing the ROMs, so you're better off installing from source.

Once you've got VICE installed, you can run the game with:
```

xvic -memory none Outpost.prg

```
You can then press <Esc> which is mapped to Run/Stop and type list to see the code. Although you might consider googling for a program that converts Commodore Basic to text, since reading code in a 22x23 display isn't exactly easy. ;)

---

### Post by mutenewt on 2007-09-27
Thx!  I'll give this a try later today.  Much appreciated.

---

