---
title: "Awk string removal question"
date: 2009-10-14
forum: Programming Talk
---

### Post by docetes on 2009-10-14
```
echo this is a \"test\" string | awk '{gsub(/\"test\"/,"", $0);print$0 }'
```

It just doesn't feel like the best way of doing it and it can take a few minutes to complete on largish files

Thanks,
Dave

---

### Post by diesch on 2009-10-14
```
echo this is a \"test\" string | sed 's/"test"//'
```

---

### Post by docetes on 2009-10-14
> **diesch said:**
> ```
echo this is a \"test\" string | sed 's/"test"//'
```

Thanks for the quick reply and that works perfectly but if I have more than one "test" it doesn't seem to work

---

### Post by docetes on 2009-10-14
```
echo this is a \"test\" string this is a \"test\" string  | sed -e 's/"test"//g'
```

adding the /g at the end makes it global. Thanks rizhun

---

### Post by ghostdog74 on 2009-10-14
> **docetes said:**
> ```
echo this is a \"test\" string | awk '{gsub(/\"test\"/,"", $0);print$0 }'
```

It just doesn't feel like the best way of doing it and it can take a few minutes to complete on largish files

Thanks,
Dave

why not?
```

echo "...." | awk '{gsub(/\"test\"/,"")}1' file

```
on large files, awk can perform better than sed.

---

### Post by diesch on 2009-10-14
awk is indeed faster than sed here, but perl is even faster:


```

$ seq -f '%f This is a "test" string' 1 1000000 > foo.txt
$ time awk '{gsub(/\"test\"/,"")}1' foo.txt > /dev/null
2,90s user 0,07s system 83% cpu 3,563 total
$ time sed -e 's/"test"//g' foo.txt > /dev/null      
8,15s user 0,12s system 86% cpu 9,537 total
$ time perl -pe 's/"test"//g' foo.txt  > /dev/null     
2,29s user 0,09s system 79% cpu 2,986 total

```

---

### Post by benj1 on 2009-10-14
actually you can convert awk to perl (a2p) so it should be just as fast.
infact theres a few awk to c compilers around so awk should be faster 
awk2c seems to be still available, heres a link [http://hpux.connect.org.uk/hppd/hpux/Languages/awk2c-0.50/]("http://hpux.connect.org.uk/hppd/hpux/Languages/awk2c-0.50/")

---

### Post by ghostdog74 on 2009-10-14
> **diesch said:**
> awk is indeed faster than sed here, but perl is even faster:


you sure? on my system, its always slower
```

# time awk '{gsub(/\"test\"/,"")}1' foo.txt > /dev/null

real    0m2.980s
user    0m2.770s
sys     0m0.149s
# time perl -pe 's/"test"//g' foo.txt  > /dev/null

real    0m4.545s
user    0m4.294s
sys     0m0.195s
# time awk '{gsub(/\"test\"/,"")}1' foo.txt > /dev/null

real    0m2.889s
user    0m2.788s
sys     0m0.040s
# time perl -pe 's/"test"//g' foo.txt  > /dev/null

real    0m4.613s
user    0m4.261s
sys     0m0.249s
# time awk '{gsub(/\"test\"/,"")}1' foo.txt > /dev/null

real    0m2.848s
user    0m2.767s
sys     0m0.051s
# time perl -pe 's/"test"//g' foo.txt  > /dev/null

real    0m4.392s
user    0m4.264s
sys     0m0.082s


```

---

### Post by diesch on 2009-10-14
Interesting. Here perl is always faster.

This is perl, v5.10.0 built for i486-linux-gnu-thread-multi
GNU Awk 3.1.6

Intel(R) Pentium(R) 4 CPU 2.00GHz

---

### Post by benj1 on 2009-10-14
i can confirm the awk v perl times
awk (well actually mawk which is a faster implementation (1.3.3 ))
```
real	0m1.417s
user	0m1.040s
sys	0m0.060s
```

perl (perl, v5.10.0 built for i486-linux-gnu-thread-multi)
```

real	0m2.779s
user	0m2.088s
sys	0m0.048s

```

just to add another comparison
```
time python -c "for line in open('foo.txt','r'): print line.replace('"test"','')" > /dev/null
```

```

real	0m2.966s
user	0m2.372s
sys	0m0.044s
```
python (2.6.2)

which is quicker than i expected, i always thought perl was significantly quicker?

---

### Post by docetes on 2009-10-15
I forgot how much i love the sheer nerdiness of this forum. I've only just started back into college after 2 years of working in the windows world(yuck) and I'll have to get back into this forum. Thanks again guys

---

### Post by diesch on 2009-10-15
> **benj1 said:**
> i can confirm the awk v perl times
awk (well actually mawk which is a faster implementation (1.3.3 ))


Ok, I was using gawk (default awk in jaunty). mawk is 'indeed faster than Perl (1,36s user 0,05s system 85% cpu 1,644 total)

> **benj1 said:**
> 
just to add another comparison
```
time python -c "for line in open('foo.txt','r'): print line.replace('"test"','')" > /dev/null
``````

real    0m2.966s
user    0m2.372s
sys    0m0.044s
```python (2.6.2)

which is quicker than i expected, i always thought perl was significantly quicker?

Here Python replaces fixed strings instead of using Regex.

```

import re
for line in open('foo.txt','r'): print re.sub('test','', line)

```is much slower than Perl. (here: 15,76s user 0,22s system 82% cpu 19,312 total)

---

### Post by benj1 on 2009-10-15
hmm interresting that mawk is default for me im using crunchbang 9.04, which uses (i thought) the default ubuntu base install.

i quick check indicates gawk was the default on 8.10, mawk on 9.04, did you do an upgrade rather than a reinstall?

regarding python timings, shouldn't you use the quickest way available to a particular language to do a task for comparison, rather than test a similar implementation across languages?

language x may implement some new pattern matching completely unrelated to regex, but 20 times faster, should it be judged on its slower regex module or its new high speed module ?

yes you could say that regex is more flexible but doesn't that reveal a problem with the test, ie not requiring that flexibility?

---

### Post by ghostdog74 on 2009-10-15
> **diesch said:**
> 
```

import re
for line in open('foo.txt','r'): print re.sub('test','', line)

```is much slower than Perl. (here: 15,76s user 0,22s system 82% cpu 19,312 total)
when you use regex in Python, do re.compile(). furthermore, there's is no need to use re module, since you "waste" some time "importing" it into the running script.For this case, using Python's internal string replace is more efficient.

---

