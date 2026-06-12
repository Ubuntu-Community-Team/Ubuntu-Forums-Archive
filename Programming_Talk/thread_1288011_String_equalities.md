---
title: "String equalities"
date: 2009-10-10
forum: Programming Talk
---

### Post by s3a on 2009-10-10
```
public class TEST1_Q9
{
    public static void main(String args[])
    {
       String s1 = "abc";[B]
       String s2 = new String("abc");
       if(s1 == s2)      System.out.print(1);[/B]
       else              System.out.print(2);
       if(s1.equals(s2)) System.out.println(3);
       else              System.out.println(4);
    }
}
```

Why is it not printing "1"?

Any input would be greatly appreciated!
Thanks!

---

### Post by pbrockway2 on 2009-10-10
"s1==s2" is true when the two reference variables *s1* and *s2* have the same value.

The [String constructor]("http://java.sun.com/javase/6/docs/api/java/lang/String.html#String(java.lang.String)") API docs are clear about *s2*; the constructor "intializes a newly created String object so that it represents the same sequence of characters as the argument;"  Mark the words "newly created".  The reference variable *s2* has a value that references (points to) a newly created string, so it will **not** have the same value as *s1*.

---

### Post by kavon89 on 2009-10-10
When you compare two Objects with double equals, the comparison checks to see if the two Objects refer to the same place(s) in memory, which would make them *exactly* equivalent.

Objects which can be compared other ways normally have an equals method. String, which is an Object, has an equals method which compares the sequence of chars and returns a boolean.

---

