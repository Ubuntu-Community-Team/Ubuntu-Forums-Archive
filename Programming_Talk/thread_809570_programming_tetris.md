---
title: "programming tetris"
date: 2008-05-27
forum: Programming Talk
---

### Post by JohnnyBoy022 on 2008-05-27
I'm trying to program tetris in c++ / wxWidgets for a challenge. I'm not having any trouble with the graphical stuff, but I just can't seem to figure out how to represent the data of the game. I've been thinking about this and trying different stuff for days. What is the best way to represent a tetris block? From what I've tried I know I want to have a 2-d array of ints to hold the data of the tetris grid (which blocks are filled and which ones are) and I want to have only one active tetris block. Once the block falls down it will become part of the grid. But I just can't figure out how to represent each block and do stuff like rotation, movement, etc... Any ideas?

---

### Post by xlinuks on 2008-05-27
There might be many ways, I would do the following:
I would first create "smart" blocks that are aware of their state and you only tell them "rotate" and they perform a inner rotate and update the info about themselves correspondingly. This is harder at the beginning but is a good start cause later on you won't have to do the math for every update - everything will happen automagically (if coded wisely of course) and your code will look less dirty and will actually deal with the logic of the game rather than repainting/updating every individual block.
Once you get that to work, figure out what should be the next logical step to implement.

---

### Post by leg on 2008-05-27
> **JohnnyBoy022 said:**
> I'm trying to program tetris in c++ / wxWidgets for a challenge. I'm not having any trouble with the graphical stuff, but I just can't seem to figure out how to represent the data of the game. I've been thinking about this and trying different stuff for days. What is the best way to represent a tetris block? From what I've tried I know I want to have a 2-d array of ints to hold the data of the tetris grid (which blocks are filled and which ones are) and I want to have only one active tetris block. Once the block falls down it will become part of the grid. But I just can't figure out how to represent each block and do stuff like rotation, movement, etc... Any ideas?
I wrote this as a J2ME project and took the same idea as you and represented the tetriminoes as a 2d array. I had to get this working fairly quickly as an example to use at work but I later regretted using such a structure. Rotation became a fair PITA as you have to swap your ints to and from the correct locations. If I were to do such a project again I would use a structure that could hold the following information:

1: a starting reference point
2: a colection of four coordinates (each piece only has four blocks)

Each coordinate would describe the position of the top left of each block from the starting position. I.E. 

starting point = 0,0
position one = 0,1
position two = 0,2
position three = 0,3
position four = 0,4

This would represent the I piece in its horizontal position. Then work all your logic for manipulating the pieces based on that structure.

---

### Post by JohnnyBoy022 on 2008-05-27
Leg, that is a really good idea about the structure only holding 4 block coordinates, since each tetroid only has 4 blocks. I think I was making this too complicated by making a 4x4 array of blocks when i really only need 4 coordinates. I will try that out.

---

### Post by leg on 2008-05-27
> **JohnnyBoy022 said:**
> Leg, that is a really good idea about the structure only holding 4 block coordinates, since each tetroid only has 4 blocks. I think I was making this too complicated by making a 4x4 array of blocks when i really only need 4 coordinates. I will try that out.You were over complicating. I know as it is exactly what I did and it really does get cumbersome manipulating that 2d array. Not to mention wasteful.

---

### Post by odyniec on 2008-05-27
Back in the ancient times, I programmed a Tetris-like game in Turbo Pascal (retro, isn't it?), and then wrote a tutorial on bit rotations using the implementation of Tetris pieces in the game as an example. I just dug it up from the depths of my hard drive and put it online, maybe it will be of some help -- [http://odyniec.net/tetris/](http://odyniec.net/tetris/).

---

### Post by skullmunky on 2008-05-29
If you get totally stumped you could sneak a peak at these excellent tutorials, which include a tetris game:

[http://zetcode.com/tutorials/pyqt4/](http://zetcode.com/tutorials/pyqt4/)

---

