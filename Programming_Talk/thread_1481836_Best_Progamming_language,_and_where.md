---
title: "Best Progamming language, and where"
date: 2010-05-13
forum: Programming Talk
---

### Post by AryaYawe1 on 2010-05-13
Hi just wondering, what is the best programming language to learn, and where is the best way to learn it online. i have been trying to learn programming a little, but keep on burning out when i go online and try and learn. Any help would be greatly appreciated.

Thanks

---

### Post by parn on 2010-05-13
Depends on your expectation and purpose. There simply isnt a "best" programming language.

If you are totally new to programming and simply wanted to learn the basics concepts, any language is fine.

---

### Post by (&amp;*4h*)#$ on 2010-05-13
You might want to try Perl. Its interpreter is already included with a regular Ubuntu installation.

Personally my first real programming language is C++, but as parn has mentioned, if you are off to learn basic programming, pretty much any language can get you started. :)

---

### Post by Tony Flury on 2010-05-13
A lot of people will also probably suggest python, which many find easier to read than for instance Perl, and by most measures is a higher level language than C (or maybe even C++). However in truth the Best Language is always the one that you know that allows you to complete the task that you have within the time that you have to complete it.

Of course by Task i don't just mean what the program has to do (commonly called the functionality) but also taking into account what environment it has to run on (linux, windows, embedded system with memory constraints etc), what performance parameters it has etc (speed, memory, response times etc).

For instance - writing an application with a GUI interface to manage uploads of pictures to flickr - since most of the "performance" is actually dependent on your internet connection and the flickr servers then a Python or similarly interpreted language implementation would be fine - i know the one i wrote is fine for me. If however you are writing some software that needs to do 100,000s of vector and surface manipulations per second for a near real time landscape rendering(for instance a fully fledged flight simulator) then probably python is not a good idea :-)

Decide what you need you program to do, and then work from there which language (or languages you need).

---

### Post by mmix on 2010-05-13
c, c++, lisp, perl, asm

i can tell you the place, but the place is not that you want.
you have to find your own place.

---

### Post by roccivic on 2010-05-13
Depends also what you want to do with that language. If you want to write your own operating system - C, if you want to write webapps - PHP, etc, etc

---

### Post by sxmaxchine on 2010-05-13
I started with html (though technically not a programming langauge) then i went to visual basic and now im learning javascript, and next i will learn php. 

Im learning web langauges.

---

### Post by nvteighen on 2010-05-13
Best programming language: None and all
Where: Nowhere and everywhere

After that Zen-like answer, here comes the more "normal" one.

Programming languages are designed with some goals in mind and each one is optimized for fulfilling those goals; ok, all Turing-complete languages are able to express the same, but the roads are different in all of them.

For example, take this program in C and in Python, respectively. It first generates a list of integers in a desired range and then prints all elements to screen in a nice format.

```

/* C */

#include <stdio.h>
#include <malloc.h>

struct list_struct
{
    int *list;
    size_t size;
};

struct list_struct list_new(int lower, int upper)
{
    struct list_struct mylist = {NULL, 0};

    /* Checking boundaries' correctness. */
    if(lower > upper)
        return mylist;

    /* Allocating */
    size_t tmp_size = upper - lower + 1;
    mylist.list = calloc(tmp_size, sizeof(int));

    /* If allocation went right, fill the list */
    if(mylist.list != NULL)
    {
        int i;
        for(i = 0; i < tmp_size; i++, lower++)
            mylist.list[i] = lower;

        mylist.size = tmp_size; /* Only save size in the structure if everything
                                 * succeeded. */
    }

    return mylist; /* If allocation went wrong, mylist.list will be NULL. */
}

void list_free(struct list_struct list)
{
    if(list.list != NULL)
    {
        free(list.list);
        list.list = NULL;
        list.size = 0;
    }
}

void list_print(struct list_struct list)
{
    int i;
    for(i = 0; i < list.size - 1; i++) /* Print all but the last. */
        printf("%d, ", list.list[i]);

    /* i = list.size - 1 here! */
    printf("%d\n", list.list[i]); /* Print the last without comma. */
}

int main(void)
{
    /* Ok, I could have asked for user input here, but let's simplify things. */
    int lower = 15;
    int upper = 65;

    struct list_struct list = list_new(lower, upper);

    list_print(list);

    list_free(list);

    return 0;
}

```

```

#!/usr/bin/env python
# ^^ allows for execution with ./ if execution permissions are given.

def list_new(lower, upper):
    return [x for x in xrange(lower, upper + 1)] # xrange already checks lower >
                                                 # upper and returns a null list
                                                 # [] in that case.

# No need for list_free. Memory management is automatic.

def list_print(some_list):
    the_string = ""

    for x in some_list[:-1]:
       the_string += "%d, " % x

    the_string += "%d" % some_list[-1]

    print(the_string) # newline is automatically added.

def main():
    mylist = list_new(15, 65)
    list_print(mylist)

main()

```

The difference in this case relies on the low-levelness of C vs. the high-levelness of Python; C is a language designed for controlling basic operations of computers in a more readable fashion than Assembly. Python, on the other hand, is designed for "controlling" more human conceptual structures and so it has a list structure built-in, while in C I had to create one basing myself on an "integer array" that actually is a memory address followed by some (in this case) manually allocated space. Of course, C is faster and allows me to handle memory, but at the cost of knowing how to deal with it :P There are of course other details; for example, the looping construct in Python (the for statement) works by being told how to work (lists have an iteration "method" defined in them that tells "for" how to iterate a list), while in C it's just a fixed structure ("for(start; continue condition; what to do at next iteration)").

