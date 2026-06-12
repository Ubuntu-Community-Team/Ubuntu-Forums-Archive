---
title: "Difference between &quot;Char&quot; and &quot;String&quot; at Java"
date: 2008-08-25
forum: Programming Talk
---

### Post by TzaB on 2008-08-25
Hello guys, i am reading a book for Java that i am trying to learn and i have a question.

I can't understand which is the difference between the variable type "char" and "string".

For example, there is a difference between "int" and "short", the bytes at the memory and the area of numbers that they have.

But, which is the difference between "char" and "string" ?
Expect that "char" use (') and "string" (").

Thanks for reading.

PS: It is my first "real" programming language. (at school i learned a fake-language for the purpose of the programming lesson)

---

### Post by CptPicard on 2008-08-25
Char is a single character, a String is a sequence of characters (possibly just one). In addition, String is an full-blown object, a char primitive data type is just two bytes in unicode. Then there is of course the object wrapper type Character for "char" (like there is Integer for int etc).

---

### Post by TzaB on 2008-08-25
Oh thank you very much. The book has an example and it is asking to write the following:

```
public class showChar
{
   public static void main(String[] args)
   {
       char c1,c2,c3,c4,c5;
       c1='H';
       c2='i';
       c3='\n';
       c4='G';
       c5='\u03E2';
       System.out.println(c1);
       System.out.println(c2);
       System.out.println(c3);
       System.out.println(c4);
       System.out.println(c5);
   }

}
```

I didn't think why it has every character alone at each line because at theory it didn't mention that "char" accepts only one character.
Anyway, i am noob :/

Thank you again

---

### Post by jimi_hendrix on 2008-08-25
you can also make an array of chars which is basically a string...is there a point for chars these days?

---

### Post by mssever on 2008-08-25
It's been so long since I've used Java that I don't know about Java's unicode support. It's important to note, though, that there's a big difference between a byte and a utf-8 character (which can take anywhere from 1-6 bytes). People often treat strings as arrays of chars, where a char is one byte. And that's a mistake nowadays. Like I said, I don't know if this applies to Java or not.

---

### Post by red_Marvin on 2008-08-25
> **jimi_hendrix said:**
> you can also make an array of chars which is basically a string...is there a point for chars these days?

Not much in programming languages further from the hardware than say, C, but on a low level -yes.

---

### Post by Reiger on 2008-08-25
Java uses a special Java representation which is close to some form of Unicode.

As for the char == int comparison: AFAIK that'll only take you up to the ANSI-range where each byte value does equal a distinct char value. Java supports a rather lot of encodings out of the box (well that slightly depends on your locale: if that doesn't support anything but ASCII some things won't work...). Among those UTF-16, UTF-8.

---

### Post by Reiger on 2008-08-25
> **red_Marvin said:**
> Not much in programming languages further from the hardware than say, C, but on a low level -yes.

It depends, personally I often have good uses for chars: if only to assign hotkeys! :)

---

### Post by CptPicard on 2008-08-25
From Sun docs with quick googling...

> **Reiger said:**
> Java uses a special Java representation which is close to some form of Unicode.

[http://java.sun.com/docs/books/tutorial/java/nutsandbolts/datatypes.html](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/datatypes.html)

*"char: The char data type is a single 16-bit Unicode character. It has a minimum value of '\u0000' (or 0) and a maximum value of '\uffff' (or 65,535 inclusive)."*

As for the wrapper type: 

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Character.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Character.html)

*"The Character class wraps a value of the primitive type char in an object. An object of type Character contains a single field whose type is char."*

---

