---
title: "BASH:  Nesting &quot;if&quot;s?"
date: 2006-08-25
forum: Programming Talk
---

### Post by LadyDoor on 2006-08-25
Is there a special syntax required to nest "if" statements in BASH? Basically, I want to set it up in this script I'm working on so that, if one thing has a certain value, then it should go one and do one of two things depending on whether something else has a given value, and if not to just do nothing...something like this (with dummy variables and numbers)

```

if (($statmente1 == 1))
  then

  if (($statement2 == 17))
    then
    command -options file
  elif (($statement2 == 3))
    then
    othercommand
  else
    yetanothercommand

else
echo $statement1 > /dev/null

```

Basically, I want to do this because it'll save me a lot of "&&" statements. Any suggestions?

--Door

---

### Post by chonger on 2006-08-25
Sure. You can nest flow control statements in bash.

[http://www.linuxvalley.it/encyclopedia/ldp/guide/abs/loops.html](http://www.linuxvalley.it/encyclopedia/ldp/guide/abs/loops.html)

---

### Post by LadyDoor on 2006-08-25
Shiny. It turns out I just had a mistake in what I was writing, which was what was preventing it from working (I left out a **fi**).

--Door

---

### Post by goatflyer on 2006-08-25
> **LadyDoor said:**
> Shiny. It turns out I just had a mistake in what I was writing, which was what was preventing it from working (I left out a **fi**).

--Door

Err... you left out TWO 'fi's  :P

---

### Post by LadyDoor on 2006-08-25
Oh...lol. I just forgot to copy/paste the second one (the one I *didn't* miss) in. Thanks, though!

---

