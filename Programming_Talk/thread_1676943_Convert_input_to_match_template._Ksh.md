---
title: "Convert input to match template. Ksh"
date: 2011-01-27
forum: Programming Talk
---

### Post by gbyx3 on 2011-01-27
Hi
 
I have a problem that I cant get around.
 
This is the template 1$sN$TTT
If input "t" (temperature,) is eg 10.5 the output should be 10105
If "t" is -10.5 the output should be 11105 
If "t" is 1.5 the output should be 10015
If "t" is -1.5 the output should be 11015
 
This is what I got
```

read t 
 
if [[ $t -lt -0.01 ]] ; then ; sN=1
else ; sN=0
fi
 

```
:P
Not that much.
I have tried a couple of solutions but cant get i right
 
//Gustav

---

