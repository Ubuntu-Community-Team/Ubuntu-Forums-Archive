---
title: "Scripting with two required conditionals"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by Djyou on 2013-06-01
Not sure were to put this really, but I'm trying to make a welcome script that greets whoever uses my computer when they log in. I've been working on the script and as of current I get an issue with an unexpected token on line 7, The greeting is set to change based on when you log in. If anyone can tell me what I'm doin wrong I would really apreciate it.

```

#! /bin/bash
# Voice synth'ed welcome script

## If earlier than 05:30
 if $(date "+%H%M") -lt 0530{
espeak -s 140 -ven-us+f4 "Why are you up this early $USER ?"
}
## If bewteen 05:30 and 12:00
if $(date "+%H%M") -gt 0530 && $(date "+%H%M") -lt 1200{
espeak -s 140 -ven-us+f4 "Good morning, $USER"
}
## If between 12:00 and 21:30
if $(date "+%H%M") -gt 1200 && $(date "+%H%M") -lt 2130{
espeak -s 140 -ven-us+f4 "Good afternoon, $USER"
}
## If later than 21:30
if $(date "+%H%M") -gt 2130{
espeak -s 140 -ven-us+f4 "Hello $USER, are you sure you should be logging in at$
}

```

As always thanks for you time in advance even if you just read this post and nothing else.

--Djyou

---

### Post by Djyou on 2013-06-01
So just noticed command line thread.

---

### Post by steeldriver on 2013-06-01
[LIST]
[*]the bash syntax for conditionals is if ... **then** ... **fi** 
[*]unlike 'C', { ... } isn't the right way to group statements - you need ; or line breaks 
[*]try using the [ ... ] test operator for the -gt 
[*]get into the habit of quoting shell expansions like $( ... ) 
[/LIST]

```

if [COLOR=#0000ff]**[**[/COLOR] [COLOR=#0000ff]**"**[/COLOR]$(date '+%H%M')[COLOR=#0000ff]**"**[/COLOR] -gt 0530 [COLOR=#0000ff]**];**[/COLOR] [COLOR=#0000ff]**then **[/COLOR]
    espeak -s 140 -ven-us+f4 "Why are you up this early $USER ?"
[COLOR=#0000ff]**fi**[/COLOR]

```

or

```

if [COLOR=#0000ff]**[**[/COLOR] [COLOR=#0000ff]**"**[/COLOR]$(date '+%H%M')[COLOR=#0000ff]**"**[/COLOR] -gt 0530 [COLOR=#0000ff]**] **[/COLOR] [COLOR=#0000ff][B]
then [/B][/COLOR]
    espeak -s 140 -ven-us+f4 "Why are you up this early $USER ?"
[COLOR=#0000ff]**fi**[/COLOR]

```

---

### Post by Djyou on 2013-06-01
Okay well that becomes much more obvious. Also flash/java habit never even touch 'C' and I still can't really use flash or java well.
Instant edit: Forgot say thanks. So thanks.

---

### Post by Djyou on 2013-06-01
Okay one problem down still more to go, the script still can't handle the double conditionals, do I just do a an else if pyramid? No more line seven error now it's line nine. Here's the new code.

```

#! /bin/bash
# Voice synth'ed welcome script

## If earlier than 05:30
 if [ "$(date '+%H%M')" -lt 0530 ]; then
espeak -s 140 -ven-us+f4 "Why are you up this early $USER ?"
fi
## If bewteen 05:30 and 12:00
if [ "$(date '+%H%M')" -gt 0530 && $(date "+%H%M") -lt 1200]; then
espeak -s 140 -ven-us+f4 "Good morning, $USER"
fi
## If between 12:00 and 21:30
if [ "$(date '+%H%M')" -gt 1200 && "$(date '+%H%M')" -lt 2130]; then
espeak -s 140 -ven-us+f4 "Good afternoon, $USER"
fi
## If later than 21:30
if [ "$(date '+%H%M')" -gt 2130]; then
espeak -s 140 -ven-us+f4 "Hello $USER, are you sure you should be logging in at$
fi

```

As always thanks in advance
--Djyou

ADDED: I'm going to try the else is pyramid idea now

---

### Post by steeldriver on 2013-06-01
For the 'simple test' brackets [ ... ] the way to logically combine tests is -a (AND) or -o (OR)

```
if [ "$(date '+%H%M')" -gt 0530 [COLOR=#0000ff]**-a**[/COLOR] "$(date '+%H%M')" -lt 1200 ]
```

