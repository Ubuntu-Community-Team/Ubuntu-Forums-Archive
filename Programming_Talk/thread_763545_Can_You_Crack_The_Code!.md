---
title: "Can You Crack The Code!"
date: 2008-04-23
forum: Programming Talk
---

### Post by Lster on 2008-04-23
Hi

Your challenge, if you accept, is to crack the following code. You are given three clues today and subsequently another clue everyday after that until it is solved. The first to solve it is the winner; if there is enough interest, maybe they would like to post the next code and it could continue similarly to the programming challenges.


So here is the encrypted text:

[PHP]8 6 14 15 19   6 20 11   11 24 24 18 4 14 8 10 2 18 12 2 9 9 15 !   24 17   24 15 22   13 17 19 2   12 25 23 22   14 16 15 2 18 24 4 24   12 1 3 14 ,   1 24 1 7   3 9 3 21 5 8 26 12 26   18 3   20 26 16 6 20 3 22 6 13 25 25   24 22   7 19 19   17 17 22 13 25 15 22 22   22 19 25 7 6   3 3 21 19   1 13   3 14   16 5 3 13   13 16 6 24 16 26 25 12 12   11 9   17 22   14 2 19   25 5 21 11 25 8 1 11 18 4 4   3 1   18 18 10 !   15   10 23 13 15 15   6 21 23 8   2 26 11 13 25 9 5 11 5   19 15   19 7 7   12 20 26   10 16 18 22 20   2 18 4 5 21 9 11 ![/PHP]

Notation of clues:
x represents any character.

Here are your clues:
1 <= x <= 26 and x is always whole.
The first word is "hello", the last word is "peppers".
Coding it involved modulo arithmetic.

Good luck! :)

To moderators and administrators: I can guarantee there is nothing objectionable in the least in the plain text! ;)

---

### Post by samjh on 2008-04-23
Can we assume the ! symbols in the cyphertext is actually supposed to be plaintext?

---

### Post by Lster on 2008-04-23
Sorry, I forgot to clarify those. The punctuation has not been encoded so they are, indeed, part of the plain text. The same goes for additional spaces to separate words...

---

### Post by CptPicard on 2008-04-23
I know the transformation you're using... now it's just a matter of search.. :p

EDIT: Okay, it probably doesn't even need a search.. let's see.. :)

---

### Post by Zugzwang on 2008-04-23
Not too hard. :guitar:

If you still want to solve it, don't look at the following code (Java):

[PHP]
/*
 * Solver.java
 *
 * Created on 23. April 2008
 *
 */

package code;

/**
 * @author Zugzwang
 */
public class Solver {
    
    /**
     * Decodes a string as encoded like the one at:
     * http://ubuntuforums.org/showthread.php?t=763545
     */
    public static String decode(String code) {

        // Split up the message
        StringBuffer result = new StringBuffer();
        String[] parts = code.split(" ");
        
        // Process message
        int currentShift = 0;
        for (int i=0;i<parts.length;i++) {
            
            // A whitespace?
            if (parts[i].length()==0) {
                result.append(' ');
            } else {
                // Number?
                try {
                    // Yes? Then decode!
                    int nr = Integer.parseInt(parts[i]);
                    int decodedLetter = (nr+currentShift) % 26;
                    currentShift = (currentShift+25) % 26;
                    result.append((char)('A'-1+decodedLetter));
                } catch (NumberFormatException e) {
                    // No? Just pass on the special character
                    result.append(parts[i]);
                }
            }
        }
        return result.toString();
    }

    /**
     * This is the actual main function - It prints out the solution for
     * the "Can You Crack the Code!" competition.
     */
    public static void main(String[] args) {
        String coded = "8 6 14 15 19   6 20 11   11 24 24 18 4 14 8 10 2 18 12 2 9 9 15 !   24 17   24 15 22   13 17 19 2   12 25 23 22   14 16 15 2 18 24 4 24   12 1 3 14 ,   1 24 1 7   3 9 3 21 5 8 26 12 26   18 3   20 26 16 6 20 3 22 6 13 25 25   24 22   7 19 19   17 17 22 13 25 15 22 22   22 19 25 7 6   3 3 21 19   1 13   3 14   16 5 3 13   13 16 6 24 16 26 25 12 12   11 9   17 22   14 2 19   25 5 21 11 25 8 1 11 18 4 4   3 1   18 18 10 !   15   10 23 13 15 15   6 21 23 8   2 26 11 13 25 9 5 11 5   19 15   19 7 7   12 20 26   10 16 18 22 20   2 18 4 5 21 9 11 !";
        System.out.println("The decoded message: ");
        System.out.println(decode(coded));
    }
    
}
[/PHP]

And the solution is:

[COLOR="White"]HELLO  AND  CONGRATULATIONS!  AS  YOU  KNOW  FROM  DECODING  THIS,  EACH  CHARACTER  IS  INCREMENTED  BY  ITS  POSITION  MINUS  ONEB  IT  IS  THEN  MODULUSED  BY  FJ  AND  INCREMENTED  BY  ONE!  I  CODED  THIS  LISTENING  TO  RED  HOT  CHILI  PEPPERS!
[/COLOR]

---

### Post by Lster on 2008-04-23
Very well done! Maybe I should have made it a little harder. I was considering incrementing it by a prime each time. Complexities can get very out of hand.

Zugzwang, maybe you would like to post a code?

---

### Post by Zugzwang on 2008-04-23
> **Lster said:**
> Zugzwang, maybe you would like to post a code?
Sure, but that will take a day or so.

Just wanted to mention that you encoded "26" even though your code doesn't allow that.  :-P

---

