---
title: "One line of code preventing me from completing my program!"
date: 2010-04-03
forum: Programming Talk
---

### Post by s3a on 2010-04-03
Here is the driver code:
```
package assignment_3a;

public class MagicSquareDemo
{
    public static void main(String[] args)
    {
        MagicSquare m1 = new MagicSquare(5);
        System.out.println(m1);
        MagicSquare m2 = new MagicSquare(-5); // negative order
        System.out.println(m2);
        MagicSquare m3 = new MagicSquare(10); // even order
        System.out.println(m3);
    }
}

```

Here is the (full) MagicSquare class (I bolded the line that is causing my troubles):
```
// Author:
// Purpose: To generate magic squares of a certain desired order

package assignment_3a;

public class MagicSquare
{

    private int order; // the order of this magic square
    private int[][] msArray; // reference to array storage // me: magic square array

// A constructor that accepts an int n n as the order of the magic square.
// Sets order to 3 if n < 3; otherwise, sets order to n+1 if n is even;
// otherwise, sets order to n.
// Finally, allocates an int array of order rows and order columns.
    public MagicSquare(int n)
    {
        if (n < 3) // Is n bellow 3?
        {
            System.out.println("This program cannot generate magic squares of negative orders like: " + n);
            System.out.println("The default order 3 is assumed for this magic square.");
            order = 3;
        }
        else if (n % 2 == 0) // Is n even?
        {
            System.out.println("This program cannot generate magic squares of even orders like: " + n);
            System.out.println("The order " + (n+1) + " is assumed for this magic square.");
            order = n + 1;
        }
        else // n >= 3 where n is an odd number
        {
            order = n;
        }
        
        // We now have a valid order n. Let's allocate space for a square array
        msArray = new int[order][order];
        doMagic();
    }
    
    
    public void doMagic()
    {
        int row = 0;
        int column = order/2;
        int k = 1;    
        
        while(k <= order*order)
        {
            msArray[row][column] = k;
            k+=1;
            --row;
            ++column;
            if(row == -1 && column == order)
        	{
        		row = 1;
        		column = order - 1;
        	}
            if(row == - 1)
            {
                row = order - 1;
            }
            if(column  == order)
            {
                column = 0;
            }
            if(msArray[row][column] != 0) // Checks if it's occupied
            {
                row+=2;
                --column;
            }
        }
    }

    // Returns the order of this magic square.
    public int getOrder()
    {
        return order;
    }

    public int magicNumber()
    {
        return (order * order * order + order)/2; // (n^3 + n)/2 formula
    }
    
    // Returns the sum of the values (of the columns) in the i&#710;th row cell(s).
    private int rowSum(int row)
    {
        int total = 0;
        for(int column = 0; column < msArray[row].length; column++)
        {
            total += msArray[row][column];
        }
        return total;
    }
    
    // Determines whether the row sums are each equal to the magic number.
   private boolean checkRowSums()
   {
       if(rowSum(order) == magicNumber())
       {
           return true;
       }
       else
       {
           return false;
       }
   }
   
   // Returns the sum of the values (of the rows) in the j&#710;th column cells.
   private int columnSum(int column)
   {
       int total = 0;
       for(int row = 0; row < msArray.length; row++)
       {
           total += msArray[row][column];
       }
       return total;
   }
   
   // Determines whether the column sums each are equal to the magic number.
      private boolean checkColumnSums()
     {
         if(columnSum(order) == magicNumber())
          {
              return true;
          }
          else
          {
              return false;
          }
     }
  
  //Returns sum of the values in the primary diagonal cells.
private int primaryDiagonalSum() // Could have a bug but I can't see one as of now
{
    int row = 0;
    int total = 0;

    for(int column = 0; column < msArray[row].length; column++)
    {
        total+=msArray[row][column];
        row+=1;
    }
    return total;
}
  
//Returns sum of the values in the secondary diagonal cells.
private int secondaryDiagonalSum()
{
    int total = 0;
    int row = (msArray.length - 1);
    
    for(int column = row; column >= 0; column--)
    {
        total+=msArray[row][column];
        row-=1;
    }
    return total;
}
  
  // Determines whether the diagonal sums each are equal to the magic number.
private boolean checkDiagonalSums()
{
    if(magicNumber() == primaryDiagonalSum() && magicNumber() == secondaryDiagonalSum())
    {
        return true;
    }
    else
    {
        return false;
    }
}

  // Determines whether the contents of the array represents a magic square.
public boolean isMagic()
{
    if(checkRowSums() && checkColumnSums() && checkDiagonalSums())
    {
        return true;
    }
    else
    {
        return false;
    }
}
  
    public String toString()
    {
        String result="Magic square of order " + order + "\n" +
                      "=========================\n\n";
        for(int row = 0; row < msArray.length; ++row) // scans rows
        {
            for(int column = 0; column < msArray[row].length; ++column) // scan columns
            {
                result = result + String.format("%5d", msArray[row][column]);
            }
            result = result + "\n";     // prepare to skip line
        }
**        //if(this.isMagic())result += "\nStatus: Valid";**
        result += "\nMagic number: " + magicNumber() + "\n";
        
        return result;
    }
    
    public boolean equals(Object obj)
    {
        boolean result = false;
        
        if(this == obj) return true;
        if(obj == null) return false;
        if(this.getClass() != obj.getClass()) return false;
        MagicSquare otherObject = (MagicSquare)obj;
        
        if(otherObject.isMagic() == this.isMagic() && otherObject.order == this.order)
        {
            result = true;
        }
        return result;
    }
}

```

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by Some Penguin on 2010-04-03
Rather than ask people to solve your homework for you, you should learn to actually check what each function assumes versus what it actually does.

