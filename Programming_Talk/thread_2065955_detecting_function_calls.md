---
title: "detecting function calls"
date: 2012-10-03
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-03
Hey,
Is there a way to know what functions were called by a program during it's execution ?

Say, I have a code, as follows
```

#include <stdio.h>

int main(void)
{
 fun1();
 fun2();
 fun3();

 return 0;
}

int fun1(){}
int fun2(){fun2_1();}
int fun3(){}

int fun2_1(){}

```

Here, the output should be something like
[i]
Functions called are as follows
fun1()
fun2()
fun2_1()
fun3()
[/i]

Is there an option on gcc for this ?

---

### Post by raja.genupula on 2012-10-03
> **IAMTubby said:**
> Hey,
Is there a way to know what functions were called by a program during it's execution ?

Say, I have a code, as follows
```

#include <stdio.h>

int main(void)
{
 fun1();
 fun2();
 fun3();

 return 0;
}


int fun1(){}
int fun2(){fun2_1();}
int fun3(){}

int fun2_1(){}

```Here, the output should be something like
[I]
Functions called are as follows
fun1()
fun2()
fun2_1()
fun3()
[/I]

Is there an option on gcc for this ?


simple one , how about placing a printf line ?

---

### Post by IAMTubby on 2012-10-03
> **raja.genupula said:**
> simple one , how about placing a printf line ?
Hey raja,
hmm.. not too sure if I want to do that, I want to write something which would automatically tell me what functions are called. 
Placing a printf is manual right ?

---

### Post by trent.josephsen on 2012-10-03
I don't know of any "automatic" method. Calling a function doesn't leave a trace on the call stack after you return, so you'd have to insert some code at the beginning of every function. The simplest way to do this would be just to stick an extra line in the C source.

gdb might be able to do something like this; it still wouldn't be fully "automatic" though.

Perhaps you should describe what problem you're trying to solve, rather than how you want to solve it, and we can suggest other solutions.

---

### Post by raja.genupula on 2012-10-03
this is for statements , how about using it for your function call 

