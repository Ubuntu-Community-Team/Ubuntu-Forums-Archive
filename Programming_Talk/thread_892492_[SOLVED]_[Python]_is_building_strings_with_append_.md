---
title: "[SOLVED] [Python] is building strings with append really best?"
date: 2008-08-17
forum: Programming Talk
---

### Post by unutbu on 2008-08-17
I've read many times that building strings from lists is better than concatenating with +. 

However, the following code seems to suggest that building a list with append is much slower than string concatenation. Is that true or is there something wrong with my code?
[php]
#!/usr/bin/env python
import timeit

timer=timeit.Timer("""
for idx in xrange(10000):
    result.append(hline)
astr=''.join(result)
""","""
result=[]
hline='-'*5+'\\n'
""")

timer2=timeit.Timer("""
for idx in xrange(10000):
    result+=hline
""","""
result=''
hline='-'*5+'\\n'
""")

timer3=timeit.Timer("""
''.join([hline for idx in xrange(10000)])
""","""
hline='-'*5+'\\n'
""")

iter=100
dt=timer.timeit(iter)
dt2=timer2.timeit(iter)
dt3=timer3.timeit(iter)

print "Time using append: %0.3f secs"%(dt)
print "Time using +     : %0.3f secs"%(dt2)
print "Time using l-comp: %0.3f secs"%(dt3)
[/php]

Returns
[php]% timeit-build-strings-0.py
Time using append: 3.480 secs
Time using +     : 0.409 secs
Time using l-comp: 0.147 secs
[/php]

---

### Post by NovaAesa on 2008-08-17
How interesting. I had always thought that append was faster as well. I guess we wrong all this time after all. Unless of course there is same kind of explanation...

---

### Post by Lster on 2008-08-17
I did my own test with the Unix time command and my own program. I timed how long it ran with all functions commented out. I then did five runs of each function and took the best time for each, minus the the time with all functions commented out.

With that I get:

> plus: 1.448s
concat: 2.560s
iterconcat: 1.223s

These results seem to roughly agree with your own. But, as long as we're only talking coefficient speed increases, I would say that it isn't really important for the type of development generally done in Python.

---

### Post by deuce868 on 2008-08-17
From what I'm reading it looks like they made some big improvements to string concat in 2.5. This seems to be the cause of the difference from what you're expected.

---

### Post by pmasiar on 2008-08-17
Strings are immutable. Changing string with + always means creating new string and abandoning the old one (for the garbage collection), while creating list of string snippets (and joining them into single one at the end) just adds new without deallocating old memory.

Amounts and sizes you used are trivial, so you don't see much difference. try more and bigger strings, straining your RAM and forcing GC to work harder.

---

