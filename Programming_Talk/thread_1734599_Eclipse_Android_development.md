---
title: "Eclipse Android development"
date: 2011-04-20
forum: Programming Talk
---

### Post by bprins on 2011-04-20
Hi,

I've been trying to get started with android development, but not much success yet.

What I have accomplished:
- installed eclipse galileo (3.5.2)
- installed java1.6 (jre+jdk)
- installed android sdk (2.1, 2.2, 3.0)
- installed eclipse android plugin (ADT)
- created virtual devices (AVD): 2.1, 2.2, 3.0

When I then follow the hello android tutorial, and adjust the source so that the activity creates a textview with 'hello android' and run the application I get the following results:
- a virtual android device pops up on initialization screen ("android" is all it says)
- in the console output the following output is shown:
```

[2011-04-20 19:46:44 - HelloDroid] ------------------------------
[2011-04-20 19:46:44 - HelloDroid] Android Launch!
[2011-04-20 19:46:44 - HelloDroid] adb is running normally.
[2011-04-20 19:46:44 - HelloDroid] Performing com.apps.HelloWorld activity launch
[2011-04-20 19:46:44 - HelloDroid] Automatic Target Mode: launching new emulator with compatible AVD 'Android2.2'
[2011-04-20 19:46:44 - HelloDroid] Launching a new emulator with Virtual Device 'Android2.2'
[2011-04-20 19:46:44 - Emulator] emulator: emulator window was out of view and was recentred
[2011-04-20 19:46:44 - Emulator] 
[2011-04-20 19:46:44 - HelloDroid] New emulator found: emulator-5554
[2011-04-20 19:46:44 - HelloDroid] Waiting for HOME ('android.process.acore') to be launched...

```
 
The "hello android" text is not shown. I tried this hello world tutorial on:
windows, ubuntu (netbeans), ubuntu (eclipse), and end up with the exact same result: the initialization screen of a virtual android device.

What am I (consistently) doing wrong?

Thanks a lot in advance.

Bas

---

### Post by LoneWolfJack on 2011-04-20
give it a few minutes... the first startup of the android emulator can take quite some time if you don't have a high-end CPU.

---

### Post by kostkon on 2011-04-20
> **LoneWolfJack said:**
> give it a few minutes... the first startup of the android emulator can take quite some time if you don't have a high-end CPU.
Indeed. It's veery slow.

---

### Post by bprins on 2011-04-21
Bloody hell!

You're right. Thanks guys. 

Now lets conquer the world with apps :-)

Cheers,

Bas

---

### Post by yuki000 on 2011-04-23
> **LoneWolfJack said:**
> give it a few minutes... the first startup of the android emulator can take quite some time if you don't have a high-end CPU.

Yes!!! 
Just wait several minutes and Hello World android show up
thank you.

---

