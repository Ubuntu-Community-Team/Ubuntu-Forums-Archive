---
title: "Java missing symbol error. Need a new perspective."
date: 2010-04-07
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-07
Okay I have two pieces of code, one compiles the other does not I'm not sure why. Here's the working piece of code. 

```
class copyArray {
    public static void main(String[] args){
        char[] copyFrom = { 'd', 'e', 'c', 'a', 'f', 'f', 'e',
                    'i', 'n', 'a', 't', 'e', 'd' };
        char[] copyTo = new char[7];
        
        System.arraycopy(copyFrom, 2, copyTo, 0, 7);
        System.out.println(new String(copyTo));
    }
}
```The code below doesn't compile. 

```
class problem1 {
    public static void main(String[] args)
    {
        //Declare Array
        int[] numeral = { 17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12};
        int[] finalNum = new int[13];
        /*int[] numeral; //Array where data starts
        int[] finalNum; //Array where data ends up
        
        //Declare Array Memory
        numeral = new int[13];
        finalNum = new int[13];*/
        
        //Put data into array
        /*numeral[0] = 17;
        numeral[1] = 6;
        numeral[2] = 45;
        numeral[3] = 2;
        numeral[4] = 3;
        numeral[5] = 17;
        numeral[6] = 6;
        numeral[7] = 9;
        numeral[8] = 8;
        numeral[9] = 6;
        numeral[10] = 1;
        numeral[11] = 4;
        numeral[12] = 12;*/
         
        
        //Manipulate Array
            //check position 0
        
            if (numeral[0] != numeral[1] 
            && numeral[0] != numeral[2] 
            && numeral[0] != numeral[3] 
            && numeral[0] != numeral[4] 
            && numeral[0] != numeral[5] 
            && numeral[0] != numeral[6] 
            && numeral[0] != numeral[7] 
            && numeral[0] != numeral[8] 
            && numeral[0] != numeral[9] 
            && numeral[0] != numeral[10] 
            && numeral[0] != numeral[11] 
            && numeral[0] != numeral[12]) 
            {   
                System.arraycopy(numeral, 0, finalNum, 0, 1);
                System.out.println(**new** String(finalNum));
            }

.......
```Compiling the second version with javac, gives me...

```

problem1.java:55: cannot find symbol
symbol  : constructor String(int[])
location: class java.lang.String
                System.out.println(new String(finalNum));


```What exactly am I doing wrong?

---

### Post by Some Penguin on 2010-04-08
Like it's telling you, there is no constructor for a String that takes as inputs an array of integers.

If you were planning to have the integers interpreted as ASCII values (or for some other encoding), you'll need to use bytes, not integers.

---

### Post by LKjell on 2010-04-08
> **Some Penguin said:**
> Like it's telling you, there is no constructor for a String that takes as inputs an array of integers.

If you were planning to have the integers interpreted as ASCII values (or for some other encoding), you'll need to use bytes, not integers.

or cast to char[] or byte[]

---

### Post by Ravenshade on 2010-04-08
.... so why does the first one work? :confused:

As far as I can see the only difference is that I've replaced char with int. Yet int throws errors.

---

### Post by Zugzwang on 2010-04-08
> **Ravenshade said:**
> .... so why does the first one work? :confused:

As far as I can see the only difference is that I've replaced char with int. Yet int throws errors.

This is because there actually *is* a suitable contructor for this case. Look [here]("http://java.sun.com/javase/6/docs/api/java/lang/String.html") for a list of all constructors. There is one of a char[] array, but none for an int[] array.

Note that LKjell's suggestion will probably not work: You cannot simply cast an array of one type into one of another type. You would rather need to copy the content element-by-element into a char array first.

---

### Post by Ravenshade on 2010-04-08
actually compiled if I changed the types to byte. Not that it came out with readable data though :lolflag:

I'll take a look at that link thanks!


but there appears to be one for an int[]...

public **String**(int[] codePoints,
              int offset,
              int count)


Okay.... I used that constructor and got...

```
-
-
-
-    
-
-    
-    
-    

```Which is just what I got from byte....I think they're doing the same thing. 

not that I have a clue how to use it...


---------------------------

...Can anyone help me print out the array of integers...I just want to print the damn things.

---

### Post by Ravenshade on 2010-04-08
Solved. 

I used System.out.println(finalNum[i])

---

