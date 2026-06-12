---
title: "Hex to Ascii, loop-question [BASH]"
date: 2013-08-21
forum: Programming Talk
---

### Post by DarkAmbient on 2013-08-21
To get the character n, I could run:
```
echo -e "\\x6e" | awk '{printf "%c", $1}'
```

or

```
echo -e \\x6e|cat
```

My question is, how do I implement that in a loop resting inside a function that would echo back the translated ascii?
This is what I've done so far:

```
dec() {
    a=""
    for h in ${@}; do
        a=$a`echo -e "\\x$h" | awk '{printf "%c", $1}'`
        #a=$a`echo -e \\x$h|cat`
    done
    echo $a
}
```


```
echo "`dec 67 6f 6f 64`"
```

Should say "good".

But all I get is the "----", from the e flag... If i skip the e flag, I get a "\".

If I format the echo + awk command in the loop like this:

```
a=$a`echo "0x21" | awk '{printf "%c", $1}'`
```

then I only get the correct ascii from some hex-values.  6e should be n, I get zero. 6f should o, returns zero, etc..


Could someone shed some light over this please?

---

### Post by trent.josephsen on 2013-08-21
Is that the exact code you tested?

```
% bash
$ dec() {
>     a=""
>     for h in ${@}; do
>         a=$a`echo -e "\\x$h" | awk '{printf "%c", $1}'`
>         #a=$a`echo -e \\x$h|cat`
>     done
>     echo $a
> }
$ dec 67 6f 6f 64
good
```

Is it possible you have something funky going on with echo?

---

### Post by steeldriver on 2013-08-21
The "%b" printf specifier in bash seems to work with \x escape codes directly - maybe no need to use echo -e and/or awk?

```

$ chars=( 67 6f 6f 64 ); for c in ${chars[@]}; do printf "%b" "\x${c}"; done; printf "\n"
good

```

From [FONT=courier new]help printf[/FONT] in bash:

```

     %b    expand backslash escape sequences in the corresponding argument

```

---

### Post by DarkAmbient on 2013-08-21
Hm, tried in terminal and I got "good" aswell..

But why do I get "----" when I got this in a scriptfile (named decode.sh in my case):

```
#!/bin/sh
dec() {
    a=""
    for h in ${@}; do
        a=$a`echo -e "\\x$h" | awk '{printf "%c", $1}'`
        #a=$a`echo -e \\x$h|cat`
    done
    echo $a
}
# should be "Your a good person!"
hex="59 6f 75 72 20 61 20 67 6f 6f 64 20 70 65 72 73 6f 6e 21"

echo "`dec 67 6f 6f 64`"
#echo "`dec $hex`"
```

And run it like sh decode.sh

EDIT:

Ok, so bash works instead of sh... (bash decode.sh). Guess I gotta read up some more on sh vs bash.

Edit2: 

```
a=$a`echo -e "\\x$h" | awk '{printf "%c", $1}'`
``` gave me no spaces.

using ```
a=$a`echo -e \\x$h|cat`
``` did.

This works now:

```
#!/bin/bash
dec() {
    a=""
    for h in ${@}; do
        a=$a`echo -e "\\x$h" | cat`
    done
    echo $a
}
# should popup "Your a good person!"
notify-send "`dec 59 6f 75 27 72 20 61 20 67 6f 6f 64 20 70 65 72 73 6f 6e 21`"
```

---

### Post by steeldriver on 2013-08-21
I think that your specific problem (the ---) may be that you are using /bin/sh which is symlinked to the dash shell, and dash is using a builtin 'echo' that doesn't support the -e option

In /bin/sh:

```

$ dec() { for c in ${@}; do **echo** -e "\x${c}" | awk '{printf "%c", $1}'; done }
$ dec "67 6f 6f 64"
----$ 

```

If you replace 'echo' with an explicit '/bin/echo' it should work even in dash:

```

$ dec() { for c in ${@}; do **/bin/echo** -e "\x${c}" | awk '{printf "%c", $1}'; done }
$ dec "67 6f 6f 64"
good$ 

```

---

### Post by DarkAmbient on 2013-08-21
> **steeldriver said:**
> I think that your specific problem (the ---) may be that you are using /bin/sh which is symlinked to the dash shell, and dash is using a builtin 'echo' that doesn't support the -e option

In /bin/sh:

```

$ dec() { for c in ${@}; do **echo** -e "\x${c}" | awk '{printf "%c", $1}'; done }
$ dec "67 6f 6f 64"
----$ 

```

```

$ dec() { for c in ${@}; do **/bin/echo** -e "\x${c}" | awk '{printf "%c", $1}'; done }
$ dec "67 6f 6f 64"
good$ 

```

Oh, that's a reason way more advanced that I wanted it to be. :p Thank you for explaining though!

Ok, found this for a starter. [Difference between sh and bash]("http://stackoverflow.com/a/5725402/2652729")
Never to late to learn stuff! :)

---

