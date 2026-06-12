---
title: "Return multiple values from a Java method."
date: 2010-04-22
forum: Programming Talk
---

### Post by stchman on 2010-04-22
I decided to throw my 2 cents into the fray and show how I do multiple value retun from a Java method.  Java method only return one value unless you use a Vector.  I have been told to use ArrayList in place of Vector, but I cannot see a difference.

Here is a code example of how I did it.

[PHP]
/*
Show how to return multiple values from a Java method
*/

import java.lang.*;
import java.util.*;

public class Tester
{
    public static void main( String [] args )
    {
        // create variable of type Tester
        Tester m = new Tester();
        
        // transition to non-static method
        m.nonStaticMethod();
    }
    
    // non static method
    void nonStaticMethod()
    {
        // create Vector to store values
        Vector Values = new Vector();
        
        // create double variables
        double a = 0.0, b = 0.0;

        // call method passing the Vector Values
        returnMultiple( Values );
        
        // extract values from Vector, converting them to Strings then parsing doubles
        a = Double.parseDouble( Values.get( 0 ).toString() );
        b = Double.parseDouble( Values.get( 1 ).toString() );
        
        // print out variables
        System.out.println( a );
        System.out.println( b );
    }

    // method to show how to return multiple values from a method using Vector
    void returnMultiple( Vector Storage )
    {
        // create variables
        double x = 0.0, y = 0.0;
    
        // init variables
        x = 900.23;
        y = x * 56.3 + 85.147;
        
        // add values to Vector
        Storage.add( 0, x );
        Storage.add( 1, y );
    }
} 
[/PHP]

As you can see by filling the Vector you can return as many values from a method as you please.

---

### Post by Some Penguin on 2010-04-22
The major reason why you might want to use ArrayList instead of Vector is that Vector has coarse synchronization -- all methods grab an exclusive lock on the entire Object.  This tends not to be necessary for normal workloads; even where you want locking, you can usually use finer-grained locking than that.

That said, modern JVMs can sometimes detect that synchronization won't be necessary, and the overhead usually isn't that bad on uncontended locks.

---

### Post by stchman on 2010-04-22
> **Some Penguin said:**
> The major reason why you might want to use ArrayList instead of Vector is that Vector has coarse synchronization -- all methods grab an exclusive lock on the entire Object.  This tends not to be necessary for normal workloads; even where you want locking, you can usually use finer-grained locking than that.

That said, modern JVMs can sometimes detect that synchronization won't be necessary, and the overhead usually isn't that bad on uncontended locks.

So there is a performance hit with using Vector over ArrayList?  I see.  

I am also a huge fan of getting out of static main right away as you can see.  Does this present any problems?

Thanks.

---

### Post by shadylookin on 2010-04-22
You haven't returned anything, you've just passed an object by reference and modified it. 

Well I guess not technically by reference more like passing a reference by value in java.

---