(don't forget the space around the [  and ]). If you want to use '&&' and '||' logical operators you can do so via the bash 'extended test' operators [[ .. ]] or since these are arithmetic tests maybe better to use the (( ... )) forms - see [http://tldp.org/LDP/abs/html/testconstructs.html](http://tldp.org/LDP/abs/html/testconstructs.html)

---

### Post by Djyou on 2013-06-01
Thank you very much, I probably would have spent hours on this only to give up in frustration plus the else if pyramid did not work. Unexpected token? any way thanks.

--Djyou

P.S. Final code

```

#! /bin/bash
# Voice synth'ed welcome script

## If earlier than 05:30
 if [ "$(date '+%H%M')" -lt 0530 ]; then
espeak -s 140 -ven-us+f4 "Why are you up this early $USER ?"
fi
## If bewteen 05:30 and 12:00
if [ "$(date '+%H%M')" -gt 0530 -a $(date "+%H%M") -lt 1200 ]; then
espeak -s 140 -ven-us+f4 "Good morning, $USER"
fi
## If between 12:00 and 21:30
if [ "$(date '+%H%M')" -gt 1200 -a "$(date '+%H%M')" -lt 2130 ]; then
espeak -s 140 -ven-us+f4 "Good afternoon, $USER"
fi
## If later than 21:30
if [ "$(date '+%H%M')" -gt 2130 ]; then
espeak -s 140 -ven-us+f4 "Hello $USER, are you sure you should be logging in at this time?"
fi

```

---

### Post by steeldriver on 2013-06-01
You're welcome, yes it does take a bit of adjustment (especially if you are used to other syntaxes like C) - tldp is a great resource though, also Greg's "bash pitfalls" wiki --> [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by VMC on 2013-06-01
i modified it a tad. Missing some brackets and constructs:

```
#! /bin/bash# Voice synth'ed welcome script


DATE=$(date "+%H%M");


## If earlier than 05:30
if [ $DATE -lt "0530" ]; then
 espeak -s 140 -ven-us+f4 "Why are you up this early $USER ?"


## If bewteen 05:30 and 12:00
elif [[ "$DATE" -gt "0530" && "$DATE" -lt "1200" ]]; then
 espeak -s 140 -ven-us+f4 "Good morning, $USER"


## If between 12:00 and 21:30
elif [[ "$DATE" -gt 1200 && "$DATE" -lt 2130 ]]; then
 espeak -s 140 -ven-us+f4 "Good afternoon, $USER"


## If later than 21:30
elif ["$DATE" -gt 2130]; then 
 espeak -s 140 -ven-us+f4 "Hello $USER, are you sure you should be logging in at$"
fi
```

---

### Post by Djyou on 2013-06-01
VMC would you mind telling me what use you modifications serve (other than lowering file size with a variable) if it worked fin before? Also where do I put the blasted thing if I want it to run whenever ANY user logs in. Thanks in advance.

--Djyou

---

### Post by dodo3773 on 2013-06-02
Here is another way you can do it too:
```

#! /bin/bash
x=$(date '+%H%M')
y="espeak -s 140 -ven-us+f4" 
(( x > 0530 && x < 1200)) && $y  "Good morning, $USER"
(( x > 1200 && x < 2130)) && $y  "Good afternoon, $USER"
(( x > 2130 && x < 0530)) && $y  "Hello $USER, are you sure you should be logging in at $x"

```


I don't use espeak. Tested with echo and it worked though.

---

### Post by Djyou on 2013-06-02
You missed on actually between 00:00 and 05:30 it's supposed to  ask why their logging in at that time.

---

### Post by dodo3773 on 2013-06-02
> **Djyou said:**
> You missed on actually between 00:00 and 05:30 it's supposed to  ask why their logging in at that time.

Not sure if that is directed at me. If so I was just giving you an example. One thing though is wouldn't it make more sense if they weren't overlapping times? Like instead of:
```

(( x > 0530 && x < 1200)) && $y  "Good morning, $USER"
(( x > 1200 && x < 2130)) && $y  "Good afternoon, $USER"

```
it could be
```

(( x > 0530 && x < 1159)) && $y  "Good morning, $USER"
(( x > 1200 && x < 2130)) && $y  "Good afternoon, $USER"

```

See what I mean?

---

### Post by VMC on 2013-06-02
> **Djyou said:**
> VMC would you mind telling me what use you modifications serve (other than lowering file size with a variable) if it worked fin before? Also where do I put the blasted thing if I want it to run whenever ANY user logs in. Thanks in advance.

--Djyou
My answer was for the first post. I was delayed a bit before I answered and no one else had responded at the time. 
I didn't notice at the time there were several responses when I submitted the reply.

---

### Post by Djyou on 2013-06-03
@dodo: Alright thanks for the clrification and I'm used to flash so > 1200 and <1201 actually don't overlap, also <1200 and >1200 wouldn't do anything at 1200  but I'll be working on it and testing how it work at different times.

@VMC Alright sorry about that didn't know. Thanks for the clarification.

---

