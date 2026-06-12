---
title: "Name Gen. Problem"
date: 2012-08-07
forum: Programming Talk
---

### Post by didinium on 2012-08-07
Hello, I am relatively new to python and am working on a name generator. I made a algorithm to make even numbers show up as 1 and odds as 2 (you might ask why not make the values for the letters themselves 1s and 2s is because some rules for names are different than others [you cant have a name like Biivhs]). I can't seem to make this work because I either haven't defined a class or a variable. So my question is will I be able to make this work or should I just rewrite everything.
```

ta=0
tb=0
tc=0
td=0
te=0
tf=0
tg=0
th=0
ti=0
tj=0
tk=0
tl=0
tm=0
tn=0
tp=0
tq=0
tr=0
ts=0
tt=0
tu=0
tv=0
tw=0
tx=0
ty=0
tz=0
a=4
b=3
c=5
d=7
e=8
f=9
g=11
h=13
i=14
j=15
k=17
l=19
m=21
n=23
o=24
p=25
q=27
r=29
s=31
t=33
u=34
v=35
w=37
x=39
y=41
z=43
def main():
    def checkeoa():
        if a%2==0:
            ta+=1
        else:
            ta+=0
    def checkeob():
        if b%2==0:
            tb+=1
        else:
            tb+=0
    def checkeoc():
        if c%2==0:
            tc+=1
        else:
            tc+=0
    def checkeod():
        if d%2==0:
            td+=1
        else:
            td+=0
    def checkeoe():
        if e%2==0:
            te+=1
        else:
            te+=0
    def checkeof():
        if f%2==0:
            tf+=1
        else:
            tf+=0
    def checkeog():
        if g%2==0:
            tg+=1
        else:
            tg+=0
    def checkeoh():
        if h%2==0:
            th+=1
        else:
            th+=0
    def checkeoi():
        if i%2==0:
            ti+=1
        else:
            ti+=0
    def checkeoj():
        if j%2==0:
            tj+=1
        else:
            tj+=0
    def checkeok():
        if number%2==0:
            tk+=1
        else:
            tk+=0
    def checkeol():
        if l%2==0:
            tl+=1
        else:
            tl+=0
    def checkeom():
        if m%2==0:
            tm+=1
        else:
            tm+=0
    def checkeon():
        if n%2==0:
            tn+=1
        else:
            tn+=0
    def checkeoo():
        if o%2==0:
            to+=1
        else:
            to+=0
    def checkeop():
        if p%2==0:
            tp+=1
        else:
            tp+=0
    def checkeoq():
        if q%2==0:
            tq+=1
        else:
            tq+=0
    def checkeor():
        if r%2==0:
            tr+=1
        else:
            tr+=0
    def checkeos():
        if s%2==0:
            ts+=1
        else:
            ts+=0
    def checkeot():
        if t%2==0:
            tt+=1
        else:
            tt+=0
    def checkeou():
        if u%2==0:
            tu+=1
        else:
            tu+=0
    def checkeoav():
        if v%2==0:
            tv+=1
        else:
            tv+=0
    def checkeow():
        if w%2==0:
            tw+=1
        else:
            tw+=0
    def checkeox():
        if x%2==0:
            tx+=1
        else:
            tx+=0
    def checkeoy():
        if y%2==0:
            ty+=1
        else:
            ty+=0
    def checkeoz():
        if z%2==0:
            tz+=1
        else:
            tz+=0
def other():
    checkeoa()
    checkeob()
    checkeoc()
    checkeod()
    checkeoe()
    checkeof()
    checkeog()
    checkeoh()
    checkeoi()
    checkeoj()
    checkeok()
    checkeol()
    checkeom()
    checkeon()
    checkeoo()
    checkeop()
    checkeoq()
    checkeor()
    checkeos()
    checkeot()
    checkeou()
    checkeov()
    checkeow()
    checkeox()
    checkeoy()
    checkeoz()
main()
other()
print ta

```

---

### Post by mevun on 2012-08-07
Quite frankly, I do not understand what your algorithm is doing.  However, I am not sure why you define all those check functions inside the function main().

Hopefully, you have an editor that can "untab" (i.e. shift to the left), the block of code starting from "def checkeoa():" to "def checkeoz():".  Also delete (or at least comment) the line "def main():".

Then all your functions that start with "check" can be called from the other() function.

---

### Post by diesch on 2012-08-07
Having hat much functions that are each doing the same thing with just different variables is a sure sign you should rewrite your code.

I too don't really understand what you want to do here, but maybe you could do it similar to this code:

```

class Thing():
       def __init__(self, letter, value):
              self.letter = letter
              self.value = value              
              if value % 2 == 0:
                     self.t = 1
              else:
                     self.t = 0

things = [
       Thing('a', 4),
       Thing('b', 3),
] 

for thing in things:
       print 'Thing %s: value=%s  t=%s' % (thing.letter, thing.value, thing.t)

```

---

### Post by Tony Flury on 2012-08-07
> **didinium said:**
> Hello, I am relatively new to python and am working on a name generator. I made a algorithm to make even numbers show up as 1 and odds as 2 (you might ask why not make the values for the letters themselves 1s and 2s is because some rules for names are different than others [you cant have a name like Biivhs]). I can't seem to make this work because I either haven't defined a class or a variable. So my question is will I be able to make this work or should I just rewrite everything.
```

ta=0
...
snipped for brevity 

```
I would echo what is already said - if you have that many variables and that many functions - you need to rewrite - I personally would not have bothered with a class here, I would have used a list.

If i were generating names - i would not try to build the name letter by letter - because you then get into the hassle of some letters not working well after others (as you pointed out). I would start with a list of syllables, and choose a random syllable from the list until a reached a randomly chosen length - it would generate pronouncable names - although probably not recognisable names in most languages.

Edit : I just tried this - using the choice function to pick a random item from a list of syllable-like strings (will post the code in a bit). ALthough my list only covered a small range of possible syllables, the results were pretty good, with nearly every word pronouncable - and a few were recognisable. If you wanted to get very clever you would produce a weighted list organised so that more common syllables were more likely to be picked, but of course that weighting will vary from language to language, and is more complex to code

---

### Post by Tony Flury on 2012-08-07
As promised my "proof of concept" name generator : 

```

#!/usr/bin/env python

import random, sys

sylables = ["ab","ac","ad","af","ag", "aj","ak","al","am","an","ap", "ar", "as",
"ash", "at", "ath","av","aw","axe","axi",
"ba","be","bi","bo","bu","bra","bro","bri","bre","bla","blo","ble","bli" "blu", "ca","ce","ci","co","cu","cra","cre","cro","cru", "clu", "clo","cli","cle","ck","cha", "chi","che","cho","chy" "da","de","do","di","dy","du","dra","dro","dru","dre"]


random.seed(int(sys.argv[1]) )

for namecount in range(1, int(sys.argv[2])+1 ):
    str = ""

    for n in range(0,random.randint(2,3)):
        str += random.choice(sylables)

    print "{0} -> {1}".format(namecount,str) 

```

first argument is a random seed - so you can generate the same set of names over and over again.
second argument is the number of names to generate.

It is by no means perfect, but it can be tuned by changing the list of syllables.

---