### Post by deuce868 on 2008-08-17
Here you go, direct reference to the patch:
[http://www.python.org/dev/summary/2006-10-01_2006-10-15/#string-concatenation](http://www.python.org/dev/summary/2006-10-01_2006-10-15/#string-concatenation)

> 
Larry Hastings posted a patch for string concatenation that delays the creation of a new string until someone asks for the string's value. As a result, the following code would be about as fast as the ''.join(strings) idiom:

result = ''
for s in strings:
    result += s


which seems to stand up to your observations.

---

### Post by unutbu on 2008-08-17
I increased the xrange to 100000, made
hline='-'*80+'\\n', and re-ran the script. 
The result seems even less in favor of append:

```
% timeit-build-strings-0.py
Time using append: 709.646 secs
Time using +     : 5.160 secs
Time using l-comp: 2.398 secs
```

Each string has a final size of 8.2MB, and timeit generates the string 100 times. This does not seem very big -- especially if timeit throws out the string before starting the next run (shouldn't it?) -- but it brings my system to its knees. (1GB RAM, 3GB swap).

PS. Why is list comprehension so much faster than append?


PPS. I increased the size of the strings by a factor of 160. The times however, increased by different factors:

```

% timeit-build-strings-0.py

                   First run   Second run     Factor
Time using append: 3.480 secs  709.646 secs   204
Time using +     : 0.409 secs  5.160 secs     13
Time using l-comp: 0.147 secs  2.398 secs     16

```
I don't know what to make of this, but I found it interesting. Since the factor for + is the smallest of the three, would it be safe to conclude that given a big enough string + beats list comprehension?

---

### Post by Lster on 2008-08-17
From what pmasiar says, which sounds right, list comprehension would not even need to copy the strings into the array as it was forming. In fact, it would probably just point to the same string (which is safe since they're immutable in Python). Then at the end it only has to create one string making just one allocation.

The other way, Python has to keep making new strings with each iteration - allocating and freeing them as they are needed!

---

### Post by unutbu on 2008-08-17
Thanks Lster. But how is list comprehension fundamentally different than append? They both deal with lists of immutable strings, so why is one so much faster than the other?

---

### Post by slavik on 2008-08-17
> **Lster said:**
> I did my own test with the Unix time command and my own program. I timed how long it ran with all functions commented out. I then did five runs of each function and took the best time for each, minus the the time with all functions commented out.

With that I get:



These results seem to roughly agree with your own. But, as long as we're only talking coefficient speed increases, I would say that it isn't really important for the type of development generally done in Python.
if the coefficient is high enough, it does matter.

EDIT: I tested join vs. concatenation in Perl and it seems like concatenation is much faster in perl (by about a factor of 3). I wasn't really surprised because Perl was built for text processing and has many optimizations in the area. I used the time command.

here's the code:
```

#!/usr/bin/perl

for (1..1000000) {
	$string.="some long string";
}	

for (1..1000000) {
	push @strings, "some long string";
}
$string = join '', @strings;

```

---

### Post by Wybiral on 2008-08-17
> **slavik said:**
> if the coefficient is high enough, it does matter.

Yeah, but I ran these same tests with MUCH larger strings (to put more strain on the Python string allocation) on both 2.4 and 2.5 and the difference between them starts to shift with large enough strings and enough appends. Try it out.

But you can cling to your coefficient increase if you'd like (hopefully you do enough testing and research to know when there isn't an algorithmic speedup available or to know that you need the coefficient increase before wasting all of your time in assembly) :)

---

### Post by Wybiral on 2008-08-17
> **slavik said:**
> iI wasn't really surprised because Perl was built for text processing
I read somewhere that Perl was built to simulate the look and feel of my bathroom floor after a night of heavy drinking...

---

### Post by Lster on 2008-08-17
[QUOTE=slavik]if the coefficient is high enough, it does matter.[/QUOTE]

That is a *very* good question! :) Theoretically, it doesn't matter (much). But then there are thousands of algorithms which are unused because of practicality rather than their theoretics. If you are coding a real world application, you can work out which algorithm is best considering the best, worst and average case. In fact, you can expand that to multiple variables and even bring in standard deviations to evaluate which algorithm is better...

[QUOTE=unutbu]But how is list comprehension fundamentally different than append? They both deal with lists of immutable strings, so why is one so much faster than the other?[/QUOTE]

EDIT: Actually, I'm not sure.

---

### Post by unutbu on 2008-08-17
```
#!/usr/bin/env python

a_str='Hello'

a_list=[]
for idx in range(100):
    a_list.append(a_str)

for elt in a_list:
    if elt is a_str:
        print "elt is identical to a_str"
    elif elt==a_str:
        print "elt is a copy of a_str"
    else:
        print "Huh?"

```
The result is a 100 lines of 
"elt is identical to a_str"

This leads me to believe that append is not allocating a new copy of a_str, it is just creating a pointer to the same a_str. I would have thought this should be fast... (and essentially identical to what list comprehension is doing).

---

### Post by pmasiar on 2008-08-17
That's interesting. I think we are missing something obvious. 

