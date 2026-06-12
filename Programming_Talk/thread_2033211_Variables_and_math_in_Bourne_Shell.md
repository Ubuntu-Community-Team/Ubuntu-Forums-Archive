---
title: "Variables and math in Bourne Shell"
date: 2012-07-25
forum: Programming Talk
---

### Post by mr.rhtuner on 2012-07-25
Hey everybody, I've been searching google and these forums and have found some solutions to the issues I've been having today within the Bourne Shell. I am following chapter 6 of the **Guide to Unix using Linux 4th Edition.**

I am working on some basic calculations with variables in the BASH SHELL and doing the same within the Bourne Shell with modifications.

In BASH, I did the following:

**let X=10+2*7**
Type echo **$X** and press Enter. You see 24 on the screen.


Now I realize that the bourne shell does NOT have LET as a command, and I need to use **expr**.

I was able to get the math to work, by doing the following:

$ expr 10 + 2 '*' 7
24 is the answer.


But how do I incorporate the variable of X into this?

I tried:

$ X=%((10 + 2 '*' 7))
but get the error: **synatx error: 'X=% unexpected**


Anybody mind giving me an idea what I am doing wrong?

---

### Post by papibe on 2012-07-25
Hi mr.rhtuner.

Try this:
```
X=$(( 10 + 2 * 7))
```
Regards.

---

### Post by mr.rhtuner on 2012-07-25
> **papibe said:**
> Hi mr.rhtuner.

Try this:
```
X=$(( 10 + 2 * 7))
```
Regards.



Thank you, I have tried that before and just tried again.

X=$ (( 10 + 2 * 7 ))
**Syntax error: 'X=$ unexpected**

I'm digging around on the internet about this too, I don't know why this is so difficult lol:confused:

---

### Post by steeldriver on 2012-07-25
no space between $ and (( ...

---

### Post by mr.rhtuner on 2012-07-25
> **steeldriver said:**
> no space between $ and (( ...

I've tried that just a moment ago, **X=$((10 + 2 * 7))** and it comes back with **syntax error: `X=$` unexpected**

I tried using the ` and ' to see if it will help but no go on that

---

### Post by Hetepeperfan on 2012-07-25
> **steeldriver said:**
> no space between $ and (( ...

also no space after the =.

```

me@desktop:~/$ X=$((10 + 2 * 7 ))
me@desktop:~/$ echo $X
24
```works perfectly for me

---

### Post by Hetepeperfan on 2012-07-25
> **Hetepeperfan said:**
> also no space after the =.

```

me@desktop:~/$ X=$((10 + 2 * 7 ))
me@desktop:~/$ echo $X
24
```works perfectly for me

sorry I did this in the Bourne Again Shell I don't know it in the oldskool bourne shell.

---

### Post by mr.rhtuner on 2012-07-25
> **Hetepeperfan said:**
> also no space after the =.

```

me@desktop:~/$ X=$((10 + 2 * 7 ))
me@desktop:~/$ echo $X
24
```works perfectly for me


Wow, that is odd.  I am doing this on a SCO Server which is running a Linux variation with the /Bin/Sh bourne shell. 

Any ideas why this wouldn't be working for me?


edit: Ahh I see.  I did the same command in my Red Hat Linux server using BASH and it worked as you said.  But I am using the old school bourne shell on a SCO group server.  Trust me, I don't want to be using SCO nor this old bourne shell at all.

---

### Post by Hetepeperfan on 2012-07-25
> **mr.rhtuner said:**
> 
edit: Ahh I see.  I did the same command in my Red Hat Linux server using BASH and it worked as you said.  But I am using the old school bourne shell on a SCO group server.  Trust me, I don't want to be using SCO nor this old bourne shell at all.

you might just type bash at the commanline to see if it is installed

"/bin/sh"

Does not always default to bash.

anyway to do it in the bourne shell:

```
expr 2 \* 7 + 10
```should do the trick, since the $((integer operation)) syntax didn't exist in the orignal bourne shell.

cheers,

Maarten

---

### Post by steeldriver on 2012-07-25
for the variable assignment part of your question does this work?

```
x=`expr 10 + 2 \* 7`; echo $x
```

---

### Post by diesch on 2012-07-25
If you have a "SCO server" you are quite likely not running Linux but SCO OpenServer, UnixWare are one of their predecessors. 

Your* /bin/sh *doesn't seem to be POSIX compliant and may not support this syntax. Try to find some docs for it or look for another shell.

---

### Post by mr.rhtuner on 2012-07-25
> **steeldriver said:**
> for the variable assignment part of your question does this work?

```
x=`expr 10 + 2 \* 7`; echo $x
```


Thank you steeldriver.  After searching another Unix/Linux forum, a member pointed me in the expr direction.

I was able to get it.



Here is what I wrote out:



```
X=`expr 10 \+ 2 \* 7`

echo $X

24
```'



So I got X as the variable holding the answer of 24....Thank you very much!


I wrote it out in a bit longer of a format but they both do the same thing.

---

### Post by mr.rhtuner on 2012-07-25
> **diesch said:**
> If you have a "SCO server" you are quite likely not running Linux but SCO OpenServer, UnixWare are one of their predecessors. 

Your* /bin/sh *doesn't seem to be POSIX compliant and may not support this syntax. Try to find some docs for it or look for another shell.


Sorry that was my mistake assuming it runs Linux. I was going to say Unix but wasn't sure if they would have a server running on such an older OS.  Regardless...I am using the SCO server which I have access to through my school to practice Linux/Unix.

Thanks again to everybody :popcorn:

---

### Post by Bachstelze on 2012-07-25
> **mr.rhtuner said:**
> Sorry that was my mistake assuming it runs Linux. I was going to say Unix but wasn't sure if they would have a server running on such an older OS.  Regardless...I am using the SCO server which I have access to through my school to practice Linux/Unix.


I suggest you stop using it, because its tools are apparently not POSIX-compliant, and you could pick up some bad habits...

---

