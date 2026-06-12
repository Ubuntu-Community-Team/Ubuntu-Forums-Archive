---
title: "I need something cool to do in BASH"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-10-23
This sounds a bit off but I need to come up with something really cool to do in bash, either just as a command or a bash script. Something that would grab non linux users attention, any ideas?

---

### Post by Keen101 on 2008-10-23
> telnet towel.blinkenlights.nl
 

try this. If it works, then you will laugh.

---

### Post by abeisgreat on 2008-10-23
thanks but I'm looking for something local in linux only, so no telnet :P

---

### Post by jrothwell97 on 2008-10-23
Try the fortune program. Run fortune at the prompt and it'll pull a random quote, joke or witticism from a database (think a fortune cookie). It's particularly nice if you can put it in .bashrc. Like so:

```
echo ""
uname -a
echo ""
echo "Welcome back."
echo ""
fortune
echo ""
```

produces this:

```

Linux Hammond 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686 GNU/Linux

Welcome back.

You have the power to influence all with whom you come in contact.

jrothwell@Hammond:~$ 

```

---

### Post by abeisgreat on 2008-10-23
> **jrothwell97 said:**
> Try the fortune program. Run fortune at the prompt and it'll pull a random quote, joke or witticism from a database (think a fortune cookie). It's particularly nice if you can put it in .bashrc. Like so:

```
echo ""
uname -a
echo ""
echo "Welcome back."
echo ""
fortune
echo ""
```

produces this:

```

Linux Hammond 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686 GNU/Linux

Welcome back.

You have the power to influence all with whom you come in contact.

jrothwell@Hammond:~$ 

```

Thats awesome
I need more idea still though

---

### Post by sisco311 on 2008-10-23
```
text=`fortune`&&cowsay $text;espeak "$text"
```

---

### Post by Kinst on 2008-10-23
> cd /bin
cat *

That'll make a bunch of garbled text scroll by.

---

### Post by abeisgreat on 2008-10-23
> **sisco311 said:**
> ```
text=`fortune`&&cowsay $text;espeak "$text"
```

thats pretty awesome too

thanks for all the ideas, keep em coming!

---

### Post by sisco311 on 2008-10-23
apt-get and aptitude easter eggs:
```
apt-get moo

aptitude moo
aptitude -v moo
aptitude -vv moo
...
aptitude -vvvvvv moo
```

---

### Post by abeisgreat on 2008-10-23
> **sisco311 said:**
> apt-get and aptitude easter eggs:
```
apt-get moo

aptitude moo
aptitude -v moo
aptitude -vv moo
...
aptitude -vvvvvv moo
```

Ahahahahah thats awesome the apt-get one is best it just goes to show that linux guy (and girl) programmers have a sense of humor.

Ok I Still want more, anything else funny or cool.

---

### Post by HittingSmoke on 2008-10-23
> **jrothwell97 said:**
> Try the fortune program. Run fortune at the prompt and it'll pull a random quote, joke or witticism from a database (think a fortune cookie). It's particularly nice if you can put it in .bashrc. Like so:

```
echo ""
uname -a
echo ""
echo "Welcome back."
echo ""
fortune
echo ""
```

produces this:

```

Linux Hammond 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686 GNU/Linux

Welcome back.

You have the power to influence all with whom you come in contact.

jrothwell@Hammond:~$ 

```

Off topic comment. lol this reminds me of the booth in Demolition Man that the depressed guy is talking to and it tell him hes a "Wonderful person who produces joy joy feelings in others" or something like that.

---

### Post by Joeb454 on 2008-10-23
I quite like experimenting with fortune and cowsay (you can install both from the repo's).

There's some particularly interesting "cows" if you find them...including ren and stimpy I believe

---

### Post by abeisgreat on 2008-10-23
> **HittingSmoke said:**
> Off topic comment. lol this reminds me of the booth in Demolition Man that the depressed guy is talking to and it tell him hes a "Wonderful person who produces joy joy feelings in others" or something like that.

Good for you lol

gimme more code haha

---

