---
title: "[Java] Increment an Integer in an ArrayList"
date: 2010-02-25
forum: Programming Talk
---

### Post by patrickaupperle on 2010-02-25
Is it possible to increase the value by one of of an Integer in an ArrayList (similar to an array num[0]++)?

---

### Post by CptPicard on 2010-02-25
Java's Integer object wrapper is immutable, so no, you'll have to create a new object and replace the old one in the ArrayList.

---

### Post by patrickaupperle on 2010-02-25
> **CptPicard said:**
> Java's Integer object wrapper is immutable, so no, you'll have to create a new object and replace the old one in the ArrayList.

Oh, ok. I just wanted to make sure that I was not doing things the hard way ;). 
Thank you.

---

### Post by GregBrannon on 2010-02-26
CptPicard,

In my Java program for Programmer's Challenge #9, I used the following array routine to tally the number of times an alpha charater appeared in the file:

```
while ( inputData.hasNext() == true )    // read data from the file
{                                       // until there is no more
   inputChar = inputData.next();       // Get the next character
   tallyIndex = (int)(inputChar.charAt(0) ); // get ascii value

   if ( tallyIndex < 97 )  // character is a numeral
   {
         tallyIndex -= 48;   // index numeral '0'/ascii 48 to zero 
   }
   else                    // character is a letter
   {
         tallyIndex -= 87;   // index alpha 'a'/ascii 97 to 10
   }
                
   inputChars[ tallyIndex ]++;  // increase resulting index by 1
}
```

Didn't I increment the integer in the array with the last statement?

I think it works, but my confidence is shaken after reading your answer.

Thanks for your help.

---

### Post by CptPicard on 2010-02-26
Seems like you're using an "array of int", where it works all right. Not so with ArrayList and the "wrapper objects" such as Integer (ArrayList<Integer>).

---

### Post by ja660k on 2010-02-26
sorry.
please delete

---

### Post by GregBrannon on 2010-02-26
> Seems like you're using an "array of int", where it works all right. Not so with ArrayList and the "wrapper objects" such as Integer (ArrayList<Integer>).

Thanks CptPicard.  The difference is a subtlety I haven't yet grasped, but I'm working on it.  You've given me something to go learn more about.

---

### Post by CptPicard on 2010-02-26
> **GregBrannon said:**
> The difference is a subtlety I haven't yet grasped, but I'm working on it.  You've given me something to go learn more about.

Read about the difference between "primitive types" and these "wrapper objects", and also how an array relates to a Collections container type...

---

