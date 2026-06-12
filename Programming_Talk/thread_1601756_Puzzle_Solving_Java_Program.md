---
title: "Puzzle Solving Java Program"
date: 2010-10-20
forum: Programming Talk
---

### Post by Hack.The.Pow. on 2010-10-20
Hey all!

I have a question I wanna see if you guys can help out with.  A friend recently gave me a super challenging puzzle.  It has 9 separate squares with different pictures of skiers and snowboarders on it.  There is a skier(or snowboarder) half on each side of every square.  To solve the puzzle you need to arrange the pieces in a 3x3 fashion matching the top halfs of skiers to their respective bottom halfs.  The hard part of the puzzle is that there are no defined borders on the puzzle pieces.  So for instance on the left side edge it could have the top part of a snowboarder but with no bottom half to the left of it.  

After trying out the ridiculous amount of possibilities to solve the puzzle I soon became very frustrated.  So i figured I would try and write a program to solve it and let the computer do the work!  

However I am having trouble trying to figure out how to handle the edges of the puzzle.  I can figure out how to code the panels as objects and the various variables that go along with them.  I'm just having a problem trying to figure out how to deal with the iterative process of the program trying to solve the puzzle.

If anybody can help me with this it would be awesome.  Thanks!

---

### Post by Zymus on 2010-10-20
Can you post the code you're using?

---

### Post by Hack.The.Pow. on 2010-10-20
I haven't actually written anything yet.  Im just looking for some pseudocode ideas on how to handle the problems with the edge pieces

---

### Post by NovaAesa on 2010-10-21
There are 4*9! possible permutations of the puzzle. You can brute force this one if you can't be bothered thinking of a better algorithm :P

---

### Post by Hack.The.Pow. on 2010-10-21
> **NovaAesa said:**
> There are 4*9! possible permutations of the puzzle. You can brute force this one if you can't be bothered thinking of a better algorithm :P

haha i know the puzzle is pretty insane.  I've been trying to figure out an elegant solution to it for a little while now but I've had a tough time.  

I wrote most of the program yet its just the algorithm that I'm hung up on.  I'll try brute forcing it and if it ends up taking way to long I'll try and find something more elegant.

---

