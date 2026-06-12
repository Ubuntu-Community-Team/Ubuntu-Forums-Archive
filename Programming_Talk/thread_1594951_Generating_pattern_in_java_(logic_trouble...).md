---
title: "Generating pattern in java (logic trouble...)"
date: 2010-10-12
forum: Programming Talk
---

### Post by Eremis on 2010-10-12
Hi guys,

I was wondering, how would I generate the above pattern in java, so the method nextNum() returns the next number... :confused:


123456
234561
345612
456123
561234
612345
123456
...
...

-- or --

123456234561345612456123561234612345123456...

-------------------------------------------------------------
ex.
System.out.print(nextNum()); --> 1
System.out.print(nextNum()); --> 2
System.out.print(nextNum()); --> 3
System.out.print(nextNum()); --> 4
System.out.print(nextNum()); --> 5
System.out.print(nextNum()); --> 6
System.out.print(nextNum()); --> 2
...
...

-------------------------------------------------------------

Any help would be appreciated... 
Thanks

---

### Post by Some Penguin on 2010-10-12
What have you tried so far?

---

### Post by Eremis on 2010-10-12
first i tried using counters,

now i am trying ArrayList

---

### Post by Eremis on 2010-10-12
is there some kind of a simple algorithm that i am missing here?

---

### Post by Some Penguin on 2010-10-12
You misunderstand the question.

What *reasoning* have you tried so far?

And yes, there is a simple answer.   Ask yourself 
(1) how do you know which row you're on, and
(2) what does each row look like, if you know which row it is.

---

### Post by Eremis on 2010-10-12
i tried something like this:

private int start = 0;
private int count = 0;
private int max = 6;
public int getNextInt() {
    if (count != max) {
        count++;  
        return (count -1)
    }
    else {
        count = start + 1;
        start ++;
        return count;
    }
}

---

### Post by Eremis on 2010-10-12
but the problem is this is what i get:

23456
3456
456
56
6

---

### Post by Eremis on 2010-10-12
how would i add the left over numbers after the 6?

---

### Post by Some Penguin on 2010-10-12
"Stopping at the maximum" is obviously not going to work.   Consider that each row has an equal number of numbers in it.

---

### Post by Eremis on 2010-10-12
I am srry, my brain is just not working, can i get another clue or something? 
I remember doing this a while ago, i dont really know why i am stuck on this because it does seem very easy.

---

### Post by Eremis on 2010-10-12
Can anybody help me?
plz!!!

---

### Post by dwhitney67 on 2010-10-12
Obviously you are not working on a nifty program to deduce the nuclear weapon's launch codes used by the North Koreans.

Is this homework?  Remember, per the forum rules, you are not allowed to post homework questions, and believe me, yours shows a damn close resemblance to one.

---

### Post by schauerlich on 2010-10-13
Observe:

```
4 % 6 == 4
5 % 6 == 5
6 % 6 == 0
7 % 6 == 1
8 % 6 == 2
```

What do you think 9 % 6 is?

---

### Post by Eremis on 2010-10-13
No, its not homework, its chargen server project... The default output should be similar but with characters... I just wanted to see the example done with numbers... So it will be easier to do this with ascii characters... 

The assignment is to create a chargen server, I can use random numbers if i wanted to (the RFC says that the order or what you sent does not matter...)

I was just trying to see if someone can help me do it the way I wanted it to work...

---

### Post by Eremis on 2010-10-13
Can you guys just show me the algorithm, it really isnt a part of the assignment... I can post the assignment if you dont belive me... 

I just want it to look like it does in the RFC (even thow its not required...)

---

### Post by Eremis on 2010-10-13
@schauerlich
"What do you think 9 % 6 is?"
well its 3, because %(mod) does remainders...

Where are you going with this?

---

### Post by dwhitney67 on 2010-10-13
> **Eremis said:**
> i tried something like this:

private int start = 0;
private int count = 0;
private int max = 6;
public int getNextInt() {
    if (count != max) {
        count++;  
        return (count -1)
    }
    else {
        count = start + 1;
        start ++;
        return count;
    }
}

Try again... prove to us that you are actually putting forth some effort here.