### Post by Lster on 2008-04-23
Yes! Each number at a particular offset actually has multiple meanings (in that case "2" or "F", it appears).

---

### Post by RIchard James13 on 2008-04-23
On casual observation of the first word and the last I was able to observe that you start with the first letter and increase by every character in that word. 
So
[PHP]8 6-1 14-2 15-3 19-4[/PHP]
gives
[PHP]8 5 12 12 15[/PHP]
which matches to 

[PHP]HELLO[/PHP]

Looking at the second word then 

[PHP]6-5 20-6 11-7[/PHP]
gives
[PHP]1 14 4[/PHP]
which matches to
[PHP]AND[/PHP]

So using that I can decode the first part of the message (using a calculator) as

[PHP]HELLO AND CONGRATULATIONS! AS ??? ???[/PHP]

X(N)=X+N-1

After that this method seems to break down. I wonder why the first part of your code can be decrypted like that?

---

### Post by Lster on 2008-04-23
Hint: I use modulo arithmetic... Are the numbers greater than 26?

---

### Post by Zugzwang on 2008-04-23
The next challenge has been posted: [http://ubuntuforums.org/showthread.php?t=763835]("http://ubuntuforums.org/showthread.php?t=763835")

---

### Post by Matthileo on 2008-04-24
> **Zugzwang said:**
> Not too hard. :guitar:

If you still want to solve it, don't look at the following code (Java):

[PHP]
/*
 * Solver.java
 *
 * Created on 23. April 2008
 *
 */

package code;

/**
 * @author Zugzwang
 */
public class Solver {
    
    /**
     * Decodes a string as encoded like the one at:
     * http://ubuntuforums.org/showthread.php?t=763545
     */
    public static String decode(String code) {

        // Split up the message
        StringBuffer result = new StringBuffer();
        String[] parts = code.split(" ");
        
        // Process message
        int currentShift = 0;
        for (int i=0;i<parts.length;i++) {
            
            // A whitespace?
            if (parts[i].length()==0) {
                result.append(' ');
            } else {
                // Number?
                try {
                    // Yes? Then decode!
                    int nr = Integer.parseInt(parts[i]);
                    int decodedLetter = (nr+currentShift) % 26;
                    currentShift = (currentShift+25) % 26;
                    result.append((char)('A'-1+decodedLetter));
                } catch (NumberFormatException e) {
                    // No? Just pass on the special character
                    result.append(parts[i]);
                }
            }
        }
        return result.toString();
    }

    /**
     * This is the actual main function - It prints out the solution for
     * the "Can You Crack the Code!" competition.
     */
    public static void main(String[] args) {
        String coded = "8 6 14 15 19   6 20 11   11 24 24 18 4 14 8 10 2 18 12 2 9 9 15 !   24 17   24 15 22   13 17 19 2   12 25 23 22   14 16 15 2 18 24 4 24   12 1 3 14 ,   1 24 1 7   3 9 3 21 5 8 26 12 26   18 3   20 26 16 6 20 3 22 6 13 25 25   24 22   7 19 19   17 17 22 13 25 15 22 22   22 19 25 7 6   3 3 21 19   1 13   3 14   16 5 3 13   13 16 6 24 16 26 25 12 12   11 9   17 22   14 2 19   25 5 21 11 25 8 1 11 18 4 4   3 1   18 18 10 !   15   10 23 13 15 15   6 21 23 8   2 26 11 13 25 9 5 11 5   19 15   19 7 7   12 20 26   10 16 18 22 20   2 18 4 5 21 9 11 !";
        System.out.println("The decoded message: ");
        System.out.println(decode(coded));
    }
    
}
[/PHP]

And the solution is:

[COLOR="White"]HELLO  AND  CONGRATULATIONS!  AS  YOU  KNOW  FROM  DECODING  THIS,  EACH  CHARACTER  IS  INCREMENTED  BY  ITS  POSITION  MINUS  ONEB  IT  IS  THEN  MODULUSED  BY  FJ  AND  INCREMENTED  BY  ONE!  I  CODED  THIS  LISTENING  TO  RED  HOT  CHILI  PEPPERS!
[/COLOR]

That is really similar to C#...
It was easier than coverting c++ to c# to convert that lol...

---

### Post by stevescripts on 2008-04-24
Lster,

I had fun with this, TY.  It proved to be just a bit more complex than I first thought.

BTW, just what sort of sounds do those red hot chili peppers make? :lolflag:

Steve
(little tcl script available upon request ;) )
Hope to find the time to do the next one ...

---

### Post by Lster on 2008-04-25
stevescripts, Red Hot Chili Peppers are a band! One of my favourites too! :)

---

### Post by steevc on 2008-04-25
> **Matthileo said:**
> That is really similar to C#...
It was easier than coverting c++ to c# to convert that lol...

Confession time. I read this post at work where I'm stuck with Windows, so I wrote a solution in C#. I'm still fairly new to the language, so it was good practice. Normally I would do this sort of task in Python, which I also need to practice.

A note on molulo operators. I hit a problem when I tried to use it on negative numbers. That gave a negative result. I suppose that is reasonable if it is defined as giving the remainder of a division. What I actually needed was something that always gave a result in a range 0-25. I just adjusted the negative numbers to work around this in a similar way to Zugzwang.

Anyway, it was fun to do. I may look at the follow-ons. I also ought to have another go at The Python Challenge. I played with it a few years back and managed 15 levels.

---

### Post by stevescripts on 2008-04-25
> **Lster said:**
> stevescripts, Red Hot Chili Peppers are a band! One of my favourites too! :)

Lster - yeah even an old-fart like me actually knows they are a band ... twas shameless attempt at humor ;)

Steve

---