[http://stackoverflow.com/questions/8254678/how-to-know-which-statement-the-running-process-is-executing](http://stackoverflow.com/questions/8254678/how-to-know-which-statement-the-running-process-is-executing)

---

### Post by dwhitney67 on 2012-10-03
You can run your C or C++ program through a profiler.

Look into gprof.  You will also need to compile your applications using the -pg option.

---

### Post by spjackson on 2012-10-03
You can use profiling to tell you how often functions were called, average length of execution etc. There is also a tool to do static analysis that will give you a tree of what calls what. But neither of these seem to be what you want, i.e. an automatic call trace at runtime that prints a trace whenever a function is called.

ltrace and strace do tracing, but not at this level. I'm not aware of a standard tool that does just what you want, but there may be one.

Someone's had a go [here]("http://sourceforge.net/projects/call-tracing/"), but it seems that it hasn't been updated for a while.

[This]("http://www.ibm.com/developerworks/linux/library/l-graphvis/") gives some strong clues, but it is 7 years old, and I don't know if it would actually work.

---

### Post by IAMTubby on 2012-10-04
> **raja.genupula said:**
> this is for statements , how about using it for your function call 

[http://stackoverflow.com/questions/8254678/how-to-know-which-statement-the-running-process-is-executing](http://stackoverflow.com/questions/8254678/how-to-know-which-statement-the-running-process-is-executing)
raja.genupla, I shall read up on pstack and get back to you. I need 1 day to try out some of the things mentioned on your link. Shall try out and get back surely.

---

### Post by IAMTubby on 2012-10-04
> **dwhitney67 said:**
> You can run your C or C++ program through a profiler.

Look into gprof.  You will also need to compile your applications using the -pg option.
dwhitney, yes Sir, thanks a lot.
I tried running a sample program using gprof, was very helpful :) .
But I need 1 day to think about it.
I shall try out and get back to you tomorrow. 

Thanks.

---

### Post by IAMTubby on 2012-10-04
> **spjackson said:**
> You can use profiling to tell you how often functions were called, average length of execution etc.
Thanks spjackson, but what is the name of the profiling tool ? gprof ? I just tried a sample program using that and liked it. Any other profiling tool?

> 
There is also a tool to do static analysis that will give you a tree of what calls what.

Sir, would you be able to tell me the name of the tool ?

> 
But neither of these seem to be what you want, i.e. an automatic call trace at runtime that prints a trace whenever a function is called.

At runtime, would have been great, but static is also manageable.

> 
ltrace and strace do tracing, but not at this level. I'm not aware of a standard tool that does just what you want, but there may be one.

Sir, I shall try them and get back to you in 1 day's time. Currently, held up with some other personal commitment.

> 
Someone's had a go [here]("http://sourceforge.net/projects/call-tracing/"), but it seems that it hasn't been updated for a while.

[This]("http://www.ibm.com/developerworks/linux/library/l-graphvis/") gives some strong clues, but it is 7 years old, and I don't know if it would actually work.
I shall refer the links and get back.

Thanks

---

### Post by spjackson on 2012-10-05
gprof is the only profiler I have used on Linux. I don't know what alternatives there might be without searching for them.

For static analysis of a call tree, it's a very only time since I've had a need to do that. I don't recall the name of the tool I used. The current favourite seems to be [Cscope]("http://cscope.sourceforge.net/") which is installable from the Ubuntu repositories. I haven't tried it myself (or its interfaces such as the Vim interface).

> 
At runtime, would have been great, but static is also manageable.
I don't understand the purpose. Static analysis tells you what can call what for all possible inputs, without following any particular path through the code. At runtime, you are after tracing the path through functions that are actually called for a given set of inputs. These give you significantly different information. I don't understand your underlying objective I'm afraid.

---

### Post by IAMTubby on 2012-10-05
> **spjackson said:**
> 
I don't understand the purpose. Static analysis tells you what can call what for all possible inputs, without following any particular path through the code. At runtime, you are after tracing the path through functions that are actually called for a given set of inputs. These give you significantly different information. I don't understand your underlying objective I'm afraid.
Sir,
you are right. Yes at runtime is what I need. So are you suggesting that gprof would be a good choice ?

I shall go through these tools in depth in the coming days, but just to get a bird's eye view, are gprof, cscope, ctags ,ltrace, strace and the backtrace function all used for the same purpose ?

Thanks.

---

### Post by IAMTubby on 2012-10-05
> **spjackson said:**
> 
I don't understand the purpose. Static analysis tells you what can call what for all possible inputs, without following any particular path through the code.
As you said, static is not really useful right ?
In what situations do people use it ? After your reply, I can't think of any scenario where I would want to use the static trace.

By the way, you can have a static output by looking at the .s file right ?
```

$gcc -S code.c

```
By digging inside code.s, you can get a static trace right ?
Sorry if I'm wrong.

---

### Post by mevun on 2012-10-05
> **IAMTubby said:**
> As you said, static is not really useful right ?
In what situations do people use it ? After your reply, I can't think of any scenario where I would want to use the static trace.


I can think of two scenarios.

One scenario is when you want to find out if you have "dead code", i.e. code which is never reached.  With function calls, you can think of this as func A is defined but never called by any other function.  Of course, a simplistic static check could miss the case where func A calls func B which then calls func A (i.e. a loop makes it look like all functions are called).

Typically, static analysis tools (i.e. which are not limited to function call hierarchies) can be useful for finding bugs.  As I already mentioned, they can find dead code (not necessarily just a whole function, but blocks like if/else branches.  Dead code usually means you have a logic bug because you thought that code would be reached.

The other scenario for a tool that gives you function call hierarchies is to help people new to a codebase.  In other words, the tool helps people who haven't written much of the source code get up-to-speed quicker.  If your boss asks you to modify function C you might want to know what functions call it to make sure you don't create any bugs.

---

### Post by spjackson on 2012-10-05
> 
The other scenario for a tool that gives you function call hierarchies is to help people new to a codebase.
Yes, I have used this kind of thing in these circumstances. It can sometimes help you get a picture of how a large system is structured.

---

### Post by spjackson on 2012-10-05
> **IAMTubby said:**
> Sir,
you are right. Yes at runtime is what I need. So are you suggesting that gprof would be a good choice ?
No, I am not. I know of no tool that gives you exactly the output you described. Nobody else has yet suggested one. If it exists, then it is somewhat obscure.

I have suggested some tools that do vaguely similar things, but nothing that does exactly what you want.

> 
I shall go through these tools in depth in the coming days, but just to get a bird's eye view, are gprof, cscope, ctags ,ltrace, strace and the backtrace function all used for the same purpose?

Those tools are not all for the same purpose.

gprof is a profiler. It is principally a tool that helps you identify where most of the cpu time is used in your code; it breaks this down by function.

cscope and ctags appear to have similar purposes to each other in creating a map of where functions are defined and called. Editors can use that information to allow you to jump from one a function call to the definition of the function, for example.

ltrace and strace also have similar purposes to each other, but different than all the others. These do trace when functions are called, but only particular types of functions. They do not trace your functions in your program.

backtrace. I don't know what this is unless you mean the backtrace command in gdb.

If you really want to trace entry to every function, I suggest you use the hooks provided by gcc which were in the article I mentioned [http://www.ibm.com/developerworks/linux/library/l-graphvis/]("http://www.ibm.com/developerworks/linux/library/l-graphvis/")

I have found a more recent example which might be easier for you to follow [http://codingrelic.geekhold.com/2010/09/gcc-function-instrumentation.html]("http://codingrelic.geekhold.com/2010/09/gcc-function-instrumentation.html")

---

### Post by IAMTubby on 2012-10-18
> **spjackson said:**
> 
I think gprof gives me what I need. But I have 1 question, is it possible to find out the return value of a function and the arguments is takes from a gprof output ?

Or, is there any other way to get this detail along with the order of function calls ?

Thanks.

---

### Post by Tony Flury on 2012-10-19
Maybe if you explain why you need the information, what you are actually trying to acheive - then we might have better luck helping you identify the tools you need.

---

### Post by IAMTubby on 2012-10-22
> **Tony Flury said:**
> Maybe if you explain why you need the information, what you are actually trying to acheive - then we might have better luck helping you identify the tools you need.
> **trent.josephsen said:**
> 
Perhaps you should describe what problem you're trying to solve, rather than how you want to solve it, and we can suggest other solutions.
Hey Tony, I have to unit test code. For this, I need to know what function calls what, so that I can go and test each function from my code, rather than allowing it's preceding function to call it(like how normally a program works).

For eg.
if main() calls fun1() and fun1() calls fun2() as shown below, I want to test fun2() through my code, rather than calling fun1() and let fun1() call fun2().
```

main()
{
 fun1();
}

fun1()
{
 fun2();
}

fun2(char* someptr)
{

}

```


My code should be something like, 
```

printf("\nEnter which function you would like to test");
//At this step, it should show the gprof output on the screen
[1]fun1 [2]fun2

//Say user selects fun2
//Then I do,
printf("\nExecuting test function...");
myptr = address_containing_some_junkvalue_for_testing;
status = fun2(myptr);


if(status == 0)
 printf("\nunit test passed ");
else
 printf("\nunit test failed ");

```

Any suggestions ?

---

### Post by Tony Flury on 2012-10-22
> **IAMTubby said:**
> Hey Tony, I have to unit test code. For this, I need to know what function calls what, so that I can go and test each function from my code, rather than allowing it's preceding function to call it(like how normally a program works).

For eg.
if main() calls fun1() and fun1() calls fun2() as shown below, I want to test fun2() through my code, rather than calling fun1() and let fun1() call fun2().
```

main()
{
 fun1();
}

fun1()
{
 fun2();
}

fun2(char* someptr)
{

}

```


My code should be something like, 
```

printf("\nEnter which function you would like to test");
//At this step, it should show the gprof output on the screen
[1]fun1 [2]fun2

//Say user selects fun2
//Then I do,
printf("\nExecuting test function...");
myptr = address_containing_some_junkvalue_for_testing;
status = fun2(myptr);


if(status == 0)
 printf("\nunit test passed ");
else
 printf("\nunit test failed ");

```

Any suggestions ?

Depends how modular your code is - is fun2 only ever called by fun1 - are there a set of 2nd level functions which are only there to help (simplify) the 1st level functions ? If there is a clear boundary between the layers - and opbvious intefaces without global variables (ugggh), then why not break all the 2nd level functions into a separate module - and Cunit test that first. You can then test the first level functions knowing that your helper functions work.

The other advantage of providing the 2nd level functions in a separate module is that if you want to test your 1st level functions without worrying about the complex functionality in the 2nd level - you could povide a stub for the 2nd Level functions (i.e vey simple code versions which provide known simple answers) and test your 1st level code with that.

I have always viewed Unit testing as (ideally) black box testing - you treat your code as a box to which you only have access to the input and outputs, and you can't see inside (and so long as the right inputs povide the right outputs you code passes) - if you need to analyse the code you are testig before you test it - then you ae moving towards far more of a white box test - ot wrong just different.

---

### Post by IAMTubby on 2012-10-22
> **dwhitney67 said:**
> 
Look into gprof.  You will also need to compile your applications using the -pg option.
> **spjackson said:**
> gprof is the only profiler I have used on Linux.
> **Tony Flury said:**
> Maybe if you explain why you need the information, what you are actually trying to acheive - then we might have better luck helping you identify the tools you need.
> **trent.josephsen said:**
> 
Perhaps you should describe what problem you're trying to solve, rather than how you want to solve it, and we can suggest other solutions.

Right now, most of my attention is on gprof and the backtrace function (Please see [http://www.gnu.org/software/libc/manual/html_node/Backtraces.html](http://www.gnu.org/software/libc/manual/html_node/Backtraces.html) )
I'm very happy with gprof, but the only problem is that my executable runs on powerPC, and so I'll have to cross compile binutils for gprof. I being a beginner, don't think , will be able to do that.

backtrace is good enough although it's static. The only problem with backtrace is that you have to call the backtrace function in the last function defined. That's a huge overhead - to go and find out the last function if it's a huge application. Is there a way to mention the backtrace function in the very beginning, and let the compiler know that you expect the backtrace for this code, and when it reaches the last function, just call it for me, rather than me calling it explicitly. Theoritically, it is possible right ?

Thanks.

---

### Post by IAMTubby on 2012-10-22
I'm sorry, I was writing the previous comment when you replied. Please can you see it for a more specific question.

> **Tony Flury said:**
> If there is a clear boundary between the layers - and opbvious intefaces without global variables (ugggh), then why not break all the 2nd level functions into a separate module - and Cunit test that first. You can then test the first level functions knowing that your helper functions work.

Tony, thanks for the reply.
The only issue with that is, I wouldn't want to manually separate it as first layer and second layer. That's why I wanted something which tells me what function calls what. From the call order, I would be able to figure out which functions come under first layer, and subsequent layers. 
Once that is done,I can proceed as you said.

---

### Post by trent.josephsen on 2012-10-22
Maybe I'm missing something, but why do you need to know the flow of control to write unit tests? Shouldn't you be able to test fun2() without knowing in what context it's called? I mean, that is kind of the central notion of **unit** testing: test your code in small units so that you know they will integrate properly.

---

### Post by IAMTubby on 2012-10-22
> **trent.josephsen said:**
> Maybe I'm missing something, but why do you need to know the flow of control to write unit tests? Shouldn't you be able to test fun2() without knowing in what context it's called? I mean, that is kind of the central notion of **unit** testing: test your code in small units so that you know they will integrate properly.
Trent, but I want a program to tell me that a function called fun2() exists ,rather than me browsing through the code and getting to know it.

---

### Post by dwhitney67 on 2012-10-22
> **IAMTubby said:**
> Trent, but I want a program to tell me that a function called fun2() exists ,rather than me browsing through the code and getting to know it.

Your goal is way too lofty.  gprof will provide metrics on what functions where called during a particular run of the application.  If the application takes in a variety of inputs, then one run may very well differ from another.

CUnit on the other hand will assist you with unit testing the code.  The latter requires that you have intimate knowledge of the code, because after all, you need to develop a test for each function so that you can verify that it performs as expected, with and without nominal input data.

It seems that you do not want to make the effort to learn the code in detail, which is generally the case once an application has been fully developed and is already deployed.  Time could also be a factor.

Typically unit testing is performed during development, and rarely done after an application has been developed/deployed.

Since it seems that the work you are doing is at the professional level, perhaps you should invest in professional-grade tools to perform the task that you need.  I was recently introduced to Klocwork (via a training class); it is a static analysis tool that can catch coding problems in software.  Whether it meets your needs or not, I cannot be certain.  Surely an off-the-shelf tool must exist that could meet your needs.

---

### Post by IAMTubby on 2012-10-22
> **dwhitney67 said:**
> Your goal is way too lofty.  gprof will provide metrics on what functions where called during a particular run of the application.  If the application takes in a variety of inputs, then one run may very well differ from another.

CUnit on the other hand will assist you with unit testing the code.  The latter requires that you have intimate knowledge of the code, because after all, you need to develop a test for each function so that you can verify that it performs as expected, with and without nominal input data.

Thanks Sir for the reply. Shall take note of the points.

> 
It seems that you do not want to make the effort to learn the code in detail, which is generally the case once an application has been fully developed and is already deployed.  Time could also be a factor.

Not at all Sir, just thought it'd be cooler to get an automatic trace of the functions.

> 
Since it seems that the work you are doing is at the professional level, perhaps you should invest in professional-grade tools to perform the task that you need.  

Yup, college internship :)

> 
I was recently introduced to Klocwork (via a training class); it is a static analysis tool that can catch coding problems in software.  Whether it meets your needs or not, I cannot be certain.  Surely an off-the-shelf tool must exist that could meet your needs.
Was just going through the wiki page, shall go through in more details . Thanks for the suggestion.

---

### Post by IAMTubby on 2012-10-30
Is it possible to generate a dynamic function call trace using nm ?
I tried reading the man pages and was excited to see -D, but I guess I have to use some other argument.

Please advise.
Thanks.

---

### Post by spjackson on 2012-10-30
> **IAMTubby said:**
> Is it possible to generate a dynamic function call trace using nm ?
I tried reading the man pages and was excited to see -D, but I guess I have to use some other argument.

No. It is not possible to get a dynamic function call trace without running the program. nm does not run the program.

---

### Post by IAMTubby on 2012-10-30
> **spjackson said:**
> No. It is not possible to get a dynamic function call trace without running the program. nm does not run the program.
okay, I meant using something like $nm -SomeOptiojn <ExecuatbleName>

---

### Post by spjackson on 2012-10-31
OK, let's return to your original post 3 weeks ago, and take your example source and put it in a file fun.c.

Now take this code and put it in a file called dotrace.sh
```

#!/bin/bash

image="$1"

echo "Functions called are as follows"
for line in $(egrep '^E' trace.txt)
do
    address=$(echo $line | sed 's/^.//')
    function_name=$(addr2line -e $image -f -s $address | head -1)
    echo ${function_name}'()'
done

```

Now let's go to my first reply which referred to [http://www.ibm.com/developerworks/linux/library/l-graphvis/]("http://www.ibm.com/developerworks/linux/library/l-graphvis/") and said:
> 
This gives some strong clues.

The source code for that article is linked on the above page, so let's get it and use it.

```

$ chmod +x ./dotrace.sh
$ wget http://www.mtjones.com/developerworks/pvtrace.zip
$ unzip pvtrace.zip
$ gcc -g -finstrument-functions -o fun fun.c pvtrace/instrument.c
$ ./fun
$ ./dotrace.sh
Functions called are as follows
main()
fun1()
fun2()
fun2_1()
fun3()

```
The output is precisely what you described in your first post. Is this what you still want? I'm afraid I've lost track somewhat.

Of course there's scope for improvement to the above script and the trace that is always written to ./trace.txt. However, the basic functionality is what you first described.

---

### Post by IAMTubby on 2012-10-31
> **spjackson said:**
> OK, let's return to your original post 3 weeks ago, and take your example source and put it in a file fun.c.

Now take this code and put it in a file called dotrace.sh
```

#!/bin/bash

image="$1"

echo "Functions called are as follows"
for line in $(egrep '^E' trace.txt)
do
    address=$(echo $line | sed 's/^.//')
    function_name=$(addr2line -e $image -f -s $address | head -1)
    echo ${function_name}'()'
done

```

Now let's go to my first reply which referred to [http://www.ibm.com/developerworks/linux/library/l-graphvis/]("http://www.ibm.com/developerworks/linux/library/l-graphvis/") and said:

The source code for that article is linked on the above page, so let's get it and use it.

```

$ chmod +x ./dotrace.sh
$ wget http://www.mtjones.com/developerworks/pvtrace.zip
$ unzip pvtrace.zip
$ gcc -g -finstrument-functions -o fun fun.c pvtrace/instrument.c
$ ./fun
$ ./dotrace.sh
Functions called are as follows
main()
fun1()
fun2()
fun2_1()
fun3()

```
The output is precisely what you described in your first post. Is this what you still want? I'm afraid I've lost track somewhat.

Of course there's scope for improvement to the above script and the trace that is always written to ./trace.txt. However, the basic functionality is what you first described.
Sir, thanks a lot for the reply. I'm trying. Will get back to you in an hour's time.

---

### Post by IAMTubby on 2012-10-31
> **spjackson said:**
> OK, let's return to your original post 3 weeks ago, and take your example source and put it in a file fun.c.

Now take this code and put it in a file called dotrace.sh
```

#!/bin/bash

image="$1"

echo "Functions called are as follows"
for line in $(egrep '^E' trace.txt)
do
    address=$(echo $line | sed 's/^.//')
    function_name=$(addr2line -e $image -f -s $address | head -1)
    echo ${function_name}'()'
done

```

Now let's go to my first reply which referred to [http://www.ibm.com/developerworks/linux/library/l-graphvis/]("http://www.ibm.com/developerworks/linux/library/l-graphvis/") and said:

The source code for that article is linked on the above page, so let's get it and use it.

```

$ chmod +x ./dotrace.sh
$ wget http://www.mtjones.com/developerworks/pvtrace.zip
$ unzip pvtrace.zip
$ gcc -g -finstrument-functions -o fun fun.c pvtrace/instrument.c
$ ./fun
$ ./dotrace.sh
Functions called are as follows
main()
fun1()
fun2()
fun2_1()
fun3()

```
The output is precisely what you described in your first post. Is this what you still want? I'm afraid I've lost track somewhat.

Of course there's scope for improvement to the above script and the trace that is always written to ./trace.txt. However, the basic functionality is what you first described.
Sir, I guess I'm doing a small mistake somewhere, This is the output I get
```

Functions called are as follows
addr2line: '-f': No such file
()
addr2line: '-f': No such file
()
addr2line: '-f': No such file
()
addr2line: '-f': No such file
()
addr2line: '-f': No such file
()
addr2line: '-f': No such file
()
addr2line: '-f': No such file
()

```

---

### Post by spjackson on 2012-10-31
My mistake. I originally had the program name fixed in the script. It is now an argument.
```

./dotrace.sh fun

```
There is a bit of a clue on line 3 of the script.
```

image="$1"

```

---

### Post by IAMTubby on 2012-10-31
> **spjackson said:**
> My mistake. I originally had the program name fixed in the script. It is now an argument.
```

./dotrace.sh fun

```
There is a bit of a clue on line 3 of the script.
```

image="$1"

```
Sir, that was wonderful. Thanks a lot, it works fine.
However, I have 1 more question in something that's not entirely related to the thread, but necessary for me to get my application working.
I have a lot of files in an application I'm working on. Is there a way to add this line
```
gcc -g -finstrument-functions -o fun fun.c pvtrace/instrument.c

```
to all of those files from maybe the shell(as in, without editing individual makefiles, far too many to edit individually).
The gcc part of my makefiles look like this, 
```

%.o : %.cpp
        $(GXX) $< -o $@ $(CFLAGS)

```

or 
```

main.o: $(DIR)/main.c
        $(CC) -c $? $(CFLAGS)

```

Thanks a lot Sir for the help.

---

### Post by IAMTubby on 2012-10-31
> **spjackson said:**
> 
Now let's go to my first reply which referred to [http://www.ibm.com/developerworks/linux/library/l-graphvis/]("http://www.ibm.com/developerworks/linux/library/l-graphvis/")
Sir, the learning resource you gave me was excellent. Thanks a lot :). I found it very helpful.

Maybe, our very own ubuntuforums.org should follow the graph kind of an approach, by which, this reply would have come under your post, 2 posts back, instead of coming in serial order of date/time posted. Will make it easier for a person viewing this thread after 5 years. Just a random thought :)

Still figuring out a way to apply the change to all the files in my application..

---

### Post by IAMTubby on 2012-10-31
> **spjackson said:**
> 
Sir, I would like to ask the above question on a different thread, not to mix with the original discussion.
Marking the thread as solved. But, further replies about the makefile option would be more than welcome.
Thanks a lot once again! 

PS : The thread about a possible make option is on [http://ubuntuforums.org/showthread.php?p=12329538#post12329538](http://ubuntuforums.org/showthread.php?p=12329538#post12329538)

---

### Post by IAMTubby on 2012-11-08
> **spjackson said:**
> ```
./dotrace.sh fun
```
Sir,This is 1 week old, but I have a question.

I got the trace working with the dotrace.sh script you provided.But I'm not able to get the graph trace. I tried running 
```
dot -Tjpg graph.dot -o graph.jpg
```. 
This is what I get on running the above
```
 
$ dot -Tjpg graph.dot -o graph.jpg
-bash: dot: command not found

```

I do have the necessary files. This is the output of ls
```
dotrace.sh  fun.c     graph.dot     pvtrace       trace.txtfun         gmon.out  instrument.c  pvtrace.zip
```

I tried to read the manual for dot utility mentioned in the Resources on the webpage you gave, but it says "Page not found"

Please advise.
Thanks.

---

### Post by spjackson on 2012-11-08
```

$ dot
The program 'dot' is currently not installed.  You can install it by typing:
sudo apt-get install graphviz

```

---

### Post by IAMTubby on 2012-11-14
> **spjackson said:**
> ```

$ dot
The program 'dot' is currently not installed.  You can install it by typing:
sudo apt-get install graphviz

```
Sir, Yes I got it working :)
But may I ask just 1 more question on this topic. I did a sudo apt-get remove after getting it to work, because I wanted to install from source. I found the source at [http://www.graphviz.org/Download_source.php](http://www.graphviz.org/Download_source.php) and successfully did a sudo make install in ~/Desktop/local. 
These are the steps I followed
```

wget http://www.graphviz.org/pub/graphviz/stable/SOURCES/graphviz-2.28.0.tar.gz
unzip graphviz-2.28.0.tar.gz
cd graphviz-2.28.0
mkdir -p $HOME/local
./configure --prefix=$HOME/local
make clean
make
make install

```

Now my ~/Desktop/graphviz-2.28.0 contains
```

aclocal.m4       config.h.in    doc                 iffe         Makefile.old
ast_common.h     config.h.old   dot.demo            INSTALL      NEWS
ast_common.h.in  config.iffe    Doxyfile            INSTALL.old  plugin
AUTHORS          config.log     Doxyfile.in         lib          plugin.demo
autogen.sh       Config.mk.old  FEATURE             libltdl      README
awk              config.status  features            libtool      rtest
builddate.h      configure      graphs              m4           share
ChangeLog        configure.ac   graphviz.7          macosx       stamp-h1
cmd              configure.old  graphviz.sln        makearch     tclpkg
compat_getopt.h  contrib        graphviz.spec       Makeargs     windows
compat.h         COPYING        graphviz.spec.in    Makefile
config           cpl1.0.txt     graphviz.vcproj     Makefile.am
config.h         debian         graphviz_version.h  Makefile.in

```

and ~/Desktop/local contains
```
bin  include  lib  share

```

How do I proceed ?
When I try doing *dot -Tjpg graph.dot -o graph.jpg*, it still gives me the error
```

The program 'dot' is currently not installed.  You can install it by typing:
sudo apt-get install graphviz

```

Thanks.

---

