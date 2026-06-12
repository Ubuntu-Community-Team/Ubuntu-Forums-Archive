---
title: "sed: capitalizing the first letter of a line"
date: 2013-10-26
forum: Programming Talk
---

### Post by sha1sum on 2013-10-26
Hello guys,

I'd like to instruct [FONT=courier new]sed[/FONT] to capitalize the first letter of every line. I've gotten this far:

```
$ echo "the first word is not capitalized." | sed 's/^t/T/'
The first word is not capitalized.

```

That seems to work (yay!). Say I'd like to do it for multiple different lines of text, then of course I could do something like this:
```
$ cat bigstory.txt | sed 's/^a/A/; s/^b/B/; s/^c/C/; s/^d/D/; s/^e/E/'
``` 
etcetera, and make a huge command. But that is not very elegant. There has to be a nice way to do it. Do you know one?

---

### Post by Bachstelze on 2013-10-26
I know I'm not supposed to say this but... Google is your friend, really.

```
sed -e 's/^\(.\)/\U\1/g' foo.txt
```

This seems to be non-standard, I do not know the standard way.

---

### Post by steeldriver on 2013-10-26
There's a special instruction \u for that - combined with the & which substitutes the whole pattern found

```

$ echo "the first word is not capitalized." | sed 's/.*/\u&/'
The first word is not capitalized.

```

FYI, to capitalize the whole thing it's \U

```

$ echo "the first word is not capitalized." | sed 's/.*/\U&/'
THE FIRST WORD IS NOT CAPITALIZED.

```

---

### Post by sha1sum on 2013-10-26
Thanks guys. I'm learning how to use the command line, this helps. sed seems to be a difficult command to work with, the way it takes arguments appears so random.

> **Bachstelze said:**
> I know I'm not supposed to say this but... Google is your friend, really.
I'll try to do that more in the future.

---

### Post by Bachstelze on 2013-10-26
sed is not just a "command", for most intents and purposes you can treat it as a programming language in its own right.

---

### Post by vasa1 on 2013-10-26
> **Bachstelze said:**
> I know I'm not supposed to say this but... Google is your friend, really.

```
sed -e 's/**^**\(.\)/\U\1/**g**' foo.txt
```

This seems to be non-standard, I do not know the standard way. Why do you say it's non-standard? And why have **g** when it's just the first occurrence in a line that needs to be changed which seems to be taken care of by **^**?

---

### Post by Bachstelze on 2013-10-26
> **vasa1 said:**
> Why do you say it's non-standard? And why have **g** when it's just the first occurrence in a line that needs to be changed which seems to be taken care of by **^**?

I say it is non-standard because it does not work on non-GNU versions of sed. I use /g because I am not very good at sed. :)

---

### Post by vasa1 on 2013-10-27
> **Bachstelze said:**
> I say it is non-standard because it does not work on non-GNU versions of sed. ...
Thanks, I didn't know that :)

---

### Post by sha1sum on 2013-10-27
Well look at that. I ask a dumb question an now we've all learned something new. You're welcome. Hehe. :biggrin:

In the main time, I found this website that is very useful for sed: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

