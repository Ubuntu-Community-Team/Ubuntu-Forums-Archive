---
title: "Multiple Variables"
date: 2008-09-01
forum: Programming Talk
---

### Post by Sub101 on 2008-09-01
Hi. I'm writing a script that uses a lot of variables. They are all named "line" then a number. eg. line1, line2 etc. I want to be able to echo each variable one after the other which I could do using: echo $line1, echo $line2. As I have over 40 variables I would like to use a more efficient method using something like $line(number) or $line$number but they obviously don't work. Any help on this would be really appreciated. 
Thanks in advance.

---

### Post by mike_g on 2008-09-01
What you are after is called an Array. Ib, by script you mean a bash script then theres a few code examples here:
[http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

---

### Post by Sub101 on 2008-09-02
Exactly what i was looking for thankyou! 

On top of that would you be able to give any advice on this: 

```
line[1]=$(sed -n '1,1p' /home/steve/Desktop/untitled/Peg.lst)
```

but i would like to replace line[[COLOR="Red"]**1**[/COLOR]] and the [COLOR="Red"]**1,1p**[/COLOR] with a variable. Essentially i would like it to increase each time alongside my while command. Does anyone have any ideas on this? 

At the moment i am using several iterations where i have typed each line in myself. I was looking for a more time effective solution. And sorry i didn't add before, it is for a bash script.

---

### Post by ghostdog74 on 2008-09-02
describe what exactly are you wanting to do. show sample inputs and outputs if possible.

---

