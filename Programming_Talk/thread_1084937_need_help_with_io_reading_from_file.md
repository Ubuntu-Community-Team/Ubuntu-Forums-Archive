---
title: "need help with io reading from file"
date: 2009-03-02
forum: Programming Talk
---

### Post by Mia_tech on 2009-03-02
guys, I'm trying to read from a file and print out number of letters, words, and lines.... the lines part is pretty easy, but I'm having problems with the words and letters.. here's the content of the file

this is a test file
for printing out the
number of letters
words and lines

here's the code I have so far

```
import java.io.*;
import java.util.*;
public class FileCounter {
    String words = "";
    int ch = 0;
    public FileCounter(String words)
    {
        this.words = words;
    }
    public FileCounter(int ch)
    {
        this.ch = ch;
    }
    public String getWrods()
    {
        return words;
    }
    public static void main(String [] args)
    {
        ArrayList<FileCounter> data = new ArrayList<FileCounter>();
        ArrayList<FileCounter> dataN = new ArrayList<FileCounter>();
        try
        {
          FileReader file = new FileReader("filecount.txt");
          BufferedReader br = new BufferedReader(file);
          String line = "";
          int counter = 0;
          String words = "";
          int ch = 0;
          int i = 0;

          while((line = br.readLine()) != null)
          {
              counter++;
              for(i = 0; i < line.length(); i++)
              {
                  words += line.substring(i, i+1);

              }
             data.add(new FileCounter(words));
             dataN.add(new FileCounter(i));

          }
          System.out.println(counter);
          System.out.println(i);
          
          for(i = 0; i < data.size(); i++)
          {
             System.out.println(data.get(i).getWrods());
          }
          
        }
        catch(Exception e)
        {
            System.out.println(e);
        }

    }
}

```

---

### Post by cabalas on 2009-03-02
Counting the number of characters in the file is easy you just do sum of the length of the lines that you have read in.  

As for the number of words a naive way of doing it would be just to split each line on spaces and count the size of the array that results, granted it won't catch everything but it is a place for you to start from.

---

### Post by Can+~ on 2009-03-02
> **cabalas said:**
> Counting the number of characters in the file is easy you just do sum of the length of the lines that you have read in.  

As for the number of words a naive way of doing it would be just to split each line on spaces and count the size of the array that results, granted it won't catch everything but it is a place for you to start from.

Or pretty much count the amount of spaces, ignoring multiple spaces like "word<space><space><space>word". Since:

word1 word2 word3 => **3 words, 2 spaces.**
word1 word2 word3 ... wordn => **n words, n-1 spaces**

Splitting into arrays is unnecessary.

---

### Post by cabalas on 2009-03-02
> **Can+~ said:**
> Or pretty much count the amount of spaces, ignoring multiple spaces like "word<space><space><space>word". Since:

word1 word2 word3 => **3 words, 2 spaces.**
word1 word2 word3 ... wordn => **n words, n-1 spaces**

Splitting into arrays is unnecessary.

Good point, though (in a desperate attempt to make it seem like this was the reason for splitting all along :P) if he wanted to make a count of all the unique words and the total number of words (which seems like a logical next step) splitting would be the way to go.

---

### Post by Mia_tech on 2009-03-03
guys, I decided to modify the text file and make it simpler, I guess if I'm able to see the code work for a simple file, I could move on to something more difficult.... following the advise to count spaces instead of words, I kind of have it working... but the spaces counting portion is too complicated and is not reporting the right amount of words... I appreciate any suggestion
text file

Lebron James
Koby Bryant
Michael Jordan
Larry Bird

java code

