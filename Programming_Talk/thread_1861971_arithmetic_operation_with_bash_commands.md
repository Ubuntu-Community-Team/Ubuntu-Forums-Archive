---
title: "arithmetic operation with bash commands"
date: 2011-10-16
forum: Programming Talk
---

### Post by ubu87 on 2011-10-16
Hello,

I'm trying to do a multiplication between two variables using bash commands, but I still get errors, please can someone tell me where I'm wrong?

```



U_SAMPLES_NUMBER=30
V_SAMPLES_NUMBER=30

numberPatternSamples=$("expr(""("$U_SAMPLES_NUMBER+1")"\*"("$V_SAMPLES_NUMBER+1")"")")

echo "$numberPatternSamples"


```

---

### Post by MadCow108 on 2011-10-16
I'd just do it like this:
```
echo $[$[$U_SAMPLES_NUMBER + 1] * $[$V_SAMPLES_NUMBER + 1]]
```

or use bc to get some reasonably readable code:
```
echo "($U_SAMPLES_NUMBER + 1) * ($V_SAMPLES_NUMBER + 1)" | bc
```

---

### Post by ezramorris on 2011-10-16
> **ubu87 said:**
> I'm trying to do a multiplication between two variables using bash commands, but I still get errors, please can someone tell me where I'm wrong?

Hi,

There are a few things wrong here, and there's a few things you have to understand in order to get this to work. :-)

[LIST]
[*]expr is a program. It's not part of bash. This means that when you run it, you separate its arguments with spaces, like any other program.
[*]If you have a look at the expr manual page ([FONT="Courier New"]man expr[/FONT]), you'll see that everything has to be passed as a different argument. This means that if you wanted to do 1+3, you would have to do [FONT="Courier New"]expr 1 + 3[/FONT], that is 1 is the first argument, + the second and 3 the third.
[*]Placing quotes round something means that it is literally passed to the command. Quoting can take the following forms:
[LIST]
[*]A \ makes the next character be passed literally.
[*]"..." will make the enclosed string be passed literally, except variables will be expanded first.
[*]'...' will make the enclosed string be passed completely literally.
[/LIST]
[*]You probably already know that $(...) captures the output of a command to store in a variable.
[/LIST]

So from that, you should be able to see why the following works:
```
numberPatternSamples="$(expr \( "$U_SAMPLES_NUMBER" + 1 \) \* \( "$V_SAMPLES_NUMBER" + 1 \))"
```

One final thing. Bash also has its own internal arithmetic functionality using the $((...)) operators, so you don't really need to call an external program:

```
numberPatternSamples="$(( (U_SAMPLES_NUMBER+1)*(V_SAMPLES_NUMBER+1) ))"
```

It also looks a bit nicer too. :-)

Hope this helps,
Ezra.

---

### Post by ubu87 on 2011-10-16
Thanks a lot ezra, now I've understood the difference, and they work both :p

Thanks also to mad cow, just the first instruction that you wrote doesn't work, The second is ok!

---

