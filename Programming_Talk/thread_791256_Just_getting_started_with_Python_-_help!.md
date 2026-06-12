---
title: "Just getting started with Python - help!"
date: 2008-05-12
forum: Programming Talk
---

### Post by drunkmatador on 2008-05-12
I'm just getting started using Python, after never really learning any programming languages, and am trying to get the basics now. I've looked at a few tutorials but can't find out exactly what I'm looking for.

I am writing a simple script that will take one letter input, and then tell you the word in the Military Alphabet (the one here in the states, anyways) that it stands for.

This would require a raw_input command, which I understand, and also some kind of "if then" statement, which I don't know how to do.

The way I imagine it is something like.. well "letter" would be the variable previously set by raw_input.. so if letter=A then print "Alpha"

or is it not going to be that simple?

Any help appreciated! Thanks.

---

### Post by ConMan318 on 2008-05-12
You could do something like:

```

array = {'A': 'Alpha', 'B': 'Bravo'}
print array[raw_input("Enter a letter:").upper]

```

This makes use of the dictionary data type rather than using 26 if-thens.  If you wanted to make it take in more than one input you'd just need to add in a loop, and obviously you'd have to finish typing out the letters and their military equivalents.

EDIT: Seeing as you don't yet know if-then statements this might seem a little complex.  To expand/simplify it a bit:
```

array = {'A': 'Alpha', 'B': 'Bravo'}
letter = raw_input("Enter a letter:").upper   # sets the value of 'letter' to the user input
print array[letter]                                # prints the dictionary value that corresponds to 'letter'

```
The original code just shortened it by skipping the step of assigning a variable; I'd imagine this one is easier to understand.

---

### Post by LaRoza on 2008-05-12
Here:

[php]
#!/usr/bin/python
import sys

mil = {'A':  'Alpha',
'B':  'Bravo',
'C':  'Charlie',
'D':  'Delta',
'E':  'Echo',
'F':  'Foxtrot',
'G':  'Golf',
'H':  'Hotel',
'I':  'India',
'J':  'Juliet',
'K':  'Kilo',
'L':  'Lima',
'M':  'Mike',
'N':  'November',
'O':  'Oscar',
'P':  'Papa',
'Q':  'Quebec',
'R':  'Romeo',
'S':  'Sierra',
'T':  'Tango',
'U':  'Uniform',
'V':  'Victor',
'W':  'Whiskey',
'X':  'X-Ray',
'Y':  'Yankee',
'Z':  'Zulu',
'1':  'Wun',
'2':  'Too',
'3':  'Tree',
'4':  'Fower',
'5':  'Fife',
'6':  'Siks',
'7':  'Seven',
'8':  'Ait',
'9':  'Niner',
'0':  'Zeero',
}

if len(sys.argv) == 1:
    words = raw_input("Enter a alphanumeric string: ")
else:
    words = sys.argv[1:]

for word in words:
    for letter in word:
        try: 
            print mil[letter.upper()]
        except KeyError:
            print "n/a"
[/php]

---

### Post by ConMan318 on 2008-05-12
^ Ooh I didn't know the toUpper function in python, glad you posted that.

