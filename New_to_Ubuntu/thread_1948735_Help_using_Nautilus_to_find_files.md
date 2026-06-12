---
title: "Help using Nautilus to find files"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-28
I just discovered Nautilus (I just upgraded to 10.10) can't find a file even when I direct it to the folder it resides in. I'm using "*.PDF" and "*.pdf" in the search function of Nautilus, starting the function at the folder level, where several PDFs live. 

Nautilus comes back with zero results. I'm wondering what I might be doing wrong (maybe the wrong thing is to use Nautilus)? 

If N is really that undependable, could someone tell me the name of a more effective file browser? Many thanks.

---

### Post by westie457 on 2012-03-28
Hi, try using pdf with no other characters or punctuation marks. That should work.

---

### Post by JC Cheloven on 2012-03-28
If your problems remain, or simply you don't like the nautilus way, consider using a dedicated search tool, as searchmonkey or catfish. Both are in the repos.
JC

---

### Post by jps2012 on 2012-03-28
Many thanks, JC and Westie. Using "pdf" alone works. I'd been reading about wildcards, and just assumed that the same syntax that would work in bash would work in Nautilus. I've learned my lesson. 

I'll take a look at SearchMonkey now. 

JPS

---

### Post by jps2012 on 2012-03-28
I asked for it, and I got it. 

I installed SearchMonkey and just ran my first search for the word "ubuntu" as a test. It's been processing for a full minute, and reports it's at 30% completion. Wow, that's slow. I'm taking a wild guess when I say SearchMonkey might take 15 times as long as the same type of search in Finder on Mac OS X. Yikes!

I'm going to try Catfish ... but I already see a problem in using it. Under Software Center, Catfish isn't listed (in the left column of the browser) as one of my installed programs (it doesn't appear under Installed Software).

But if I go to Get Software,  Catfish only offers a "Remove" action, not an install. 

Ubuntu seems to be telling me I **have** Catfish installed, and I **don't have** Catfish installed. (Obviously the Software Center is having some issues with reading my system. A bug that comes with 10.10?)

Isn't it ironic that if I ask Ubuntu to help me find a better file browser, Ubuntu gets lost in an existential endless interrogatory loop? 

Well, I tried to execute Catfish from the command line, which tells me (authoritatively, rather than "maybe/maybe not") Catfish is not installed. I'm downloading it now.

I might then try "sudo apt-get bertrand-russell" to help the Software Center overcome its existential crisis.

---

### Post by jps2012 on 2012-03-28
I just ran a test for find "pdf" using Catfish, versus using SearchMonkey for the same search on my home folder. 

Catfish took less than 3 seconds to locate all files containing "pdf" as text or part of a file name. 

SearchMonkey took more than 3 minutes to complete the same search. 

If we're voting on the basis of speed alone (instead of also looking at the design of the GUI, the range of options offered by each program, whether searches can be recursive, etc.) my vote definitely goes for Catfish. 

Thanks for telling me about it, JC.

---

