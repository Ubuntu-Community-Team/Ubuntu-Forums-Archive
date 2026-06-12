---
title: "How do I create a Wordlist From a Wordlist? Which Wordlist Generator?"
date: 2008-10-18
forum: Programming Talk
---

### Post by damlays on 2008-10-18
I am not a programmer, but if it existing you would know about it..


I have a wordlist. Let's say "names" and it goes like (john, tom, william..)
and I want to create an other new list by using this list, like;

--------------------
john1
john2
....
john9999
tom1
...
...
tom9999
...
--------------------

This is the most simple manuplation that I want to make to the first list but according to the possible needs which will appear in future, I would like to make some other manuplations and create new lists like;

---------------------
(Capitalization)
John1
...

----OR------

(Putting something inside words)
jAohn
tAom
wAilliam
...

----OR------

(Combining words within other words in an other wordlist)
Let's say I have a second wordlist like (TABLE, DESK, ...)

and new (third) wordlist should be like;

johnTABLE
johnDESK
tomTABLE
tomDESK
williamTABLE
williamDESK
------------------

So I hope I can make it understandable what I am looking for. I don't know if classic programs can do it like John the Ripper, etc.. But I didn't see any example in anywhere that show they can do it. Examples that I saw were always about creating some wordlists for brute forse attack.

SO, my main question is : Is there a way (software) which allows me to generate wordlists by making this kind of intelligent choices?

---

### Post by geirha on 2008-10-18
Sounds like an easy task to do in python. Check LaRoza's sticky on how to learn programming for links to python tutorials.

---

### Post by nvteighen on 2008-10-18
Possible, of course. There might even someone writing something like this out there...

Hard or easy? It depends on what programming language you choose for this. You're not a programmer, so I won't enter into technical jargon, but basically you can organize programming languages by studying its distance to the computer's elements: there are 1) those that are give you direct access to the memory, processor and devices are designed to control the computer and set it up for doing tasks ("low-level languages") and 2), in the other side, languages that, after you have the computer set up, give you concepts not-related to the computer itself to do the tasks you want ("high-level languages"). Obviously, this is a continuum and you have languages higher/lower level than other (some also talk of "middle-level languages").

But, whatever you choose you'll have to pay a trade-off. If you go for low-level, you gain control over the computer's parts (and therefore, e.g. speed or write a new operating system), but lose simplicity to write even simple programs that are intended to do some process that's not related to a computer (e.g. your example) and also you have to take care over security breaches, crashes and even serious data corruption. In the other hand, a high-level language doesn't allow you to control the computer by hand but makes your life easier when you don't need that control.

