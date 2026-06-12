---
title: "help in c and c++"
date: 2007-09-07
forum: Programming Talk
---

### Post by damansandhu on 2007-09-07
ok , i have now kdevelop and eclipse , how to compile and run program in them?

---

### Post by Fixman on 2007-09-07
I was just to make a thread asking to same thing

---

### Post by Mirrorball on 2007-09-07
Read the ... manual. Then come back here if you are puzzled or it's not working as it is supposed to. But please do your homework first. I hope you won't think I'm rude.

---

### Post by aks44 on 2007-09-07
09/1993 ;)

> **Mirrorball said:**
> I hope you won't think I'm rude.

(indeed, my own post looks quite rude, but nvm)



@Fixman: KDevelop or Eclipse?

@damansandhu: errmm... which product exactly are you asking help about?

---

### Post by damansandhu on 2007-09-07
the one which will be easier for a noob like me.

---

### Post by aks44 on 2007-09-07
> **damansandhu said:**
> the one which will be easier for a noob like me.

AFAIK KDevelop may be easier than Eclipse+CDT to get it up and running.

But don't take my words for granted. I only found that KDevelop worked out of the box while Eclipse would require you to install (& configure? not sure about that with Ubuntu's repos) the CDT plugin, which *may* introduce some burden.

Maybe someone that experienced CDT could shed some more light on this?

(anyway KDevelop is not for the faint of heart either, better start with Kate or GEdit + command line)

---

### Post by Tomosaur on 2007-09-07
> **damansandhu said:**
> ok , i have now kdevelop and eclipse , how to compile and run program in them?


An IDE like those is not a 'make programming easier' tool. They are for developers who need to manage large projects, or who already know how to program and can afford to be lazy.

If you are new to programming - then an IDE is just going to add another confusing layer - it really is best to go without.

What you need is a good text editor with syntax highlighting. I find that Kate is the best for this, but Gedit is pretty much the same thing.

To compile and such, you will need to install the build-essential package. In the terminal, type:

```

sudo apt-get install build-essential

```

Once it's installed, open up whichever text editor you like, then type the following C code:
```

#include <stdio.h>

int main(){
        printf("Hello World!\n");
        return 0;
}

```

Save the file as 'hello.c' in your home directory.

Now, open up a terminal, and type the following:
```

gcc -o ~/hello ~/hello.c

```

To run your program, just type the following:
```

~/hello

```

Congratulations, you know how to write, compile and run a basic C program :)

Later on you will need to do some extra stuff to get your programs to work, but for really simple stuff like this that's all you need.

---

### Post by pmasiar on 2007-09-08
> **damansandhu said:**
> the one which will be easier for a noob like me.

If you are really just a beginner programmer, you may have better luck and more fun by learning basics using more forgiving language with simpler syntax (and also shell: to learn language one line at a time) like Python

See wiki in my sig if you like Python better

---

