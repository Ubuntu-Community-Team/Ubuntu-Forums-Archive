---
title: "Ubuntu 9.04 G++ bug!"
date: 2009-12-16
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-16
Hello.

The function sleep doesn't work right, how to fix it?

for example:

```
#include <iostream>
#include <unistd.h> 

int main()
{
cout << "Hello world!";
sleep(10);
return 0;
}
```I don't know how does this happen, but before typing "Hello World", the program just hangs up for 10 seconds! The same bug in every program where I use operator sleep(ms). **sleep**(ms) is **NOT! in the beginning, **but it acts like it is in the beginning and *1000 (ms => s).

Can someone explain, why is this happening, and how can I fix it?
Thanks.

---

### Post by ajgreeny on 2009-12-16
What function do you mean, suspend?  Or are you speaking of the ```
sleep ##; some-command
```which delays the running of the command by ## time?

---

### Post by OVERPOWER8 on 2009-12-16
> **ajgreeny said:**
> What function do you mean, suspend?  Or are you speaking of the ```
sleep ##; some-command
```which delays the running of the command by ## time?

Yes, exactly.

I just need an extreme correct time delay, just like sleep(ms), but for some reason because of the sleep function, the program hangs.

---

### Post by ajgreeny on 2009-12-16
What exactly are you trying to do, and what command, including the sleep part, are you using?

---

### Post by MadCow108 on 2009-12-16
its no bug its a feature

of course it "hangs" (its sleeping actually, so no cpu use)
you haven't flushed the output buffer

put a << endl behind the hello world which adds a endline character and flushes the stream
or just call cout.flush()

---

### Post by Logan513 on 2009-12-16
> **OVERPOWER8 said:**
> Hello.

The function sleep doesn't work right, how to fix it?

for example:

```
#include <iostream>
#include <unistd.h> 

int main()
{
cout << "Hello world!";
sleep(10);
return 0;
}
```I don't know how does this happen, but before typing "Hello World", the program just hangs up for 10 seconds! The same bug in every program where I use operator sleep(ms). **sleep**(ms) is **NOT! in the beginning, **but it acts like it is in the beginning and *1000 (ms => s).

Can someone explain, why is this happening, and how can I fix it?
Thanks.

I think you need to read up on sleep. If I'm correct it's not sleep(ms); as it is sleep(s); So It IS doing it correctly...

---

### Post by Physical Hook on 2009-12-16
sleep(seconds) - of course it'll *hang* for a while. 
The easiest way to check whether it really hangs or simply does the job, add another cout right before the return statement.

---

### Post by OVERPOWER8 on 2009-12-17
> **MadCow108 said:**
> its no bug its a feature

of course it "hangs" (its sleeping actually, so no cpu use)
you haven't flushed the output buffer

put a << endl behind the hello world which adds a endline character and flushes the stream
or just call cout.flush()

Thanks for explanation, now it works.

---

### Post by Zugzwang on 2009-12-17
> **OVERPOWER8 said:**
> 
Anyway it hangs at the beginning. Is there a way to make it not to hang?

That's a little bit hard to believe. Can you post a *complete* program for us to verify that on our computers that actually compiles?

---

### Post by OVERPOWER8 on 2009-12-17
> **Zugzwang said:**
> That's a little bit hard to believe. Can you post a *complete* program for us to verify that on our computers that actually compiles?

I made a mistake, it works.

---

