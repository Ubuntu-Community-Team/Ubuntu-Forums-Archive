---
title: "vim, custom commands"
date: 2013-09-17
forum: Programming Talk
---

### Post by jerome1232 on 2013-09-17
So I am taking a programming with C course, because I don't want to use a full featured IDE which wants me to create a project and etc... I am using Vim to edit my source, currently when I want to compile I'll either send vim to the background with ctrl+z, then compile and test my program or I'll run it with :! gcc etc.... I understand vim allows you to write custom commands and I was hoping to make one to run my compile, so I could do something like :

:compile

and have it compile the file I am currently editing (everything will be single file programs)

The command would be something like

```
gcc -std=c99 -Wall *src/myfile.c* -o *bin/myfile.bin*
```

Now I get how to write that command except the output directory, I'm unsure how to specify the filename so that it's automatically the same file name but .bin instead of .c and in the bin subdirectory instead of in the src subdirectory.

---

### Post by 1clue on 2013-09-17
It all depends on what you're trying to accomplish.

Me, I'd use make instead of gcc directly.  Your above command would then become something like:
```
:!make myfile.bin
```

You can also compile a C app that does something you want, and run that from the command line.

To execute an external shell command, you do this:
<esc>:! <command>

To read the results of that into the file, you do this:
<esc>:r! <command>

To make a macro of vim commands, you do this:
<esc>qa<sequence of vim commands>q
which would define macro 'a' with whatever sequence of commands you typed.  To use the command you would type:
@a

There's a lot more to this, and while I've been using vim constantly for over 14 years I'm by no means an expert.

---

### Post by jerome1232 on 2013-09-17
I basically don't want to have to rewrite my compile command when I switch computers etc..., the make file sounds promising, trying to understand a tutorial right now.

---

### Post by 1clue on 2013-09-17
It's been years since I did any significant c programming, but I know that make has gone through some changes since then.  It has a lot of standard functionality, for example if you type *make something.o* and there's a *something.c* in your current directory, it will know what to do without a makefile.

For that matter the c programmers might be using some other build tool now.  I'd look for some threads about c and see what they use.  Or download some source for an active project and see what they use.

Given what you just said, I would strongly recommend that you use a standard, currently used build tool, whatever that is.  That ensures that current methodology is going to be applied to your project, and will also help you understand or participate in Open Source at some point.  Or commercial software.

If you start switching computers I would suggest using some sort of source code control like git.

---

### Post by jerome1232 on 2013-09-23
makefiles were just the ticket!

---

### Post by trent.josephsen on 2013-09-23
N.B. Vim's :make command will run make for you, or you can change the makeprg option to change what it does. To be fair, it only saves one character over :!make :P

I write mostly small programs and rarely use real makefiles; I just set the following environment variable in .zshrc so that I get all the warnings I like running make.

```
export CFLAGS="-std=c11 -Wall -Wextra -Wwrite-strings"
```

You'd have to write an explicit makefile to tell it to add .bin to the filename, though -- that's not a typical thing to do.

---

### Post by 1clue on 2013-09-23
Last I checked, the final binary was just the name without extension.  Not sure if you have a reason for adding the .bin, but if you want to it would work.

So it would be something like this:
hello.c   ->   hello.o   ->   hello

---

### Post by jerome1232 on 2013-09-23
Well it's just a bunch of small programs, so I wrote one makefile with targets for each different assignment I do, so I can type :!make thisprog and it'll compile, I'm adding the .bin because I want to, I've seen binaries in linux with no extension, with .run, .bin and others, it doesn't really matter. I just like .bin so I can see from the name it's a binary.

Ie when I start a new assignment I just add a new line for the new assignment.

The makefile looks like this right now, I'm sure I'm not doing this the standard way, but it's working well for my intended use.
```
test: test.c
	gcc -std=c99 -ggdb -Wall test.c -o bin/test.bin

Ex5.16main: Ex5.16main.c Ex5.16function.c
	gcc -std=c99 -ggdb -Wall Ex5.16main.c Ex5.16function.c -o bin/Ex5.16main.bin

FirstCprogram: FirstCprogram.c
	gcc -std=c99 -ggdb -Wall FirstCprogram.c -o bin/FirstCprogram.bin

reverseDigits: reverseDigits.c
	gcc -std=c99 -ggdb -Wall reverseDigits.c -o bin/reverseDigits.c

dice: dice.c
	gcc -std=c99 -ggdb -Wall dice.c -o bin/dice.c

processImage: processImage.c
	gcc -std=c99 -ggdb -Wall processImage.c -o bin/processImage.bin -L. -lbitmap

clean:
	rm bin/*

```

---

### Post by 1clue on 2013-09-24
Do me a favor:

Move your makefile to another directory, and then type:

make test
make FirstCprogram
...
Also, you should be able to just make a rule with a wildcard filename, based on suffixes.  Don't remember what the syntax is exactly but for example the Linux kernel makefile is only about suffixes, almost nothing is specific to a single file.

---

### Post by jerome1232 on 2013-09-26
if I moved my make file and ran 'make test' inside the directory where test.c resides, It runs a generic 'cc test.c -o test' which doesn't compile of course because I have c99 specific code in there. (I guess c11 is the new standard, I'll start using that)

If you are suggesting there's a more dynamic way to write the make file I'm all for it, I'm beginning to slap assignments (or projects I suppose) into their own sub directories as they are becoming multi-file assignments. I really only grasped enough of makefiles to figure out something that worked for me.

---

### Post by trent.josephsen on 2013-09-26
> **jerome1232 said:**
> if I moved my make file and ran 'make test' inside the directory where test.c resides, It runs a generic 'cc test.c -o test' which doesn't compile of course because I have c99 specific code in there.

That's what CFLAGS is for...

```
$ CFLAGS="-std=c99 -ggdb -Wall" make test
clang -std=c99 -ggdb -Wall    test.c   -o test
```

Ok, so I'm using clang, but it would also work with gcc.

Having a custom directory and file suffix for your executables changes things a bit, since you can no longer rely on make's builtin rules, but this seems to work (and will create the bin/ directory for you if necessary):

```
CFLAGS=-std=c99 -ggdb -Wall
BINDIR=bin

$(BINDIR):
	mkdir $(BINDIR)

$(BINDIR)/%.bin: %.c $(BINDIR)
	$(CC) $(CFLAGS) $(CPPFLAGS) $< -o $@
```
I tried to make a rule that would just move the implicitly built executable to bin/foo.bin, but it didn't seem to work properly.

However, you still need custom rules for programs that require specific libraries. IRL these would probably be different projects with their own Makefiles, and that wouldn't be a problem. But eh, this was more of a mental exercise than anything else.

---

### Post by 1clue on 2013-09-26
Try setting your CFLAGS environment variable.  Look at the current make documentation.  There are symbols it understands, you can cause ... don't remember the term used, there are rules based solely on the suffix that you can set up, and then if you have something special you can have something like you have already for that.

IMO they teach you backwards to frontwards, at least for the first few chapters.  My book is over 10 years old and it's in a different city.

---

### Post by jerome1232 on 2013-09-26
Okay, I understand most of that sample makefile, I'm confused about what the '$<' and the '$@' do, I've seen it in a few tut's I've perused but none of them explain it, they just pop it in like it's something that should already be understood. I'll have to experiment with it tomorrow.

---

### Post by 1clue on 2013-09-27
Start with this.  Pick a format.

[http://www.gnu.org/software/make/manual/](http://www.gnu.org/software/make/manual/)

---

