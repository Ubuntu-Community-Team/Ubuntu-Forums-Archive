---
title: "Shell Script running a Shell Script"
date: 2008-08-07
forum: Programming Talk
---

### Post by kooseefoo on 2008-08-07
Okay, I have a little bit of a unique problem.

I have a shell script that asks the user a series of questions, and then executes a command based upon the responses. Example:

```
What is your name?
What is your quest?
What is the airspeed velocity of an unladen swallow?
```

Instead of having the user interact with this script and answer the questions, I want another shell script to answer them. Yes, I do realize how sloppy and horrible that is. Unfortunately, the shell script that prompts the user is far too complex for me to have time to disassemble it.

The solution another person sent me is a script that looks something like this:

```

echo "Arthur" > input.txt
echo "We seek the holy grail" >> input.txt
echo "African or European swallow?" >> input.txt
./montypython.sh < input.txt
```
Where ./montypython.sh is the script prompting for responses. This solution doesn't seem to work.

Does anybody have a slick way to do this?

Thanks,
Chris Champion


NOTE: I'm using csh, not bash. That's not by choice. :)

---

### Post by bodhi.zazen on 2008-08-07
csh and bash are similar, but a little different.

goggle is your best friend here :

looks like set input is what you want :

[http://www.kingston.ac.uk/support/unix/Scripts.html](http://www.kingston.ac.uk/support/unix/Scripts.html)

[http://www.bo.infn.it/alice/alice-doc/mll-doc/impgde/node36.html](http://www.bo.infn.it/alice/alice-doc/mll-doc/impgde/node36.html)

---

### Post by mssever on 2008-08-07
I've heard of a package called expect that exists for several languages and does what you want. I don't think that you can write an expect script in bash (or csh), though--try Python for that.

---

### Post by dtmilano on 2008-08-08
No, you can't write an expect script in bash, only in expect ;-)
There's a tool called autoexpect that will help you writing the script.

Also try python-pexpect (in repos).

---

### Post by EnGorDiaz on 2008-08-08
im sorry im so immature but lol

"African or European swallow?"

---

### Post by sharma2008 on 2008-08-08
i am also same category..

---

### Post by kooseefoo on 2008-08-08
Thanks a lot!

I couldn't help myself with the Monty Python reference...

I have another question about scripting, if anyone would care to give me a hand. This is just a one-liner (sorry, I can't post the actual script)

```

VARIABLE = rsh server "command" | awk 'PROGRAM'

```

Note that "command" does include a `pwd` in it so that my directory gets passed on.

Whenever my script hits this line, it returns the following error:
VARIABLE: command not found

I don't want to redirect the output of this statement to a file and then read it back into my variable. Are there some ninja moves with `, ', and " that I must learn?

Thanks,
Chris Champion

---

### Post by kooseefoo on 2008-08-08
Problem solved after a while of tinkering with things.

In case anyone is interested:


I needed to add strike characters (`) around the whole thing, and then escape (\) the embedded ` within the rsh command.

Also, I had spaces around the equals sign for the variable name.

---

