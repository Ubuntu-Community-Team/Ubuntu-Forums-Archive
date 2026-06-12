---
title: "Bash handling arguments with spaces"
date: 2012-11-11
forum: Programming Talk
---

### Post by kiplingw on 2012-11-11
Hey forum,

I'm having a problem with Bash and my head is sore from banging it against my desk. All I am trying to do is have my shell script preserve the arguments passed to it and then pass those original argument on to an inferior process. Between start and finish, other functions are executed, so I cannot simply call the inferior process with $@ as an argument because that shell variable is clobbered by then.

Here is an example of the problem I am having:
```

#!/usr/bin/env bash
Arguments=$@
for Index in ${Arguments}
do
    echo $Index
done

```

This is what is produced:
```

$ ./minimal.sh some thing something\ else
some
thing
something
else

```

This is what I had expected to see:
```

$ ./minimal.sh some thing something\ else
some
thing
something else

```

Any help appreciated.

---

### Post by Vaphell on 2012-11-11
```
for Index **in ${Arguments}**; do ...
```
if you dropped that part, it would work. *for variable;* implicitly iterates over script parameters

also you have to keep your $@ in double quotes to protect against individual parameters dissolving into pieces

when you have params like:
"abc" "def" "g h i"
and you do something like
```
for p in $@; do ...
```
$@ is substituted and the shell sees this
```
for p in abc def g h i; do ...
```
and you want this
```
for p in "abc" "def" "g h i"; do ...
```
that's why you have to quote $@


look at this example showcasing parameters passing through without any distortions
params-parent.sh (parent):
```
#!/bin/bash

echo "=== $0 ==="
for p; do printf "(%s)" "$p"; done; echo " [$#]"
echo
echo "*** parameters used directly"
echo "BAD"
./params-child.sh [COLOR="Red"]$@[/COLOR]
echo "GOOD"
./params-child.sh [COLOR="Blue"]"$@"[/COLOR]
echo
echo "*** parameters used indirectly (array)"
param=( [COLOR="Blue"]"$@"[/COLOR] )
echo "BAD"
./params-child.sh [COLOR="Red"]${param[@]}[/COLOR]
echo "GOOD"
./params-child.sh [COLOR="Blue"]"${param[@]}"[/COLOR]
```
params-child.sh (child):
```
[COLOR="DarkGreen"]#!/bin/bash

echo "=== $0 ==="
echo "number of parameters received: $#"
echo -n "parameters: "
for p; do printf "(%s)" "$p"; done
echo[/COLOR]
```


```
$ ./params-parent.sh "a b" c d\ e $'f\tg' 
=== ./params-parent.sh ===
(a b)(c)(d e)(f	g) [4]

*** parameters used directly
BAD
[COLOR="DarkGreen"]=== ./params-child.sh ===
number of parameters received: [COLOR="Red"]7[/COLOR]
parameters: [COLOR="Red"](a)(b)(c)(d)(e)(f)(g)[/COLOR][/COLOR]
GOOD
[COLOR="DarkGreen"]=== ./params-child.sh ===
number of parameters received: [COLOR="Blue"]4[/COLOR]
parameters: [COLOR="Blue"](a b)(c)(d e)(f	g)[/COLOR][/COLOR]

*** parameters used indirectly (array)
BAD
[COLOR="DarkGreen"]=== ./params-child.sh ===
number of parameters received: [COLOR="Red"]7[/COLOR]
parameters: [COLOR="Red"](a)(b)(c)(d)(e)(f)(g)[/COLOR][/COLOR]
GOOD
[COLOR="DarkGreen"]=== ./params-child.sh ===
number of parameters received: [COLOR="Blue"]4[/COLOR]
parameters: [COLOR="Blue"](a b)(c)(d e)(f	g)[/COLOR][/COLOR]

```

---

### Post by kiplingw on 2012-11-11
> **Vaphell said:**
> ```
for Index **in ${Arguments}**; do ...
```
if you dropped that part, it would work. *for variable;* implicitly iterates over script parameters



Hey Vaphell. The problem is I need to preserve the arguments to the script because I need to pass them on to an inferior process later. That is why I need to keep the Arguments variable. I can't count on $@ to still be valid because it will be clobbered by that time, having called many internally defined script functions by then, each in turn writing over it.

---

### Post by Vaphell on 2012-11-11
That part was more about printing parameters out. Read the rest of my post, it goes into detail and provides an example. $@ is only clobbered when you allow it.

---

### Post by kiplingw on 2012-11-12
Hey Vaphell. Maybe I'm missing something, but I believe I've already tried what you are saying:

```

#!/usr/bin/env bash
Arguments=( "$@" )
for Index in "${Arguments}"
do
    echo $Index
done

```

```

$ ./minimal.sh --foo doo\ zoo
--foo

```

Something aint right.

---

### Post by Vaphell on 2012-11-12
no you didn't
**for X in $Y; ...** is not the same as **for X; ...** nor it's the same as **for X in "${ARRAY[COLOR="Blue"][@][/COLOR]}"; ...**

---

### Post by kiplingw on 2012-11-12
Vaphell, I understand that. As I've said three times now, I need to preserve the script's arguments and cannot rely on them being implicitly available through the shorthand for loop notation. As soon as a new stack frame is created for a new local function being called, those parameters are gone. I call many local functions before invoking the inferior process.

