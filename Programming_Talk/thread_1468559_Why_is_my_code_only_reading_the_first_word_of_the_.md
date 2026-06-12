---
title: "Why is my code only reading the first word of the input line?"
date: 2010-05-01
forum: Programming Talk
---

### Post by s3a on 2010-05-01
_Here is the driver code:_
```
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Main
{
    public static void main(String[] args) throws FileNotFoundException
    {
        Scanner keyboardScan = new Scanner(System.in);
        System.out.print("Enter file name: ");
        String filename = keyboardScan.next();
        Index index = new Index(filename);
        System.out.println(index);
    }
}
```

_Here is my WordToken class:_
```
import java.util.ArrayList;

public class WordToken
{
    // the following is from page 2

    String word;
    // ArrayList is a frequently used data structure.
    // Appropriate here because we append line numbers to the end of the list.
    ArrayList<Integer> lineNumberList = new ArrayList<Integer>();
    // other possible data structures
    // LinkedList<Integer> lineNumList = new LinkedList<Integer>();
    // TreeSet<Integer> lineNumList = new TreeSet<Integer>(); // Does not allow duplicates
    // Maintains elements in sorted order.
    public WordToken(String word, int lineNumber)
    {
        this.word = word;
        lineNumberList.add(lineNumber);
    }
    public void addLineNum(int lineNumber)
    {
        lineNumberList.add(lineNumber);
    }
    public String toString()
    {// is the following line temp or not?
       return word + lineNumberList;
    }
    public int compareWords(String scannedWord, boolean found)
    {
    // implement this
        return -1; //temp
    }
    // the above is from page 2
}
```

_Here is my Index class:_
```
import java.io.File;
import java.io.FileNotFoundException;
import java.util.LinkedList;
import java.util.Scanner;

public class Index
{
    // LinkedList is appropriate here because, to keep the words sorted, insertions may be made at any position in the list.
    String scannedWord;
    Scanner lineScan;
    
    private LinkedList<WordToken> wordTokenList = new LinkedList<WordToken>();
    {
        // other possible data structures:ArrayList, TreeSet
    }

//    public boolean exists(String scannedWord, int lineNumber)
//    {
//        boolean found = false;
//        for(int counter = 0; counter < wordTokenList.size(); counter++)
//        {
//            // Avoid creating duplicate words
//
//            if(scannedWord.compareToIgnoreCase(wordTokenList.get(counter).word) == 0)
//            {
//                //wordTokenList.get(counter).addLineNum(lineNumber);
//                found = true;
//                break;
//            }
//
//        }
//    }

    public Index(String fileName) throws FileNotFoundException
    {
            // implement this using the code given on page 1
            Scanner fileScan = new Scanner(new File(fileName));
            int lineNumber = 0;
            
            while(fileScan.hasNext()) // while there is a next line
            {
                ++lineNumber;
                String line = fileScan.nextLine();
                //System.out.println("Line " + lineNumber + "  " + line); // For testing purposes?
                lineScan = new Scanner(line);
                lineScan.useDelimiter("\\W+"); // extract words // stops at punctuation I think
                
                
                while(lineScan.hasNext()) // while there is a next word
                {
                    scannedWord = lineScan.next(); // assigns the word
                    add(scannedWord, lineNumber); // I added this after commenting all below

//                    boolean found = false;
//                    if(wordTokenList.isEmpty())
//                    {
//                        wordTokenList.add(new WordToken(scannedWord, lineNumber));
//                    }
//                    //System.out.println("word " + word + " on line   " + lineNumber); // For testing purposes?
//                    else // is scannedWord in the list already?
//                    {
//                        for(int counter = 0; counter < wordTokenList.size(); counter++)
//                        {
//                            // Avoid creating duplicate words
//
//                            if(scannedWord.compareToIgnoreCase(wordTokenList.get(counter).word) == 0)
//                            {
//                                wordTokenList.get(counter).addLineNum(lineNumber);
//                                found = true;
//                                break;
//                            }
//                        }
//                        if(!found) // Avoid creating duplicate words
//                        {
//                            int position = -1;
//                            for(int counter = 0; counter < wordTokenList.size(); counter++)
//                            {
//                                if(scannedWord.compareToIgnoreCase(wordTokenList.get(counter).word) > 0)
//                                {
//                                    position = counter - 1; // isn't this supposed to be ==> position = counter; <== ?
//                                    break;
//                                }
//                            }
//                            if(position != -1)
//                            {
//                                wordTokenList.add(position, new WordToken(scannedWord, lineNumber));
//                            }
//                        }
//                    }
                }
            }
    }

    public void add(String scannedWord, int lineNumber)
    {
        
                    // If wordTokenList is empty, add a new WordToken(word, lineNumber) to it. Otherwise, if word is already in the list, add lineNumber to its number list Otherwise, determine where word should be alphabetically placed in wordTokenList and add it at that position.
                    boolean found = false;
                    if(wordTokenList.isEmpty())
                    {
                        wordTokenList.add(new WordToken(scannedWord, lineNumber));
                    }
                    else // is scannedWord in the list already?
                    {
                        for(int counter = 0; counter < wordTokenList.size(); counter++)
                        {
                            // Avoid creating duplicate words

                            if(scannedWord.compareToIgnoreCase(wordTokenList.get(counter).word) == 0)
                            {
                                wordTokenList.get(counter).addLineNum(lineNumber);
                                found = true;
                                break;
                            }
                        }
                        if(!found) // Avoid creating duplicate words
                        {
                            int position = -1;
                            for(int counter = 0; counter < wordTokenList.size(); counter++)
                            {
                                if(scannedWord.compareToIgnoreCase(wordTokenList.get(counter).word) > 0)
                                {
                                    position = counter - 1; // isn't this supposed to be ==> position = counter; <== ?
                                    break;
                                }
                            }
                            if(position != -1)
                            {
                                wordTokenList.add(position, new WordToken(scannedWord, lineNumber));
                            }
                        }
                    }
    }
    
    public String toString()
    {
        return wordTokenList.toString();
    }
}
```