If you choose a language of the low-level group, like C (the language in which the Linux kernel is written), you'll have a great headache to deal even with character strings... They simply don't exist in C, so you have to "create" them (it's not exactly true, but almost) before even thinking on doing what you want; in languages of the high-level group (e.g. Python, Perl, bash, awk, and a long etc.), you surely will have strings already there for you, so you just care for your problem.

So, if I were to write this, I'd go for a high-level language unless this is needed as an essential piece for a computer system. We people here tend to be Python-biased (as some stuff in Ubuntu is written on that language... for example, the Ubuntu Installer!) but other languages of the same kind will work without trouble.

Hope this not only gets you the picture of what's involved in programming your idea, but also some little concepts on programming.

---

### Post by damlays on 2008-10-18
thank you for answers..

it seems that I must learn a programming language at least a little bit..because there is no ready solution (software) arround to do this. Am I right?

Iheard that pyton is not very difficult to learn. If I start to learn, where should I start?
Can I learn it under windows ennvironment and make .exe files for windows?

---

### Post by geirha on 2008-10-18
Start with LaRoza's sticky thread here at the programming talk forum. You'll find information on how to set up python on windows there. It is possible to create .exe-files from python code, though this is not common to do. You just double-click the .py-file to run it.

---

### Post by true_friend on 2008-10-18
Python is easy to learn, its true and C# is also a good high level language. In sticky threads you can find out about it as well.

---

### Post by damlays on 2008-10-20
as a last question : if I want to execute a pyton code in linux, is it easy to run it or do I have to install software first?

For example I can execute perl scripts with just writing in "vi" editor as text in a *.pl file and making the file executable. with chmod +x command 
Is there any easy way like this to run pyton scripts?

---

### Post by geirha on 2008-10-20
Same way, create a .py-file in your favorite editor and make the first line read:
```
#!/usr/bin/env python
``` Then make it executable and run with ./script.py

---

### Post by damlays on 2008-10-22
I worked on pyton and with some help of wise guys (thanks for them) I can have script that works perfect for the function which I was looking for. I would like to share my script:

```
import sys

def transformer(word):
    result = []
    for i in xrange(0,100):
        result.append(word + str(i))
    return result

def main():
    if len(sys.argv) != 3:
        print 'Usage: python ' + sys.argv[0] + ' input.txt output.txt'
        sys.exit(1)
    try:
        i = open(sys.argv[1],'r')
    except:
        print 'Error: file not found (' + sys.argv[1] + ')'
        sys.exit(1)
    o = open(sys.argv[2],'w')
    for line in i.xreadlines():
        o.write('\n'.join(transformer(line.strip())))
    o.write('\n')

if __name__ == '__main__':
    main()
```



now I am thinking about an other code which will solve all problems about generating wordlist from a wordlist:

If we have two different text files like one.txt and two.txt,
one.txt contains;
john
tom
william
..
in it. And two.txt has
apple
orange
...

The command we need is a function which combines these two files and creates a third text file like;
johnapple
johnorange
tomapple
tomaorange
williamapple
williamorange
...


Which kind of changes do I need to make in my code to do so. Is it hard to do?

---

### Post by geirha on 2008-10-22
I would suggest using getopt to parse the command line arguments, and use a '-a' option to append the words of a file with the words of another file.

[http://www.python.org/doc/2.5.2/lib/module-getopt.html](http://www.python.org/doc/2.5.2/lib/module-getopt.html)

---

### Post by rye_ on 2008-10-22
Ignore

---

### Post by damlays on 2008-10-24
Okay, here is the code in C that makes what I want (written in the last message of mine). It combines two wordlist files and makes a third one with writing the combination of each line together.

But in this stage I need the help of some master programmers. This code is unfunctional in files more that 2GB. Can expert programmers show how we should make the necessary changes in the script to make the program work with very huge files? (more than 2GB)

```
#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[])
{
  if (argc < 4)
  {
    printf("Usage: %s input1.txt input2.txt output.txt\n", argv[0]);
    return 1;
  }
  FILE *input_1 = fopen(argv[1], "r");
  if (input_1 == NULL)
  {
    printf("Error opening input file (%s)\n", argv[1]);
    return 1;
  }
  FILE *input_2 = fopen(argv[2], "r");
  if (input_2 == NULL)
  {
    printf("Error opening input file (%s)\n", argv[2]);
    return 1;
  }
  FILE *output = fopen(argv[3], "w");
  if (output == NULL)
  {
    printf("Error opening output file (%s)\n", argv[3]);
    return 1;
  }
  char buffer_1[256];
  char buffer_2[256];

  while (1)
  {
    if (fgets(buffer_1, 256, input_1) != NULL)
    {
      buffer_1[strlen(buffer_1)-1] = '\0';
      rewind(input_2);
      while (1)
      {
        if (fgets(buffer_2, 256, input_2) != NULL)
        {
          fprintf(output, "%s%s", buffer_1, buffer_2);
        }
        else
        {
          break;
        }
      }
    }
    else
    {
      break;
    }
  }

  fclose(input_1);
  fclose(input_2);
  fclose(output);
  return 0;
}It's C code, and it's about as efficient as it gets, holding only the current line in memory, reusing the file descriptor of the second input file by rewinding the read position.

Here's how to run it:

```

---

### Post by ghostdog74 on 2008-10-24
> **damlays said:**
> 
If we have two different text files like one.txt and two.txt,
one.txt contains;
john
tom
william
..
in it. And two.txt has
apple
orange
...

The command we need is a function which combines these two files and creates a third text file like;
johnapple
johnorange
tomapple
tomaorange
williamapple
williamorange
...
?

```

awk 'FNR==NR{_[$0]next}{ for ( i in _){print $0 i}}' two.txt one.txt

```

---

### Post by geirha on 2008-10-24
> **damlays said:**
> 
But in this stage I need the help of some master programmers. This code is unfunctional in files more that 2GB. Can expert programmers show how we should make the necessary changes in the script to make the program work with very huge files? (more than 2GB)

define _FILE_OFFSET_BITS 64 and it should handle large files. 
Read about it here: [http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)

Thought you said you were not a programmer, and now you're solving problems in C? :)

---

### Post by damlays on 2008-10-24
actually I am from old ages, I was a programmer of basic in Commodore 64:) I can understand the flow of a high level program if I know the command syntax a little bit ..but I can deal with that C program only with the help of some today's programmers like you..

I'll have a look and try your and ghostdog74's hints ..

---

### Post by ghostdog74 on 2008-10-24
> **damlays said:**
> 

I'll have a look and try your and ghostdog74's hints ..

take note my code is only for your simple example. If you have 2GB files each, then my method is not suitable.

---

