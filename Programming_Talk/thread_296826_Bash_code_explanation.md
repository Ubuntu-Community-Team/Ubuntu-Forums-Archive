---
title: "Bash code explanation"
date: 2006-11-10
forum: Programming Talk
---

### Post by Ramses de Norre on 2006-11-10
```
 :(){ :|:& };:
```
I have a little question, the above code should be a bash script that executes a fork bomb, so it creates as many processes as possible with the intention to make a computer unusable.

But I don't really understand the code, so could anyone explain this line of code? Why does it make this processes? I just don't understand the syntax I'm afraid (although I do know bash to a certain extent).

---

### Post by shining on 2006-11-10
This example of fork bomb can be found on wikipedia:
[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)
There is a link to an explanation:
[http://www.euglug.org/pipermail/euglug/2005-August/004338.html](http://www.euglug.org/pipermail/euglug/2005-August/004338.html)

---

### Post by po0f on 2006-11-10
Ramses de Norre,

From what I can tell, it declares a function ":(){ :|:& };" and executes it immediately.  Inside the function, it calls itself.  ":" is bash short-hand for 0 or true, so that gets piped to itself again, calling it again, etc, etc.

Or you could just read the link posted above, better explanation.

---

### Post by Ramses de Norre on 2006-11-10
Ow I'm sorry, that's exactly the page were I found the example but I didn't see the explanation link.. Thanks for pointing me to it ;)

---

