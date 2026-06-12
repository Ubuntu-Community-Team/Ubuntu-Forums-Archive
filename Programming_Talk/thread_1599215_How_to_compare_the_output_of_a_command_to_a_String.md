---
title: "How to compare the output of a command to a String"
date: 2010-10-17
forum: Programming Talk
---

### Post by hallucynogenyc on 2010-10-17
Hello there, newbie here ;)

What I need to do is to know if the 4th argument of the script starts with (+ or -) or not. I have archived the goal by using a "temp" variable which gets assigned the output of the command at the beginning of the script, but obviously that's not the way to go. Here are the lines of the code involved on it:

temp=$(echo "$4" | cut -c1)

elif [ "$temp"} != "+" ] && [ "$temp" != "-" ]

I wanted do insert the "echo "$4" | cut -c1" inside the second line, however doing so has failed in all the ways I've tried it.

Anyone?

Thanks in advance

---

### Post by geirha on 2010-10-17
In bash, use the more powerful [[ keyword instead of the [ command.
```

if [[ $4 = [-+]* ]]; then
  echo "Fourth argument starts with a + or a -."
else
  echo "Fourth argument does not start with a + or a -."
fi

```

If you're scripting for sh, you can achieve the same with a case
```

case $4 in
  [-+]*) echo "Fourth argument starts with a + or a -.";;
  *) echo "Fourth argument does not start with a + or a -.";;
esac

```

[BashFAQ 31 -- What is the difference between test, [ and [[ ?](http://mywiki.wooledge.org/BashFAQ/031)

---

### Post by hallucynogenyc on 2010-10-17
Thanks for your reply. Using metacharacters to identify the first character sounds much better than the solution I was trying to approach, and I'll for sure do it this way.

However, I still got the same question. I know I don't need it now, but I still would like to know why wasn't my code working:

> elif [ { echo "$4" | cut -c1; } != "+" ] && [ { echo "$4" | cut -c1; } != "-" ]

I used the {} because I saw it somewhere, without knowing what where they exactly used for.

Now, don't get me wrong, I'm an old Ubuntu user and have been programming for some years in other languages, I just decided to learn scripting and it's all too strange for a first-day learner :)

---

### Post by geirha on 2010-10-17
It's important to know that [ is NOT part of the if syntax, it's a regular command, like grep and cut etc. Furthermore, [ does not execute any commands, it simply tests some files or strings and returns true or false.

Anyway, this (pretending foo and bar are commands):
```
temp=$(foo)
bar "$temp"

```
is the same as:
```
bar "$(foo)"
```

Which means you can do:
```

if [[ $(echo "$4"|cut -c1) = "-" ]]; then 
  echo yes
else
  echo no
fi

```

---

### Post by hallucynogenyc on 2010-10-17
I see. So the $() doesn't need to assign the result to a variable (as I had read somewhere), as it can be used as the result itself. Great!

Thank you very much, you're helping me a lot :)

---

