---
title: "why is this bash conditional statement wrong?"
date: 2009-07-30
forum: Programming Talk
---

### Post by akimatsu123 on 2009-07-30
```
if [[ ("$bool_cracked" != "y") || ("$bool_cracked" != "Y") ]]
then 
echo "Will restart aircrack-ng. Press any key to continue (Ctrl+C to quit)..."
else 
fi
```

the above is a script from my wifi cracking script. yes, i know, only perform it on your own wifi blablabla. i'm just doing this for learning purposes, and since it seemed fun to write a aircrack0ng script, that's what im doing. 

the above statement throws out the error "syntax error near unexpected token `fi'" what's wrong with my script? thanks

---

### Post by wojox on 2009-07-30
There is nothing between the else and fi. Your telling it If this then do this Else (then there is nothing there to do).

---

### Post by Majorix on 2009-07-30
Just remove the "else". You won't need it unless you want to do something if the condition is not met.

---

### Post by hyperAura on 2009-07-30
so in bash scripting language fi is like saying the if conditional statement is finished??

---

### Post by wojox on 2009-07-30
Yes kind of weird huh?

---

### Post by hyperAura on 2009-07-31
well yeah it looks quite weird to me as ive never seen a programming language using something to denote the end of a conditional statement..:)

---

