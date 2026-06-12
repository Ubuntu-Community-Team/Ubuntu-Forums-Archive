---
title: "Exclamation mark, shell script"
date: 2013-10-20
forum: Programming Talk
---

### Post by sha1sum on 2013-10-20
hello guys

When I type in the terminal: 

```
owner@linuxbox:~$ echo "oh yeah!"
```

I get the following output:

```
owner@linuxbox:~$ echo "oh yeah!"
echo "oh yeah"
oh yeah
```

Apparently the exclamation mark means something for the shell, but I don't know what. Can somebody explain to me what's happening here?

---

### Post by The Cog on 2013-10-20
Run the command "man bash" and search for the heading HISTORY EXPANSION. the ! character starts a history expansion expression.
You can prevent interpretation with single-quotes:
echo 'Oh yeah!'
Or, for nostalgia:
echo 'You got the BFG9000, oh yes!'

---

### Post by steeldriver on 2013-10-20
In bash, ! indicates the start of a history substitution - for example

```
!*n* # substitute the *n*th command from the shell's history list
```

```
!-*n* # substitute the command from *n* places earlier in the history list
```

or when ! is followed by *string*, substitute the most recent command that started with *string* 

Because anything in double quotes is still subject to expansion by the shell

 ```
echo "oh year!"
```

tries to substitute the last command that started with a double quote - so if that happens to be an empty command "" then this is what you see

```

$ ""
: command not found
$ echo "oh yeah!"
echo "oh yeah"
oh yeah

```

If you want the shell to treat ! as literal, you can use single quotes instead

```

$ echo 'oh yeah!'
oh yeah!

```

---

### Post by sha1sum on 2013-10-20
I understand. Thanks guys!

---

### Post by drmrgd on 2013-10-20
Another way that I've done it - like in the case when I wanted to echo a variable in the same sentence and didn't want to deal with concatenating - is to use the '-e' option of echo and the hex code for an exclamation mark:

```

$ echo -e "Hello World\x21"
Hello World!

```

Most times single quotes is the way to go, though.

---

### Post by ofnuts on 2013-10-21
You can also escape it outside quotes:
```

echo yes\!

```

---

