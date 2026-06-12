---
title: "Unable to find simple answer"
date: 2010-01-29
forum: Programming Talk
---

### Post by lunarcloud on 2010-01-29
I want to simply read the text from a one string text file, and set that string to a variable in my bash script.

/home/sam/variant = "kubuntu"
OS = text inside of /home/sam/variant

I've scowered the web and only found complicated things that aren't what I'm doing or simply don't work.

It can't be this hard to do.

---

### Post by lunarcloud on 2010-01-29
NEVERMIND!

I discovered that using $() around a command gives you the output of that command.

Sorry. 

OS=$(cat /home/sam/variant)

worked beautifully.

Well, I'll leave this up in case others have this problem. I feel silly.

---

### Post by lisati on 2010-01-29
Thank you for sharing this. I'm sure it will help someone.

---

