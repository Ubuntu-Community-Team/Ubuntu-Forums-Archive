---
title: "C mixes decimals with chars in array"
date: 2012-08-14
forum: Programming Talk
---

### Post by scorpious on 2012-08-14
I'm creating a programme that finds the shortest route between two points H and S in a maze. such as the one shown.
```


#####
#H# . S
# . # . #
# .  .  . #
#####
```

I'm doing it by finding the H, changing it to a zero and systematically changing the dots to decimals that increase further away from the H.

```
#####
#H#6S
#1# 5#
#2 3 4#
#####
```

This works for small mazes but when paths become larger than 35 steps my programme confuses the # with the number 35 and everything becomes a mess. Is there a way to get C to look at a item in an array and tell the difference between the char "#" and the decimal "35"?

---

### Post by Bachstelze on 2012-08-14
No. The character '#' and the integer 35 are the same thing. You need to reconsider your design completely.

---

### Post by scorpious on 2012-08-14
Then are there any chars that do not have a decimal value that I could convert the #'s and S to?

---

### Post by Bachstelze on 2012-08-14
No. ***The [font=monospace]char[/font] type is an integer type.*** Any character is represented internally as an integer,

---

### Post by scorpious on 2012-08-14
ok thanks.

---

### Post by Bachstelze on 2012-08-14
If you want to do this in C you will need to distinguish between the displayed maze and the maze in which you will do your computations. For example you coud make the maze an array of ints, not of chars. Then you would give the "walls" a value of -1, and the problem is solved. And you would have a display function that would display a # for the -1 values. Of course you need to write the display function yourself, you can't use any of the standard functions.

I believe I told you that in your previous thread already...

---

### Post by durdenstationer on 2012-08-14
> **scorpious said:**
> Then are there any chars that do not have a decimal value that I could convert the #'s and S to?

To get what you want you'll have to use C++ where character literals are actually characters.

---

### Post by dwhitney67 on 2012-08-14
> **durdenstationer said:**
> To get what you want you'll have to use C++ where character literals are actually characters.
Huh?  How's it any different from C?

All characters can be interpreted as integers; the converse is not true.

For reference... read the man-page for 'ascii'.

P.S.  Perhaps you meant wide-characters?

---

### Post by durdenstationer on 2012-08-14
> **dwhitney67 said:**
> Huh?  How's it any different from C?

It's different in the way I and the other person above mentioned.  Character literals are treated as the integer value of the literal in C and as the actual character in C++.  This is the reason why sizeof 'A' will give you different results in C and C++.  This is pretty basic knowledge.

> **dwhitney67 said:**
> P.S. Perhaps you meant wide-characters?

No, I didn't mean that at all.  I meant exactly what I said.

---

### Post by dwhitney67 on 2012-08-14
> **durdenstationer said:**
> This is the reason why sizeof 'A' will give you different results in C and C++.  This is pretty basic knowledge.


This is news to me.  It seems that 'A' is interpreted as an int.  I didn't know that.

---

### Post by spjackson on 2012-08-14
> **durdenstationer said:**
> It's different in the way I and the other person above mentioned.  Character literals are treated as the integer value of the literal in C and as the actual character in C++.  This is the reason why sizeof 'A' will give you different results in C and C++.  This is pretty basic knowledge.

While it is true that in C++ (sizeof '#' != sizeof 35), I don't see how that helps at all in this instance. Presumably the maze is a 2 dimensional array of something, perhaps char, perhaps int. Once the value gets into a variable, you can no longer tell what type of literal it started out as.

```

#include <iostream>

int main()
{
    char /* or int - same result */ maze[5][5];

    maze[0][0] = '#';
    maze[1][1] = 35;

    if (maze[0][0] == maze[1][1]) {
        std::cout << "How did doing this in C++ help us?\n";
    }
    else {
        std::cout << "Yippee! C++ has fixed it for me!\n";
    }
}

```It seems to me that the OP wants to store different **types** of thing in the maze, and a sensible way to do that is to store an appropriate user-defined type. In C++, that may perhaps be done polymorphically or not, but in C I suspect that we want something like:
```

typedef enum { empty, wall, point, distance } maze_element_type;

struct maze_element {
  maze_element_type type;
  union {
    int   distance_from_h;
    char  point_label; /* 'H' or 'S' */
  };
};

struct maze_element maze[5][5];

```

---

### Post by Bachstelze on 2012-08-14
> **dwhitney67 said:**
> This is news to me.  It seems that 'A' is interpreted as an int.  I didn't know that.

A character constant like 'A' is not "interpreted as an int". It *is* an int.

---

### Post by lisati on 2012-08-14
After a quick look at this thread, I believe the issues you are experiencing could be related to what you describe in your [other thread]("http://ubuntuforums.org/showthread.php?t=2040060").

A value of "35" as seen on the screen, commonly stored in an array of **char** (or similar) is not stored the same way as what gets stored in a variable of type **int**.

Take a look here:
[http://en.wikipedia.org/wiki/Data_type](http://en.wikipedia.org/wiki/Data_type)
[http://en.wikipedia.org/wiki/ASCII](http://en.wikipedia.org/wiki/ASCII)

---

