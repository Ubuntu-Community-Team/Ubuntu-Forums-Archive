---
title: "Help with bash scripting"
date: 2011-10-21
forum: Programming Talk
---

### Post by SavvasKatseas on 2011-10-21
Hi,

this is a newbie question, so a) if this isn't the right place for it to be feel free to move it and b) if it's easily solveable don't hesitate to just reply with a link where I can read up on it.

I'm trying to write a bash script, and I've included a variable there that points to a file, say:

```
VARIABLEA=/home/user/script.name
```

Now, I want a variable B to contain an echo command that writes something to the file which variable A points to. What I've tried so far is:

```
VARIABLEB=echo "whoo hey hoo hola" >> $VARIABLEA
```

Which doesn't work. Bash informs me that there's no whoo command. Then I've tried command expansion with `

```
VARIABLEB=`echo "whoo hey hoo hola" >> $variableA`
```

Which doesn't work either. Nothing is written to the file.

I'm sure it must a simple thing that I'm missing here and I'd like to know what that is. Any advice or reading material would be appreciated. :)

---

### Post by MG&amp;TL on 2011-10-21
I think you have to declare the value of the variables before you redirect the output of them. I just tried this in an interactive shell (i.e. no script), and the thing works if you declare separately, but not if you don't.

E.g:

```
variableA="Hello"
variableB="mfyile"
echo $variableA >> $variableB
```

This is also the standard way of doing things in other languages.

---

### Post by nothingspecial on 2011-10-21
Always quote your variables.

Use $(commands) instead of backticks.

---

### Post by Lars Noodén on 2011-10-21
> **nothingspecial said:**
> Always quote your variables.

Use $(commands) instead of backticks.

+1 to both

Also, the program [tee](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tee.1.html) allows you to sent output to both [font=Courier New]stdout[/font] and to a file.  Though that's probably more use in a different situation, MG&TL's sequence is probably better.

---

### Post by AlphaLexman on 2011-10-21
> **SavvasKatseas said:**
> Hi,

this is a newbie question, so a) if this isn't the right place for it to be feel free to move it and b) if it's easily solveable don't hesitate to just reply with a link where I can read up on it.

I'm trying to write a bash script, and I've included a variable there that points to a file, say:

```
VARIABLEA=/home/user/script.name
```

Now, I want a variable B to contain an echo command that writes something to the file which variable A points to. What I've tried so far is:

```
VARIABLEB=echo "whoo hey hoo hola" >> $VARIABLEA
```

Which doesn't work. Bash informs me that there's no whoo command. Then I've tried command expansion with `

```
VARIABLEB=`echo "whoo hey hoo hola" >> $variableA`
```

Which doesn't work either. Nothing is written to the file.

I'm sure it must a simple thing that I'm missing here and I'd like to know what that is. Any advice or reading material would be appreciated. :)

```
[COLOR="Red"]#!/bin/bash[/COLOR]

VARIABLEA=[COLOR="red"]"[/COLOR]/home/user/script.name[COLOR="red"]"[/COLOR]

VARIABLEB=[COLOR="red"]$([/COLOR]echo "whoo hey hoo hola"[COLOR="red"])[/COLOR]

echo ${VARIABLEB} >> ${VARIABLEA}
```

The proper corrections are in red.

Also note that in the OP, "$variableA" is NOT equal to "$VARIABLEA" and *nix systems are case sensitive!

**EDIT** @MG&TL: you should not have whitespace around the equal sign when defining a variable (probably just a typo right?)

---

### Post by MG&amp;TL on 2011-10-21
> **AlphaLexman said:**
> @MG&TL: you should not have whitespace around the equal sign when defining a variable (probably just a typo right?)

Yeah. Oops, fixing it, its cool. :)

---

### Post by SavvasKatseas on 2011-10-22
Thanks a lot for all the help!
It's working now.

I'll try reading a bit more about backticks and $(command).
Tee is also interesting, it will allow me to send something both to the terminal and to a file, if I understood correctly. That'll come in handy :)

---

### Post by mörgæs on 2011-10-22
Moved to Programming Talk.

---