Otherwise, if all you want is a CharGen algorithm, here's a basic one:
```

...

private static int MAX_NUM = 6;
private static int num = 0;

public int nextNum()
{
   return ++num % MAX_NUM;   // this returns a value from 0 to (MAX_NUM-1); is this desirable?
}

public static void main(String[] args)
{
   while (true)
   {
      for (int i = 0; i < MAX_NUM; ++i)
      {
         System.out.print(nextNum());
      }
      System.out.println();
   }
}
...

```
Now, if you want something more elaborate such as you have described in your OP, then get back to the "drawing" board.  I can tell you now that the code above is a good clue, and hopefully it will put you in the right direction.

---

### Post by schauerlich on 2010-10-13
> **Eremis said:**
> @schauerlich
"What do you think 9 % 6 is?"
well its 3, because %(mod) does remainders...

Where are you going with this?

```
>>> for x in range(0,25):
...     print (x % 6) + 1
... 
1
2
3
4
5
6
1
2
3
4
5
6
1
2
3
4
5
6
1
2
3
4
5
6
1
```

Notice any patterns you could exploit?

---

### Post by Eremis on 2010-10-13
Yeah, I am working on it...
will get back with the answer (hopefully...)

BTW 
@schauerlich
each number on the line says how many chars or nums print from biginning?

1 23456 1 --> 1
2 3456 12 --> 2
3 456 123 --> 3
...

???

---

### Post by dwhitney67 on 2010-10-13
> **Eremis said:**
> Yeah, I am working on it...
will get back with the answer (hopefully...)

BTW 
@schauerlich
each number on the line says how many chars or nums print from biginning?

1 23456 1 --> 1
2 3456 12 --> 2
3 456 123 --> 3
...

???

You'll make a great news reporter someday.  Not independent thought runs through your head; but you are damn good at repeating what others have presented.  Kudos.

I cannot believe you have not posted a complete project by now, that at least mimics what you require.  At a minimum, you should have something that prints this pattern:
```

123456
234567
345678
....

```
Yes, the 7 and 8 are incorrect... but jeez louise, this would be more than what you have presented thus far.


P.S.  Think!!!
```

1 23456
2 34567
3 45678
....

```
1 + (num % 6)...
2 + (num % 6)...
3 + (num % 6)...

Get this far, then afterwards worry about the trailing number(s) that are out of range.

---

### Post by Eremis on 2010-10-13
I have not posted the answer yet, because I had to go to work...
Just got back to the problem...
I dont have hours and hours to think about this sort of stuff, thats why I posted the question here in the first place...

---

### Post by Eremis on 2010-10-13
@dwhitney67

No, I have a lot of independent thoughts...

Ive spent about 2 hours thinking about this problem, and no luck, thats why I asked the forum... 

> 
I cannot believe you have not posted a complete project by now, that at least mimics what you require. At a minimum, you should have something that prints this pattern:

123456
234567
345678


I can print that with no problem... Just use one counter and start printing from that number 6 nums at a time, every time the line prints add 1 to the counter and re-print... I did not even bother posting that, its the extra characters at the end that bother me...

Anyways, I need to finish this today, so I guess I will use the random to generate characters..

I would still appriciate it if someone posted how to do it... 
Thanks for the help so far thow

---

### Post by GenBattle on 2010-10-13
You seem to be focused too much on trying to get your method for generating this output working. Multiple people have posted multiple algorithms which will do exactly what you want, but you seem to have ignored them or are too ignorant to understand them.

If you cannot understand the help people are giving you in no uncertain terms, you need to seriously consider whether programming is for you.

People are not being mean; they simply expect you to show a certain minimum level of programming ability, or at least some enthusiasm and initiative.

---

### Post by Eremis on 2010-10-13
@GenBattle

Way to discurage a college freshman from programming, most of my peers (all of them) are in java 150, I tested out of it, so I am in 400 level class, and stugling on a small portion of this programm (simply because I dont have enough expirience with programming...)

I choose to take the harder class because I wanted to learn something new...

And your calling me ignorant?

---

### Post by schauerlich on 2010-10-13
If you're taking the harder class, you should expect to put in more effort. You should at least *look* and what dwhitney and I have posted, compare it to your own method, and see how it works.

Programming is about problem solving. It's okay to ask for help solving problems, but don't ask for someone to solve it for you. And when people show you how to solve it yourself, don't whine when they don't give you "teh codez".

---

### Post by lisati on 2010-10-13
Having had a quick look at the thread, I'd suggest that something similar to post 6 could be part of *one* possible solution.

