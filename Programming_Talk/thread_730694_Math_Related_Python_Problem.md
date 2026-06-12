---
title: "Math Related Python Problem"
date: 2008-03-21
forum: Programming Talk
---

### Post by Lster on 2008-03-21
Hi

Firstly, thanks to those who recommended I learned Python - I love the language more every time I find out another of it's features. I've already started using it for solving Project Euler problems but I'm having a few problems with one of the challenges that I believe is probably related to my lack of knowledge.

I'm trying to solve this puzzle:
[http://projecteuler.net/index.php?section=problems&id=183](http://projecteuler.net/index.php?section=problems&id=183)

Now I played around with it all and came to a solution. However, Project Euler states:

[QUOTE=Project Euler]For example, &#931;D(N) for 5 &#8804; N &#8804; 100 is 2438.[/QUOTE]

And I get 3690, instead. I've checked Python documentation again and again and I can't see any errors. I did find this page, though:

[http://erl.nfshost.com/wordpress/2008/02/29/euler-183/](http://erl.nfshost.com/wordpress/2008/02/29/euler-183/)

Which shows the method I am attempting... Could anyone give me any pointers on why it isn't working? Just a nudge in the right direction would be appreciated! :)

Here's my code:

...

Thanks,
Lster

---

### Post by dvase on 2008-03-21
I would check to make sure that python is doing floating point arithmetic where required.  I'm just a beginning python programmer myself, but I have had problems in the past with python assuming integer arithmetic when I really needed floating point calculations.  When declaring a variable and giving it a value (e.g. t in your code), declaring it as "t = 0.0" seems to tell python that it is floating point number not an integer.

---

### Post by Martin Witte on 2008-03-21
I'm not too sure what's going wrong. Your D function seems to work, I've tried to write the problem like this
```
def D ( x ):
    while x % 2 == 0:
        x /= 2
    
    while x % 5 == 0:
        x /= 5
    
    if x == 1:
        return -1
    return 1


def M(N):
    Pmax = 0
    retval = (0, 0)
    for k in range(1, N + 1):
        r = N/float(k)
        P = r**k
        if P > Pmax:
            Pmax = P
            retval = (N**k, k**k)
    return retval

sum = 0
for N in range(5, 101):
    m = M(N)
    d = D(m[1]) * N
    sum += d
print sum

```

also with a wrong result...

---

### Post by Lster on 2008-03-21
dvase, that's a very good point but I have already tried that and I still can't get it to work. Any ideas?

Thanks,
Lster

---

### Post by Lster on 2008-03-21
Martin Witte, I can't see anything wrong with your code, myself. Anyone spot any mistakes? I am really stumped!

---

### Post by Wybiral on 2008-03-21
Do we have a version in any other language (other than mathematica) that does work so I can compare them?

---

### Post by KnightWhoSaysNi on 2008-03-21
The code below works for the example (the only difference is simplifying the fraction before the terminating test). But the floating-point division and the GCD function both overflow when used on the actual problem size.
I guess the brute-force method could be fixed by comparing the P(n) using integers and calculating  GCD non-recursively. However a more mathematical solution may be in order.

```
def Pmax(n):
    pmax=0
    for k in range(1,n):
        num=n**k
        denom=k**k
        p=(float)(num)/(float)(denom)
        if p>pmax:
            pmax=p
            pmax_num=num
            pmax_denom=denom
    return (pmax_num,pmax_denom)


def gcd(n,d):
    if d==0: return n
    return gcd(d,n % d)

def Terminating(x):
    (n,d)=x
    g=gcd(n,d)
    d /= g
    while d % 2 == 0:
        d /= 2   
    while d % 5 == 0:
        d /= 5
    if d == 1:
        return True
    return False

def D(n):
    if Terminating(Pmax(n)):
        return -n
    else:
        return n

sumd=0
for n in range(5,101):
    sumd += D(n)
print sumd
```

---

### Post by pmasiar on 2008-03-21
OP:

Are you aware that "n / a" returns integer, if both n and a are integers? It's old Python wart, will be removed in Py3K, due this september.

---

### Post by Wybiral on 2008-03-21
You should be able to fix the floating-point problem with the Decimal class.

My version of KnightWhoSaysNi's implementation:
```

from decimal import Decimal

def pmax(n):
    pm = 0
    for k in xrange(1, n):
        num = n ** k
        denom = k ** k
        p = Decimal(num) / Decimal(denom)
        if p > pm:
            pm = p
            result = (num, denom)
    return result

def gcd(n, d):
    while d:
        n, d = d, n % d
    return n

def isterminating(x):
    n, d = x
    d /= gcd(n, d)
    while d % 2 == 0:
        d /= 2
    while d % 5 == 0:
        d /= 5
    return -1 if d == 1 else 1

print sum(n * isterminating(pmax(n)) for n in xrange(5, 101))

```

But if you try to solve the 5-1000 version with this, well, I hope you have a lot of time to wait for it :)

---

### Post by Lster on 2008-03-22
Well, I've coded a hybrid that I think is faster still (using the calculus insight in that blog). It becomes slower and slower, still, and taking into account it's avergae speed depreciation, it will take almost an hour.

I'm on 43% right now...

...

---

### Post by Jessehk on 2008-03-22
[quote=projecteuler.net]
Each problem has been designed according to a "one-minute rule", which means that although it may take several hours to design a successful algorithm with more difficult problems, an efficient implementation will allow a solution to be obtained on a modestly powered computer in less than one minute.
[/quote]

:)

---

### Post by Lster on 2008-03-22
I was thinking about that too. When I *do* solve it, I can see how others have kept speed acceptable!

63% now...

---

### Post by Wybiral on 2008-03-22
Have you tried [185]("http://projecteuler.net/index.php?section=problems&id=185") yet? That one has been my favorite so far :)

---

### Post by Lster on 2008-03-22
I had a small try and can solve the smaller one with optimized brute force (that sounds like somewhat of an oxymoron). Have you managed to complete it? :)

---

### Post by Wybiral on 2008-03-22
> **Lster said:**
> I had a small try and can solve the smaller one with optimized brute force (that sounds like somewhat of an oxymoron). Have you managed to complete it? :)

Yeah, but even mine was somewhat brute (there's some theory behind it though). The C version solves it in a second or two, the Python one is a bit slower (lots of tight looping, it might benefit from psyco or something, but I haven't got around to trying that yet). I can send it to you if you'd like.

---

### Post by Lster on 2008-03-22
I'd love to see a solution to it! I'm guessing you use brute force searching but exclude some values you know can't be in those positions. Also, on each string, you can do checks to see if it is a possible candidate.

Those were the first two things I noticed... I'd be interested to see what you have found! :)

... 98%!

---

### Post by Lster on 2008-03-22
Done!

It was... [Now removed!]! (The answer is white to hide it from those who don't want to see!)

---

### Post by Wybiral on 2008-03-22
> **Lster said:**
> I'd love to see a solution to it! I'm guessing you use brute force searching but exclude some values you know can't be in those positions.

Actually, mine doesn't exclude anything (I didn't try too hard, but it looked like the 0 correct one was the only rule that could be used to deduce anything). Well, you'll see... I PM'd it to you.

---