Off-hand, I see obvious problems in checkRowSums, checkColumnSums, either primaryDiagonalSums or secondaryDiagonalSums (there's insufficient documentation to indicate what you have in mind for them, but as considered a pair, one must quite clearly be wrong).  Step through them and look at what they actually do...

---

### Post by s3a on 2010-04-03
Ok I think I fixed those problems. (Thanks for mentionning them):

```
// Author:
// Purpose: To generate magic squares of a certain desired order

package assignment_3a;

public class MagicSquare
{

    private int order; // the order of this magic square
    private int[][] msArray; // reference to array storage // me: magic square array

// A constructor that accepts an int n n as the order of the magic square.
// Sets order to 3 if n < 3; otherwise, sets order to n+1 if n is even;
// otherwise, sets order to n.
// Finally, allocates an int array of order rows and order columns.
    public MagicSquare(int n)
    {
        if (n < 3) // Is n bellow 3?
        {
            System.out.println("This program cannot generate magic squares of negative orders like: " + n);
            System.out.println("The default order 3 is assumed for this magic square.");
            order = 3;
        }
        else if (n % 2 == 0) // Is n even?
        {
            System.out.println("This program cannot generate magic squares of even orders like: " + n);
            System.out.println("The order " + (n+1) + " is assumed for this magic square.");
            order = n + 1;
        }
        else // n >= 3 where n is an odd number
        {
            order = n;
        }
        
        // We now have a valid order n. Let's allocate space for a square array
        msArray = new int[order][order];
        doMagic();
    }
    
    
    public void doMagic()
    {
        int row = 0;
        int column = order/2;
        int k = 1;    
        
        while(k <= order*order)
        {
            msArray[row][column] = k;
            k+=1;
            --row;
            ++column;
            if(row == -1 && column == order)
        	{
        		row = 1;
        		column = order - 1;
        	}
            if(row == - 1)
            {
                row = order - 1;
            }
            if(column  == order)
            {
                column = 0;
            }
            if(msArray[row][column] != 0) // Checks if it's occupied
            {
                row+=2;
                --column;
            }
        }
    }

    // Returns the order of this magic square.
    public int getOrder()
    {
        return order;
    }

    public int magicNumber()
    {
        return (order * order * order + order)/2; // (n^3 + n)/2 formula
    }
    
    // Returns the sum of the values (of the columns) in the i&#710;th row cell(s).
    private int rowSum(int row)
    {
        int total = 0;
        for(int column = 0; column < msArray[row].length; column++)
        {
            total += msArray[row][column];
        }
        return total;
    }
    
    // Determines whether the row sums are each equal to the magic number.
   private boolean checkRowSums()
    {
        int row = 0;
        boolean isEqual = true;
        while(isEqual && row < order)
        {
            if(rowSum(row) == magicNumber())
            {
                isEqual = true;
                row += 1;
            }
            else
            {
                isEqual = false;
                break;
            }
        }
        return isEqual;
    }
   
   // Returns the sum of the values (of the rows) in the j&#710;th column cells.
   private int columnSum(int column)
   {
       int total = 0;
       for(int row = 0; row < msArray.length; row++)
       {
           total += msArray[row][column];
       }
       return total;
   }
   
   // Determines whether the column sums each are equal to the magic number.
    private boolean checkColumnSums()
    {
        int column = 0;
        boolean isEqual = true;
        while(isEqual && column < order)
        {
            if(columnSum(column) == magicNumber())
            {
                isEqual = true;
                column += 1;
            }
            else
            {
                isEqual = false;
                break;
            }
        }
        return isEqual;
    }
   //      private boolean checkColumnSums()
//     {
//         if(columnSum(order - 1) == magicNumber())
//          {
//              return true;
//          }
//          else
//          {
//              return false;
//          }
//     }
  
  //Returns sum of the values in the primary diagonal cells.
private int primaryDiagonalSum() // Could have a bug but I can't see one as of now
{
    int row = 0;
    int total = 0;

    for(int column = 0; column < msArray[row].length; column++)
    {
        total+=msArray[row][column];
        row+=1;
    }
    return total;
}
  
//Returns sum of the values in the secondary diagonal cells.
private int secondaryDiagonalSum()
{
    int total = 0;
    int row = (msArray.length - 1);
    
    for(int column = row; column >= 0; column--)
    {
        total+=msArray[row][column];
        row+=1;
    }
    return total;
}
  
  // Determines whether the diagonal sums each are equal to the magic number.
private boolean checkDiagonalSums()
{
    if(magicNumber() == primaryDiagonalSum() && magicNumber() == secondaryDiagonalSum())
    {
        return true;
    }
    else
    {
        return false;
    }
}

  // Determines whether the contents of the array represents a magic square.
public boolean isMagic()
{
    if(checkRowSums() && checkColumnSums() && checkDiagonalSums())
    {
        return true;
    }
    else
    {
        return false;
    }
}
  
    public String toString()
    {
        String result="Magic square of order " + order + "\n" +
                      "=========================\n\n";
        for(int row = 0; row < msArray.length; ++row) // scans rows
        {
            for(int column = 0; column < msArray[row].length; ++column) // scan columns
            {
                result = result + String.format("%5d", msArray[row][column]);
            }
            result = result + "\n";     // prepare to skip line
        }
**        //if(this.isMagic())result += "\nStatus: Valid";**
        result += "\nMagic number: " + magicNumber() + "\n";
        
        return result;
    }
    
    public boolean equals(Object obj)
    {
        boolean result = false;
        
        if(this == obj) return true;
        if(obj == null) return false;
        if(this.getClass() != obj.getClass()) return false;
        MagicSquare otherObject = (MagicSquare)obj;
        
        if(otherObject.isMagic() == this.isMagic() && otherObject.order == this.order)
        {
            result = true;
        }
        return result;
    }
}

```

But my friend and I are still stuck on what I have bolded. :( So, I'd appreciate it if someone could at least give me a hint on what the problem could be since you don't like giving answers.

---

### Post by gnometorule on 2010-04-03
This is a pointer, so derefence using 'this->(member)' (or *this.(member)).

If posting here with compilation issues, you should add compiler error messages; and remove any references to hw in your code and language, instead underlining how you bravely did this for fun. :)

EDIT: ...and please start out by mentioning which language your code is in. I jumped to the line you highlighted, assuming then it was C++. I don't know Java. So pls ignore what I say.

---

### Post by LKjell on 2010-04-03
Try to see if you understand the math between this: 

```
private int primaryDiagonalSum() // Could have a bug but I can't see one as of now
{
    int total = 0;

    for(int i = 0; i < order; i++)
    {
        total += msArray[i][i];
    }
    return total;
}

//Returns sum of the values in the secondary diagonal cells.
private int secondaryDiagonalSum()
{
    int total = 0;

    for(int i = 0; i < order; i++)
    {
        total += msArray[i][order - i - 1];
    }
    return total;
}
```

---

### Post by dwhitney67 on 2010-04-03
> **s3a said:**
> 
But my friend and I are still stuck on what I have bolded. :( So, I'd appreciate it if someone could at least give me a hint on what the problem could be since you don't like giving answers.
Boo hoo.

Didn't one of your threads get shutdown yesterday because it involved a homework assignment.  This is the exact same problem.

Here's a hint... it is called System.out.println().  Use it often when debugging your application.  Jeez.

---

### Post by LKjell on 2010-04-03
I think there is a math problem. Programming is not just about typing something random on the screen. You actually have to plan your structure and debug stuff with a pencil. Yea go grab the pencil it is very useful!

And then there are stuff about code readability. Have your if statement in two lines if that is possible. And stuff you can cut down to one line do that!

```
    if(checkRowSums() && checkColumnSums() && checkDiagonalSums())
    {
        return true;
    }
    else
    {
        return false;
    }

```

```
    return checkRowSums() && checkColumnSums() && checkDiagonalSums()

```

---

### Post by s3a on 2010-04-04
Oh, I see what my mistake was! I also shrinked my code like advised. By the way, I do ask programming help when it's not my homework too so it's not like I'm some evil child that's trying to just get programming homework over with. I actually care about this and I'm hoping to be one of you Linux programmers in the future.

I think on my summer break, I am going to try to debug lots of mini code which is easier but a nice way to train myself. I just need to find a site that has a bunch of mini code segments for people that like debugging for fun but I'll worry about that this summer.

---

### Post by Bachstelze on 2010-04-04
> **dwhitney67 said:**
> 
Here's a hint... it is called System.out.println().  Use it often when debugging your application.  Jeez.

No, no, no, no! That's what gdb is for!

---

### Post by dwhitney67 on 2010-04-04
> **Bachstelze said:**
> No, no, no, no! That's what gdb is for!

Oh that's great!  I did not know that.  How can I debug a Java program?

---

### Post by Bachstelze on 2010-04-04
> **dwhitney67 said:**
> Oh that's great!  I did not know that.  How can I debug a Java program?

You.. rewrite it in C++? :D Nah, seriously, my brain was still in C++ mode for some reason...

*goes to the failboat*

---

### Post by dwhitney67 on 2010-04-04
> **Bachstelze said:**
> You.. rewrite it in C++? :D Nah, seriously, my brain was still in C++ mode for some reason...

*goes to the failboat*

Actually, after Googling a bit, I know it is possible; I just don't know how to do it from the command line, using Sun's Java compiler, and then running gdb.

I thought it would be simple like:
```

$ javac -g MyProgram.java
$ gdb java
(gdb) b main
(gdb) run MyProgram
(gdb)

```

---

### Post by CptPicard on 2010-04-04
> **dwhitney67 said:**
> Actually, after Googling a bit, I know it is possible;


man jdb :)

---

### Post by dwhitney67 on 2010-04-04
> **CptPicard said:**
> man jdb :)

Thanks.

---