---

### Post by Eremis on 2010-10-14
OMG I GOT IT!!!!!!

```

public class Chargen {
    
    private int start;
    private int count;
    private int length;

    public Chargen() {
        count = 0;
        length = 0;
    }

    public int getNextInt() {
        if (length != 6) {
            count ++;
            length ++;
            return (count - 1);
        }   
        else {
            count = (count - 4);
            length = 1;
            return (count - 1);
        }   
    }

    public static void main(String[]args) {
        Chargen c = new Chargen();
        for (int i = 0; i < 70; i++) {
            for (int j = 0; j < 6; j++) {
                System.out.print(c.getNextInt() + " ");
            }
            System.out.println();
        }
    }
}


```

Thx for not giving away the ans!!!

---

### Post by Eremis on 2010-10-14
k actualy i noticed one problem,

after it gets to the end (char)126 there are problems...

how would i get it to keep going?

---

### Post by Eremis on 2010-10-14
k so here is my chargen generator.
it has the problem when it gets to the end char 126...

```

/**
 * The class that produces the defacto standard charecter sequence produced by 
 * chargen servers.
 *
 * @author $%$%$%$%
 *
 * @version 11 October, 2010
 */

public class DefactoChargenCharacterSource implements ChargenCharacterSource { 

    /** The counter for the generator. */
    private int count;

    /** The other counter for the genereator. */
    private int length;

    /** The begining of ascii code. */
    protected final int BEGIN = 33;
    
    public DefactoChargenCharacterSource() {
        this.count = this.BEGIN;
        this.length = 0;
    }
    
    public char getNextChar() {
        if (count == 126) {
            this.count = 33;
            this.length = 0;
            return (char)(count - 1);
        } 
        else {
            if (length != 70) {
                this.count ++;
                this.length ++;
                return (char)(count - 1);
            }
            else {
                this.count = (count - 68);
                this.length = 1;
                return (char)(count - 1);
            }
        }
    }

    public static void main(String[]args) {
        DefactoChargenCharacterSource source = new DefactoChargenCharacterSource();
        for (int i = 0; i < 100; i++) {
            for (int j = 0; j < 70; j++) {
                System.out.print(source.getNextChar() + " ");
            }
            System.out.println();
        }
    }
}



```

---

### Post by GenBattle on 2010-10-14
> **Eremis said:**
> @GenBattle

Way to discurage a college freshman from programming, most of my peers (all of them) are in java 150, I tested out of it, so I am in 400 level class, and stugling on a small portion of this programm (simply because I dont have enough expirience with programming...)

I choose to take the harder class because I wanted to learn something new...

And your calling me ignorant?

If you gave up after a forum post from someone like me, then you would only be proving me right :P

I have seen far too many people go to university and try to take up programming because of a promise of higher salaries or perfect working conditions, when they in fact have no passion or natural skill for the subject matter, so you can understand my frustration. :mad:

Maybe you should take up the 150 class. Talk to one of your lecturers/Professors. They're usually reasonably knowledgeable, and most of them are more than happy to help a student interested in their subject who has a problem such as yours.

You might think me ignorant if you want, but i am just offering you advice, as is everyone else in this thread (such as lisati). 

I'm starting to think you're ignoring them on purpose just to troll the forum, or to frustrate someone to the point where they give you the full program which you just have to compile and hand in.

---

### Post by dwhitney67 on 2010-10-14
The code won't cut it:
```

    public int getNextInt() {
        if (length != 6) {
            count ++;
            length ++;
            return (count - 1);
        }   
        else {
            count = (count - 4);
            length = 1;
            return (count - 1);
        }   
    }

```
In the code above, you are too focused on the number of columns (ie length) for each line; you need to focus on the row number, for this is a factor in determining the number that is returned.

You may also need to consider using the pre-increment operator, not just the post-increment.

To recap:
```

+---------- row number
|
|
v
123456
234561
345612
456123
561234
612345
123456
......

```

If you take a careful look at the first row, the numbers are merely generated using the following:
```

num = row + (counter++ % 6)

```
When you iterate to start with the second row (TODO: determine when you are at the next row), you will note that the formula above will start yielding nums ranging from 2 through 7.  But alas, the 7 is out of range!  We want numbers ranging from 1 through 6.  How can we possibly convert that awful 7 to something in our desired range??????

