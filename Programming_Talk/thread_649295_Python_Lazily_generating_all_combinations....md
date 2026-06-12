---
title: "Python: Lazily generating all combinations..."
date: 2007-12-24
forum: Programming Talk
---

### Post by CptPicard on 2007-12-24
An interesting Python exercise I decided to try out as this is a fundamental thing I use a lot in my code and I wanted to check out if Python was fast enough for purpose at least some of the time...

Consider a set of alphabet, say, ('a', 'b','c'). Now, we want to create the set of strings of length n that contain all the possible arrangements of the alphabet. Of course we want to do this using a generator, because the complete "realized" list is big.

This was actually borne out of the discussion on a separate thread on whether Python is functional or not. Of course, the concept of iterators/generators/lazy lists is fundamentally based on continuations, which preserve stack.

Python of course doesn't support continuations, and its generators are only "continuation-ish". To demonstrate:

[php]
def combinations(alphabet, length):
	if length == 0:
		yield tuple()
		return
	for x in alphabet:
		for y in combinations(alphabet, length-1):
			yield tuple(x)+y


def generate(stack, alphabet, length):
	if len(stack) == length:
		yield tuple(stack)
		return
	else:
		for x in alphabet:
			stack.append(x)
			generate(stack, alphabet, length)
			stack.pop()

combinations(('a','b','c'), 10)  # ok
generate([], ('a','b','c'), 10)  # not ok
[/php]

The latter method would probably be much more efficient *if* Python's generators preserved stack state... but by all means tell me if the second method is wrong somehow :)

On another note, Merry Christmas everyone. I've got to admit I feel like a no-lifer escaping to try out code right after the rest of the family has gone to bed after a nice evening, on Christmas night no less ;)

EDIT: Some more tests... straight recursion implementation where instead of yield()ing a completed result row, a function is called, is some 3 times faster... of course there are way less function calls.

EDIT2: And Java does in 7 seconds what didn't finish on Python in 10 minutes... I'm not migrating our tools any time soon ;)

---

### Post by LaRoza on 2007-12-24
> **CptPicard said:**
> 
On another note, Merry Christmas everyone. I've got to admit I feel like a no-lifer escaping to try out code right after the rest of the family has gone to bed after a nice evening, on Christmas night no less ;)

Merry Christmas.

I am going to be on here on Christmas also (it is not Christmas yet, still the day before here)

Someone has to patrol the ABT forum answering questions. (me)

---

### Post by kripkenstein on 2007-12-25
> **CptPicard said:**
> 
EDIT: Some more tests... straight recursion implementation where instead of yield()ing a completed result row, a function is called, is some 3 times faster... of course there are way less function calls.

EDIT2: And Java does in 7 seconds what didn't finish on Python in 10 minutes... I'm not migrating our tools any time soon ;)
I'm surprised Python is **that** slow on this task. Can you try to see what happens when you do this non-recursively, i.e., hard-code 10 nested loops? I don't mean it should be coded this way ;) -  just to see if the reason it is slow is because of function calls.

---

### Post by CptPicard on 2007-12-25
Nonrecursive version finished in 6 min 40 sec. Slower than I thought.

As a test, I took a more limited example of solution size 10^7. The first, generator-base solution ran in 2 min 7 s. Nonrecursive is 40s, recursive 1 min 27s. Java is around 0.9s.

So yes... Python is pretty slow in this on all accounts, and function calls are really slow considering that the Java solution is recursive as well, using an int[] as stack. My experience tells me that the C solution would be a little bit faster still but not by much. This is a good example of the effect of the size of your constants when workload explodes combinatorially. You might not notice the difference otherwise, but it is there. Another moral of the story is that compared to other solutions, JIT-compiled Java is actually quite good, and often there is no reason to take the one step further to C.

---

### Post by kripkenstein on 2007-12-25
> **CptPicard said:**
> Nonrecursive version finished in 6 min 40 sec. Slower than I thought.

