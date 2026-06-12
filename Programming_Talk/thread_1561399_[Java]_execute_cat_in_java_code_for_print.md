---
title: "[Java] execute cat in java code for print"
date: 2010-08-26
forum: Programming Talk
---

### Post by giuseppe_84 on 2010-08-26
Hello all

[COLOR=#000000]I apologize for my English, [/COLOR][COLOR=#000000]I would run the command 
[/COLOR]```
[COLOR=#000000]cat / tmp / test.txt > / dev/lp0 [/COLOR]
```[COLOR=#000000]in Java code 
[/COLOR]I have tried in various ways:
```

[COLOR=#000000]Process p = Runtime.getRuntime().exec("cat  /tmp/test.txt > /dev/lp0");
p.destroy();[/COLOR]
```
[COLOR=#000000]
[/COLOR][COLOR=#000000]but nothing happens

or
[/COLOR]```
[COLOR=#000000]  
String[] arr =  new String[5];
  [/COLOR][COLOR=#000000]arr[0] = "/bin/bash ";
    arr[1] = "cat ";
    arr[2]= "/tmp/[/COLOR][COLOR=#000000]test.txt [/COLOR][COLOR=#000000]";
    arr[3] = " > ";
    arr[4]= "/dev/lp0";
Process p = Runtime.getRuntime().exec(arr);[/COLOR]
```
[COLOR=#000000]or
[/COLOR]```
[COLOR=#000000]  
String[] arr =  new String[4];
  [/COLOR][COLOR=#000000]  arr[0] = "cat ";
    arr[1]= "/tmp/[/COLOR][COLOR=#000000]test.txt [/COLOR][COLOR=#000000]";
    arr[2] = " > ";
    arr[3]= "/dev/lp0";
Process p = Runtime.getRuntime().exec(arr);[/COLOR]
```

[COLOR=#000000]with the last two attempts gave me this kind of Exception
[/COLOR]```

java.io.IOException: Cannot run program "/bin/bash ": java.io.IOException: error=2, No such file or directory
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:460)
        at java.lang.Runtime.exec(Runtime.java:593)
        at java.lang.Runtime.exec(Runtime.java:466)
        at provacomm.Main.main(Main.java:40)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
        at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
        at java.lang.ProcessImpl.start(ProcessImpl.java:65)
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:453)
        ... 3 more

```[COLOR=#000000]can someone help me [/COLOR][COLOR=#000000]thanks[/COLOR]

---

### Post by Zugzwang on 2010-08-26
> **giuseppe_84 said:**
> 
[/COLOR]I have tried in various ways:
```

[COLOR=#000000]Process p = Runtime.getRuntime().exec("cat  /tmp/test.txt > /dev/lp0");
p.destroy();[/COLOR]
```


Huh? You are starting the process and immediately destroy it (which is likely, but not guaranteed to happen before it has finished)? Don't you rather want to wait until it has finished first? Call "waitFor()" instead of "destroy()".

At a side note, it probably makes more sense to open "/dev/lp0" for writing using a "BufferedOutputStream" or something like that to write your stuff there and simply forget about doing it in a subprocess. If you want the whole thing to be portable, you might want to look into AWT/Swing's printing functionalities.

---

### Post by Some Penguin on 2010-08-26
1.  Don't append extra spaces.   Read the exception again -- you don't actually HAVE a command named "/bin/bash ", do you?  You have "/bin/bash".

2.  Pipes.  Get the output stream from the process and redirect it.  ">" is not an argument.

3.  Don't use two extra processes -- 'bash' and 'cat' -- when Java is perfectly capable of opening files itself.

---

### Post by giuseppe_84 on 2010-08-26
> **Zugzwang said:**
> Huh? You are starting the process and immediately destroy it (which is likely, but not guaranteed to happen before it has finished)? Don't you rather want to wait until it has finished first? Call "waitFor()" instead of "destroy()".

At a side note, it probably makes more sense to open "/dev/lp0" for writing using a "BufferedOutputStream" or something like that to write your stuff there and simply forget about doing it in a subprocess. If you want the whole thing to be portable, you might want to look into AWT/Swing's printing functionalities.

I put p.destroy () because if after launching the application I tried to print again from the terminal told me "device is busy", but if I delete it still does not work,  I tried to open the door and write but I wanted to know if it was possible to directly execute the command

---

### Post by giuseppe_84 on 2010-08-26
> **Some Penguin said:**
> 1.  Don't append extra spaces.   Read the exception again -- you don't actually HAVE a command named "/bin/bash ", do you?  You have "/bin/bash".

2.  Pipes.  Get the output stream from the process and redirect it.  ">" is not an argument.

3.  Don't use two extra processes -- 'bash' and 'cat' -- when Java is perfectly capable of opening files itself.


I tried this way

```

[COLOR=#000000]String[] arr =  new String[3];
  [/COLOR][COLOR=#000000]  arr[0] = "cat";
    arr[1]= "/tmp/[/COLOR][COLOR=#000000]test.txt[/COLOR][COLOR=#000000]";
    arr[2]= "/dev/lp0";
Process p = Runtime.getRuntime().exec(arr);

[/COLOR]but does not work


```

---

### Post by giuseppe_84 on 2010-08-26
> **Some Penguin said:**
> 
Pipes.  Get the output stream from the process and redirect it.  ">" is not an argument.



you can show me how please

---

### Post by Zugzwang on 2010-08-26
> **giuseppe_84 said:**
> I put p.destroy () because if after launching the application I tried to print again from the terminal told me "device is busy", but if I delete it still does not work,  I tried to open the door and write but I wanted to know if it was possible to directly execute the command

Ok, so then first wait for the task to finish and *then* destroy it. By the way: Why don't you let the "lpr" command do the printing if you really want to do it the hard way?

And with respect to input/output streaming of processes in Java, have a look at the following example: [http://www.java2s.com/Code/JavaAPI/java.lang/ProcessgetOutputStream.htm](http://www.java2s.com/Code/JavaAPI/java.lang/ProcessgetOutputStream.htm)

And by the way. The following code:
```

String[] arr =  new String[3];
    arr[0] = "cat";
    arr[1]= "/tmp/test.txt";
    arr[2]= "/dev/lp0";
Process p = Runtime.getRuntime().exec(arr);


```

does not work because "cat" is not a program but a shell command. So you will need to invoke the shell to run the "cat" command. But as already stated in this post, this is not the right way to solve your problem. We do understand that you rather like to stick to "solutions" which you understand, but I must say that calling "cat" to write to "/dev/lpr" using the Java process interface reminds me of this comic: [http://www.xkcd.com/763/](http://www.xkcd.com/763/)

---

### Post by giuseppe_84 on 2010-08-26
> **Zugzwang said:**
> Ok, so then first wait for the task to finish and *then* destroy it. By the way: Why don't you let the "lpr" command do the printing if you really want to do it the hard way?

And with respect to input/output streaming of processes in Java, have a look at the following example: [http://www.java2s.com/Code/JavaAPI/java.lang/ProcessgetOutputStream.htm](http://www.java2s.com/Code/JavaAPI/java.lang/ProcessgetOutputStream.htm)

And by the way. The following code:
```

String[] arr =  new String[3];
    arr[0] = "cat";
    arr[1]= "/tmp/test.txt";
    arr[2]= "/dev/lp0";
Process p = Runtime.getRuntime().exec(arr);


```does not work because "cat" is not a program but a shell command. So you will need to invoke the shell to run the "cat" command. But as already stated in this post, this is not the right way to solve your problem. We do understand that you rather like to stick to "solutions" which you understand, but I must say that calling "cat" to write to "/dev/lpr" using the Java process interface reminds me of this comic: [http://www.xkcd.com/763/](http://www.xkcd.com/763/)

I have to print  documents with special printer, I opened the door / dev/lp0 write, and I  could write about it, but some printers give me problems, what do you  advise me to do and if you can show me some examples, I thought about using the command 'cat' in the code because that way I could always print

---

### Post by spjackson on 2010-08-26
> **giuseppe_84 said:**
> [COLOR=#000000]
[/COLOR]```
[COLOR=#000000]
String[] arr =  new String[5];
  [/COLOR][COLOR=#000000]arr[0] = "/bin/bash ";
    arr[1] = "cat ";
    arr[2]= "/tmp/[/COLOR][COLOR=#000000]test.txt [/COLOR][COLOR=#000000]";
    arr[3] = " > ";
    arr[4]= "/dev/lp0";
Process p = Runtime.getRuntime().exec(arr);[/COLOR]
```
If you want to go down the road of calling 'cat' in a separate process, I think that the following should work for you.
[COLOR=#000000]
[/COLOR]```
[COLOR=#000000]
String[] arr =  new String[5];
  [/COLOR][COLOR=#000000]arr[0] = "/bin/bash";  // N.B. No trailing space
    arr[1] = "-c";
    arr[2]= "cat /tmp/[/COLOR][COLOR=#000000]test.txt > [/COLOR][COLOR=#000000]/dev/lp0[/COLOR][COLOR=#000000]";
Process p = Runtime.getRuntime().exec(arr);[/COLOR]
```

---

