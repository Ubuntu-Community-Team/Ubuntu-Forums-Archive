---
title: "[java]Unknown Error"
date: 2008-10-04
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-04
Hello,

Ive come into this error, i tried searching for the answer on Google but i cant seem to find what it means. Also what would the solution be, because i cant seem to find out what it does to the code, how it changes the flow of the program or anything like that. I also don't know what section of code is producing the error, there are over 5000 lines of code and i haven't received this error until i compiled the different parts together.

> 
GC Warning: Repeated allocation of very large block (appr. size 5185536):
    May lead to memory leak and poor performance.


Thanks
~Cody Woolaver

---

### Post by pp. on 2008-10-04
It's a warning, not an error.

It tells you that your program repeatedly asked the OS to allocate it a very large chunk of memory. The size given is roughly five Millions, presumably bytes.

It also says that your program might therefore not run as fast as expected or that it just possibly might gobble more memory than it releases.

Does your program allocate large buffers for arrays, buffer whole files in RAM or something of that sort?

---

### Post by Pyro.699 on 2008-10-04
Yes, the program does create large Arrays and Vectors. Is it possible to clear ALL information with a segment of code? Basically ive created a simple daemon tool  that just runs in the background with while(true){}

Thanks
~Cody Woolaver

---

### Post by tinny on 2008-10-04
Can you post any code?

What JRE are you using? Sun Java?

I hope your not using GCJ...? GNU compiler for Java. Ive had a simlar issue to this when using GCJ.

---

### Post by Pyro.699 on 2008-10-04
I cant really post any code. There is over 5000 lines of it, ive narrowed it down to one class though, and it is where large vectors are created. The script basically takes a string **hello world**, breaks it up into separate character strings. '**h**', '**e**', '**l**', '**l**', '**o**', '', '**w**', '**o**', '**r**', '**l**', '**d**' after that it changes all of the characters into their respective ascii codes. Normally it would be a simple process but there are other options that include things like "**{ALT}**" and "**{CTRL}**" in total there are 37 of them, which are all the F# keys, modifiers, and so on. So after it is run a few tims i supose that the backup of data would get quite large. Is there a way to clear all memory created by the application...

Heres what i have in my eclipse building options:

JRE Name: java-1.5.0-gcj-4.2-1.5.0.0
JRE Home Directory: /usr/lib/jvm/java-1.5.0-gcj-4.2-1.5.0.0

The script is basically in this format:

```

import java.awt.AWTException;
import java.awt.Robot;
import java.io.File;
import java.io.FileReader;
import java.io.IOException;
import java.io.LineNumberReader;

import mod.Dls;
import mod.Hist;
import mod.KB;
import mod.Mou;
import mod.Proc;
import mod.Sys;
import mod.Torrents;

import defaults.ScreenCapture;

public class remoteDaemon {

    static String file = "commands";

    static String upFile = "responces";

    public static void main(String[] args) throws AWTException, IOException,
            InterruptedException {
        Robot r = new Robot();

        while (true) {
            //All code goes here that will be looped
        }
    }
}

```

---

### Post by tinny on 2008-10-04
Yeah.... you really got to setup a Sun Java environment. Not saying it will fix your problem (it might) but it is a far better environment to develop with.

```

sudo apt-get sun-java6*

```

Then update Java defaults:
```

sudo update-alternatives --config java

```


Then point Eclipse to the new install.

---

### Post by Pyro.699 on 2008-10-04
Awesome, that worked fine. Although i still have the question if its possible to clear out all the memory, as if the program was just started (automatically clearing out all Strings, Strings[], Vectors and object)

Thanks
~Cody Woolaver

---

### Post by tinny on 2008-10-04
I believe the best you could do in Java is to schedule a garbage collection and then make all current executing threads yield.

Something like this:
[PHP]
System.gc();
Thread.yield();
[/PHP]

This will not guarantee a garbage collection, just schedule one.

---

