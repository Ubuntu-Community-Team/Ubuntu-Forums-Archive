---
title: "Command line replace"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by max20 on 2013-09-05
I trying to figure out how to have a command line replace kind like the example below

Command Line.
$ echo ${var} | var=2

Output:
$ 2

something like that









a233663_drdrb

---

### Post by matt_symes on 2013-09-05
Hi

I really don't understand your question, so i'll have a punt at...

```
matthew-S206:/home/matthew % var=2 && echo ${var}
2
matthew-S206:/home/matthew % 

```

Are you trying to achieve something like that ?

Kind regards

---

### Post by HiImTye on 2013-09-06
always quote your variables to avoid future problems 
```
v='2'; echo "$v"
```
edit: nvm I see you used curly braces its just backwards   [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by max20 on 2013-09-10
Is there a way to switch the echo and the var around like:
```
matthew-S206:/home/matthew % echo ${var} && var=2 
2
matthew-S206:/home/matthew %
```

---

### Post by Dave_L on 2013-09-10
> **max20 said:**
> Is there a way to switch the echo and the var around like:
```
echo ${var} && var=2 
2

```

I don't think so, since expressions are evaluated from left to right.

Why do you want to do that?

---

### Post by max20 on 2013-09-18
I'm trying to create an alias such as
alias search='find . -iname "*.jpg"'

where the dot(.) can be replace like
$ search ./folder

---

### Post by steeldriver on 2013-09-18
You can use a bash *function *instead of an alias

```
function mysearch() { find "$1" -iname '*.jpg' ; }
```

See [http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)

---

