---
title: "(Java - involving basics of classes etc) Which of the following statements are true?"
date: 2009-12-08
forum: Programming Talk
---

### Post by s3a on 2009-12-08
Based on what I know;

The default value for a (data field? - what is that exactly) of a boolean type, numeric type, object type is:
false, 0, and null respectively.

But for the numeric example why is the following variable x not initialized as 0?

public class Program
{
public static void main (String [] args)
{
double x; // If it was double x = 5; it would work
System.out.println(x);
}
}

Basically I am trying to answer the following practice test question:
[B]"35. Which of the following statements are true?
A. local variables do not have default values.
B. data fields have default values.
C. A variable of a primitive type holds a value of the primitive type.
D. A variable of a reference type holds a reference to where an object is stored
in the memory.
E. You may assign an int value to a reference variable.
"[/B]

(Assuming I am right when I chose B for #34)
"34. The default value for data field of a boolean type, numeric type, object
                     , respectively.
    type is
    A.  true, 1, Null
    B.  false, 0, null
    C.  true, 0, null
    D.  true, 1, null
    E.  false, 1, null"

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2009-12-08
Please don't ask us to do your homework!!!

---

### Post by jespdj on 2009-12-09
> **s3a said:**
> The default value for a (data field? - what is that exactly) of a boolean type, numeric type, object type is:
false, 0, and null respectively.
With a "data field", they most likely mean a member variable of a class.

> **s3a said:**
> But for the numeric example why is the following variable x not initialized as 0?
Because the variable x is not a member variable of your class Program, but a local variable in the main() method. Local variables in Java are not automatically initialized to default values, in contrast to member variables.

---

