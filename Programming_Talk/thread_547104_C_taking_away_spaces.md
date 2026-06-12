---
title: "C taking away spaces"
date: 2007-09-09
forum: Programming Talk
---

### Post by caoinan on 2007-09-09
Ok this is another one of the exercise from my book that I'm doing but I'm going to try just asking about a specific part. using for loops how do I take away spaces each time the loop ends so when it starts again it will have one less space on the line before the characters being printed

---

### Post by CptPicard on 2007-09-09
By looping over a variable that decreases by one each time you run the loop, until the variable is zero. You initialize it to the number of spaces you want to have on the first line.

Then inside the loop you simply print as many spaces, by using another loop, as you need to be printing for that particular iteration of the outer loop. You get this value from the variable the outer loop is decrementing.

---

### Post by caoinan on 2007-09-09
I'm sorry i dont quite understand how do you take away a letter or space each go around. maybe it would help if you wrote in code what your saying while explaining it.

---

### Post by CptPicard on 2007-09-09
If I understand your excercise correctly, the point is not to "take away" spaces, but to print less spaces each time around, no? :) So you print like... 5 spaces, 4 spaces, 3 spaces... right?

---

### Post by caoinan on 2007-09-09
yes thats right I dont want the answer but I figure I'll just tell you the question and see if you can explain to me how to do it without directly giving me the answer. also note that those letters are supposed to form a pyramid
> 
4.  Have a program request the user to enter an uppercase letter. Use nested loops tto produce a pyramid pattern like this:
          A
        ABA
      ABCBA
    ABCDCDA        
  ABCDEDCBA

The pattern should extend to the character entered. For example, the preceding pattern would result from an input of E. ...

so I am supposed to use 4 loops right? 1 outer and 3 inner loops?

---

### Post by CptPicard on 2007-09-09
Yes... one outer and three loops inside, on the same level with each other, one after the other.

I really would suggest you make this easier for yourself and try to think it through first by making a pyramid of "*"s. The pedagogical content will be pretty much the same, and once you get that, you'll find it easy to extend to the final solution...

---

### Post by caoinan on 2007-09-09
ok I'll do that but will you explain to me in code  how to like 5 spaces then the next go around 4 then 3 and so on. I didnt see it mentioned how to take away characters 1 by 1 in the book and I've reread this chapter. I get how loops work just not how to get that particular spacing

---

### Post by CptPicard on 2007-09-09
By making the variable in the loop smaller each time around. Suppose you need a loop that produces for you the values 5,4,3,2,1,0:

```

for (int i = 5; i >= 0; i--) {
  // i counts downwards each time through here
}

```

---

### Post by caoinan on 2007-09-09
I'm sorry I really hate hate asking for the answer but could you give me the answer so I can see how it works. I know your probably thinking that I'm not trying but (I know I seem n00bish) i've been trying this exercise for hours     EDIT:(you dont have to if you dont want to I think this chapter went way over my head and I like learning programming but I really need a class in it)

---

### Post by CptPicard on 2007-09-09
I really would prefer to hear what exactly the problem is, so I could help you to understand it yourself. I have a fleeting suspicion you don't understand how the loop actually works, so you aren't able to draw the conclusions that you should be having :)

I am going to walk you to a solution here as a teaching exercise ok? I promise you eventually get the answer (but we'll leave the ascii characters out of it, it's a boring extra bit we do not need) :)

Let's say we're making a three-row pyramid just to make graphics smaller so our end result is 

```

  *
 ***
*****

```

So we need to have rows with 2 spaces, 1 space and 0 spaces, followed by 1 star, three stars and 5 stars, respectively.

Now, we have an outer loop just like I gave you, but with 2 instead of 5.

Let's print the spaces we need, first. In order for you to see what you're printing, I suggest you print stars or any other character first, so that you can see your result.

Now... it is obvious that inside your top-level loop, you need another loop to produce the number of spaces on that row. As you know, i contains the number of spaces you need to print. Now... a sub-excercise.. tell me how do you print i spaces?

---

### Post by caoinan on 2007-09-09
you type
```

printf(" ");

```

---

### Post by CptPicard on 2007-09-09
No, that produces exactly 1 space. :)

You want... "i" spaces. :) How would you print, say, 3 spaces? Take your cue from there and substitute i for 3 :)

---

### Post by caoinan on 2007-09-09
> **CptPicard said:**
> No, that produces exactly 1 space. :)

You want... "i" spaces. :) How would you print, say, 3 spaces? Take your cue from there and substitute i for 3 :)

```

printf("i ");

```

---

### Post by CptPicard on 2007-09-09
This prints "i " the string ... use a loop... use a loop.. to go through numbers from 0 until i, and print a " " each time... :)

---

### Post by caoinan on 2007-09-09
do you use an instant messenger so this will be faster and I can ask questions quicker

---

### Post by CptPicard on 2007-09-09
Well, good point... check your private messages for my contact details.

---

