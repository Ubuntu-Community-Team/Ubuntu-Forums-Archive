---
title: "problem in 4 main operations  code"
date: 2011-01-02
forum: Programming Talk
---

### Post by keimasi on 2011-01-02
:KS:KS    [LEFT][LEFT]Hi 2 all.[/LEFT][/LEFT]
  [LEFT][LEFT]I wrote the 4 main operation but It does not execute in multiply operation. What should I do. Please guide me?[/LEFT][/LEFT]
  [LEFT][LEFT]It works correct :   ./calc 2 + 3[/LEFT][/LEFT]
  [LEFT][LEFT]But this not:    ./calc 3 ‘*’ 5[/LEFT]
[LEFT]>     [LEFT][RIGHT]#!/bin/bash[/LEFT][/RIGHT]
  [LEFT][LEFT]If [ $# != 3 ][/LEFT][/LEFT]
  [LEFT][RIGHT]Then[/LEFT][/RIGHT]
  [LEFT][RIGHT]         Echo missing data   [/LEFT][/RIGHT]
  [LEFT][RIGHT]         Exit [/LEFT][/RIGHT]
  [LEFT][RIGHT]Fi[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]echo $1[/LEFT][/RIGHT]
  [LEFT][RIGHT]echo $2[/LEFT][/RIGHT]
  [LEFT][RIGHT]echo $3[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]#plus operation[/LEFT][/RIGHT]
  [LEFT][RIGHT]If [ $2 = + ][/LEFT][/RIGHT]
  [LEFT][RIGHT]   Then [/LEFT][/RIGHT]
  [LEFT][RIGHT]        Expr  $1 + $2[/LEFT][/RIGHT]
  [LEFT][RIGHT]        Exit[/LEFT][/RIGHT]
  [LEFT][RIGHT]Fi[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]#minus operation[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]If [ $2 = - ][/LEFT][/RIGHT]
  [LEFT][RIGHT]   Then [/LEFT][/RIGHT]
  [LEFT][RIGHT]        Expr  $1 - $2[/LEFT][/RIGHT]
  [LEFT][RIGHT]        Exit[/LEFT][/RIGHT]
  [LEFT][RIGHT]Fi[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]#multiply operation[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]If [ $2 = * ][/LEFT][/RIGHT]
  [LEFT][RIGHT]   Then [/LEFT][/RIGHT]
  [LEFT][RIGHT]        Expr  $1 ‘*’ $2[/LEFT][/RIGHT]
  [LEFT][RIGHT]        Exit[/LEFT][/RIGHT]
  [LEFT][RIGHT]Fi[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]#division  operation[/LEFT][/RIGHT]
  [LEFT][RIGHT] [/LEFT][/RIGHT]
  [LEFT][RIGHT]If [ $2 = / ][/LEFT][/RIGHT]
  [LEFT][RIGHT]   Then [/LEFT][/RIGHT]
  [LEFT][RIGHT]        Expr  $1 / $2[/LEFT][/RIGHT]
  [LEFT][RIGHT]        Exit[/LEFT][/RIGHT]
  [LEFT][RIGHT]Fi[/LEFT][/RIGHT]
  :confused:
[/LEFT][/LEFT]

---

### Post by odyniec on 2011-01-02
First of all, edit your post and reformat the source code, it's hard to read the way you posted it. Second, I assume it's not the actual script that works for you, because I'm pretty sure bash does not accept commands starting with uppercase characters.

The "*" operator problem comes from the fact that you're not quoting the $2 parameter in your script, and bash expands "*" to the list of files in the current directory (see the "Special parameters" section in bash manual page). Your if statement should look like this:

```
if [ "$2" = "*" ]; then
    expr $1 "*" $3
    exit
fi
```

You should also quote it in the rest of the script.

---

### Post by ziekfiguur on 2011-01-02
You should use a decent text editor (gedit for instance) to write your script.
You should to write '*' instead of ‘*’ (note the difference between ' and ‘)

---

### Post by keimasi on 2011-01-02
**tnx. I just correct this. I wrote that in word :d bcz of this** [B]it was in uppercase characters.
now it works.

  [/B]```

#!/bin/bash
if [ $# != 3 ]
then
         echo missing data   
         exit 
fi

echo $1
echo &#8220;$2&#8221;
echo $3

#plus operation
if [ &#8220;$2&#8221; = + ]
   then 
        expr  $1 + $3
        exit
fi

#minus operation

if [ &#8220;$2&#8221; = - ]
   then 
        expr  $1 - $3
        exit
fi

#multiply operation

if [ &#8220;$2&#8221; = &#8220;*&#8221; ]
   then 
        expr  $1 \*  $3
        exit
fi

#division  operation

if [ &#8220;$2&#8221; = / ]
   then 
        expr  $1 / $3
        exit
fi

```

[B]tnx.
[/B]

---

### Post by Arndt on 2011-01-02
> **keimasi said:**
> **tnx. I just correct this. I wrote that in word :d bcz of this** [B]it was in uppercase characters.
now it works.

  [/B]```

#!/bin/bash
if [ $# != 3 ]
then
         echo missing data   
         exit 
fi

echo $1
echo “$2”
echo $3

#plus operation
if [ “$2” = + ]
   then 
        expr  $1 + $3
        exit
fi

#minus operation

if [ “$2” = - ]
   then 
        expr  $1 - $3
        exit
fi

#multiply operation

if [ “$2” = “*” ]
   then 
        expr  $1 \*  $3
        exit
fi

#division  operation

if [ “$2” = / ]
   then 
        expr  $1 / $3
        exit
fi

```

[B]tnx.
[/B]

You need to watch your double quote characters: “ and " are not likely to have the same effect. Of those two, only " is ASCII.

---

### Post by worksofcraft on 2011-01-02
> **keimasi said:**
> .... I wrote that in word ...

 

It is not good idea to use word processors for writing computer software. Word processors are for controlling appearance, but software depends on actual character codes and their sequence. The way source code it looks is mostly immaterial for the way it works.

---

### Post by unknownPoster on 2011-01-02
> **worksofcraft said:**
>  The way source code it looks is mostly immaterial for the way it works.

Unless it is Python. ;)

That being said, it's not an excuse to write poorly formatted code. If you want someone else to help with your project, or review your code, you want to make it as easy as possible for them to read your code without difficulty.

---