---

### Post by GenBattle on 2010-10-14
Another algorithm to try would be [Circular Shift]("http://en.wikipedia.org/wiki/Circular_shift"). This usually applies to a binary buffer, but if you use an int array you should be able to rotate ints through the array. 

Sure it may be more memory intensive and involve minimal arithmetic, but it's as valid as any other algorithm to get the job done.

---

### Post by spjackson on 2010-10-14
> **GenBattle said:**
> Another algorithm to try would be [Circular Shift]("http://en.wikipedia.org/wiki/Circular_shift"). This usually applies to a binary buffer, but if you use an int array you should be able to rotate ints through the array. 

Sure it may be more memory intensive and involve minimal arithmetic, but it's as valid as any other algorithm to get the job done.
I had thought that a reasonable way to do this would be with an array of the character set to use and 2 indexes, as shown. (The original post was about numbers but it was said that a wider character set was the aim.)
```

[1][2][3][4][5][6]
 |           |
 RowStart    |
             CurrentPos

```If CurrentPos reaches end, set it to start. If CurrentPos reaches RowStart, increment RowStart. If RowStart reaches end, set it to start. This works.

However, the hints to use % were intriguing, and as a result, the following succinct method does the job very well, albeit in a somewhat opaque way. I'd definitely write a comment if used in production code!

```

/* C Code */
    static int cycle_point = -1;
    const static int set_size = 6;

    cycle_point++; /* consider MAX_INT overflow */
    return (((cycle_point / set_size) + cycle_point) % set_size) + 1;

```Perhaps there's a simpler expression, but I couldn't see it.

---

### Post by Reiger on 2010-10-14
As noted that C code (and for that matter equivalent Java code) is liable to start producing wrong results pretty quickly due to integer overflow. The better approach would be to define a data structure which tracks positions that (through the use of modulus) are guaranteed not to overflow, but you do need to keep additional state.

Essentially it is the cyclic array/buffer minus the actual array: just the state counters/positions.

---

### Post by spjackson on 2010-10-14
> **Reiger said:**
> As noted that C code (and for that matter equivalent Java code) is liable to start producing wrong results pretty quickly due to integer overflow.

It's actually very easy to avoid overflow, I just didn't write it:
```

    if (cycle_point == set_size * set_size) {
        cycle_point = 0;
    }

```Less succinct of course.

---

### Post by Reiger on 2010-10-14
Well, I was more thinking along the lines of:

counter = (counter + 1) % size

That is guaranteed not to overflow, if counter begins at anything but Integer.MAX_SIZE (as the constant is called in Java, IIRC).

---

### Post by spjackson on 2010-10-14
> **Reiger said:**
> Well, I was more thinking along the lines of:

counter = (counter + 1) % size

That is guaranteed not to overflow, if counter begins at anything but Integer.MAX_SIZE (as the constant is called in Java, IIRC).
Good tip. It would be OK if you are using 2 counters and did something similar to both. However, the full sequence repeats at size squared and I'm just using a single counter. So, for completeness...

```

/* C Code */ 
int next_num()
{
    static int cycle_point = -1;
    const static int set_size = 6;

    cycle_point = (cycle_point + 1) % (set_size * set_size);
    return (((cycle_point / set_size) + cycle_point) % set_size) + 1;
}

```

---

### Post by dwhitney67 on 2010-10-14
Since we're throwing out solutions, here's the one I came up with the other night.  It's probably not that efficient, but it works.
```

class CharGen
{
   private int max_num;
   private int counter = 0;
   private int row     = 0;

   public CharGen(int max_num)
   {
      this.max_num = max_num;
   }

   public int nextNum()
   {
      if ((counter % max_num == 0) && (++row > max_num))
      {
         row = 1;
      }

      int num = row + (counter++ % max_num);

      return num - (num > max_num ? max_num : 0);
   }

   public static void main(String[] args)
   {
      int MAX_NUM = 6;

      CharGen c = new CharGen(MAX_NUM);

      //while (true)
      for (int j = 0; j < MAX_NUM*2; ++j)
      {
         for (int i = 0; i < MAX_NUM; ++i)
         {
            System.out.print(c.nextNum());
         }
         System.out.println();
      }
   }
}

```
It should be easy to translate to C or C++.

---

### Post by Eremis on 2010-10-19
Thanks for all the help guys, I got it

---

