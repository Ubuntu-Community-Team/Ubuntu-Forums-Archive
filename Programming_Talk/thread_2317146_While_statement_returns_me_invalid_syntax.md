---
title: "While statement returns me invalid syntax"
date: 2016-03-13
forum: Programming Talk
---

### Post by aurelien6 on 2016-03-13
Hola,

Does someone else know about the condition which isn't valid in Python.
when i compute, it returns me invalid syntax..?
pt0 changes each loop i really don't understand what happened.
If someone could help me, tx
```

a = a_i
eps_t = 10**-13                 #uncertainty TOF error in second
t0 = 47629.8*10**-9             #TOF peak center in second
tp0 = sqrt(2*m_i*a_i/(q_i*E)) +  d*sqrt(1/(2*q_i*E*a_i/m_i) -t0
    
while abs(tp0) > eps_t:
             a = a -tp0*10**3
             tp0 = sqrt(2*m_i*a/(q_i*E)) +  d*sqrt(1/(2*q_i*E*a/m_i) -t0
```

---

### Post by Bucky Ball on 2016-03-14
*Thread moved to Programming Talk.*

---

### Post by Vaphell on 2016-03-14
post the actual error message. Syntax error has nothing to do with the math. It's about the technical side of the code itself: missing parentheses, incorrect indentation and such.

---

### Post by spjackson on 2016-03-14
> **aurelien6 said:**
> 
```

tp0 = sqrt(2*m_i*a_i/(q_i*E)) +  d*sqrt(1/(2*q_i*E*a_i/m_i) -t0

```
```

             tp0 = sqrt(2*m_i*a/(q_i*E)) +  d*sqrt(1/(2*q_i*E*a/m_i) -t0
```
Each of these two lines contains 4 of these '(' but only 3 of these ')'. Parentheses must balance.

---

### Post by aurelien6 on 2016-03-14
Here is the error message if it could help you


  File "/Users/asanchez/anaconda/scripts/Momentum_Reconstruction.py", line 63
    while abs(tp0) >= eps_t:
        ^
SyntaxError: invalid syntax

But spjackson I think the matter isn't coming from the parenthesis.
Well in fact before posting it, i was thinking of the function abs() in condition which the compilator should not really appreciate.

---

### Post by aurelien6 on 2016-03-14
I tried to change differently but there is again an incomprehensible invalid syntax...

eps_t = 10**-13                 #uncertainty TOF error in second
t0 = 47629.8*10**-9             #TOF peak center
tp0 = mp.sqrt(2*m_i*a/(q_i*E)) +  d*mp.sqrt(1/(2*q_i*E*a/m_i) -t0
t_ab = abs(pt0)
    
while t_ab >= eps_t:
<TAB>a = a -tp0*10**3
<TAB>tp0 = mp.sqrt(2*m_i*a/(q_i*E)) +  d*mp.sqrt(1/(2*q_i*E*a/m_i) -t0
<TAB>t_ab = abs(tp0)

%run Momentum_Reconstruction.py
  File "/Users/asanchez/anaconda/scripts/Momentum_Reconstruction.py", line 62
    t_ab = abs(pt0)
       ^
SyntaxError: invalid syntax

---

### Post by aurelien6 on 2016-03-14
Well, it's solved.
You were right about the variable tp0 definition,
I have fixed it by put d=0 and threw the second term.
Hence, the second part is vanished and there is no more invalid syntax.
Thanks guys

---

