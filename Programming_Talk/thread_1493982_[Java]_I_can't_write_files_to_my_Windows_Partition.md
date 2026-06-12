---
title: "[Java] I can't write files to my Windows Partition"
date: 2010-05-26
forum: Programming Talk
---

### Post by skytreader on 2010-05-26
Greetings.

So, my hard drive is partitioned between Ubuntu (v9) and Windows Vista. I am new to Ubuntu and, as most of my work is already under Windows, I seldomly save files on the Ubuntu partition of my HD.

So, I was programming in Java (coding under Ubuntu, gedit to be specific), and was trying to write a simple text file to my Windows partition. My code:

```

PrintWriter OutputWriter = new PrintWriter(new BufferedWriter(new FileWriter("test.txt")));
OutputWriter.print("Why do I tire of counting sheep?");
OutputWriter.close();
```(This file is saved on my Windows partition of course.)

However, it doesn't work under this set-up. So, I copy-pasted my files to the Ubuntu partition and it worked. Am I right in thinking that this is some security feature of Ubuntu? How do I work around this (i.e., I can save files on my Windows partition even when I'm running my classes from Ubuntu?)

Note that I am compiling from command-line using Sun's javac.

Much thanks for any help (--,)...

---

### Post by dv3500ea on 2010-05-26
You will need to change to the directory that you want to write the file to before running the compiled executable.
eg.
[CODE]
cd /media/windows-partition/path/to/file
/full/path/to/compiled/executable
[CODE]
Note that programs compiled on windows will not run on ubuntu and visa versa.

---

### Post by PaulM1985 on 2010-05-26
> **dv3500ea said:**
> Note that programs compiled on windows will not run on ubuntu and visa versa.

Really?  Should be alright if OP is using Java.

---

### Post by skytreader on 2010-05-26
> You will need to change to the directory that you want to write the file to before running the compiled executable.My bad. I was compiling with packages and I kept looking for the written files inside the package folder. My mistake here...everything is working fine.

> Note that programs compiled on windows will not run on ubuntu and visa versa.     They will. I'm using Java after all---Write Once, Run Anywhere (you got a JRE installed).

[Case Closed. Thanks (--,)]

---

### Post by soltanis on 2010-05-26
It's usually the "write once" part that gets you with Java.

---

