---
title: "Can someone at least give me a hint to what is wrong with my Java program?"
date: 2010-04-02
forum: Programming Talk
---

### Post by s3a on 2010-04-02
Here is my driver code:
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

Here is my MagicSquare class:
```
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
        if (n < 3) // is n bellow 3?
        {
            System.out.println("This program cannot generate magic squares of negative orders like: " + n);
            System.out.println("The default order 3 is assumed for this magic square.");
            order = 3;
        }
        else if (n % 2 == 0) // is n even?
        {
            System.out.println("This program cannot generate magic squares of even orders like: " + n);
            System.out.println("The order " + (n+1) + " is assumed for this magic square.");
            order = n + 1;
        }
        else // n >= 3 where n is an odd number
        {
            order = n;
        }
        // we now have a valid order n
        // Let's allocate space for an square array
        msArray = new int[order][order];
        doMagic();
    }
    
    private void doMagic()
    {
        System.out.println("Implement the magic square "); // He wrote that
        
        int row = 0;
        int column = order/2;
        int k = 1;
        
        while(k<=order*order)
        {
            if(row == -1 && column == order)
            {
                row = 1;
                column = order - 1;
            }
            else if(row == 0)
            {
                    row = order - 1;
            }
            else if(column == order)
            {
                    column = 0;
            }
            else if(msArray[row][column] != 0)//if A[row][col] is occupied??
            {
                row +=2;
                column-=1;
            }
            else
            {
                msArray[row][column] = k;
                k += 1;
                --row;
                ++column;
            }
        }
        // By "done," I don't think he means System.exit(0);
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
        for(int r = 0; r < msArray.length; ++r) // scans rows
        {
            for(int c = 0; c < msArray[r].length; ++c) // scan columns
            {
                result = result + String.format("%5d", msArray[r][c]);
            }
            result = result + "\n";     // prepare to skip line
        }        
        result = result + "\nMagic number: " + magicNumber() + "\n";

        return result;
    }
    
    public boolean equals(Object obj) // Make more efficient later! // order && is magic?
    {
        if(this == obj) return true;
        if(obj == null) return false;
        if(this.getClass() != obj.getClass()) return false;
        MagicSquare otherObject = (MagicSquare)obj;
        
        if(otherObject.isMagic() && this.isMagic() && otherObject.checkRowSums() == this.checkRowSums()
           && otherObject.checkColumnSums() == this.checkColumnSums())
        {
            return true;
        }
        else
        {
            return false;
        }
    }
}

```

I think the problem is in my MagicSquare class' doMagic() method. My teacher sent us a flowchart but I sometimes disagree with it but the code above is what my teacher told us to do via the flowchart. (unless I misunderstood the flowchart or something)

Any input would be greatly appreciated as always!
Thanks in advance!

P.S.
[http://en.wikipedia.org/wiki/Magic_square](http://en.wikipedia.org/wiki/Magic_square)

---

### Post by LKjell on 2010-04-02
Ok here is the algorithm remember that you need to understand and know how to implement this and probably need to include where you get it. Otherwise you might be flagged as a cheater! Use at your own risk. 

```
        while(k<=order*order)
        {
		if(msArray[row][column] == 0) {
			System.out.println(row + " " + column+ " :" +k);
			msArray[row][column] = k++;

			if(column == order -1 && row == 0) {
				row++;
				continue;
			}

			if(column < order-1) {
				column++;
			} else {
				column = 0;
			}

			if(row == 0) {
				row = order -1;
			} else {
				row--;
			}

		} else {
			row = row + 2;
			column--;
			System.out.println(row + " " + column+ " :" +k);
			msArray[row][column] = k++;

			if(column < order-1) {
				column++;
			} else {
				column = 0;
			}

			if(row == 0) {
				row = order -1;
			} else {
				row--;
			}
		}
        }
```

---

### Post by s3a on 2010-04-02
Thanks for your answer but could you illustrate what you did a little bit so that I can understand what's going on? I didn't know what the continue; statement was but I read about and I'm glad you showed it to me but as for the rest could you just please explain a little bit? Also, what was I doing wrong in my version?

---

### Post by cariboo on 2010-04-02
Please don't ask the members to do your homework for you. This thread is closed.

From the forum code of Conduct:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