```
import java.io.*;
public class FileCounter {
        
    public static void main(String [] args)
    {
        
        try
        {
            FileReader file = new FileReader("filecount.txt");
            BufferedReader br = new BufferedReader(file);
            String line = "";
            int counter = 0;
            String first = "";
            String last = "";
            int words = 0;
            int cha = 0;
            int space = line.indexOf(" ")+1;
            while((line = br.readLine()) != null)
            {
                //counting lines
                counter++;
                //counting spaces instead of words
                for(int i = 0; i < line.length(); i++)
                {
                    if(line.substring(i, i+1).equals(" "))
                    {
                        words++;
                    }
                }
                //counting characters
                cha += line.length();
             }
            
                System.out.println("Lines: "+counter);
                System.out.println("Characters: "+cha);
                System.out.println("Words: "+words);

            
        }
        catch(Exception e)
        {
            System.out.println(e);
        }
          
    }
}


```

---

### Post by geirha on 2009-03-03
Your current approach is counting the spaces between the words only. And if there are two words on a line, there are only 1 space on that line ...

Try the split approach cabalas mentioned; [http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split(java.lang.String)](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split(java.lang.String)). Slightly more intuitive I think.

```

String[] s = "a word here and there".split(" "); // See what value s.length has after this.

```

It'll work fine as long as there are only one space in between the words. To handle more spaces, either change the regex you pass to split, or loop through the String-array and check for empty strings.

---

### Post by cabalas on 2009-03-03
While the splitting method is more intuitive it is more costly than just iterating through the loop. I would try replacing the for loop with something similar to the following (note this is off the top of my head and untested so it may not work.)

[PHP]
int spaces = 0;
for(char ch : line.trim()) {
  if(ch == ' ')
    spaces++;
}

if(spaces > 0)
  words = space + 1;
[/PHP]

---

### Post by Can+~ on 2009-03-03
Since I don't know Java, here's the example on python.

The method I use is pretty much using an auxiliar boolean value, that toggles each time a sequence of spaces is found:

(Python 2.5.2)
[PHP]#!/usr/bin/python

#Sample text for testing
sample = "this is      space and 		tabulations"

#Initial variables
word_count = 0
word_flag = False

for character in sample:
	
	#If it's an empty space (space or \t)...
	if character in " \t":
		#We just ended a word then, swap to false.
		word_flag = False

	#If not, and the last word was not an space
	elif not word_flag:
		#Then we are starting a new word, count it.
		word_count += 1
		word_flag = True

	print character, word_flag


print "count:",word_count[/PHP]

The result of this is:

```
t True
h True
i True
s True
  False
i True
s True
  False
  False
  False
  False
  False
  False
s True
p True
a True
c True
e True
  False
a True
n True
d True
  False
	False
	False
t True
a True
b True
u True
l True
a True
t True
i True
o True
n True
s True
count: 5

```

I insist with my first opinion, you don't need to split into arrays or use regular expressions when the solution can be easily attainable just by thinking with logic. The problem should be seen as a change of states, you are actually not counting the "spaces" but the change from character to space, so it's about creating a situation where a boolean changes from true to false (or viceversa) and counting each time it happens.

With this method you don't even need to use strip (I think java is trim()).

---

### Post by Mia_tech on 2009-03-03
guys, thanks for all the help especially to geirha... I think that the String.split(" "); was the best approach... here's the final code

```
import java.io.*;
public class FileCounter {
        
    public static void main(String [] args)
    {
        
        try
        {
            FileReader file = new FileReader("filecount.txt");
            BufferedReader br = new BufferedReader(file);
            String line = "";
            int lCounter = 0;
            int wCounter = 0;
            int chaCounter = 0;
            String s[];
         
            while((line = br.readLine()) != null)
            {
                //counting lines
                lCounter++;
                //counting spaces instead of words
                s = line.split(" ");
                wCounter += s.length;
                //counting characters
                chaCounter += line.length();
             }
            
                System.out.println("Lines: "+lCounter);
                System.out.println("Characters: "+chaCounter);
                System.out.println("Words: "+wCounter);

            
        }
        catch(Exception e)
        {
            System.out.println(e);
        }
          
    }
}
```

---

