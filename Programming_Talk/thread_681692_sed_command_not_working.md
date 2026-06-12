---
title: "sed command not working?"
date: 2008-01-29
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-01-29
This has been really bugging me :-/

```
echo "HOME123" | sed "s/HOME123/$HOME/g" > gconf4.xml
```

I get this output:

```
sed: -e expression #1, char 12: unknown option to `s'
```

What am I doing wrong?

Thanks!

---

### Post by Trumpen on 2008-01-29
Your shell replaces $HOME with /home/username which contains one or more "/" characters. This means that when you try to execute your command sed is actually run as

```
sed "s/HOME123//home/username/g" 
```

which is obviously an error.

Try changing the command with:

```
echo "HOME123" | sed "s;HOME123;$HOME;g" > gconf4.xml
```

In fact, sed allows you use any character you like as a delimiter in a substitute command (s///).

---

### Post by oodlesOfmoodles on 2008-01-29
Oh cool. Thanks its working!

Thanks for taking your time to help me!

---

