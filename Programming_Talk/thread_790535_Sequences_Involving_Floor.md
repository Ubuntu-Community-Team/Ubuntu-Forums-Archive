---
title: "Sequences Involving Floor"
date: 2008-05-11
forum: Programming Talk
---

### Post by Lster on 2008-05-11
Hi!

I have two sequences I would like to find a particular term in. The first sequence, S, I already know (its values are all integers). The second sequence is related to the first by the equation:

K[n] = &#931; floor(c / S[i] / S[n+1])

In which, c is a known integer constant.

So, for example:

K[1] = floor ( c / S[1] / S[2] )
K[2] = floor ( c / S[1] / S[3] ) + floor ( c / S[2] / S[3] )
K[3] = floor ( c / S[1] / S[4] ) + floor ( c / S[2] / S[4] ) + floor ( c / S[3] / S[4] )
...

However, to compute these values requires iteration and although acceptable for small n, is unmanageable for large n. So my question would be, is there anyway of simplifying the above into either a closed form expression or one like:

K[a+1] = K[a] * S[a] / S[a+1] + c / S[a] / S[a+1]

Thank you,
Lster

---

### Post by Bichromat on 2008-05-11
Except if the sequence S has some particular property, I'm afraid there's nothing you can do. I don't think there's a way to transform floor(A*B) to an expression involving floor(A) and B.

---

### Post by Lster on 2008-05-11
That was my fear! :)

In which case I must use a different method entirely I suppose...

---

### Post by Bichromat on 2008-05-11
After toying with a little python script which tests if floor(floor(A)*B/A) equals floor(B) for random floats A and B, it seems that it is true in 50% of the cases.

Now, if someone can find a way to discriminate between good (A,B) pairs and bad ones...

---

### Post by Lster on 2008-05-11
That's interesting. When I have some more time I will try out some possible methods...

---

### Post by Can+~ on 2008-05-11
But if everyting are integers, why do you need floor in the first place? It's integer division, so you'll always have integers as a result (unless any of this values is a float)

And why is the constant C and S[n+1] (constant for the sum) inside the sum? I mean, you could do something like

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-1.png[/IMG]

Also, if you could tell the formula of S_i, then we could probably establish a more efficient equation.

---

### Post by Bichromat on 2008-05-11
You're right, I thought c was a real value. But if it's not, then there's no need for floor().

Anyway, you can't factorize when doing integer division :
5/2+5/3 != 5*(1/2+1/3)

---

### Post by Jessehk on 2008-05-11
> **Bichromat said:**
> 

Anyway, you can't factorize when doing integer division :
5/2+5/3 != 5*(1/2+1/3)


Uh...yes, you can.

---

### Post by Bichromat on 2008-05-11
> **Jessehk said:**
> Uh...yes, you can.

5/2=2
5/3=1
=> 5/2+5/3=3

1/2=0
1/3=0
=> 5*(1/2+1/3)=0

No, you can't.

---

### Post by Jessehk on 2008-05-11
Ah, I misunderstood you. I didn't know that by integer division, you meant an operation without decimals ie, 1/3 = 0.

Certainly you could factor out that 5 with normal fractions.

---

### Post by Can+~ on 2008-05-11
> **Bichromat said:**
> 5/2=2
5/3=1
=> 5/2+5/3=3

1/2=0
1/3=0
=> 5*(1/2+1/3)=0

No, you can't.

You're right. But if you try those same numbers on the OP's equation, then, when S[n] is bigger than the Multiplication of C*S[i] the sum is 0 too, so that's a huge source of error.

Looks like this needs floats. Unless S[n] is decreasing function, where S[n] is always smaller or equal than the ones before it.

---

### Post by Bichromat on 2008-05-12
I don't see how you would use floats. The floor() function makes it impossible, doesn't it ?

---

### Post by Lster on 2008-05-12
[QUOTE=Can+~]Looks like this needs floats. Unless S[n] is decreasing function, where S[n] is always smaller or equal than the ones before it.[/QUOTE]

I have changed the sequence S to be decreasing, what can I do now? By the way, the only additional information about values in S is that they only have one distinct prime factor.

I have a couple of ideas related to the new decreasing sequence! I'll get back to you all! :)

---

### Post by Lster on 2008-05-12
I was wrong... :( ;)

---