I chose C and Python because it was a bit more straightforward; high- vs. low-levelness is something easy to grasp. I could have used Lisp and C++, for example, to show different approaches on metaprogramming (Lisp macros vs. C++ templates) or different approaches on Object-Oriented Programming (OOP). 

The idea I want you to understand is that languages are designed with their own particular features because they respond to different tasks. A good programmer is one who knows what language to use in which case, so knowing several languages is a requirement. There might be special cases: experimentation or budget constraints that force people to use a suboptimal solution, but the ideal is what I've told you above.

---

### Post by trent.josephsen on 2010-05-13
Just for kicks, and so you can see the point, here's the same program in Perl:

```
#!/usr/bin/perl
print join ", ", 15..65;
print $/;
```
:D

---

### Post by Tony Flury on 2010-05-13
@nvteighen - I think you can do this far more easily in python : 

```

#!/usr/bin/env python
print ",".join(str(x) for x in range(16,65))

```

If this does not work my excuse is I am unable to test it due to being forced to use Windows XP at work and not being allowed to install python.

---

### Post by slackthumbz on 2010-05-13
Well, I would contend that the best language ever was [Lovecraft]("http://undefined.com/ia/2006/11/01/new-language-lovecraft/"). Sadly the spec was never implemented ;)

---

### Post by nvteighen on 2010-05-13
> **Tony Flury said:**
> @nvteighen - I think you can do this far more easily in python : 

```

#!/usr/bin/env python
print ",".join(str(x) for x in range(16,65))

```

If this does not work my excuse is I am unable to test it due to being forced to use Windows XP at work and not being allowed to install python.

I wanted to keep a certain similarity between both examples without falling into C-like Python either; also, I wanted to explicitly stress out the use of functions... :p

Btw, it should be range(16, 65 + 1)... as I wanted 65 to be printed.

---

### Post by Tony Flury on 2010-05-13
> **nvteighen said:**
> I wanted to keep a certain similarity between both examples without falling into C-like Python either; also, I wanted to explicitly stress out the use of functions... :p

Btw, it should be range(16, 65 + 1)... as I wanted 65 to be printed.

Mine was more of a respone to trent.josephsen I guess - to show that python could be just as direct as perl - without the risk of looking like line noise in some cases :-)

I did try perl once, but found its reliance on (in my perception) a lot of punctuation to define specific semantics to be confusing (at least to my little brain).

Also as an illustration of the roles and capabilities of different languages, the single line Perl/python examples illustrate the curtness of the development cycle which is possible (admitedly at the expense of direct control and performance).

---

### Post by trent.josephsen on 2010-05-13
You want LINE NOISE??? I'll give you LINE NOISE! ;)

```
$,=', ';$\=$/;print 15..65
```

I think I'm reaching something of a lower limit here (26 bytes).  Maybe another byte or two could be shaved off.  Perl 6 has the say feature built-in, so you could do

```
$,=', ';say 15..65
```

Only 18 bytes.  But that's just ridiculous :)

The point is that all languages have different strengths.  The fact that Perl can do the work of that comparatively monstrous C program in less than 30 bytes is evidence of that.  Perl is concise and makes complicated text processing look easy, at the disadvantage of sometimes looking like line noise.  C is fast and close to the hardware, at the expense of requiring great attention to detail.  Java is portable, relatively fast, and fairly high-level -- but it's too verbose and clunky for quick scripts.

I always recommend Python, as it's easy to pick up, but you can learn to program in any language.  Good design, as I am fond of saying, transcends language boundaries.

---

### Post by AryaYawe1 on 2010-05-14
Thanks for all the help

---

### Post by ja660k on 2010-05-15
If you do chose to learn perl,python

please make sure you dont write C code in perl or python script...
because if you do, the Perl 1337 will laugh at you and your python will take FOREVER to run.

That being said, learn C as well as Python, 
python has a sweet module, called ctypes
which can "import" from c code we write, 
so we can do heavy processing in c, return raw data and let python clean it up because in that way, python is awesome.

this is a way to speed things up, because python is interpreted and because of that, slow.

---

### Post by KdotJ on 2010-05-15
No one ever seems to like java :-(

---

### Post by lisati on 2010-05-15
I could put a plug in for languages like [BASIC]("http://en.wikipedia.org/wiki/BASIC"), [FORTRAN]("http://en.wikipedia.org/wiki/Fortran"), [COBOL]("http://en.wikipedia.org/wiki/COBOL") and [Pascal]("http://en.wikipedia.org/wiki/Pascal_%28programming_language%29"), because they were among the first languages I did anything with. (Wait, I forgot to mention [PL/1]("http://en.wikipedia.org/wiki/Pl/1"))

Popular in the forums are some which have already been mentioned: C, C++, perl, Python, etc.

Edit: worthy of mention: Assembly language, which isn't for the faint hearted. The main advantages are that a well written ASM program can run quickly and you have a LOT of control over how it works. The down side is that it's fairly low-level stuff, and can easily tie you to a particular family of processors running a particular OS.

---

### Post by mihnea.radulescu on 2010-05-15
What about Smalltalk?

Pharo Smalltalk release: [http://www.pharo-project.org/home](http://www.pharo-project.org/home)

---

