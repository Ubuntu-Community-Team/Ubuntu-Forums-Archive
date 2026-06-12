---
title: "Number Cycle In BASH"
date: 2013-09-18
forum: Programming Talk
---

### Post by spiritech on 2013-09-18
how can i tell bash to reset to 0 after reaching a desired value.  at the moment i have a small script outputting numbers and i use a {function} to correct anything that is above 255. so -

```
function  { if [[ $v -le 255 ]]
                                then echo -n "$v "
                                else until [[ $v -le 255 ]]; do let v=v-255; done; echo -n "$v "
```

the code is fine if the numbers are not to large, however when the numbers become to high, like 20392859286598265962596, the function becomes very slow.

i generate the numbers using different formulas and the numbers can become very high. is there a way i can tell bash to reset/restart each time it reaches a desired value. for instance 10 would result in.

```
v=3; let v=v*3;

3
6
9
2
5

and not

3
6
9
12
15
```

spiritech

---

### Post by steeldriver on 2013-09-18
Not sure I really understand what you want to do, but it sounds like modulo division but be what you are looking for

```

$ for i in {1..10}; do echo $((i*i*i % 255)); done
1
8
27
64
125
216
88
2
219
235

```

---

### Post by spiritech on 2013-09-18
> **steeldriver said:**
> Not sure I really understand what you want to do, but it sounds like modulo division but be what you are looking for

i would like the bash calculator to be cyclic instead of infinate.

---

### Post by spiritech on 2013-09-18
> **steeldriver said:**
> 

```

$ for i in {1..10}; do echo $((i*i*i % 255)); done
1
8
27
64
125
216
88
2
219
235

```

yes this does what i needed.

---

### Post by Vaphell on 2013-09-18
if the allowed numbers are supposed to be in 0-255 range, then it should be **%256**

---

### Post by spiritech on 2013-09-18
ok, i have tried using this in the followong way.

```
echo $((3+3+3+3+3 % 10))

15
```

and it still gives me 15 instead of 5.

i have also tried 

```
for i in {3..10}; do echo $((i+i+i % 10)); done

9
12
15
18
21
24
27
20


```

i replaced the 255 with 10 and expected it to cycle to 9 and reset. not sure what i am doing with this.

---

### Post by spiritech on 2013-09-18
```
echo $(($[256+256]%255))

2

echo $(($[3+3+3+3+3] % 10))

5

for i in {3..10}; do echo $(($[i+i+i] % 10)); done
9
2
5
8
1
4
7
0


```

a second expansion containing the formula solves my problem.

---

### Post by steeldriver on 2013-09-18
Thanks Vaphell ;)

@spiritech, remember bash will follow the standard math operator precedence rules -->  [https://en.wikipedia.org/wiki/Order_of_operations](https://en.wikipedia.org/wiki/Order_of_operations)

---

### Post by Vaphell on 2013-09-18
indeed, % goes before + so $(( (a+b+c)%d ))
$[]? i don't know this one o.O

edit:
[http://stackoverflow.com/questions/2415724/bash-arithmetic-expression-vs-arithmetic-expression](http://stackoverflow.com/questions/2415724/bash-arithmetic-expression-vs-arithmetic-expression)

> The manpage for bash v3.2.48 says:

  [QUOTE]  [...] The format for arithmetic expansion is:

         $((expression))

    The old format $[expression] is deprecated and will be removed in upcoming versions of bash.

So $[...] is old syntax that should not be used anymore.
[/quote]

---