As a test, I took a more limited example of solution size 10^7. The first, generator-base solution ran in 2 min 7 s. Nonrecursive is 40s, recursive 1 min 27s. Java is around 0.9s.

So yes... Python is pretty slow in this on all accounts, and function calls are really slow considering that the Java solution is recursive as well, using an int[] as stack. My experience tells me that the C solution would be a little bit faster still but not by much. This is a good example of the effect of the size of your constants when workload explodes combinatorially. You might not notice the difference otherwise, but it is there. Another moral of the story is that compared to other solutions, JIT-compiled Java is actually quite good, and often there is no reason to take the one step further to C.
Actually I suspect C would be significantly better than Java in this case. Since the operations are so simple, even two machine ops instead of one would lead to double the speed.

Any chance you can go ahead and see how fast this would be in C? :)

---

### Post by CptPicard on 2007-12-25
Ok, still at the 10^7 example. Without any optimization flags, the C version runs in 0.8-0.9s, which is pretty much the same as the Java version. With -O2, we get 0.3s and -O3, 0.15s.  Goes as low as 0.12s with -fomit-frame-pointer -march=i686 -O9. :) While you're right that yes we're getting substantial increases, Java is still more than adequate... for now :) In simple recursion in this case, fully optimized C is like 700 times faster than Python.

Note that all examples put a bit of load inside the innermost loop by computing the sum of the completed result item. This avoids the possibility that some compiler does some funky dead code optimization by figuring out that nothing is actually done at the end.

---

### Post by Wybiral on 2007-12-25
It's a known fact that CPython has issues with recursion. It's just too slow. I suggest you take a look at [Stackless Python]("http://www.stackless.com/"). It's probably exactly what you're looking for. If you don't want that, then use C and [SWIG]("http://www.swig.org/") to write this bottleneck as a module for Python (if you write it in C, SWIG will turn it into a Python module painlessly).

EDIT:

If C isn't your cup of tea, SWIG handles C++ as well (it will even wrap your classes up into a Python representation!)

---

### Post by the_darkside_986 on 2007-12-25
This is an interesting thread. Is it possible to try it with Psyco, the Python machine-code compiler?

I realized python was painfully slow when I tried to play Frets on Fire version from the repos, but I downloaded the official package from their website, and it uses psyco *.so files and stuff and it runs at a playable speed.

Python seems like such an easy language and good for GUI development. Too bad the implementation is so painfully slow.

---

### Post by CptPicard on 2007-12-25
@Wybiral: Yes, I know, I know.. :) Of course I would have done that already if I had a genuine problem here. I don't want to introduce platform-specifics though as my client is on mostly on Windows and I am on Linux. Python was a possible alternative to Java. I find myself having to refactor my Java a bit too much all the time as I need to introduce quick ad hoc features, and something like duck typing would be cool.

I am, though, trying to lure him into buying us a kick-*** Linux "CPU server" for him to use and for me to remotely administer :)

> **the_darkside_986 said:**
> This is an interesting thread. Is it possible to try it with Psyco, the Python machine-code compiler?

Well, the algorithm itself is so trivial that that certainly it's possible to try. Hack away, I'd be interested in hearing the result. You'll have to rerun everything on the same box of course for it to be comparable ;)

> Python seems like such an easy language and good for GUI development. Too bad the implementation is so painfully slow.

It really depends on your needs. Python if fast enough for most stuff, but when you start going exponential like that, every last instruction starts showing up in the numbers...

---

### Post by Wybiral on 2007-12-25
Certain things are slow in Python, on its own it isn't meant to be a number-crunching language, it's meant to hold together the modules that do the number crunching. But as a HLL it's really not that bad. Python shines the brightest when you learn to make use of the standard modules instead of writing your own routines, and is especially powerful in its ease of interfacing with C/C++.

---

### Post by pmasiar on 2007-12-28
CptPicard, you may consider asking this question on python mailing list. I suspect there is some module what makes this generation much faster....

---