Google [suggests:](http://wiki.python.org/moin/PythonSpeed/PerformanceTips#head-bcf69f4e2cacc9683c2f9a1f401e891cac50506f) what I said, but also says that 2.5 improved +, so... my speed trick knowledge is old and not relevant anymore?

Maybe you want to post this question to python mailing list for real experts to look at it?

---

### Post by slavik on 2008-08-17
> **Wybiral said:**
> I read somewhere that Perl was built to simulate the look and feel of my bathroom floor after a night of heavy drinking...
your bathroom has lots of text on it???

---

### Post by LaRoza on 2008-08-17
> **slavik said:**
> your bathroom has lots of text on it???

If he eats alphabet soup, yes.

---

### Post by pmasiar on 2008-08-17
GC is important part of the test but is turned off:

[http://docs.python.org/lib/module-timeit.html](http://docs.python.org/lib/module-timeit.html) says: 

"By default, timeit() temporarily turns off garbage collection during the timing. The advantage of this approach is that it makes independent timings more comparable. This disadvantage is that GC may be an important component of the performance of the function being measured. If so, GC can be re-enabled as the first statement in the setup string."

---

### Post by days_of_ruin on 2008-08-17
> **LaRoza said:**
> If he eats alphabet soup, yes.

More like ASCII soup:
> @P=split//,".URRUU\c8R";@d=split//,"\nrekcah xinU / lreP rehtona tsuJ";sub
p{
@p{"r$p","u$p"}=(P,P);pipe"r$p","u$p";++$p;($q*=2)+=$f=!fork;map{$P=$P[$f^ord
($p{$_})&6];$p{$_}=/
^$P/ix?$P:close$_}keys%p}p;p;p;p;p;map{$p{$_}=~/^[P.]/&&
close$_}%p;wait until$?;map{/^r/&&<$_>}%p;$_=$d[$q];sleep
rand(2)if/\S/;print

And yes that does actually run.

---

### Post by unutbu on 2008-08-17
@pmasiar, thanks for pointing out GC. I thought we might be on to something here,
but when I added gc.enable() to the Timer argument:
```

timer=timeit.Timer("""
for idx in xrange(100000):
    result.append(hline)
astr=''.join(result)
""","""
gc.enable()
result=[]
hline='-'*80+'\\n'
""")

```
the result was even worse:
```

% timeit-build-strings-0.py
Time using append: 874.004 secs
Time using +     : 5.178 secs
Time using l-comp: 2.525 secs
```

---

### Post by unutbu on 2008-08-17
The problem seems to be in the way I am (mis)using timeit. When I simply use 'time', it looks like append is superior to +.

[PHP]#!/usr/bin/env python
# Modification of http://www.skymind.com/~ocrow/python_string/stest.py

import time

def method1():
    out_str = ''
    for num in xrange(loop_count):
        out_str += hline
    return out_str

def method2():
    str_list = []
    for num in xrange(loop_count):
        str_list.append(hline)
    out_str = ''.join(str_list)
    return out_str

def method3():
    out_str = ''.join([hline for num in xrange(loop_count)])
    return out_str


dat={}
def call_method(num):
    func_str='method' + str(num)
    t1=time.time()
    z = globals()[func_str]()
    t2=time.time()
    dt=t2-t1
    size=len(z) / 1024    
    dat[func_str]=dt

loop_count = 100000*100
hline='-'*80+'\n'
for num in range(1,4):
    call_method(num)

print "Time using append: %0.3f secs"%dat['method2']
print "Time using +     : %0.3f secs"%dat['method1']
print "Time using l-comp: %0.3f secs"%dat['method3']
[/PHP]

Result:

[PHP]% time-string-concatenation-2.py
Time using append: 3.793 secs
Time using +     : 5.300 secs
Time using l-comp: 2.365 secs[/PHP]

---

### Post by unutbu on 2008-08-17
Append/join *is* faster than string concatenation using +.

[PHP]#!/usr/bin/env python
import timeit

def test_append():
    result=[]
    hline='-'*80+'\\n'
    for idx in xrange(100000):
        result.append(hline)
    astr=''.join(result)

def test_plus():
    result=''
    hline='-'*80+'\\n'
    for idx in xrange(100000):
        result+=hline

def test_list_comprehension():
    hline='-'*80+'\\n'
    ''.join([hline for idx in xrange(100000)])

timer=timeit.Timer('test_append()',"""
from __main__ import test_append
""")

timer2=timeit.Timer('test_plus()',"""
from __main__ import test_plus
""")

timer3=timeit.Timer('test_list_comprehension()',"""
from __main__ import test_list_comprehension
""")

iter=100
dt=timer.timeit(iter)
dt2=timer2.timeit(iter)
dt3=timer3.timeit(iter)

print "Time using append: %0.3f secs"%(dt)
print "Time using +     : %0.3f secs"%(dt2)
print "Time using l-comp: %0.3f secs"%(dt3)[/PHP]

[PHP]% timeit-build-strings-1.py
Time using append: 3.640 secs
Time using +     : 4.980 secs
Time using l-comp: 2.217 secs
[/PHP]

If anyone can explain what was improper about my use of Timer in my original post, I'd be much obliged.

---

### Post by pmasiar on 2008-08-17
Strange. I tried my own version, creating all partial strings to be concatenated, instead of copying them like you did:

[php]
mport timeit

runs = 5
total = 400000


set_plus = "gc.enable();res=''"
stm_plus = "for x in xrange(%i): res += str(x)" % total

set_app = "gc.enable();app = []"
stm_app = """\
for x in xrange(%i): app.append(str(x))
res = ''.join(app)
""" % total

timer_plus = timeit.Timer(stm_plus, set_plus)
timer_app = timeit.Timer(stm_app,   set_app)

print "time using append: %.3f sec" % timer_app.timeit(runs)
res = ''
print "time using +     : %.3f sec" % timer_plus.timeit(runs)
[/php]

but I got the same result which should be wrong according to what I knew about string concatenation in Python.

Would you care to ask experts at Python main list? Or if you are scared, at Python-tutor (for beginners)? I am quite interested why it is so.

---

### Post by ghostdog74 on 2008-08-18
another way is to time it at the OS itself. separate your 3 tests into 3 separate scripts. Then use the time command for each
```

# time python script1.py 

```
my results: append+join slowest. list comprehension+join fastest.

---

### Post by slavik on 2008-08-18
> **days_of_ruin said:**
> More like ASCII soup:

And yes that does actually run.
keep in mind that the code was intended to me as unreadable as possible and it is unreadable because of the design, rather than the use of Perl.

---

### Post by pmasiar on 2008-08-18
> **slavik said:**
> keep in mind that the code was intended to me as unreadable as possible and it is unreadable because of the design, rather than the use of Perl.

Yes, but it is still amazing that code like that compiles and runs correctly! Perl is the only language AFAIK capable of running haiku of obfuscations like that. 

And also APL, but that was different. Maybe perl6 with unicode operators will match obfuscability of APL :-)

---

### Post by slavik on 2008-08-18
> **pmasiar said:**
> Yes, but it is still amazing that code like that compiles and runs correctly! Perl is the only language AFAIK capable of running haiku of obfuscations like that. 

And also APL, but that was different. Maybe perl6 with unicode operators will match obfuscability of APL :-)
perl6 will have nice things.

