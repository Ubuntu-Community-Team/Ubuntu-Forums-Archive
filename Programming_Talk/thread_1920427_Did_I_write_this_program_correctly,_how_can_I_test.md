---
title: "Did I write this program correctly, how can I test it with a file?"
date: 2012-02-04
forum: Programming Talk
---

### Post by venom104 on 2012-02-04
Here is the program description

Your task

Create a subdirectory called "stdinout" in your "cisp453" directory  (which in return is in your home directory of the normal user). Do all  the work in "stdinout".

The source file must be named "stdinout.c", otherwise my grader script  won't work, and no points will be rewarded. Your stdinout.c program  should perform a simple task: echo everything from stdin to stdout, exit  when end-of-file of stdin is encountered. You may assume there are no  errors to handle (making the program a whole lot easier to write!). Read  the man page of "read" to find out how to detect end-of-file of an  input file. I suggest that you use a loop, and read stdin byte-by-byte.

For your own testing, you can name the executable file anything you  want, as I will recompile your source code to an executable name that I  choose for verification purposes.

Here is an executable that you can use for comparison purposes. Note  that you need to change the permission of the file to let it execute.  WinSCP can do this (check the "x" flag for user), or execute "chmod u+x  inout" in a CLI.

When you are done, execute "tar czvf ~/stdinout.tgz -C / `pwd`" from the "stdinout" directory, then submit the archive file.

Here is what I wrote [http://pastebin.com/9U4LzMvf](http://pastebin.com/9U4LzMvf)

The professor said something about sending output from another file as  input to this file and seeing if it works. How do I do that? I tried  doing this text.txt | ./a.out but it doesn't echo the output. Does that  mean something is wrong with my binary executable?

I'm not asking for you to do the assignment for me, I'm just asking for  help in determining wheiter or not I did the assignment correctly.

EDIT
I solved it on my own, the proper command was cat textfile.txt | ./a.out  and my program was written incorrectly, I was using the file descriptor  0 instead of 1 in my write call.

---

### Post by r-senior on 2012-02-05
For reference, the other way to pass a file to a program via stdin is:

```
./myprogram < inputfile.txt
```

---

