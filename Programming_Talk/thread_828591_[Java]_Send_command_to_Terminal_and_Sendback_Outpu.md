---
title: "[Java] Send command to Terminal and Sendback Output"
date: 2008-06-13
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-13
Hello,

I know that i have done this before but i completely forget how to do this. Basically i want to send a command, *md5sum*, and return the output from the command.

[quote=Example]
cody@Charmander:~/Documents$ md5sum To-Do.txt
42efd5aa5e9e307b13a0d277d5d7d7b3  To-Do.txt
[/quote]

What i need returned is *42efd5aa5e9e307b13a0d277d5d7d7b3* but that can be derived from *42efd5aa5e9e307b13a0d277d5d7d7b3 To-Do.txt*. I know that i am going to have to use a _Stream_ or something close to that.

This will end up being its own method, it will look like this:
```

public static String md5sum(String path){
//Gets the md5sum of the file "path"
}

```

Thank you very much for any help
~Cody Woolaver

---

### Post by Elegorod on 2008-06-14
Since Java 1.5 there is java.lang.ProcessBuilder and Process. Using them, it's really easy to start a process and get its input, output and error streams

---

### Post by Shin_Gouki2501 on 2008-06-14
did u try google for java md5 examples on files? my guess is that works pretty nice and you wouldn't have to use CLI comannds..

---

### Post by Pyro.699 on 2008-06-14
I have a md5 code, but the one that i have takes way too long to process... the one that is built into linux is much quicker. Thankyou

---

### Post by Shin_Gouki2501 on 2008-06-14
ok i don't want to argue about performance here ;)
np

---