sigils are for life (@array; @array[1];)
a function can ask for a reference in a nice way (and named parameters, as well as default parameters).

sub func (int rw $x, int r $y);
$x will be a reference, while $y will be a value.

lazy list generation and such:
@arr = (1..inf); @arr[1] = 42; #this will be remembered, but when querying @arr, it will be generated on the fly a la Python's xrange() or Haskell's laziness (in the case of pugs)

but we are digressing from the topic.

The thing about the GC is that it doesn't have to call free on every unused block of memory, from what I've read about Java's GC, it supposedly copies the stuff that is used to another part of memory and calls free() on the other part.

Also, what is the point of having immutable strings? (I remember the reason being told to me when taking a Java class, but I forget)

---

### Post by unutbu on 2008-08-18
I think I understand what's going on: Timer only runs its second argument once. It does not re-run it before every run. So app = [] was only getting called once, and, tainted by the previous runs, was getting larger and larger.

[PHP]
#!/usr/bin/env python
import timeit

runs = 20
total = 400000

set_plus = "gc.enable();res=''"
stm_plus = "for x in xrange(%i): res += str(x)" % total

set_app_once = "gc.enable();app = []"
stm_app_once = """\
for x in xrange(%i): app.append(str(x))
res = ''.join(app)
""" % total

set_app_every = "gc.enable();"
stm_app_every = """\
app = []
for x in xrange(%i): app.append(str(x))
res = ''.join(app)
""" % total

timer_plus = timeit.Timer(stm_plus, set_plus)
timer_app_once = timeit.Timer(stm_app_once, set_app_once)
timer_app_every = timeit.Timer(stm_app_every, set_app_every)

print "time using append, initialized once : %.3f sec" % timer_app_once.timeit(runs)
print "time using append, initialized every: %.3f sec" % timer_app_every.timeit(runs)
print "time using +                        : %.3f sec" % timer_plus.timeit(runs)
[/PHP]
Result:
[PHP]
% timeit-build-strings-3.py
time using append, initialized once : 12.997 sec
time using append, initialized every: 8.224 sec
time using +                        : 8.629 sec
[/PHP]

---

