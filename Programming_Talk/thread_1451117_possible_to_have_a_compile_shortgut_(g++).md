---
title: "possible to have a compile shortgut (g++)?"
date: 2010-04-10
forum: Programming Talk
---

### Post by Søren on 2010-04-10
hi,

im just compiling some basic programs in ubuntu after switching recently from Ubuntu from windows and c++ from Java ... 

i comile from the command line using:

$ g++ -Wall -W -Werror myprogram.cpp -o myprogram
$ ./myprogram

what i want is to not have to type this every compile cycle. something like a keyboard shortcut that means "compile that".

please note that i am aware that i could use and ide, but i am at work and am not allowed to install exotic software on this system.

---

### Post by tooatw on 2010-04-10
i use just
> g++ -o 1 program.cpp
> ./1

and when i want to compile again i just press up and select the g++ line and press enter again

---

### Post by Søren on 2010-04-10
very helpfful, thanks.

---

### Post by Søren on 2010-04-10
btw, what does the "-o" and the "1' there mean?

---

### Post by matthew.ball on 2010-04-10
I think -o is an optimisation flag. The 1 is the name of the executable to be output by the g++ compiler.

Judging from your question, I would say you might be interested in Makefiles. Basically just a text file, but it handles all your compilation code in one place. Just type make and it will compile your project.

Especially useful when you use multiple files and need to link them at compile them.

---

### Post by NovaAesa on 2010-04-10
-o indicates that whatever follows should be the output file.

Makefiles are the way to go here.

---

### Post by Søren on 2010-04-10
ok. * is off to learn about makefiles*

---

### Post by gmargo on 2010-04-10
Here's a basic Makefile for you. Drop it into that directory (name it "Makefile" or "makefile") and type "make".

```

CXXFLAGS=-Wall -W -Werror

all: myprogram

myprogram: myprogram.cpp

```

---

### Post by geirha on 2010-04-10
make is the way to go, but just to show a different approach that may be useful to know in other situations:

You can make a wrapper function in bash. 
```
compile () {
  g++ -Wall -W -Werror -o "${1%.*}" "$1"
}

```
If you put that at the end of your ~/.bashrc and open a new terminal (so the .bashrc gets sourced), you can do
```
compile foo.cpp
# which will execute: g++ -Wall -W -Werror -o "foo" "foo.cpp"

```

[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by Lux Perpetua on 2010-04-10
**make** might be too big a hammer for this. I don't create a makefile (or put an entry in a makefile) for every throwaway program that I write. It's possible that Søren simply isn't aware of shell aliases. If you put the line ```
alias g+d='g++ -all -W -Werror'
```in the file ~/.bashrc (or just type it on the terminal), then you can just do ```
g+d myprogram.cpp -o myprogram
./myprogram
```

geirha's solution is cooler, though.

---

### Post by BackwardsDown on 2010-04-10
> **Søren said:**
> i comile from the command line using:

$ g++ -Wall -W -Werror myprogram.cpp -o myprogram
$ ./myprogram

what i want is to not have to type this every compile cycle. something like a keyboard shortcut that means "compile that".


You can also use:

```
g++ -Wall -W -Werror myprogram.cpp -o myprogram && ./myprogram
```

---

### Post by TSP on 2010-04-10
I have a shell script in /usr/local/bin/ with this content

#!/bin/bash

SOURCE=$1

if [ -f $SOURCE ];
then
    NAME=`echo $SOURCE | awk -F. '{print $1}'`
else
    echo "File doesn't exists!"
    exit
fi

# compile
g++ -g -Wall -o$NAME.run $SOURCE

if [ $? -eq 0 ];
then
    chmod +x $NAME.run
fi

---

### Post by Søren on 2010-04-11
awesome, learning lots here.

and yeah i wasn't aware of shell aliases heh. adding that script to bash seems like my solution. thats a really awesome script! i like how it checks for chmod..sweet

im setting up my ubuntu to run primarily from the command line. uninstalling the desktop etc.

---

### Post by geirha on 2010-04-11
Actually, chmod +x is completely unnecessary. That g++ line will either create an executable binary, or none at all. awk is a bit overkill too, but should work for all typical cases.

---

### Post by Søren on 2010-04-13
i used a ruby script (cause i know it better than bash) so i get i overkilled too. :p

---

### Post by phrostbyte on 2010-04-13
It is worth using a Makefile for even simple programs. First of all, you never know if a simple program might end up being kind of complicated. :) No matter how complex, it should be simple to compile (ie. just typing "make"). You can think of a Makefile is kind of like writing a small bash wrapper / alias around compiling your program, but it adds functionality that is difficult to achieve with bash script alone. Just my 2 cents.

---

### Post by phrostbyte on 2010-04-13
There is also an endless amount of build systems / techniques out there. Even one that written in Ruby, I think it is called Rake. 

You can say some of these systems are a little more advanced for complex builds, something huge (lets say KDE) might use something different then just a simple Makefile. For simple things I think just a plain Makefile is easiest.

---

### Post by Søren on 2010-04-13
believe it or not, i didnt even know about tab-completion when i first wrote this thread (which i learned about today). knowing that i can tab complete things takes a lot of the pain out of my original worry. but learning make files will be useful soon. :D

---

