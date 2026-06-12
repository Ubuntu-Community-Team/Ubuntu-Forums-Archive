---
title: "bash: if santax help: [ X ] &amp;&amp; [ Y ] || [ Z ]"
date: 2013-04-28
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-04-28
How do i write this in sh/bash

Javascript/php:
```
if ( 1 == 1 && ( 1==2 || 2==2 ) ) {

}
```
This is the closest i can get without breaking it:
```

if [ 1 -eq 1 ] && [ 1 -eq 2 ] || [ 2 -eq 2 ];then

fi

```

---

### Post by varunendra on 2013-04-29
Edit: Forget it, it's all wrong. The following posts explain why.. trying variations, may post corrected one later..
[s]
```
if [[ 1 -eq 1 && 1 -eq 2 || 2 -eq 2 ]];then

fi
```
works for me.

For example : 
```
a=2; b=3; c=4; if [[ $a -eq 2 && $b -eq 2 || $c -eq 4 ]]; then echo yes; fi
```
..change the declared values or test values and see the difference. It works as -
**IF ([COLOR="#FF0000"]condition 1[/COLOR]) AND ([COLOR="#000080"]condition2[/COLOR] OR [COLOR="#8B4513"]condition3[/COLOR]), THEN** go ahead..
[/s]

---

### Post by schragge on 2013-04-29
There's a subtle difference between &&/|| and -a/-o in that the former short-curcuit, but the latter don't. See [compound comparison]("http://tldp.org/LDP/abs/html/comparison-ops.html#CCOMPARISON1") in ABS.

In this particular case, I'd use arithmetic evaluation
```
[s]((1==1 && 1==2 || 2==2))[/s]
```

Also, using of parentheses to explicitly group subexpressions is allowed inside double-brackets and arithmetic expressions.

[highlight]Edit[/highlight] || has lower precedence than &&, so parentheses are needed. See **spjackson**'s explanation below.

---

### Post by spjackson on 2013-04-29
The truth table for the original Javascript/php is:
```

TTT==>T
TTF==>T
TFT==>T
TFF==>F
FTT==>F
FTF==>F
FFT==>F
FFF==>F

```
However both of these suggestions:
```

if [[ 1 -eq 1 && 1 -eq 2 || 2 -eq 2 ]];then

((1==1 && 1==2 || 2==2))

```
have the truth table
```

TTT==>T
TTF==>T
TFT==>T
TFF==>F
FTT==>T
FTF==>F
FFT==>T
FFF==>F

```
i.e. different in 2 cases.

Just as in the original, you need a bracket;
```

if [[ 1 -eq 1 && ( 1 -eq 2 || 2 -eq 2 ) ]];then

((1==1 && (1==2 || 2==2)))

```

---

### Post by varunendra on 2013-04-29
> **spjackson said:**
> 
Just as in the original, you need a bracket;
```

if [[ 1 -eq 1 && ( 1 -eq 2 || 2 -eq 2 ) ]];then

```

Verified this one ^^ with my example, changing all three variables and seems perfect!

---

### Post by pqwoerituytrueiwoq on 2013-04-29
Thanks everyone :)
[this is where i needed it](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/commit/ee7805ca205e13e7eb890e4b8d2350c5ff4aade9#KernelUpdateScriptGenerator)

---

### Post by schragge on 2013-04-29
Two things about your script.

1. It downloads kernel-related packages to current directory and then counts files to check if they were successfully downloaded. What if there already were previously downloaded older kernel packages in the folder?

2. This
```

if [ "`uname -m`" == "x86_64" ];then
arch="amd64"
else
arch="i386"
fi

```
probably could be replaced with
```
arch=`dpkg --print-architecture`
```
and this[FONT=monospace]
```
[/FONT][ $(ls /boot | grep $VER_A | wc -l) -gt 3 ]
```
with
```
[[ -d /lib/modules/$VER_A ]]
```

---

### Post by pqwoerituytrueiwoq on 2013-04-29
If there are files present it will ask you if you want to delete them, if you say no wget will not replace them and will get the other files
edit:
opps now what you meant, thanks :)
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/commit/7689c91afe6533370a69f62aa26e064d77543f09#KernelUpdateScriptGenerator](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/commit/7689c91afe6533370a69f62aa26e064d77543f09#KernelUpdateScriptGenerator)

---

