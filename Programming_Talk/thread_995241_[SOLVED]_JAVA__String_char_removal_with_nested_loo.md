---
title: "[SOLVED] JAVA:  String char removal with nested loop"
date: 2008-11-27
forum: Programming Talk
---

### Post by Igniteflow on 2008-11-27
I'm trying to make a nested loop which will search for and remove chars from a string.  The keyword contains six letters, alphabet of course is 26.  Can anyone show me what I'm doing wrong?  The second loop works fine to remove one char, but I need it to remove all six, so that only the letters of the alphabet remain that are not in the keyword. 

[php]
for (int j = 0; j < keyword.length(); j++)
    	letter = keyword.charAt(j);
 		for (int i = 0; i < alphabet.length(); i ++)
    	    if (alphabet.charAt(i) != letter) r += alphabet.charAt(i);
[/php]

---

### Post by pp. on 2008-11-27
I have used a number of object oriented languages, but Java is not among them. 

However, I am somewhat surprised that you attempt to solve that problem the same way one would solve it in - say - assembler.

Are not strings collections? Doesn't Java provide methods for collections which can select members by some criteria?

In some kind of pseudo code, my solution would look something like

letter_in_keyword := keyword.asSet();
selection_of_alphabet := alphabet.select([X|not(letter_in_keyword.contains(X))]).

---

### Post by Igniteflow on 2008-11-27
Thanks for the input, although I'm only eight weeks into programming so I don't really know how to implement what your saying.  

I'm thinking if the second loop worked for to remove one letter from the string, then logically it should be possible to run through multiple letters and remove them by using a nested loop.  

[Goes back to staring at screen]

---

### Post by pp. on 2008-11-27
> **Igniteflow said:**
> I don't really know how to implement what your saying.

[Goes back to staring at screen]

The answer to that one isn't on the screen. It's in the Java documentation of classes. Determine the class of your strings and find out if those classes support anything like the selection of letters.

> **Igniteflow said:**
> 
I'm thinking if the second loop worked for to remove one letter from the string, then logically it should be possible to run through multiple letters and remove them by using a nested loop.  

[Goes back to staring at screen]

Don't tell us that it doesn't work. Do tell us what output you get.

---

### Post by jespdj on 2008-11-27
> **pp. said:**
> However, I am somewhat surprised that you attempt to solve that problem the same way one would solve it in - say - assembler.

Are not strings collections? Doesn't Java provide methods for collections which can select members by some criteria?
No, strings in Java are not collections in that sense.

However, class String contains a lot of useful methods, including methods for finding and replacing text in a String by using regular expressions, for example.

Look at the [API documentation](http://java.sun.com/javase/6/docs/api/index.html) for class java.lang.String.

---

### Post by pp. on 2008-11-27
> **jespdj said:**
> No, strings in Java are not collections in that sense.

However, class String contains a lot of useful methods,

Thank you, I wasn't aware of that particular design decision in Java. However, if there are no strings methods which lend themselves to the purpose, I am sure you can convert Strings into Collections and process those in a brisk manner.

---

### Post by pp. on 2008-11-27
> **Igniteflow said:**
> 
I'm thinking if the second loop worked for to remove one letter from the string

Just in case you insist on fixing that low-level code instead of letting Java do the work for you:

You say that you remove a letter from a string. Look again at your code and tell me where, exactly, that ***removal*** takes place.

---

### Post by Igniteflow on 2008-11-27
[php]
for (int i = 0; i < alphabet.length(); i ++)
            if (alphabet.charAt(i) != letter) r += alphabet.charAt(i);  
[/php]

Removes letter (char letter = "A"; ), sorry I should have included the variable type.  
So it reduces "ABCDEFGHIJKLMNOPQRSTUVXYZ" to "BCDEFGHIJKLMNOPQRSTUVXYZ"
Please don't take my staring at the screen remark to mean I'm just sitting here waiting for someone to tell me the answer, I've been working on this for hours trying to fix it myself.  I've read the APIs and haven't come up with anything that works yet, but am working on it.
I did have the above code working but the problem is it appends (+=) the output on each loop resulting in a huge, useless string.  

Error output from original code is:

[php]
RemoveChar.java:17: variable letter might not have been initialized
    	    if (alphabet.charAt(i) != letter) r += alphabet.charAt(i);

[/php]

---

### Post by Igniteflow on 2008-11-27
[php]
String box;
String[] keyword = {"W","H","I","C","Y","K"};
String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

while (xxx < 6)
    {
    for (int i = 0; i < keyword.length; i++) {
    String t = (keyword[i]);
    box = alphabet.replaceAll(t, "");
    System.out.println(box);
    xxx++;
    }
[/php]

So I combined some the replace method to come up with this, which outputs
[php]
ABCDEFGHIJKLMNOPQRSTUVXYZ
ABCDEFGIJKLMNOPQRSTUVWXYZ
ABCDEFGHJKLMNOPQRSTUVWXYZ
ABDEFGHIJKLMNOPQRSTUVWXYZ
ABCDEFGHIJKLMNOPQRSTUVWXZ
ABCDEFGHIJLMNOPQRSTUVWXYZ
[/php]
I've been working on this for almost 11 hours now in total, could someone please throw me a bone and show me how I can stop alphabet reseting itself on each loop???

---

### Post by wrtpeeps on 2008-11-27
You are not saving the stored alphabet in the variable named alphabet, you are storing it in the variable named box. Thus, each loop is just executing and modifying the original alphabet. Try the code below:

[PHP]
String[] keyword = {"W","H","I","C","Y","K"};
String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

while (xxx < 6)
    {
    for (int i = 0; i < keyword.length; i++) {
    String t = (keyword[i]);
    alphabet = alphabet.replaceAll(t, "");
    System.out.println(alphabet);
    xxx++;
    }  [/PHP]

---

### Post by Igniteflow on 2008-11-27
thanks wrtpeeps, actually i had just finished it before i got your post. i arrived at
[php]
class RemoveChar  // removes all letters in keyword array from alphabet
{
    public static void main (String []args)
    {
    String box;
    String[] keyword = {"W","H","I","C","Y","K"};
    String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int x = 0;
       
    while (x < 6)
    {
    for (int i = 0; i < keyword.length; i++) {
    String t = (keyword[i]);
    box = alphabet.replaceAll(t, "");
    alphabet = box;
    x++;
    }
    System.out.println(alphabet);
    }
 	
 	}// end main
}//end class
[/php]
which seems pretty similar.  Programming, it's so frustrating, but ridiculously satisfying when I do actually figure something out.

is wrt a reference to the wireless flash software at all?

---

### Post by wrtpeeps on 2008-11-27
> **Igniteflow said:**
> thanks wrtpeeps, actually i had just finished it before i got your post. i arrived at
[php]
class RemoveChar  // removes all letters in keyword array from alphabet
{
    public static void main (String []args)
    {
    String box;
    String[] keyword = {"W","H","I","C","Y","K"};
    String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int x = 0;
       
    while (x < 6)
    {
    for (int i = 0; i < keyword.length; i++) {
    String t = (keyword[i]);
    box = alphabet.replaceAll(t, "");
    alphabet = box;
    x++;
    }
    System.out.println(alphabet);
    }
 	
 	}// end main
}//end class
[/php]
which seems pretty similar.  Programming, it's so frustrating, but ridiculously satisfying when I do actually figure something out.

**is wrt a reference to the wireless flash software at all?**

Nope. :)

Good job getting it done anyway.

---

