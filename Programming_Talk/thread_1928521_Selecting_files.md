---
title: "Selecting files"
date: 2012-02-20
forum: Programming Talk
---

### Post by achuth on 2012-02-20
Sir,
I have 5 files in my folder **ABCD ABCd ABcd aBcD** and **abcd**
I would like to select (using **ls** command) those files which have exactly two lower case alphabets in their name.

I used the following command, but it failed

**ls *[a-b]*[a-b]***

How can I select the files **ABcd** and **aBcD** ?

---

### Post by cortman on 2012-02-20
I assume you just want to list them with ls? Use egrep-

```
ls | egrep '^[A-Z]*[a-z][A-Z]*[a-z][A-Z]*$'
```

This will match files with any number of upper case letters and only two lowercase. With Perl you could make a far more elegant regex, but this will work.

---

### Post by ofnuts on 2012-02-20
> **achuth said:**
> Sir,
I have 5 files in my folder **ABCD ABCd ABcd aBcD** and **abcd**
I would like to select (using **ls** command) those files which have exactly two lower case alphabets in their name.

I used the following command, but it failed

**ls *[a-b]*[a-b]***

How can I select the files **ABcd** and **aBcD** ?
```

ls *([[:upper:]])[[:lower:]]*([[:upper:]])[[:lower:]]*([[:upper:]])
# or
ls *([![:lower:]])[[:lower:]]*([![:lower:]])[[:lower:]]*([![:lower:]])

```(yes, bash regexps are very verbose)

PS: things like [a-z]/[A-Z] won't usually work (unless you set LC_COLLATE to 'C')

---

### Post by cortman on 2012-02-20
> **ofnuts said:**
> ```

ls *([[:upper:]])[[:lower:]]*([[:upper:]])[[:lower:]]*([[:upper:]])
# or
ls *([![:lower:]])[[:lower:]]*([![:lower:]])[[:lower:]]*([![:lower:]])

```(yes, bash regexps are very verbose)

PS: things like [a-z]/[A-Z] won't usually work (unless you set LC_COLLATE to 'C')

I must have missed the "ls" only part of the OP's question... egrep sure makes it a little cleaner. I didn't know what regex flavor ls supported.

---

### Post by achuth on 2012-02-20
I would like to list only files with exactly two lower case alphabets in it.

---

### Post by ofnuts on 2012-02-21
> **achuth said:**
> I would like to list only files with exactly two lower case alphabets in it.So what doesn't work in the code bits above (whether it's sed or ls?)

---

### Post by achuth on 2012-02-21
Yes ok. It is working fine.
Thanks.
But please explain the following command a bit more.

ls *([[:upper:]])[[:lower:]]*([[:upper:]])[[:lower:]]*([[:upper:]])

---

### Post by Vaphell on 2012-02-22
[http://www.linuxjournal.com/content/bash-extended-globbing](http://www.linuxjournal.com/content/bash-extended-globbing)

[COLOR="Navy"]*([COLOR="DarkGreen"]pattern-list[/COLOR])[/COLOR]   Matches zero or more occurrences of the given patterns

```
[COLOR="Navy"]*([COLOR="DarkGreen"][[:upper:]][/COLOR])[/COLOR] [[:lower:]] [COLOR="Navy"]*([COLOR="DarkGreen"][COLOR="DarkGreen"][[:upper:]][/COLOR][/COLOR])[/COLOR] [[:lower:]] [COLOR="Navy"]*([COLOR="DarkGreen"][[:upper:]][/COLOR])[/COLOR]
```

---

### Post by ofnuts on 2012-02-22
> **achuth said:**
> Yes ok. It is working fine.
Thanks.
But please explain the following command a bit more.

ls *([[:upper:]])[[:lower:]]*([[:upper:]])[[:lower:]]*([[:upper:]])

[LIST]
[*]>=0 uppercase
[*]1 lowercase
[*]>=0 uppercase
[*]1 lowercase
[*]>=0 uppercase
[/LIST]
That makes anything alphabetic with exactly two lowercase characters.

---

