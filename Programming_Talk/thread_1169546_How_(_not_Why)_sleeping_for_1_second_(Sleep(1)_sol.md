---
title: "How ( not Why) sleeping for 1 second (Sleep(1) solved a &quot;segmentation fault&quot; problem"
date: 2009-05-25
forum: Programming Talk
---

### Post by eric stockman on 2009-05-25
While testing a C++ program I was confronted with the dreaded "segmentation fault" problem . The program ( a spreadsheet affair ) made heavy use of dynamic memory-allocation with the typical C++ usage of "new" and "delete" .
( C++ is maybe a better C , but certainly not an easier C . The language contains some dark corners ) . 
In order to follow up the allocation of the memory I rewrote the program to allocate and free the memory myself with the old faithfull's "calloc" and "free" .Result ? Just the same ?
So I sprinkled  the source with lots of printf()'s and getchar()'s  to follow-up where things where going wrong.
Result ? No more segmentation-faults ?? I could step through the test- program without any problem.

After commenting-out the getchar's without changing something else the fault re-appeared again ??
I could trace the error occured in the first phase of the program , so after constructing my spreadsheet-object and allocating the memory and before the first usage of the object I coded a sleep(1) instruction : result no more segmentation faults ???
I have to sleep only once , next time the object is used everything works smoothly.

This business goes beyond my capabilities . One should think that once an object is constructed and calloc() returns all the reserved memory is available and usable ?
We are not talking about reserving some giga-bytes here , at most a kilo-byte is involved .
Who said 'computer-programming is so boring ' ?
E.S

---

### Post by jespdj on 2009-05-25
Without more details (is the program multi-threaded? what does the code look like? etc.) it's very hard to say what might be the cause of this.

Next time use a programming language that doesn't require you do to manual memory management...

---

### Post by MeLight on 2009-05-25
Some code would be appreciated

---

### Post by dwhitney67 on 2009-05-25
> **eric stockman said:**
> While testing a C++ program I was confronted with the dreaded "segmentation fault" problem . The program ( a spreadsheet affair ) made heavy use of dynamic memory-allocation with the typical C++ usage of "new" and "delete" .
( C++ is maybe a better C , but certainly not an easier C . The language contains some dark corners ) . 
In order to follow up the allocation of the memory I rewrote the program to allocate and free the memory myself with the old faithfull's "calloc" and "free" .Result ? Just the same ?
So I sprinkled  the source with lots of printf()'s and getchar()'s  to follow-up where things where going wrong.
Result ? No more segmentation-faults ?? I could step through the test- program without any problem.

After commenting-out the getchar's without changing something else the fault re-appeared again ??
I could trace the error occured in the first phase of the program , so after constructing my spreadsheet-object and allocating the memory and before the first usage of the object I coded a sleep(1) instruction : result no more segmentation faults ???
I have to sleep only once , next time the object is used everything works smoothly.

This business goes beyond my capabilities . One should think that once an object is constructed and calloc() returns all the reserved memory is available and usable ?
We are not talking about reserving some giga-bytes here , at most a kilo-byte is involved .
Who said 'computer-programming is so boring ' ?
E.S

Using 'new' and 'delete' are the proper things to do in C++; you should not be using free(), malloc(), or calloc().

Next time try to fix the problems with your application rather than mask them with a kludge.

calloc() reserves memory, but it does not construct the object.

Post some code if you need genuine help.

---

### Post by soltanis on 2009-05-25
Calloc doesn't initialize objects; in fact, it initializes the allocated memory to 0's.

You are right that calloc (or malloc) doesn't return until the memory is actually allocated for you to use, but just because you called the function doesn't mean it was successful; check the pointers to make sure it is not NULL.

And if you are trying to initialize an object into the memory, you do need to use new and delete, not malloc and free, because those will actually call the constructors and destructors.

More likely than not, when you were adding debug statements, you changed something in the code that kept it from breaking. You really need to use a debugger to step through your code and check the state of variables (compile with the -g option for extra debugging and line info) so that you can pin down this issue.

EDIT.

Apparently, Linux has this issue where it may allocate memory that isn't actually free (read under bugs in man 3 malloc); but this is only under conditions where the system is really out of memory. I doubt this is the cause of your problem.

---

### Post by samjh on 2009-05-26
> **soltanis said:**
> Apparently, Linux has this issue where it may allocate memory that isn't actually free (read under bugs in man 3 malloc); but this is only under conditions where the system is really out of memory. I doubt this is the cause of your problem.

That "bug" caused two multi-page debates on this very forum.

See:
[http://ubuntuforums.org/showthread.php?t=612606](http://ubuntuforums.org/showthread.php?t=612606)
[http://ubuntuforums.org/showthread.php?t=614962](http://ubuntuforums.org/showthread.php?t=614962)

---

### Post by Quikee on 2009-05-26
> How ( not Why) sleeping for 1 second (Sleep(1) solved a "segmentation fault" prob

You did not solve a problem with "sleeping for 1 second". You don't solve problems in this way - you just (temporary) avoided the problem. First you have to know what the problem is to be able to solve it, but you obviously don't know this.

---

### Post by eric stockman on 2009-05-26
Thanks every soul for reacting.
 My program works now , but still with the sleep(1) in it !
 Any attempt to comment-out this one-time-instruction is punished with a 'segmentation fault ' ??? .
 I have made a shorter test-version of the program code ( just the crucial and offending section ) .
Is there a way and place where I can put this source-code on the forum so the c- & cpp-savys can check this out for themselves ?

TIA .
eric stockman

---

### Post by Zugzwang on 2009-05-27
> **eric stockman said:**
> 
Is there a way and place where I can put this source-code on the forum so the c- & cpp-savys can check this out for themselves ?


Even easier: Comment that command out & use valgrind for getting hints on where the problem is likely to be.

---

### Post by Reiger on 2009-05-27
> **eric stockman said:**
> Is there a way and place where I can put this source-code on the forum so the c- & cpp-savys can check this out for themselves ?

TIA .
eric stockman

You can attach files to your post through "Manage Attachments" (conveniently stashed away below the "post reply" etc. buttons). Be aware that there is usually something like a 1 MB limit to these file uploads.

---

### Post by sid.rao on 2011-08-29
Hi Eric Stokman,

I know this thread ended some time back but were you able to solve this problem, did u identify why sleep was solving your problem.??
I am facing the exact same situation here. Any suggestions would be much appreciated.

Thanks.

---

### Post by HappyHoward on 2011-08-29
I have been in this situation. My recommendation would be (as someone already suggested) to use valgrind (with memory checking enabled) to find the source of the problem.

As an anecdote here's what happened to me:
I was working in a quite big project, using C++ with QT3. Our application worked well until i did some simple changes. Under some circumstances some text on the screen should turn red. After that the program started crashing, but not at the exact position of the modified code. If I added some random code ( like a debug output) the crash would move to a different place or disappear.

It turned out the problem was in a lib we used, developed by another department. This code (a class defined in the lib we used) illustrates the problem:

```

class Object
{
   public:
      Object();

   private:
      int mNumber;
      #ifdef EXTRA_DATA
      int extra_data;
      #endif
};

```

As you can see the size of Object depends on whether EXTRA_DATA is defined or not. When the lib was built they had EXTRA_DATA defined, but we knew nothing of that flag so when we built our application and linked their lib into our app, our view of the size of Object differed. I don't remember exactly how, but this lead to these crashes.

---

### Post by dwhitney67 on 2011-08-29
> **sid.rao said:**
> did u identify why sleep was solving your problem.??


As was discussed earlier in this thread, usage of sleep() does not, and will not, solve any problem.  It may, if one is lucky, mask the problem.

If you are having trouble with your code, consider opening a new thread where you can post your code.  Otherwise use **valgrind** to examine your code during runtime to analyse where/if there are any issues.

---

