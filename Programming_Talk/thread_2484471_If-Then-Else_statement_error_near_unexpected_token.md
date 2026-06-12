---
title: "If-Then-Else statement error near unexpected token 'Then'"
date: 2023-02-27
forum: Programming Talk
---

### Post by lefleur on 2023-02-27
Hi everyone. I'm currently trying to learn programming right now for a class, but I'm kind of stumped. I started the course late and my professor unfortunately did not provide many resources. I am not here to get answers for my homework, but I'm here to figure out how to do things and learn from my mistakes. Please don't get the wrong idea.

This is currently what I have:
If speed >= 24 OR speed <= 56; then
Display "Speed is normal"
else
Display "Speed is abnormal"
end if

And this is the error that pops up:

line 1: syntax error near unexpected token `then' 
line 1: `If speed >= 24 OR speed <= 56; then'


The original question in the textbook was:

Design an If-Then-Else statement (or a flowchart with a dual alternative decision structure) that displays “Speed is normal” if the speed variable is within therange of 24 to 56. If speed holds a value outside this range, display “Speed is abnormal.”

---

### Post by aljames2 on 2023-02-27
Not sure you’ll get a specific answer here since it’s homework related.

All I will say is If-then-else logic is common in some way in all languages.  Check your syntax for the language you are studying.  There are likely thousands of examples in the google-verse.

---

### Post by MAFoElffen on 2023-02-28
First, what language is your interpreter?

Second, there is a flaw in your logic:
> **lefleur said:**
> Hi everyone. I'm currently trying to learn programming right now for a class, but I'm kind of stumped. I started the course late and my professor unfortunately did not provide many resources. I am not here to get answers for my homework, but I'm here to figure out how to do things and learn from my mistakes. Please don't get the wrong idea.

This is currently what I have:
If speed >= 24 [COLOR=#ff0000]OR[/COLOR] speed <= 56; then
Display "Speed is normal"
else
Display "Speed is abnormal"
end if

And this is the error that pops up:

line 1: syntax error near unexpected token `then' 
line 1: `If speed >= 24 OR speed <= 56; then'


The original question in the textbook was:

Design an If-Then-Else statement (or a flowchart with a dual alternative decision structure) that displays &#8220;Speed is normal&#8221; if the speed variable is [COLOR=#ff0000]within therange of 24 to 56[/COLOR]. If speed holds a value outside this range, display &#8220;Speed is abnormal.&#8221;
Your conditions are speed >= 24 AND speed <= 56... That is your range. If it is less than 24 OR greater than 56, then it is out-of-range.

Then, depending on what your interpreter, you just need to express that, right?

<<This post would fit in (and probably should be moved to) the "Programming Talk" section.>>

If this were BASH ( to bring it back relevant to Linux), it would be expressed as
```

#!/bin/bash

speed=$1

if [$speed -ge 24] && [$speed -le 56]
then
    echo "Speed is normal."
else
    echo"Speed is abnormal."
fi

```

The hardest things in programming is logical expression... Expressing things to consistently evaluate as true or false to follow your logic flow.

---

### Post by coffeecat on 2023-02-28
> **MAFoElffen said:**
> 
<<This post would fit in (and probably should be moved to) the "Programming Talk" section.>>


As the OP doesn't specifically state that they are using Ubuntu, I've moved this to *Programming Talk*

> **aljames2 said:**
> Not sure you&#8217;ll get a specific answer here since it&#8217;s homework related.

I don't think the OP was asking for a specific answer. Their first paragraph appears to fit comfortably within our [rules on homework]("https://ubuntuforums.org/showthread.php?t=2158945"):  

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you.

@lefleur, good luck and welcome to the forum.

---

### Post by ActionParsnip on 2023-02-28
What language are you coding in? You gave us some code but didn't state the language being used....? Python? C++? BASH?

---

### Post by MAFoElffen on 2023-02-28
That is what I asked.

"End If" implies a derivative of BASIC, but most "stdout" in languages use print standments to handle stdout, instead of Display statements... "Display" in BASIC would be a print statement to terminal only.

---

### Post by lefleur on 2023-03-01
Hi everyone. I'm sorry for not including the fact I was using Ubuntu in the original post. I was just Googling things and that clearly got me confused with using things like "End If" and so on. Regardless, thank you for your help! This helped me understand a lot better.

---

### Post by MAFoElffen on 2023-03-01
> **lefleur said:**
> Hi everyone. I'm sorry for not including the fact I was using Ubuntu in the original post. I was just Googling things and that clearly got me confused with using things like "End If" and so on. Regardless, thank you for your help! This helped me understand a lot better.
So what "is" your class? Programming Logic?

And where where you expressing your statements, where you got errors? What language?

---

### Post by lefleur on 2023-03-02
> **MAFoElffen said:**
> So what "is" your class? Programming Logic?

And where where you expressing your statements, where you got errors? What language?

I'm using Bash in Ubuntu. I was just using the program through command prompt. I already turned in my work though, and I understand it much better now :)

---

### Post by ronakmehta on 2023-03-09
well The problem with your code is that you have a semicolon following the condition of the if statement, as well as the term "then" following the condition. Most programming languages, including the one you appear to be using, do not require them and result in a syntax error.


You should Remove the semicolon and the phrase "then" from the if statement to correct the problem. Here's the updated code:
[COLOR=#2E95D3][FONT=&quot]
if speed >= 24 OR speed <= 56
    Display "Speed is normal"
else
    Display "Speed is abnormal"
end if

[COLOR=#000000]Also, keep in mind that the terms "if" and "else" are written in lowercase in most programming languages, including the one you appear to be using.
[/COLOR]


[/FONT][/COLOR]

---

