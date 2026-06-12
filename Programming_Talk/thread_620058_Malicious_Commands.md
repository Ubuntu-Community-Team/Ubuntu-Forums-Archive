---
title: "Malicious Commands ?"
date: 2007-11-22
forum: Programming Talk
---

### Post by thirddeep on 2007-11-22
I was reading the malicious commands thread at the top.  There was one item that I have never seen before, nor do I understand it.

Obviously I had to try it :-)

Sadly, either it does not work, or I am doing something wrong.

Here is the code :
```
:(){:|:};:
```
Of course I am doing this in a virtual image not to damage my system ....

So :

a) How is it suppose to work ?
b) Why does it not work ?

The image that I test in is RHEL 4.5, kernel 2.6.9-55-ELsmp, bash version 3.00.15(1)-release.

Thd.

---

### Post by smartbei on 2007-11-22
It is called a fork bomb. What it does is recursively spawn new processes of itself. See [http://www.answers.com/topic/fork-bomb?cat=technology](http://www.answers.com/topic/fork-bomb?cat=technology) for more information. I myself know next to nothing about bash scripting, so I am not sure why it **doesn't** work. :)

The version they have there of the fork bomb posted above is:
```

:(){ :|:& };:

```

Perhaps it does work. I am not on my Ubuntu PC right now, so I can't tell.

---

### Post by thirddeep on 2007-11-22
Fork bombs I understand :-)

The code you posted works ... very good :)

Now I would love for someone to explain it to me ....

Thd.

---

### Post by Siph0n on 2007-11-22
[http://www.euglug.org/pipermail/euglug/2005-August/004338.html](http://www.euglug.org/pipermail/euglug/2005-August/004338.html)

---

### Post by Ramses de Norre on 2007-11-22
> **thirddeep said:**
> 
```
:(){:|:};:
```
Of course I am doing this in a virtual image not to damage my system ....

So :

a) How is it suppose to work ?
b) Why does it not work ?


a) see post above.
b) because there must be spaces between the curly braces and the function calls, "{:|:}" -> "{ :|: }", the additional "&" you will mostly see, makes it extra nasty, it backgrounds all calls to the functions.

BTW: are you sure a VM will protect you? It'd appear to me that every process forked in the VM corresponds with one forked in your host, except when it's handled different (threads in the VM process instead of new processes or something), I'm not really into VM design :) More safe would be to set good limits in /etc/security/limits.conf, that will limit the number of processes that can be forked, I've got this in there:
```
*                               soft    nproc                   1024
*                               hard    nproc                   2048
```
and a fork bomb can't kill my system, it executes but fails after a minute or five.

---

### Post by thirddeep on 2007-11-22
Thanks for the link to an explanation !

Yes VMware protected my host.  VMware (server) did not crash, nor did the underlying OS (Ubuntu 7.4). 

Thd.

---