_Here is the input text file:_
> "Look at me!
Look at me!
Look at me NOW!
It is fun to have fun
But you have to know how."
-- Dr. Seuss (The Cat in the Hat)


_Here is what the output should be:_
> at, 1, 2, 3

But, 5

Cat, 6

Dr, 6

fun, 4, 4

Hat, 6

have, 4, 5

how, 5

in, 6

is, 4

It, 4

know, 5

Look, 1, 2, 3

me, 1, 2, 3

NOW, 3

Seuss, 6

The, 6, 6

to, 4, 5

you, 5



_Here is my output:_
> Enter file name: 
in.txt
[Look[1, 2, 3]]

I don't understand why it is just giving me the first word since I have the while loops. Also, my teacher wants us to call methods instead of implementing all the code inside one method but having the code already structured the way it is, it is kind of complicated for me to use the compareWords method in the WordToken class to satisfy the uses of the Index class especially with the boolean found value involved. (The compareWords method is supposed to compare two String objects (that are case-insensitive) and is supposed to return whether the two String objects are equal or not.)

Any help would be GREATLY appreciated!
Thanks in advance!

Edit: The point of this *if(scannedWord.compareToIgnoreCase(wordTokenList.get(counter).word) > 0)* was to place the words alphabetically and I think the problem might be with *position = counter - 1;*. I also noticed that changing the arithmetic after the counter variable outputs more than just "Look". **Having relooked at it, I think it should be position = counter + 1; which gives me more words but not in alphabetical order and not all words are showing.**

---

### Post by dwhitney67 on 2010-05-01
For displaying your output, it would seem to me that you need a wee bit more code than what you have here:
```

public String toString()
{
    return wordTokenList.toString();
}

```
System.out.println() is calling this function when you attempt to print 'index'.


P.S.  It has been a while since I perused the Java API documentation, but I recall that there is a Hash Map container.  If so, you could define the key to be that of a String, and the value to be a Vector of integers.  It would speed up your code considerably, as opposed to searching through an ArrayList.

---

### Post by s3a on 2010-05-04
Well actually my code had some other logical error which I finally solved with the help of my teacher but could you please tell me how to modify my overrided toString() method:

public String toString()
    {
        return wordTokenList.toString();
    }

so that instead of returning:
```
[at[1, 2, 3], But[5], Cat[6], Dr[6], fun[4], Hat[6], have[4, 5], how[5], in[6], is[4], It[4], know[5], Look[1, 2, 3], me[1, 2, 3], NOW[3], Seuss[6], The[6], to[4, 5], you[5]]
```

it returns:
```
at, 1, 2, 3 
But, 5 
Cat, 6 
Dr, 6 
fun, 4, 4 
Hat, 6 
have, 4, 5 
how, 5 
in, 6 
is, 4 
It, 4 
know, 5 
Look, 1, 2, 3 
me, 1, 2, 3 
NOW, 3 
Seuss, 6 
The, 6, 6 
to, 4, 5 
you, 5 

```

