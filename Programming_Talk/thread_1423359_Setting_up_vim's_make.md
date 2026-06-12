---
title: "Setting up vim's :make"
date: 2010-03-06
forum: Programming Talk
---

### Post by Cenoforums on 2010-03-06
Hi,

I'm trying to do something for a while now but I can't see to tackle it very well.
I'm programming a PIC and I want to automatize this work flow:
-I write a program, compile it with :make and read the output from the compiler inside vim.
-If the program was compiled correctly, I then run a separate program called picload to load my compiled program into the pic. picload requires no input and only drops text to stdout, so I imagine it won't be a problem running it inside vim

So far I was able to change what make does like this
:set mp=make\ &\ rm\ xxx
Where xxx is a dummy file in my work directory so I could test the whole thing. I can see the output from rm in my vim window, which is good, but aparently rm is issued before make is finished compiling which is not good.

The trickier part is my if condition. If the compilation was successful, then run program, else don't run. I can test if the compilation was successful by grep'ing the output of make for a specific text line but I don't know if it's the best way to do this,

Any ideas?

---

### Post by ajgreeny on 2010-03-06
Use two && instead of just the one.
```
:set mp=make\ &&\ rm\ xxx
```
This means the second part will not start until the first has completed successfully; This is standard command line and I'm surprised you did not know it.

I can't help with the second bit of your question, other than to add that if the first part of the command does not complete successfully, I think there will be an error message appear, but I'm not enough of a programmer to really know about this.

---

### Post by Cenoforums on 2010-03-06
I'm not surprised, my shell knowledge is rather flaky. I don't know half as much as I should. thanx for the quick answer!

Using :set mp=make\ &&\ rm\ xxx works as expected, I can read rm's messages in my vim window, but now my quickfix setup is screwed. If there's a compilation error and rm does not run, I get an error like

"E40: Can't open errorfile /tmp/v911692/6"

I can't imagine how this would screw up the temp files, but I'm guessing that make's output isn't being saved properly and quickfix now cannot read it. Any idea how to fix this?

---

### Post by Cenoforums on 2010-03-13
For future reference, this is how I solved it:

```
set mp=(make\ $*&&\ rm\ XXX)
```

The $* after make is to be able to run stuff like "make clean".

---

