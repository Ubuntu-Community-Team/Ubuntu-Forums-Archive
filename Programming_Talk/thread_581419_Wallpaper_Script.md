---
title: "Wallpaper Script"
date: 2007-10-19
forum: Programming Talk
---

### Post by Doctor J on 2007-10-19
By way of introduction, i've put together batch files back in the old days, but am still pretty green when it comes to shell scripting.  The system in question is Dapper AMD64.

Here's a script i picked up from the Wiki recently.  The object is to pick a random image from a specified directory and use that image for the Desktop Background.  The script is attached.

As of now, i still can't get the script to complete:

```
dave@ubuntu:/bin$ ./wallpaper
./wallpaper: line 16: ((: echo $NIMGS | wc -w: syntax error in expression (error token is "$NIMGS | wc -w")
cut: invalid option -- w
Try `cut --help' for more information.
dave@ubuntu:/bin$

```

What needs to change?

---

### Post by tkharris on 2007-10-19
```
N='echo $NIMGS | wc -w'
```

Did you mean:

```
N=`echo $NIMGS | wc -w`
```

Perhaps?

---

### Post by Doctor J on 2007-10-20
Now it appears we're in the realm of punctuation i don't commonly use.  Is that the character above the <TAB> key on a QUERTY keyboard?  If so, can i get a quick introduction to what the difference is when it comes to parsing??

---

### Post by cwaldbieser on 2007-10-21
> **Doctor J said:**
> Now it appears we're in the realm of punctuation i don't commonly use.  Is that the character above the <TAB> key on a QUERTY keyboard?  If so, can i get a quick introduction to what the difference is when it comes to parsing??

That character is called a backtick or a backquote.  The following examples are equivalent:
```

$ VAR=`echo hello`
$ VAR=$(echo hello)

```

In both cases, the shell exceutes the pipeline between the special syntax and the standard output is collected and assigned to the variable, VAR.
I find the $(...) syntax easier to read, but backticks are still frequently used.

---

### Post by jkerr on 2007-10-27
I was looking for something like this, and since it was short and sweet, looked into how to fix it...

As tkharris stated, change your N= line to use backticks, this will evaluate what's in backticks and set it to your variable.  After that, the only change it to change your top line to

```
#!/bin/bash
```

As it appears that RANDOM is a bash function, then you're done.

---