The above is how my output is supposed to be (I am not talking just talking about the formatting). I am talking about the repeated line numbers if a word appears on a line more than once. I rather have it not repeat. That's not my problem. I took care of that. I just need to know how to have it in that comma form and not the default toString [] stuff. I'd also like to be able to have it jump to the next line for each word as opposed to having all the words horizontally stacked together when printed on the screen.

---

### Post by dwhitney67 on 2010-05-04
Iterate through each element of the list (ie wordTokenList).

---

### Post by s3a on 2010-05-04
I modified the toString() method of the Index class as follows:

```
public String toString()
    {
        //return wordTokenList.toString(); // this is good but im attempting to use an interator as follows
        
        ListIterator<WordToken> iterator = wordTokenList.listIterator();
        String str = "";
        
        while(iterator.hasNext())
        {
            str += iterator.next() + "\n";
        }
        return str;        
    }
```

However, the output hasn't changed one bit. It's still:

```
[at[1, 2, 3], But[5], Cat[6], Dr[6], fun[4], Hat[6], have[4, 5], how[5], in[6], is[4], It[4], know[5], Look[1, 2, 3], me[1, 2, 3], NOW[3], Seuss[6], The[6], to[4, 5], you[5]]
```

What am I doing wrong?

---

### Post by dwhitney67 on 2010-05-05
Maybe you just neglected to recompile your code?

I really don't know; I have not seen your latest code (with the bug fix), so I took the time to write my own, which produces the type of results you seek.

For WordToken.java:
```

import java.util.ArrayList;
import java.util.ListIterator;

public class WordToken
{
   private String             myWord;
   private ArrayList<Integer> myLineNumbers = new ArrayList<Integer>();

   public WordToken(String word, int lineNumber)
   {
      myWord = word;
      myLineNumbers.add(lineNumber);
   }

   public void addLineNumber(int lineNumber)
   {
      myLineNumbers.add(lineNumber);
   }

   public String getWord()
   {
      return myWord;
   }

   public String toString()
   {
      String str = myWord;

      ListIterator<Integer> it = myLineNumbers.listIterator();

      while (it.hasNext())
      {
         str += ", " + it.next();
      }

      return str;
   }

   public static void main(String[] args)
   {
      WordToken wt = new WordToken("foo", 1);
      wt.addLineNumber(2);
      wt.addLineNumber(3);
      wt.addLineNumber(4);

      System.out.println("word token = " + wt.toString());
   }
}

```

For Index.java:
```

import java.util.LinkedList;
import java.util.ListIterator;


public class Index
{
   private LinkedList<WordToken> myWordTokens = new LinkedList<WordToken>();

   public Index()
   {
   }

   public void addToken(String word, int lineNumber)
   {
      // check if list is empty; if so, then obviously a new word token
      if (myWordTokens.isEmpty())
      {
         myWordTokens.add(new WordToken(word, lineNumber));
      }
      else
      {
         // need to search if the word token already exists
         ListIterator<WordToken> it = myWordTokens.listIterator();
         WordToken               wt = null;
         boolean                 found = false;
         int                     pos = 0;

         while (it.hasNext())
         {
            wt = it.next();

            int cmp = word.compareToIgnoreCase(wt.getWord());

            if (cmp == 0)
            {
               found = true;
               break;
            }
            else if (cmp > 0)
            {
               ++pos;
            }
         }

         if (!found)
         {
            myWordTokens.add(pos, new WordToken(word, lineNumber));
         }
         else
         {
            wt.addLineNumber(lineNumber);
         }
      }
   }

   public String toString()
   {
      ListIterator<WordToken> it = myWordTokens.listIterator();
      String str = "";

      while (it.hasNext())
      {
         WordToken wt = it.next();

         str += wt.toString() + "\n";
      }

      return str;
   }

   public static void main(String[] args)
   {
      Index index = new Index();

      index.addToken("Dopey",  1);
      index.addToken("Sneezy", 2);
      index.addToken("Dopey",  3);
      index.addToken("Happy",  5);
      index.addToken("Doc",    6);
      index.addToken("Grumpy", 7);
      index.addToken("Grumpy", 8);
      index.addToken("Grumpy", 9);
      index.addToken("Doc",    10);
      index.addToken("Sneezy", 11);
      index.addToken("Happy",  12);

      System.out.println(index.toString());
   }
}

```

EDIT:  The issue described below has been corrected with an update to the code.
---------------------------------------------------------
P.S.  Actually, my results are a bit off.  The output is not sorted.  The insertion of a new WordToken into the LinkedList needs to be done with more care.

---

### Post by s3a on 2010-05-07
It somehow did not compile properly and I got it working now, thanks.

---

