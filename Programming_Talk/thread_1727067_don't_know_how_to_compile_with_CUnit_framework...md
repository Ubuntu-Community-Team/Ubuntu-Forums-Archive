---
title: "don't know how to compile with CUnit framework.."
date: 2011-04-12
forum: Programming Talk
---

### Post by Praveen30 on 2011-04-12
i went to this site--
[http://w3.scs.ryerson.ca/~schi/cps707/]("http://w3.scs.ryerson.ca/%7Eschi/cps707/")

In "users without administration permission", it is written here--
"The files required for compiling will be found in the **CUnit/include and CUnit/lib **directories".But after extracting the files i am not able to find include and lib...i am including some screenshots what i am getting...please tell me how to compile it...

---

### Post by dwhitney67 on 2011-04-12
Step 1:  Download CUnit package from Source Forge.

Step 2:  Find where you saved the package on your system, and uncompress it:
```

tar xjf CUnit-2.1-2-src.tar.bz2

```

Step 3: Go into the CUnit-2.1.2 directory.
```

cd CUnit-2.1.2

```

Step 4: Run the following sequence of commands:
```

mkdir -p $HOME/local
./configure --prefix=$HOME/local
make clean
make
make install

```

Step 5:  Goto the directory $HOME/local.  Verify that you have the following sub-directories: doc, include, lib, and share.  Each of these should have the products you seek.

Step 6.  To build an application using CUnit, something like this is used:
```

gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog

```

Note:  In your source code, include CUnit header files such as:
```

#include <CUnit/CUnit.h>
...

```

---

### Post by Praveen30 on 2011-04-12
Thanks...now i am able to locate those files...but i am getting error after compilation--

praveen@praveen-laptop:~/Desktop/one$ gcc -Wall -I$HOME/local/include/CUnit Basic_Simple.c -L$HOME/local/lib -lcunit -o Basic_Simple

praveen@praveen-laptop:~/Desktop/one$ ./Basic_Simple

./Basic_Simple: error while loading shared libraries: libcunit.so.1: cannot open shared object file: No such file or directory

i am trying to run this first time so please help....

---

### Post by dwhitney67 on 2011-04-12
> **Praveen30 said:**
> 

./Basic_Simple: error while loading shared libraries: libcunit.so.1: cannot open shared object file: No such file or directory


Sorry about that; I forgot to offer the instructions to run your application.  Try something like:
```

LD_LIBRARY_PATH=$HOME/local/lib ./Basic_Simple

```

Alternatively, you can add the LD_LIBRARY_PATH to your ~/.bashrc file, thus making it available each/every time you log in.  Something like:
```

export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$HOME/local/lib

```
If you go this way, please source your ~/.bashrc file, then run your program:
```

<edit ~/.bashrc>

source ~/.bashrc

./Basic_Simple

```

---

### Post by Praveen30 on 2011-04-12
> **dwhitney67 said:**
> Sorry about that; I forgot to offer the instructions to run your application.  Try something like:
```

LD_LIBRARY_PATH=$HOME/local/lib ./Basic_Simple

```Alternatively, you can add the LD_LIBRARY_PATH to your ~/.bashrc file, thus making it available each/every time you log in.  Something like:
```

export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$HOME/local/lib

```If you go this way, please source your ~/.bashrc file, then run your program:
```

<edit ~/.bashrc>

source ~/.bashrc

./Basic_Simple

```

Hats off to you.
Thanks a lot!!!!:P

---

### Post by Praveen30 on 2011-04-12
Can you tell me one more thing after executing commands, i am getting this--
[PHP]
     CUnit - A unit testing framework for C - Version 2.1-2
     http://cunit.sourceforge.net/


Suite: Simple_suite1
  Test: test of maxi ...FAILED
    1. Basic_Simple.c:34  - CU_ASSERT_EQUAL(maxi(3,6),3)

Run Summary:    Type  Total    Ran Passed Failed Inactive
                         suites      1         1     n/a     0           0
                          tests       1         1      0       1           0
                        asserts     2          2     1        1         n/a

Elapsed time =    0.000 seconds
Testing completes..
[/PHP]can you please explain these things...what is this n/a and all other things in short.....???

---

### Post by dwhitney67 on 2011-04-12
n/a is an abbreviation for "not applicable".

The results you posted, which by the way would have looked better if enclosed in CODE tags, merely offer a summary of the test results.

For example, the following [test program]("http://w3.scs.ryerson.ca/~schi/cps707/basic-example.html") from the CUnit web-site produces the following results:
```

     CUnit - A unit testing framework for C - Version 2.1-2
     http://cunit.sourceforge.net/


Suite: Suite_1
  Test: test Deposit ...passed
  Test: test Withdraw ...passed
  Test: test set balance ...passed
  Test: test get balance ...FAILED
    1. testBank.c:35  - CU_ASSERT_EQUAL(getBalance(),5000)

Run Summary:    Type  Total    Ran Passed Failed Inactive
              suites      1      1    n/a      0        0
               tests      4      4      3      1        0
             asserts      4      4      3      1      n/a

Elapsed time =    0.000 seconds

```
As indicated above, only one test suite exists, and thus only one was executed.  Test suites are not evaluated for pass/fail, thus in the Passed column "n/a" is shown.

In the test suite, there are 4 tests, of which each was executed.  Of these tests, 3 Passed and 1 Failed.

There were a total of 4 assert() calls in the test suite (this does not imply that there is 1 assert() per test, but in this case it is probably true).  Anyhow, 3 succeeded and 1 failed.

---

### Post by mehwish on 2012-02-27
Hi,

I am new to CUnit frame work .. Can you please share a basic program which help in crating test cases.

Suppose we want to test a max function ...
My .c file is like this

# include <stdio.h>
# include <stdlib.h>

/*int main ()
{
   int maxi(int, int);
   int i=2;
   int j=4;
   int result = maxi(i,j);
   return 0;
}
*/

    int maxi(int i1, int i2)
    {
      return (i1 > i2) ? i1 : i2;
    }

and the test file is

# include <stdio.h>
# include <stdlib.h>
# include <CUnit/CUnit.h>
# include "max.c"

int main ()
{

   CU_ASSERT( maxi(2, 4) == 4);
   CU_ASSERT( maxi(0,-4) == 0);
   CU_ASSERT( maxi(2, 2) == 2);
}

When i am running this code then m getting error as
CU_assertImplementation: Assertion `((void *)0) != f_pCurSuite' failed.


Please help :(

---

### Post by IAMTubby on 2012-09-17
> **dwhitney67 said:**
> Step 1:  Download CUnit package from Source Forge.

Step 2:  Find where you saved the package on your system, and uncompress it:
```

tar xjf CUnit-2.1-2-src.tar.bz2

```

Step 3: Go into the CUnit-2.1.2 directory.
```

cd CUnit-2.1.2

```

Step 4: Run the following sequence of commands:
```

mkdir -p $HOME/local
./configure --prefix=$HOME/local
make clean
make
make install

```

Step 5:  Goto the directory $HOME/local.  Verify that you have the following sub-directories: doc, include, lib, and share.  Each of these should have the products you seek.

Step 6.  To build an application using CUnit, something like this is used:
```

gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog

```

Note:  In your source code, include CUnit header files such as:
```

#include <CUnit/CUnit.h>
...

```
dwhitney, I'm sorry to revive a 1-year old thread, but I promise not to make too many posts here. Just had a doubt regarding the compilation steps mentioned in step4.
Why is it that if you follow the normal procedure, by which I mean
```

./configure
make clean
make 
make install

```
it won't work ?

If it works on a directory called $HOME/local, then , it should work on say, the /$HOME/Desktop also right, which is the default path for me when I open a terminal ?

Of course, thanks to you, I have it working, but I was stuck for a few days, because the normal procedure doesn't work and I didn't know that you have a create a directory called $HOME/local.

For future purposes.. how are users supposed to know of these special steps/considerations while building a software from source ?

Thanks.

---

### Post by Bachstelze on 2012-09-17
It probably does not matter at all where CUnit is installed. I haven't read the thread but perhaps dwhitney67 said to install it in $HOME because OP does not have root privileges, or something of that sort. Anyway, what matters is that after you have installed CUnit, wherever that may be, you have to make the compiler aware of where to find the headers and libraries. This is exactly what the [font=monospace]-I[/font] and [font=monospace]-L[/font] flags do in step 6 above. If you installed CUnit somewhere else, you just specify that path instead of [font=monospace]$HOME/local[/font], and it will work just as well.

---

### Post by IAMTubby on 2012-09-17
> **Bachstelze said:**
> It probably does not matter at all where CUnit is installed. I haven't read the thread but perhaps dwhitney67 said to install it in $HOME because OP does not have root privileges, or something of that sort. Anyway, what matters is that after you have installed CUnit, wherever that may be, you have to make the compiler aware of where to find the headers and libraries. This is exactly what the [font=monospace]-I[/font] and [font=monospace]-L[/font] flags do in step 6 above. If you installed CUnit somewhere else, you just specify that path instead of [font=monospace]$HOME/local[/font], and it will work just as well.
ohh okay :).
I'll try installing elsewhere and invoke from that path and get back later.

Don't have access to the files now.

Thanks a lot.

---

### Post by IAMTubby on 2012-10-10
> **IAMTubby said:**
> ohh okay :).
I'll try installing elsewhere and invoke from that path and get back later.

Don't have access to the files now.

Thanks a lot.
Thanks a lot Bachstelze, that worked :)

---

### Post by IAMTubby on 2012-10-10
> **dwhitney67 said:**
> 
dwhitney,
I have most of the things figured out, but I don't quite understand what CU_PASS(message) and CU_FAIL(message) do.
At first, I though it was a printf-like message, which can be put in anywhere and it would just print to know where control has reached without performing any logical operation/checking for outcome of the test.

But I'm getting weird results.
For eg, 
Say I'm testing the below function
```

void testFPRINTF(void)//That's all my test function is, no other code
{
   CU_PASS("works ");
}

```, it gives
```

Suite: Suite_1
  Test: This is test of fprintf() ...passed

Run Summary:    Type  Total    Ran Passed Failed Inactive
              suites      1      1    n/a      0        0
               tests      1      1      1      0        0
             asserts      1      1      1      0      n/a

```

But if the code is, 
```

void testFPRINTF(void)
{
   CU_FAIL("fails ");
}

```, it prints
```

Suite: Suite_1
  Test: This is test of fprintf() ...FAILED
    1. test.c:43  - CU_FAIL("fails ")

Run Summary:    Type  Total    Ran Passed Failed Inactive
              suites      1      1    n/a      0        0
               tests      1      1      0      1        0
             asserts      1      1      0      1      n/a

```

**These are my doubts**
1.In the above code, I'm not making any assertion, right ? CU_PASS and CU_FAIL are not assertions, but it gets displayed in the output.

2.Even if we assume CU_PASS and CU_FAIL to be assertions, how does the result of the test and the assertion, depend on just these statements.According to the CUnit documentation, CU_PASS and CU_FAIL are not supposed to make any logical decisions. I quote from the documentation, *Register a passing assertion with the specified message. No logical test is performed.*

3.Why is that CU_FAIL atleast prints a message, but the same code with CU_PASS doesn't print anything ?

4. I feel like I haven't understood CU_PASS and CU_FAIL at all. Otherwise, such a simple API won't give me so many aberrations, when the other assertions were straight-forward.

5.> **dwhitney67 said:**
> 
For example, the following [test program]("http://w3.scs.ryerson.ca/~schi/cps707/basic-example.html") from the CUnit web-site produces the following results:

Is this link moved to a different location ?


Please advise.

---

### Post by dwhitney67 on 2012-10-10
I haven't used CUnit before, so I'm not that familiar with it.

If I had to guess, I would assume that CU_PASS and CU_FAIL (and other related friends) are macros.  If you care to, you can look these up in the CUnit header file(s).

When a test passes, it seems logical that one would only care about the result of the whole test.  If a test fails, then it is immensely helpful to know exactly where the test failed, and due to what reason.  Hence the reason CU_FAIL prints the location of the error.

---

### Post by IAMTubby on 2012-10-10
> **dwhitney67 said:**
> 
When a test passes, it seems logical that one would only care about the result of the whole test.  If a test fails, then it is immensely helpful to know exactly where the test failed, and due to what reason.  Hence the reason CU_FAIL prints the location of the error.
dwhitney, Thanks for that, yes that should be the reason why only "passed" is mentioned.

The rest I shall look into the required files, and post the answer on this thread if I manage to figure out.

Thanks a lot Sir.

---

### Post by IAMTubby on 2012-10-20
> **Bachstelze said:**
> It probably does not matter at all where CUnit is installed. I haven't read the thread but perhaps dwhitney67 said to install it in $HOME because OP does not have root privileges, or something of that sort. Anyway, what matters is that after you have installed CUnit, wherever that may be, you have to make the compiler aware of where to find the headers and libraries. This is exactly what the [font=monospace]-I[/font] and [font=monospace]-L[/font] flags do in step 6 above. If you installed CUnit somewhere else, you just specify that path instead of [font=monospace]$HOME/local[/font], and it will work just as well.
Bachstelze, I tried intalling in a different path and it worked. But what if I don't explicitly mention any path ? I would have thought that the necessaary files(doc, include, lib and share) would have got created in the current directory, but that doesn't seem to happen.


What if I just run these steps ?
```

./configure 
make clean
make
sudo make install

```

It doesn't create the necessary files in the current directory : doc, include, lib and share. 
So where else do the necessary files get created ?

---

### Post by dwhitney67 on 2012-10-20
> **IAMTubby said:**
> 
So where else do the necessary files get created ?

An educated guess... it is created in /usr/local.

What does the output from "sudo make install" indicate???????????

---

### Post by IAMTubby on 2012-10-20
> **dwhitney67 said:**
> An educated guess... it is created in /usr/local.

dwhitney, thanks for the reply. Yes the files do exist there.
But I have a couple of questions
1)Why doesn't this syntax work ? 
```
gcc -Wall -ISomePath -LSomePath -lcunit -o test test.c
```

2)I tried appending /usr/local/lib and /usr/local/include to PATH and my path now looks as follows
```

$ echo $PATH
:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/bin:/usr/local/include

```
And then I tried doing, (Assume test.c contains some CUnit using code) 
```

$gcc test.c
$gcc -lcunit test.c

```
But no, it doesn't detect. Why ?

> 
What does the output from "sudo make install" indicate???????????
Hmm, Sir, I didn't get that ?

Thanks.

---

### Post by dwhitney67 on 2012-10-21
Get into the habit, when compiling/linking, to place compiler options first, then your module, and finally the linker options.  The ordering matters!

For example:
```

gcc -Wall -I/usr/local/include -o test test.c -L/usr/local/lib -lcunit

```

Library paths are not meant to be stored in PATH, but instead within LD_LIBRARY_PATH.  PATH is used to store the paths to commonly used executable files.  The exception to this rule is when dealing with Windoze, but since we're here in Linux land there's no point discussing it. 

If you share a system with many users, you may opt to add a particular library path to the system library cache.  This is done via ldconfig.  If you are not familiar with this utility, don't worry about it.  For more information on it, summon the man-page.

---

