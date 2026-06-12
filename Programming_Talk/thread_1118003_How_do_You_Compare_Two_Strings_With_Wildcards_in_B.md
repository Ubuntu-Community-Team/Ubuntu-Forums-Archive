---
title: "How do You Compare Two Strings With Wildcards in Bash?"
date: 2009-04-06
forum: Programming Talk
---

### Post by Penguin Guy on 2009-04-06
```

[COLOR="Red"]if [ "foobar" == *"bar" ]; then[/COLOR]     # Won't work because you need double brackets '[[...]]'
[COLOR="Red"]if [[ "foobar" == "*bar" ]]; then[/COLOR]   # Will not work because * is inside quotes
[COLOR="Green"]if [[ "foobar" == *"bar" ]]; then[/COLOR]   # Will work

```

Thanks to everyone who helped!

---

### Post by akvino on 2009-04-06
I am not sure if this is what you're looking for but if I were you I would set a variable to take the input or if you want

'$*' will give you the entire input argument.

---

### Post by Martin Witte on 2009-04-06
It has to do with quotation, see [this link]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html")
```
martin@pc ~
$ if [[ "abc: GPG encrypted data" = *': GPG encrypted data' ]]; then echo Match
; fi
Match

```

---

### Post by Penguin Guy on 2009-04-06
Thank you! I just needed to put the '*' outside the quotation marks and use double square-brackets.

---

### Post by Penguin Guy on 2009-04-06
Here is the correct code:
```
#!/bin/bash
# Compare Test

if [[ "abc: GPG encrypted data" = *": GPG encrypted data" ]]; then
 echo "Match!"
 exit 0
else echo "No match."
fi

exit 1
```

---

### Post by ghostdog74 on 2009-04-06
you can also use case/esac

---

### Post by Penguin Guy on 2009-04-07
Unless I am actually comparing multiple items, I think I'll stick with if for now, thanks anyawy!

---

