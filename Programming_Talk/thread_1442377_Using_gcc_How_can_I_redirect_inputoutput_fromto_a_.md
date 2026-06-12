---
title: "Using gcc: How can I redirect input/output from/to a text file?"
date: 2010-03-29
forum: Programming Talk
---

### Post by Crimson_Tider on 2010-03-29
Hi. I am just starting to reteach myself programming by going through "Thinking in C: Foundations for Java & C++"
by Bruce Eckel and Chuck Allison on mindview.net. In the exercise at the end of the first chapter, they say that I should "Find out how to do redirection in your environment, and experment with redirecting the input/output from/to a text file for the second program."

So how do I do this?

Background information:

The source code for the "second program" that they are referring to is this:

```
/* avg.c: Averages 2 integers */
#include <stdio.h>

int main() {
/* Declarations must be at beginning: */
int num1, num2;
float sum;

puts("Enter the first number:");
scanf("%d",&num1);
puts("Enter the second number:");
scanf("%d",&num2);

sum = num1 + num2;
printf("The average is %.2f\n", sum/2);
return 0;
}
```

I have tried searching for this, but I haven't found anything that works. The one I most recently tried is this:

```
$ gcc -Wall -o Average avg.c > output.log
$ ./Average
```

And all that did was create a totally empty file called output.log.

So how do I do this?

---

### Post by derekeverett on 2010-03-29
If I'm understanding what your trying to do correctly, you need to compile your program first.

Then run it while redirecting the output to a text file.

Your redirection looks right to me. Your just trying to re-direct the output of the compiler - not your program.

---

### Post by Crimson_Tider on 2010-03-29
> **derekeverett said:**
> If I'm understanding what your trying to do correctly, you need to compile your program first.


Is this not what I am doing with that first command?

---

### Post by derekeverett on 2010-03-29
> **Crimson_Tider said:**
> 

```
$ gcc -Wall -o Average avg.c > output.log
$ ./Average
```

So how do I do this?

The first line is where you are compiling your program. 
The second line is where you are attempting to run your program.

I suggest the issue is that you need to redirect the output when you run the program. If it all works correctly, you will be asked for your input and then the output will be directed to the specified text file.

---

### Post by Crimson_Tider on 2010-03-29
> **derekeverett said:**
> I suggest the issue is that you need to redirect the output when you run the program.

How do I do that?

I know I'm an idiot; I ask for your patience. :)

---

### Post by derekeverett on 2010-03-29
> **Crimson_Tider said:**
> How do I do that?

I know I'm an idiot; I ask for your patience. :)

No worries. This stuff can be frustrating until you figure it out. Then your allowed to call yourself an idiot ;)

You need to compile your program first to produce an executable file.

Something like this
```

gcc -o myProgram.c myProgram

```

This should produce an executable program in the same directory called myProgram.

You can then run myProgram with
```

./myProgram

```

It is this second part, where you run the program that you can redirect the output if you choose.

Consider redirecting the output from the program ls.
```

ls > myDirectoryListing.txt

```

myDirectoryListing.txt would now contain the output of the ls command.

---

### Post by Crimson_Tider on 2010-03-29
Okay; I think I get it now! I ran
```
$ ./Average > output.log
```

But now I have a new problem. When I hit enter after typing in that command, I just got a blinking cursor. It took me a while to figure out that I still needed to type in two numbers and hit enter after each one just like I did before. But there is no output there in the terminal to tell me to do that. How can I still make the program print out "Enter the first number:" and "Enter the second number:" in the terminal?

---

### Post by derekeverett on 2010-03-29
> **Crimson_Tider said:**
> Okay; I think I get it now! I ran
```
$ ./Average > output.log
```

But now I have a new problem. When I hit enter after typing in that command, I just got a blinking cursor. It took me a while to figure out that I still needed to type in two numbers and hit enter after each one just like I did before. But there is no output there in the terminal to tell me to do that. How can I still make the program print out "Enter the first number:" and "Enter the second number:" in the terminal?

Look at fputs maybe... as it requires you to specify the direction of the output.

```

fputs("How old are you? ", stdout);

```

That would be the first thing I try.....

---

### Post by Compyx on 2010-03-30
> **derekeverett said:**
> Look at fputs maybe... as it requires you to specify the direction of the output.

```

fputs("How old are you? ", stdout);

```

That would be the first thing I try.....

That's still not going to work, since stdout is redirected to file.
What I think the authors meant is that you also redirect stdin, ie. you write a text file with two lines, each containing a single integer value. You then use something like:
```

./Average <foo >bar

```
That way your program reads the integers from file 'foo' and outputs the average of those numbers to file 'bar' (along with the prompts from the program).

---

### Post by derekeverett on 2010-03-30
> **Compyx said:**
> That's still not going to work, since stdout is redirected to file.
What I think the authors meant is that you also redirect stdin, ie. you write a text file with two lines, each containing a single integer value. You then use something like:
```

./Average <foo >bar

```
That way your program reads the integers from file 'foo' and outputs the average of those numbers to file 'bar' (along with the prompts from the program).

I wasn't sure about fputs, but I believe your right now that I think about it. I'm not sure there is a way to accomplish this without generating the output file in the program. 

As far as the file input goes, the way I read it the author wanted both. The op hasn't returned in sometime to ask about that yet. I figured one obstacle at a time was plenty! ;)

---

### Post by MindSz on 2010-03-30
I think it'd be easier to do this kind of thing with fprintf instead of redirection.

---

### Post by derekeverett on 2010-03-30
> **MindSz said:**
> I think it'd be easier to do this kind of thing with fprintf instead of redirection.

That wouldn't be the assignment though. Using redirection is the point of the Authors assignment.

---

### Post by MindSz on 2010-03-30
Oh, sorry ... I kinda skipped over that part. :P

---

### Post by Compyx on 2010-03-30
A really decent guide on shell scripting including redirection of streams is the [Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/index.html"), I think the chapter on [I/O redirection]("http://tldp.org/LDP/abs/html/io-redirection.html") could be very helpful for your assignment.

---

### Post by Seq on 2010-03-30
> **Crimson_Tider said:**
> Okay; I think I get it now! I ran
```
$ ./Average > output.log
```

But now I have a new problem. When I hit enter after typing in that command, I just got a blinking cursor. It took me a while to figure out that I still needed to type in two numbers and hit enter after each one just like I did before. But there is no output there in the terminal to tell me to do that. How can I still make the program print out "Enter the first number:" and "Enter the second number:" in the terminal?

As pointed out, you're redirecting *all* output (well.. *all* stdout output). This is what shell redirection does.

Another way to do redirection is using `tee`. It is not built-in to the shell, but achieves essentially the same effect while still echoing text to the console for you to see (and provide input to your prompts).

```
Average | tee output.log
```

---

### Post by Crimson_Tider on 2010-03-30
Okay, thanks a lot guys! The suggestion to use both an input file and output to a file worked; I'll try the other suggestions a little later. By the way, I'm really diggin' this forum; I never thought I could have gotten so much help for such a simple problem! This is really going to make it easy for me to get help with problems as I relearn programming.

---

