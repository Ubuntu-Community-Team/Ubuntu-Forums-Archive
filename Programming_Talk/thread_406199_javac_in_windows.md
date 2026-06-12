---
title: "javac in windows"
date: 2007-04-10
forum: Programming Talk
---

### Post by Bobtheknight on 2007-04-10
My betters,

This is a windows question, I hope that's okay.

I am trying to program java on windows (vista), however after I install it the command prompt would not recognize "javac"

"'javac' is not recognized as an internal or external command,
operable program or batch file."

After I go to C:\Program Files\Java\jdk1.6.0_01\bin> javac is there, like the documentation says.  

So my question is how do I associate that javac in the above directory to command prompt so it runs like "dir?"

Thanks in advance,
Bob

---

### Post by marianom on 2007-04-10
100% guessing here but it might be because you don't have the java dir in your windows path.

As far as I recall from those long gone days, you need to add it, reboot the machine to see the change. If it's not there, windows don't know how to look for the javac file.

---

### Post by phossal on 2007-04-10
Yeah, in XP, it's done like this:

Control Panel -> System -> Advanced -> Environment Variables -> Path (Edit to include the path to the /bin folder). I haven't had the misfortune of using Vista yet, but I'm sure it's much, much different - and more complicated. ;)

Regards.

---

### Post by samjh on 2007-04-10
The windows installer for java doesn't add to path.  You will need to set C:\Program Files\Java\jdk1.6.0_01\bin to your PATH environment variable.

Consult Vista documentation.  Or even better: invoke the power of Google.

---

### Post by Bobtheknight on 2007-04-10
Thanks, I'll find out on Thursday when I go into work again.  I don't like windows either but it's a work computer, and this is not the place to complain about it -_-.

Bob

---

### Post by pbrockway2 on 2007-04-10
To add a link to what the others have said [http://java.sun.com/javase/6/webnotes/install/jdk/install-windows.html#Environment](http://java.sun.com/javase/6/webnotes/install/jdk/install-windows.html#Environment)

---