---

### Post by Vaphell on 2012-11-12
>  I need to preserve the script's arguments and cannot rely on them being implicitly available through the shorthand for loop notation. 

but it was you who quoted some *for* loop as being a problem. My example (with parent script calling child script with its own parameters) you apparently missed shows that unclobbered parameters are passed to another script just fine, either by using *child "$@"* or by using *array=("$@"); child "${array[@]}"*
Show the crux of your problem or we will be running in circles here.

---

### Post by kiplingw on 2012-11-12
> **Vaphell said:**
> but it was you who quoted some *for* loop as being a problem. My example (with parent script calling child script with its own parameters) you apparently missed shows that unclobbered parameters are passed to another script just fine, either by using *child "$@"* or by using *array=("$@"); child "${array[@]}"*
Show the crux of your problem or we will be running in circles here.

The loop I was showing you was not my actual problem code, but just a minimal. I believe I've also tried the syntax you mentioned, but maybe I missed something.

The problem code is [here]("https://bazaar.launchpad.net/~avaneya/avaneya/trunk/view/head:/Extras/Viking%20Lander%20Remastered/Launcher/Source/autorun.sh"). An attempt is made to preserve the script's arguments on line 42, and passed to an inferior process on lines 437 and 442.

---

### Post by Vaphell on 2012-11-12
ok, from the top
assume parameters: [COLOR="Blue"]"a b" "c" "d e"[/COLOR]
when you do something like this:
```
Arguments=[COLOR="Blue"]$@[/COLOR]
```
bash does this:
```
Arguments=a b c d e
```
any information about what constitutes a single entity is lost. Storing all params in a single variable can NEVER work properly if you can stumble upon any whitespace. In other words: don't do it.

```
/usr/bin/env python "${PYTHON_LAUNCHER_MAIN}" ${Arguments}
```
is equal to
```
/usr/bin/env python ... [COLOR="Blue"]a b c d e[/COLOR]
```
quoting that variable ("${Arguments}") won't work, bash would see this:
```
/usr/bin/env python ... [COLOR="Blue"]"a b c d e"[/COLOR]
```
as i said, original information about parameters is destroyed



now, if you want to pass parameters through without any change you have two options
1. call all parameters directly (preparation line not needed)
```
/usr/bin/env python "${PYTHON_LAUNCHER_MAIN}" [COLOR="Blue"]"$@"[/COLOR]
```
which is equal to
```
/usr/bin/env python ... [COLOR="Blue"]"a b" "c" "d e"[/COLOR]
```
2. use array
```
Arguments=( [COLOR="Blue"]"$@"[/COLOR] )  # Arguments=( [COLOR="Blue"]"a b" "c" "d e"[/COLOR] )
/usr/bin/env python "${PYTHON_LAUNCHER_MAIN}" [COLOR="Blue"]"${Arguments[@]}"[/COLOR]
```
which is equal to
```
/usr/bin/env python ... [COLOR="Blue"]"a b" "c" "d e"[/COLOR]
```

array approach is potentially more flexible because you can do nifty things like this with the array:
```
Arguments=( "x" "y" [COLOR="Blue"]"$@"[/COLOR] "z" ) # args=( "x" "y" [COLOR="Blue"]"a b" "c" "d e"[/COLOR] "z" )
Arguments+=( "111" "222" )     # args=( "x" "y" [COLOR="Blue"]"a b" "c" "d e"[/COLOR] "z" "111" "222" )
...
/usr/bin/env python ... "${Arguments[@]}"
=
/usr/bin/env python ... "x" "y" [COLOR="Blue"]"a b" "c" "d e"[/COLOR] "z" "111" "222"

```
quoting these "$@" and "${array[@]}" is crucial though, without it parameters will break down to pieces, just like they do in your current scenario. I showcased it in my earlier post, with red color marking the results of such a negligence and blue color marking the proper solutions.
If you don't know bash' in-and-outs well, go with the following rule of thumb: **"no variable is left unquoted"**

---

### Post by kiplingw on 2012-11-12
> **Vaphell said:**
> ok, from the top
2. use array
```
Arguments=( [COLOR="Blue"]"$@"[/COLOR] )  # Arguments=( [COLOR="Blue"]"a b" "c" "d e"[/COLOR] )
/usr/bin/env python "${PYTHON_LAUNCHER_MAIN}" [COLOR="Blue"]"${Arguments[@]}"[/COLOR]
```
which is equal to
```
/usr/bin/env python ... [COLOR="Blue"]"a b" "c" "d e"[/COLOR]
```


I don't know why, but suddenly this seems to work now. I could have sworn I had tried this already. Regardless, thanks for the bash refresher.

---

### Post by Vaphell on 2012-11-12
most likely you missed either **""** (parameters breaking down) or **[@] **(only first element will be shown)... or both. You need everything to be in order for it to work (**[COLOR="Blue"]"[/COLOR]${X[COLOR="Blue"][@][/COLOR]}[COLOR="Blue"]"[/COLOR]**)

---

### Post by kiplingw on 2012-11-12
Yes, that could be. The syntax is quite cumbersome.

---

