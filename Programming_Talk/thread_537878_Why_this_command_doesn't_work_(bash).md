---
title: "Why this command doesn't work (bash)"
date: 2007-08-29
forum: Programming Talk
---

### Post by Yuzem on 2007-08-29
I am making a script and I need to make a list of files to play in Banshee.
Banshee isn't the problem, the same happens with moc and totem.

The next command works:
```
totem "file1.mp3" "file2.mp3" "etc.mp3"
```

Then I get the list of files in the way I want with the following command from a directory with mp3 files:
```
find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' '
```

If I paste the result of the previous command in front of "totem" It works, but if I put all together it doesn't work:
```
totem $(find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```

Any ideas?

---

### Post by Nekiruhs on 2007-08-29
Why do you have quotes around "$PWD", wouldn't it just be $PWD? Thats saying find the string "$PWD", not the value of PWD variable.

---

### Post by Ramses de Norre on 2007-08-29
> **Nekiruhs said:**
> Why do you have quotes around "$PWD", wouldn't it just be $PWD? Thats saying find the string "$PWD", not the value of PWD variable.

```
~$ echo $PWD
/home/ramses
~$ echo "$PWD"
/home/ramses
~$ echo "\$PWD"
$PWD

```

If you've got spaces in your path you even _must_ use quotes.

---

### Post by duff on 2007-08-29
```
# cat script.sh 
#!/bin/bash

function f {
        echo "\$1: $1"
        echo "\$2: $2"
        echo "\$3: $3"
}

f "foo bar baz"
eval f "foo bar baz"

# ./script.sh 
$1: foo bar baz
$2: 
$3: 
$1: foo
$2: bar
$3: baz

```

---

### Post by Yuzem on 2007-08-29
mmm... I don't understand that code, I am a newbie :lolflag:

What I want is a working alternative to the following code:
```
totem $(find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```

I don't know why it doesn't work but there must be a way to do that...
...or not?:(

---

### Post by duff on 2007-08-29
> **Yuzem said:**
> mmm... I don't understand that code, I am a newbie :lolflag:

What I want is a working alternative to the following code:
```
totem $(find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```

I don't know why it doesn't work but there must be a way to do that...
...or not?:(

then put "eval" before totem

---

### Post by Yuzem on 2007-08-29
Wow!!! Thanks a lot!
That works perfectly.

---

