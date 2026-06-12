---
title: "regular expression for consecutive appearance of a character"
date: 2010-07-23
forum: Programming Talk
---

### Post by beanryu on 2010-07-23
Hi people, I've been trying to come up with a regular expression for find strings like:
mmm
xxxxxxx
iiii

that is, if I use grep "express" test.dat
It will output the lines above.

I might be really dumb, I just can't seem to find a solution.

---

### Post by ghostdog74 on 2010-07-23
```

$ cat file
mmm
xxxxxxx
iiii
abc

$ grep -E  "(.)\1" file
mmm
xxxxxxx
iiii


```

---

### Post by Some Penguin on 2010-07-23
It's pretty simple if you're allowed to use backreferences.  You can refer to a previous capturing group in the same regular expression, at least in languages like Perl.

---

### Post by bigboy_pdb on 2010-07-23
I'm assuming that this is what you want:

```

egrep -o '(.)\1+' < file

```

The "-o" option prints only the characters matching the expression. The brackets capture (remember) whatever is inside them. In this case it's the dot, which is any character. The 1 preceded by a backslash references what was captured by the brackets. The plus sign signifies that one or more occurrence of what precedes it must be matched.

In other words for each character it encounters, it matches and remembers it. When the next character and any following characters are the same as the remembered character they count as matches and since nothing else is left to be matched, everything that was matched is printed.

egrep is for extended regular expressions. If you want to do it using non-extended regular expressions, you can use the following code:

```

grep -o '\(.\)\1\+' < file

```

The only difference between extended and non-extended regular expressions is that in non-extended regular expressions certain characters must be preceded by backslashes to give them special meaning whereas with extended regular expressions those characters have a special meaning and preceding them by backslashes causes them to be interpreted as the character typed. For example:

**Non-extended Regular Expressions:**
**+** matches the plus sign
**\+** matches one or more occurrence of what is before it

**Extended Regular Expressions:**
**+** matches one or more occurrence of what is before it
**\+** matches the plus sign

Notice that in the example the only difference is that the definitions are inverted.

---

