---
title: "Bash Scripting: echo not supporting end-of-options"
date: 2010-02-25
forum: Programming Talk
---

### Post by kayvortex on 2010-02-25
I've built a simple bash shell script, but at some point I need to do a:
> var1="$(echo "$var2" | sed *fairly_complex_substitute_expr* -)"

So, I need to make sure *echo* will actually echo *var2* (which could be anything). However, since bash's *echo* (and also */bin/echo*) does not recognize "--" as an end-of-options option, I'm pretty much stuck if *var2* is "-e" or "-n" or "-E", right?

Does anybody know of a way to make bash's *echo* print out "-n", for example. Id est, does anyone know how to make the following work:
```
echo '-n' '-e' '-E' # does not echo "-n", "-e", or "-E"
```

I could, of course, use *printf*:
```
printf -- "-n\n"
```
which works OK; or put a character in and then cut it:
```
var="_$var" && echo "$var" | cut -c 2-
```
or use *awk*:
```
echo | awk '{ print substr("'"$var"'",1) }'
```
but this seems like a pointless complication when
```
echo -- -n
```
would have been so much simpler! (Zsh's *echo* allows me to use "-" to signify the end of options; although why it's not "--" I don't know.)

If I am genuinely stuck with the more convoluted methods, does anyone at least know why this behaviour is not implemented?

---

### Post by croto on 2010-02-26
if you don't mind an extra space, you could do something like
```

echo '' '-n' '-e' '-E'

```
It looks like an argument not recognized as an option serves as an end-of-option flag...

---

### Post by geirha on 2010-02-26
Use here-string (assuming you are scripting in bash)
```
sed ... <<< "$var"
```
printf should also be safe
```
printf "%s" "$var" | sed ...
```
Though with the here-string, you don't get the overhead of a pipe, so it should be more efficient.

---

### Post by kayvortex on 2010-02-26
croto:
I'd have to cut the space from the output, but yes that's a workaround I considered.

geirha:
Thanks, that's even better than echoing and piping. (Yes, I'm scripting in bash; and also zsh too actually, and zsh can use the here-string as well.)

I'll take the lack of responses on *echo* itself as tacit confirmation that there's no direct way for bash's *echo* to print strings identical to its accepted options. However, there are enough workarounds here for me to mark the thread as solved. Thanks for the help.

---

