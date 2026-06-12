---
title: "Java Help"
date: 2008-06-05
forum: Programming Talk
---

### Post by samurailink3 on 2008-06-05
I'm making a "Game of Life" simulation, but I want my 2D array to loop around... I want the "Lifeforms" to reach the end of the game board and then appear on the other side. My problem is I'm having trouble conceptualizing how to put this into action.

Another question! I'm looking for a really good Java book to learn from over the summer. I know a little bit, but I'd like to use something that will hold my interest and teach me core concepts. If there is anything that has a gaming or multimedia approach, that would be great, but not required. What great books would you recommend??

Thanks all!!

---

### Post by KingTermite on 2008-06-05
Don't know any good Java books, but for your array problem, you just need to keep track of the head and tail of your "lifeform". 

Just adjust head to be element 0 in array once he reaches the end. Keep specific pointers to the head and tail will always let you know where the start and where they end, regardless of where in the array they appear.

---

### Post by mike_g on 2008-06-05
> Another question! I'm looking for a really good Java book to learn from over the summer. I know a little bit, but I'd like to use something that will hold my interest and teach me core concepts. If there is anything that has a gaming or multimedia approach, that would be great, but not required. What great books would you recommend??
The only java book I have read was Objects First, which I found quite good. It dosent really cover games tho.

> Don't know any good Java books, but for your array problem, you just need to keep track of the head and tail of your "lifeform".
That would work in C using pointer manipulation, but I'm not sure it would work in a 2d array in java. AFAIK you have to use indexing  to access the content. It would work for sure if you used a 1d array tho. This alternative would be slower, but should work and wont cause a vertical offset when wrapping:
```

if(x == NUM_X_CELLS) 
    x = 0;
else if(x < 0) 
    x = NUM_X_CELLS -1;
if(y == NUM_Y_CELLS)
    y = 0;
else if(y < 0)
    y = NUM_Y_CELLS -1;

```
That would basically require checking every new position, and wrapping if it exceeds a boundary.

---

### Post by samurailink3 on 2008-06-05
Ah! Well, the lifeform isn't like a snake unfortunately.
[http://www.bitstorm.org/gameoflife/](http://www.bitstorm.org/gameoflife/)
This is the code I'm basing it off of, but instead of the "Walls" acting like walls, I want the "lifeforms" to go through one side, and come out the other.

---

### Post by mike_g on 2008-06-05
Yeah, I know what the game of life is. I coded my own version a little while ago ;)

The code I posted should do what you want. Its not the fastest way to go about it, but then its not as if the overhead will be noticeable anyway.

---

### Post by samurailink3 on 2008-06-05
Cool!! I'll see what I can do with this a bit later. Thanks for the help! Anyone else recommending Java books?

---

### Post by CptPicard on 2008-06-05
The easiest way to make your board wrap around is to just use the modulus (%) operator when checking for the state of your neighbours... if you've got an index i along one axis and size of board of n in that direction, then the neighbours are (i - 1) % n and (i + 1) % n. Modulo n arithmetic will cause the wraparound you want, try it out. :)

---

### Post by WW on 2008-06-05
> **CptPicard said:**
> The easiest way to make your board wrap around is to just use the modulus (%) operator ...
The modulus is *almost* exactly what you want.  The problem is when (i-1) is -1 (i.e. when i == 0):

ModulusTest.java
```

class ModulusTest {

  public static void main (String args[]) {

    int j = -1;
    int n = 10;
    System.out.println("j is " + j);
    System.out.println("n is " + n);
  
    int k1 = j % n;
    int k2 = (j+n) % n;

    System.out.println("    j % n is " + k1 + " (Darn it!)");
    System.out.println("(j+n) % n is " + k2 + "  (OK!)");
  }
}

```
```

$ javac ModulusTest.java 
$ java ModulusTest 
j is -1
n is 10
    j % n is -1 (Darn it!)
(j+n) % n is 9  (OK!)
$ 

```
In Java, (-1 % n) is -1.  The code shows that you can get the desired wrap-around by adding n to the value to be "wrapped". That is, if i is your coordinate, the coordinate preceding i is **(i-1+n) % n**.

---

### Post by samurailink3 on 2008-06-13
Ok, cool! Thanks a ton! I'll have to review this and see what happens!

---

### Post by Shin_Gouki2501 on 2008-06-13
this one is in C but i like the overall clar concept:
[http://fog.neopages.org/helloworldgeneticalgorithms.php](http://fog.neopages.org/helloworldgeneticalgorithms.php)
Be sure to check it out its very easy to understand(and to port to java)

---

### Post by jespdj on 2008-06-16
Good Java books:

[Head First Java](http://oreilly.com/catalog/9780596009205/)
[Thinking in Java](http://www.mindview.net/Books/TIJ/) (an older edition is free for download)

[Sun's Java Tutorials](http://java.sun.com/docs/books/tutorial/) are also a good place to go to lean Java.

---

### Post by samurailink3 on 2008-06-19
Cool, I'll check into these. Thanks!! I'm looking to really beef up my coding skills over the summer.

---

### Post by japhyr on 2008-06-23
I really enjoyed the books by Rogers Cadenhead - Sams Programming with Java in 24 Hours, and Java in 21 Days or something like that.

---

### Post by samurailink3 on 2008-06-23
Cool, I'll take a look at those as soon as I can. Thanks for the suggestions!

---

