---
title: "from QBASIC to C"
date: 2010-02-11
forum: Programming Talk
---

### Post by geonomica on 2010-02-11
hy,
I'm translating a QBASIC code in C.
I'm not a programmer "guru"  and I need some explanations:
The QBASIC code is:
7010     FOR k = 1 TO pop
7015         IF a(k, c   at   1) = 0 THEN GOTO 7080
7020            FOR j = 1 TO c
7030                IF b(j) = 0 THEN GOTO 7050
7040                IF a(h, j) > a(k, j) THEN GOTO 7080
7050            NEXT j

7051            FOR j = c   1 TO c   at
7052                IF b(j) = 0 THEN GOTO 7056
7055                IF a(h, j) <> a(k, j) THEN GOTO 7080
7056            NEXT j
7061         IF a(k, c   at   1) < d THEN contr = contr   1
7062         IF a(k, c   at   1) >= d THEN corr = corr   1
7080     NEXT k

And I tried to translate in C with that code:
for(k=0;(k<pop) && !(a[k][c at 1]);k  )
            {
                for(j=0;(j<c) && !(b[j] && a[h][j]>a[k][j]);j  );
                for(j=c 1;(j<=c at) && !(b[j] && a[h,j]!=a[k,j]);j  );
                    {
                        if (a[k][c at 1] < d) contr  ;
                        else corr  ;
                    }
            }

My questions are:
a. the output result are different so, if QBASIC code is correct, my C code i incorrect. Where is the error?
b. what is the meaning of cicle 7020 - 7050 and 7051 - 7056. It's seem does nothing

Thanks for help!!!

---

### Post by nvteighen on 2010-02-11
> **geonomica said:**
> hy,
I'm translating a QBASIC code in C.
I'm not a programmer "guru"  and I need some explanations:
The QBASIC code is:
7010     FOR k = 1 TO pop
7015         IF a(k, c   at   1) = 0 THEN GOTO 7080
7020            FOR j = 1 TO c
7030                IF b(j) = 0 THEN GOTO 7050
7040                IF a(h, j) > a(k, j) THEN GOTO 7080
7050            NEXT j

7051            FOR j = c   1 TO c   at
7052                IF b(j) = 0 THEN GOTO 7056
7055                IF a(h, j) <> a(k, j) THEN GOTO 7080
7056            NEXT j
7061         IF a(k, c   at   1) < d THEN contr = contr   1
7062         IF a(k, c   at   1) >= d THEN corr = corr   1
7080     NEXT k

And I tried to translate in C with that code:
for(k=0;(k<pop) && !(a[k][c at 1]);k  )
            {
                for(j=0;(j<c) && !(b[j] && a[h][j]>a[k][j]);j  );
                for(j=c 1;(j<=c at) && !(b[j] && a[h,j]!=a[k,j]);j  );
                    {
                        if (a[k][c at 1] < d) contr  ;
                        else corr  ;
                    }
            }

My questions are:
a. the output result are different so, if QBASIC code is correct, my C code i incorrect. Where is the error?
b. what is the meaning of cicle 7020 - 7050 and 7051 - 7056. It's seem does nothing

Thanks for help!!!

Because you aren't increasing the counter variables at your loops:
```

for(k=0;(k<pop) && !(a[k][c at 1]);**k++**)
{
    ...
}

```

The QBASIC FOR...NEXT clause always increases the pointer by one... It's actually sugar for the FOR x = 0 TO whatever STEP 1...NEXT clause.

---

### Post by rCXer on 2010-02-11
Edited: nvteighen has given a good explanation

---

### Post by geonomica on 2010-02-11
thanks at all!
really in copy/past I've lost the increase operator: si the cicle is
... for(k=0;(k<pop) && !(a[k][c+at+1]);k++)...


The QBASIC code works in multi criteria analysis but I've difficult to find exact algorithm, so I'm translating code "step by step"

thanks

---

### Post by geonomica on 2010-02-11
hopps!:(
I've lost all formatting sign. The code is:
for(k=0;(k<pop) && !(a[k][c+at+1]);k++)
            {by
                for(j=0;(j<c) && !(b[j] && a[h][j]>a[k][j]);j++);
                for(j=c+1;(j<=c+at) && !(b[j] && a[h,j]!=a[k,j]);j++);
                if (j>c+at && b[j])
                    {
                        if (a[k][c+at+1] < d) contr++;
                        else corr++;
                    }
            }
        lower[h]=corr/(contr+corr);
        contr=corr=0;

---

### Post by geonomica on 2010-02-11
nobody can help me?

---

### Post by wmcbrine on 2010-02-11
You already posted [a whole other thread about this](http://ubuntuforums.org/showthread.php?t=1399434), in which you declined to even explain what the purpose of this code is. You're asking for a blind line-by-line translation, which is ridiculous.

---

### Post by geonomica on 2010-02-11
The code implements a multicriteria decision making algorithm, as I told in past thread.
Is very difficult for me understand algorithm from  BASIC code, so, since I've to translate from BASIC to C, I'm working line by line to obtain the whole procedura. I hope in C I'm understand exactly the algorithm.

I think is not ridiculous!
If you can't help me...by

---

### Post by wmcbrine on 2010-02-11
> **geonomica said:**
> The code implements a multicriteria decision making algorithm, as I told in past thread.Yes. Unfortunately that statement is meaningless to me, and I think to others. What "multicriteria"? What decisions, about what?

> *If you can't help me...by*Not so much "can't", as, why should we? What you're asking for is hard work, with no discernable reward being offered. At a minimum, I'd at least like to know that the program did something meaningful, as opposed to just helping you make... decisions... based on... multiple criteria.

---

### Post by geonomica on 2010-02-11
multicirteria algorithm aid to choise the optimum decision under several criteria.
example: we have 10 project described under 25 indicator. different project has different performance under same indicator. The multicriteria algorithm elaborates information for search the best project

---

