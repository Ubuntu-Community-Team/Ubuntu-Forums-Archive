---
title: "sed caps on the mac"
date: 2016-03-06
forum: Programming Talk
---

### Post by maclenin on 2016-03-06
I wish to toggle the case of (only) the leading alpha character of multiple file names on a mac, using (bsd) sed (and tr, perhaps) via the command line.

Is there a better way?

Sample file name / pattern: *A2b.txt*

One way: to lower or to upper
```
for a in *
do
b=$(echo "${a}" | sed -e 's/\(.\)\(.*\)/\1/' | tr '[:upper:]' '[:lower:]') < --- isolate and toggle cap (to lower or to upper) of the leading character
c=$(echo "${a}" | sed -e 's/\(.\)\(.*\)/\2/') < --- isolate all but the leading character
d="${b}${c}" < --- re-attach leading character to remainder of file name
mv "${a}" "${d}" < --- rename file to that with toggled cap
done

```

Notes:
1. I use *rename 's/(.)/\L$1/' ** and *rename 's/(.)/\U$1/' ** to achieve the same in linux.
2. I'd rather not "homebrew" a mac solution. Would prefer to go (mac) native, if possible.

Thanks for any guidance!

---

### Post by sudodus on 2016-03-06
You can use the character **^** for case modification of parameters in bash. From man bash:

>        ${parameter^pattern}
       ${parameter^^pattern}
       ${parameter,pattern}
       ${parameter,,pattern}

              Case modification.  This expansion modifies the case of alphabetic characters in parameter.  The pattern is expanded to produce a pattern just as in pathname expansion.  Each character in the expanded value of parameter  is  tested  against pattern, and, if it matches the pattern, its case is converted.  The pattern should not attempt to match more than one character.  The ^ operator converts lowercase letters matching pattern to uppercase; the , operator converts matching uppercase letters to lowercase.  The ^^ and ,, expansions convert each matched character in the expanded value; the ^ and , expansions match and convert only the first character in the expanded value.  If pattern is omitted, it is treated like a ?, which matches every character.  If parameter is @ or *, the case modification operation is applied to each positional parameter in turn, and the expansion is the resultant list.  If parameter is an array variable subscripted with @ or *, the case modification operation is applied to each member of the array in turn, and the expansion is the resultant list.


Maybe the following link might give you some inspiration: [Post #5 in '~> Capitalize the first letter <~'](http://ubuntuforums.org/showthread.php?t=2315984&p=13450691#post13450691)

---

### Post by maclenin on 2016-03-07
Cheers for the guidance!

However, bash on the mac in question (and gnu bash at that) is a few generations behind (3.2.57) the most current (4.3.xx), so doesn't boast the fancy operators / functionality you've posted my way and linked to for inspiration!

So, I'll make do with the working mock-up until something better (& compatible) comes along!

Thanks, again!

---

