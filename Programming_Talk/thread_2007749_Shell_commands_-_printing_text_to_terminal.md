---
title: "Shell commands - printing text to terminal"
date: 2012-06-21
forum: Programming Talk
---

### Post by castiglione on 2012-06-21
I was just wondering if it were possible to print text to a specific screen location using shell commands?
 
I.e. Print "Test" at line 2, horizontal space 5, and things of that nature, overwriting pre-existing text if necessary?
 
Thanks in advance!
 
c

---

### Post by codemaniac on 2012-06-21
> **castiglione said:**
> I was just wondering if it were possible to print text to a specific screen location using shell commands?
 
I.e. Print "Test" at line 2, horizontal space 5, and things of that nature, overwriting pre-existing text if necessary?
 
Thanks in advance!
 
c

If you want to format your output in a terminal , there are many tools available like awk , perl or Bash-builtin commands like echo , printf .

The below command would print two newlines and 4 spaces prefixed with "Text" .
```
printf "\n\n%-4sText"
```


However not clear what exactly you are trying to achieve .
It would be helpful if you post your requirement clearly .

---

### Post by Habitual on 2012-06-21
> **castiglione said:**
> I was just wondering if it were possible to print text to a specific screen location using shell commands?...

It is!
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x405.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x405.html)

tput is the command you are looking for. :)

Edit: Here's what it looks like (yellow is just highlighting, NOT in the code I posted![IMG]http://i771.photobucket.com/albums/xx360/E522260/Screenshot.png[/IMG]

Here's the code that generated the output:
[http://susepaste.org/36118090](http://susepaste.org/36118090)

HTH further. :)

---

