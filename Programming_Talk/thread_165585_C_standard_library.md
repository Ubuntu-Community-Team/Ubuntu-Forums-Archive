---
title: "C standard library"
date: 2006-04-24
forum: Programming Talk
---

### Post by sanderjd on 2006-04-24
This may seem like a silly question, but I'm wondering how I make the C standard libraries work. I have been somewhat surprised at the seeming lack of built in support for programming in C. I already installed the make and gcc packages I needed but now I have no standard library support, and I don't know where to find it. I've looked a bit through the forums but I can't seem to find anything about it. Really I'm just looking for the quickest way to get a fully-functional C/C++ development environment working. Any thoughts are helpful.

---

### Post by cstudent on 2006-04-24
Start with installing the build essential package.
From a terminal window enter:
```

sudo apt-get install build-essential

```

Then you can use many different ways to write code.

Vi or Vim, Emacs or XEmacs, Anjuta, Glade or Eclipse to name a few. These can all be installed using apt-get or synaptic. The IDE I've been using lately is Code Blocks which I download from here: [http://www.savefile.com/projects/547711](http://www.savefile.com/projects/547711)

For some help with the C library itself I sometimes use this site: [http://ccs.ucsd.edu/c/](http://ccs.ucsd.edu/c/)

Hope this gets you going.

---

### Post by xtoph on 2006-04-26
im having the same trouble.  ive done c/c++ on windows and unix school computers.  now i have ubuntu on my home box.  i also have the make and gcc packages, and i know how to use VI.  i have directories called usr/include/c++/4.0 and 4.2.  they look suspiciously identical, and contain files like *cstdlib*.

so how come i cant even get a hello world to compile?  how do the includes work?
ive tried to include <stdlib>, <cstdlib>, "cstdlib.h", "cstdlib"
i get an error for every include attempt, plus this one if i dont use any includes
[I]
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status[/I]

a little help?

---

### Post by LordHunter317 on 2006-04-26
The issue is almost certianly in the command you're running, or you're missing 'libc6-dev'.  Did you install 'build-essential'?  It looks like you didn't.

---

### Post by cstudent on 2006-04-26
You need to install the build-essential package.

Open a terminal window and enter:
```

sudo apt-get install build-essential

```

Once installed open Vi or whatever text editor you want to use and enter your hello world code and save the file as helloworld.c
```

#include <stdio.h>

int main()
{
    printf("Hello World!\n");
    return 0;
}

```

Open a terminal window again and navigate to the directory you stored your file and use gcc to compile.
```

gcc helloworld.c -o helloworld

```

If no errors are listed and you return to the command prompt it worked. Then run your program like so:
```

./helloworld

```

This will hopefully get you started on your way.

---

### Post by xtoph on 2006-04-27
wow.  i guess i should have read that closer the first time.  thanks guys.

---