And to threadstarter, check out [http://en.wikibooks.org/wiki/Python_Programming](http://en.wikibooks.org/wiki/Python_Programming) for an easy introduction to python.

---

### Post by LaRoza on 2008-05-12
> **ConMan318 said:**
> ^ Ooh I didn't know the toUpper function in python, glad you posted that.

And to threadstarter, check out [http://en.wikibooks.org/wiki/Python_Programming](http://en.wikibooks.org/wiki/Python_Programming) for an easy introduction to python.

Just upper().

I also added some more function to it. Not only does it have the prompt, it will convert any command line arguments to it if they exist.

```

~$./alpha.py LaRoza
Lima
Alpha
Romeo
Oscar
Zulu
Alpha
~$

```

---

### Post by ConMan318 on 2008-05-12
I kow it's just upper(), I was referring to the C equivalent that I am used to.  How can you get a program to take in a command line argument?  I've seen it done so much that I never thought about it much, but I've never tried to do it.

---

### Post by LaRoza on 2008-05-12
> **ConMan318 said:**
> I kow it's just upper(), I was referring to the C equivalent that I am used to.  How can you get a program to take in a command line argument?  I've seen it done so much that I never thought about it much, but I've never tried to do it.

In Python:

[php]
import sys
#sys.argv is the array of command line arguments. The name of the program is sys.argv[0]
for arg in sys.argv:
    print arg
[/php]

In C:
[php]
#include <stdio.h>
int main(int argc,char ** argv)
{
    /* argc is argument count, and argv is argument vector. 
    They don't have to be named this but they always are.*/
    int i = 0;
    do
    {
        printf("Argument: %d is %s\n",i,argv[i]);
    }while (++i<argc);
    return 0;
}
[/php]

---

### Post by ConMan318 on 2008-05-12
Ah, that will certainly come in handy.  Thanks!

---

### Post by LaRoza on 2008-05-12
Perhaps I should explain this a bit more...

The first two lines are the shebang and importing sys which is needed to get command line arguments.

The next bunch of lines is a dictionary. I copied the list from a site (quickly googled) and kept the list format and added quotes and the ','.

See comments of the rest of the code.
[php]
#!/usr/bin/python
import sys

mil = {'A':  'Alpha',\
'B':  'Bravo',\
'C':  'Charlie',\
'D':  'Delta',\
'E':  'Echo',\
'F':  'Foxtrot',\
'G':  'Golf',\
'H':  'Hotel',\
'I':  'India',\
'J':  'Juliet',\
'K':  'Kilo',\
'L':  'Lima',\
'M':  'Mike',\
'N':  'November',\
'O':  'Oscar',\
'P':  'Papa',\
'Q':  'Quebec',\
'R':  'Romeo',\
'S':  'Sierra',\
'T':  'Tango',\
'U':  'Uniform',\
'V':  'Victor',\
'W':  'Whiskey',\
'X':  'X-Ray',\
'Y':  'Yankee',\
'Z':  'Zulu',\
'1':  'Wun',\
'2':  'Too',\
'3':  'Tree',\
'4':  'Fower',\
'5':  'Fife',\
'6':  'Siks',\
'7':  'Seven',\
'8':  'Ait',\
'9':  'Niner',\
'0':  'Zeero',\
}

# if there are no command line arguments the words are taken in interactively
## Note: The first argument is the program name, 
## so the length of this is always positive and greater than 0
# else the words equal everything but the first command line argument.
if len(sys.argv) == 1:
    words = raw_input("Enter a alphanumeric string: ")
else:
    words = sys.argv[1:]

# For each value in words, for the command line args, this is each individual argument
# For the interactive words, it is one big word. The spaces will be "n/a", but you can change that
# For each letter in each word, print the associated key. 
# The keys of the dictionary are capitalized, so the letters are converted to uppercase.
# The try, except blocks prevent characters not listed from halting the program. For unrecognized characters, "n/a" is printed.
for word in words:
    for letter in word:
        try: 
            print mil[letter.upper()]
        except KeyError:
            print "n/a"
[/php]

---

### Post by Wybiral on 2008-05-12
> **LaRoza said:**
> added quotes and the ",\". The slashes allow the dictionary to span many lines, otherwise it would have to be all one line.

Python doesn't mind if you put your list or dick on multiple lines.

---

### Post by LaRoza on 2008-05-12
> **Wybiral said:**
> Python doesn't mind if you put your list or dick on multiple lines.

It did mind the lack of ',' and I did it all in one move so it didn't add typing. Editted post to reflect reality. Thanks.

---

### Post by Wybiral on 2008-05-12
> **LaRoza said:**
> It did mind the lack of ',' and I did it all in one move so it didn't add typing. Editted post to reflect reality. Thanks.

Well, it is a shame to restrict such a big, pythonic, dic_t_ like that.

---

### Post by LaRoza on 2008-05-12
> **Wybiral said:**
> Well, it is a shame to restrict such a big, pythonic, **dict** like that.

A freudian slip? That is some typo you have there :lol:

You might want to fix it.

---

### Post by drunkmatador on 2008-05-12
Thanks a bunch. Still pretty confused on what all your code means though.. seems this is a little more complicated of a project than I thought. If you'd like to go into detail a little more, or simplify it that would be great. But if not, you could maybe link me to a better starting place. :)

I really just want to learn to program so that I can make rpg games eventually.

---

### Post by LaRoza on 2008-05-12
> **drunkmatador said:**
> Thanks a bunch. Still pretty confused on what all your code means though.. seems this is a little more complicated of a project than I thought. If you'd like to go into detail a little more, or simplify it that would be great. But if not, you could maybe link me to a better starting place. :)

I really just want to learn to program so that I can make rpg games eventually.

My script is simple in operation. It defines a dictionary, which is like a list (array) but uses keys instead of numeric indices. So:

```

capitals = {"USA":"Washington D.C.","France":"Paris","England":"London"}

```

To get the captital of "USA", you just reference:
```

captials["USA"]

```

So, the letter or number in my script is a key for its corresponding value.

Next, I added the functionality to be useful in a way I would use it. You don't need all that. The first code snippets are simpler, mine works similiarly to them, but allows one to use a command line argument.

So if the script is named "alpha.py" and is executable:

Command line arguments:
```

~$./alpha.py "Testing"
Tango
Echo
Sierra
Tango
India
November
Golf
~$

```

Interactive:
```

~$./alpha.py 
Enter a alphanumeric string: testing
Tango
Echo
Sierra
Tango
India
November
Golf
~$

```

Your original description could work also, but would be much longer. I didn't feel like doing every letter, but it follows the same pattern:

```

#!/usr/bin/python

letter = raw_input("Enter an alphanumeric characters: ").upper()
if letter == 'A':
    print "Alpha"
elif letter == 'B':
    print "Beta"
....
else:
    print "Not known"

```

---

### Post by TheIrishGuy on 2008-05-12
[Beginning Python-From Novice To Professional 2005]("http://books.feeditout.com/download.php?book=QmVnaW5uaW5nX1B5dGhvbi1Gcm9tX05vdmljZV9Ub19Qcm9mZXNzaW9uYWxfMjAwNS5wZGY=")

---

### Post by pmasiar on 2008-05-12
OP: see wiki in my sig - I collect links for Python beginners. Sticky FAQ has even more links (less focused on beginners IMHO)

---

### Post by drunkmatador on 2008-05-12
Thank you for the tutorials, both of you! I will check all of them out today and see how far that I can get.

LaRoza you are extremely helpful, more than I expected. Thank you. A couple easy questions, if I wanted to print something that is referenced in the dictionary, would it be like "print captials["USA"]"? Haha I know, I am an absolute beginner.

---

### Post by LaRoza on 2008-05-12
> **drunkmatador said:**
> Thank you for the tutorials, both of you! I will check all of them out today and see how far that I can get.

LaRoza you are extremely helpful, more than I expected. Thank you. A couple easy questions, if I wanted to print something that is referenced in the dictionary, would it be like "print captials["USA"]"? Haha I know, I am an absolute beginner.

Yes, although "capitals" would have to be spelled correctly.

---

### Post by drunkmatador on 2008-05-12
Oh haha. Didn't realize you had spelled it wrong when I copy and pasted. :)

---

### Post by LaRoza on 2008-05-12
> **drunkmatador said:**
> Oh haha. Didn't realize you had spelled it wrong when I copy and pasted. :)

Oh, I see I misspelled it. You were right, it would be the way it is.

---

