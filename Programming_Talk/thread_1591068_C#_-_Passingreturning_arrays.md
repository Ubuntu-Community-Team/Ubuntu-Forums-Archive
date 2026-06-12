---
title: "C# - Passing/returning arrays"
date: 2010-10-08
forum: Programming Talk
---

### Post by lazypeterson on 2010-10-08
Alright, basically I'm making a program that has bubble sort/selection sort methods for sorting a .txt file with 20,000 numbers. It's going alright so far, but I cannot figure out why 

right at:

```

            long[] mySortedArray = new long[ARRAY_SIZE];
            mySortedArray = BubbleSort(myUnsortedArray);
```

it's saying that I cannot implicitly convert a 'long' to a 'long[]'. I'm stumped because mySortedArray is definitely declared declared as an array, and I don't see why the BubbleSort method cannot go through with the procedure.

Here's all of the code:

```
using System;

namespace Lab5 {
    class Program {
        
        

        static void Main(string[] args) {

            System.IO.StreamReader inFile = new System.IO.StreamReader("sort_me_20k.txt");
            const int ARRAY_SIZE = 20000;
            long [] myUnsortedArray= new long[ARRAY_SIZE];
            //TODO: Declare an array of size ARRAY_SIZE of the appropriate type (these are 64-bit integers ...)
            // CHECK

            string s;

            for (int i = 0; i < ARRAY_SIZE; i++) {
                s = inFile.ReadLine(); // Reads a line of the file, and stores in s
                long val = long.Parse(s);
                myUnsortedArray[i] = val; // array with the 20,000 numbers


                //TODO: Convert the string to the appropriate type, and store in the array
                // CHECK
            }
            inFile.Close();

            // Measure how long it takes to sort
            DateTime startTime = DateTime.Now;

            //
            //TODO: Sort the array:
            
            long[] mySortedArray = new long[ARRAY_SIZE];
            mySortedArray = BubbleSort(myUnsortedArray);
            //

            // Stop measuring running time
            DateTime endTime = DateTime.Now;
            TimeSpan duration = endTime - startTime;
            Console.WriteLine("Sorting took " + duration.TotalSeconds + " seconds.");

            // Output the file:
            System.IO.StreamWriter outFile = new System.IO.StreamWriter("out.txt");
            for (int i = 0; i < ARRAY_SIZE; i++) {
                outFile.WriteLine(mySortedArray[i]);
            }
            outFile.Close();

            Console.ReadKey();
        }

//TODO: change "TYPE" to the correct type, fill in the functions as appropriate

// I've reported my sort times. Of course, this will vary depending on the power of
// your machine, how many programs you have open, and many other factors.

        static long BubbleSort(long[] x) {   // My version took about 4.05 sec @ 20k items
            //To clone the array (so as to make this sort not desctructive)
            long [] mySortedArray = x.Clone() as long[];  // The "as" keyword is another way to "cast"

            bool sorted = false; 
            while (sorted = false) 
            {
                sorted = true;
                int i=0;
                i++;
                int other = 0; 

                for (i = 0; i < x.Length - other; i++) { 

                if (mySortedArray[i] > mySortedArray[i + 1])
                {
                    long temp1 = mySortedArray[i];
                    long temp2 = mySortedArray[i + 1];
                    mySortedArray[i] = temp2;
                    mySortedArray[i + 1] = temp1;
                    sorted = false;
                }
            }   

        }
            return mySortedArray;
    }

```

Any help would be greatly appreciated. Thanks!

---

### Post by Some Penguin on 2010-10-08
"static long BubbleSort(long[] x) "

---

### Post by lazypeterson on 2010-10-08
Oh jesus. I feel retarded for having wasted an entire thread on such a careless mistake. 

However, it would have taken me an embarrassingly longer time than I've already spent trying to figure this out and for that I thank you very much.

---

