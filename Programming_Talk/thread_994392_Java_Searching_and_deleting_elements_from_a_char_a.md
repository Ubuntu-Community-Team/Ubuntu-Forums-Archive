---
title: "Java: Searching and deleting elements from a char array"
date: 2008-11-26
forum: Programming Talk
---

### Post by Igniteflow on 2008-11-26
I have a Char array I converted from a string and now I want to search through it and delete some specified letters. The array is simply the alphabet so there will only be a single occurrence of each letter.  
Can anybody advise me on how I can do this either with a char array or string?  
The only thing I have found so far is for strings:
[php]
public static String removeChars(String s, char[] a) {
StringBuffer r = new StringBuffer();
for (int i = 0; i < s.length(); i ++) {
if (!contains(s.charAt(i), a)) {
r.append(s.charAt(i));
}
}
return r.toString();
}
[/php]
...and I can't get it to work. The rest of my program is working so if anyone could help me sort out the final piece of the puzzle I'd hugely appreciate it.

---

### Post by dwhitney67 on 2008-11-26
> **Igniteflow said:**
> I have a Char array I converted from a string and now I want to search through it and delete some specified letters. The array is simply the alphabet so there will only be a single occurrence of each letter.  
...

This really seems like a homework problem.  Have you referred to the [Java String API]("http://java.sun.com/javase/6/docs/api/java/lang/String.html")?  I'm sure your answer lies with one (or two) of the String methods.

Btw, if your intent is to remove specific characters from a string, why did you convert that string to a char array??

---

### Post by Igniteflow on 2008-11-27
I know how to convert a string to a character array
[php]
char[] cArray = string.toCharArray();
[/php]
So I am looking for a method to remove individual characters from either a string or a char array because once the method is done I could change the output back to a string.
My problem is that I can't find a way to search through a string or a char array for a specific character and remove it.
I've spent hours looking in reference books and online and can do just about everything else e.g. find and replace, concatenate, split, tokenize, remove white space etc. but I haven't found anything to simply delete single characters/letters.

---

### Post by dwhitney67 on 2008-11-27
Here's some hints...

Within the String API you will find the following methods: indexOf(), substring(), and length().

Using these methods, you should be able to find an individual character from within the string, and remove it.

P.S.  There is no need to convert the String to a char array for this exercise.

---

### Post by PaulM1985 on 2008-11-27
You could try using an ArrayList.  It has methods to add, remove, contains etc.  You could add all of your chars to this and then use the contains or removes methods.

---

### Post by drubin on 2008-11-27
For the record all Arrays/Strings (char arrays) are of a static fixed width. The only way to add eleements/remove is to create a new array and merge the data into the new one in the order you would like.

The String/ArrayList/Vector objects do this internally so you do not need to worry about this. They provide nicer wrappers for lists that need expanding/removing.

---

