---
title: "I managed to bring Ubuntu down!"
date: 2005-06-03
forum: Programming Talk
---

### Post by agger on 2005-06-03
Or rather, my program did:

---
[HTML]
<pre>
#include <stdio.h>
#include <malloc.h>

main () 
        char *p;
        long n = 0;
        int kilo = 1024;
        int mega = kilo*kilo;
        int delta = 4;
        while ((p = (char *) malloc(delta)) != NULL) {
                if (n%mega== 0) {
                     printf("%d Mb allocated\n", n/mega);
                }
                n+=delta;
        }
        printf("Managed to allocate %d bytes before crashin ...\n", n);

}
<pre>
[/HTML]
---
OK, this is clearly memory-hogging, as everybody would agree.
The program (with delta=4 as here) severely slows down the system,
and caused my Firefox and Thunderbird to die (disappear completely).
Fun to see in the system monitor, but isn't there some sort of a security issue here - I mean, shouldn't the kernel or whatever program manages the various processes detect this kind of antisocial behaviour and give offending applications lower priority so they won't interfere with the business of other users?

Because someone with malicious intent *might* write a similar program which 
also reserves enough memory to make the system useless but not enough to get itself killed?

---

### Post by thumper on 2005-06-03
A couple of things.

You are fragmenting the heap something wicked, but you probably know that already.

Most likely firefox and thunderbird failed due to poor defensive programming.  Many programs still just expect to be able to allocate memory and most don't check to make sure that it has been allocated before dereferencing it, or fail to catch a memory exception.

Most likely if C, then malloc, assign into null pointer causes segmentation violation and program dies (SIGSEGV).

Since your program very quickly grabs all available memory, the moz apps probably try to allocate a block of memory to do something, fail and crash and burn.

Absolutely nothing to do with the security of the OS kernel, and everything to do with the defensive quality of the moz apps.

Tim

---

### Post by jerome bettis on 2005-06-03
just tried it with firefox and thunderbird open from a terminal so i could see what happened when they went down.

they didn't.  :-P

328 Mb allocated
329 Mb allocated
330 Mb allocated
331 Mb allocated
Killed

at about 141 mb the system 'froze' and my hard drive starting going nuts for a few minutes.  then it went real quick up 331.  i'm using the ck patchset on this kernel so that very well might have something to do with it.  [http://kem.p.lodz.pl/~peter/cko/](http://kem.p.lodz.pl/~peter/cko/)

oh yeah you're missing the { after main() ...

---

### Post by thumper on 2005-06-03
Often hard to replicate exact memory errors like this.

Thunderbird may have tried to download mail while the "memory hog" app was running, firebird may have been reloading a document.

Not many apps crash while doing nothing  ;-)

---

### Post by LordHunter317 on 2005-06-03
[QUOTE=thumper]Most likely firefox and thunderbird failed due to poor defensive programming.[/quote]No, they most likely failed due to the POS OOM killer in the kernel, which nailed the wrong process.

> Many programs still just expect to be able to allocate memory and most don't check to make sure that it has been allocated before dereferencing it, or fail to catch a memory exception.

Most likely if C, then malloc, assign into null pointer causes segmentation violation and program dies (SIGSEGV).Firefox and Thunderbird are mostly C++ and I belive use mostly C++ memory management.  Meaning if they die due to lack of memory, it'll be with a SIGABRT, not a SIGSEGV.

> Absolutely nothing to do with the security of the OS kernel, and everything to do with the defensive quality of the moz apps.Actually, you're quite wrong in this case.  Firefox and Mozilla probably did nothing to cause their own deaths.

> Not many apps crash while doing nothing They do on Linux if you run out of memory.

The acid test of course, is to set /proc/sys/vm/overcommit_memory to "2" and rerun the program.  It should quickly run out of memory to allocate.

---

### Post by vague- on 2005-06-03
[QUOTE=agger]Because someone with malicious intent *might* write a similar program which also reserves enough memory to make the system useless but not enough to get itself killed?[/QUOTE]

That is what resource limits are for.  Give each user what they should need, if they have a problem with the limit they can always contact you.

---

### Post by thumper on 2005-06-03
[QUOTE=LordHunter317]No, they most likely failed due to the POS OOM killer in the kernel, which nailed the wrong process.[/QUOTE]
Well I guess my lack of understanding about the kernel is showing.  :?

[QUOTE=LordHunter317]Firefox and Thunderbird are mostly C++ and I belive use mostly C++ memory management.  Meaning if they die due to lack of memory, it'll be with a SIGABRT, not a SIGSEGV.[/QUOTE]
Surely if it was C++ then they would get a bad_alloc exception thrown and not a SIGABRT?

[QUOTE=LordHunter317]They do on Linux if you run out of memory.[/QUOTE]
What I was meaning by this was the app not doing anything, only awaiting input from the user, and another app using up the memory.

Thanks for the input though.

---

### Post by LordHunter317 on 2005-06-03
> **thumper]Surely if it was C++ then they would get a bad_alloc exception thrown and not a SIGABRT?[/quote]And if the exception unwinds the stack all the way to the bottom the default behavior is to throw SIGABRT.  GCC before 3.4 simply throws SIGABRT said:**
> What I was meaning by this was the app not doing anything, only awaiting input from the user, and another app using up the memory.Which is correct.  What's incorrect is the expectation that if the application is nothing, it won't die due to memory pressure on Linux (unless overcommit_memory is set to '2').    Simply enough too much RAM in use can cause death, even if the application is completely idle.

If it was just about any other platform, your explanation would be perfectly correct.

As an aside, most servers should obviously have overcommit_memory set to '2' so a runaway process doesn't kill something else critical.

---

### Post by agger on 2005-06-06
[QUOTE=LordHunter317]And if the exception unwinds the stack all the way to the bottom the default behavior is to throw SIGABRT.  GCC before 3.4 simply throws SIGABRT; after, you get the exception name and output out of the default handler.

Which is correct.  What's incorrect is the expectation that if the application is nothing, it won't die due to memory pressure on Linux (unless overcommit_memory is set to '2').    Simply enough too much RAM in use can cause death, even if the application is completely idle.

If it was just about any other platform, your explanation would be perfectly correct.

As an aside, most servers should obviously have overcommit_memory set to '2' so a runaway process doesn't kill something else critical.[/QUOTE]
 Well, thanks for the plentiful response!

But does this mean that if I have a system with N users I can put ressource limits on each, so that no one of them may at any time use more than 1/N of the CPU cycles and 1/N of the memory?

(Of course, often this distribution would be uneven - e.g., between "users" and "staff").

---

