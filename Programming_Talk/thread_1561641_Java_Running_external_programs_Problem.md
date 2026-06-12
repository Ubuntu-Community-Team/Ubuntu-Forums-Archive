---
title: "Java Running external programs Problem"
date: 2010-08-26
forum: Programming Talk
---

### Post by psychok7 on 2010-08-26
hi everyone.. i have been trying to run a compiled C program under ubuntu with Java and it has been giving me errors.

```

//the second stkeys is the c object that came from the compilation
Process p = Runtime.getRuntime().exec("/stkeys/stkeys");

```

and i get this ERROR: 

```

java.io.IOException: Cannot run program "stkeys": java.io.IOException: error=2, No such file or directory
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
        at java.lang.Runtime.exec(Runtime.java:610)

```

not sure if i am doing this right but the stkeys(executable) is under the stkeys folder.
i can only find windows examples on the internet file.exe but for linux i only find shell commands example. can anyone help me?

---

### Post by Zugzwang on 2010-08-26
The file name of the program you are trying to execute starts with a "/", thus your Java application searches in **the root folder of the file system**. So try "stkeys/stkeys" instead and check that the directory from which you start your application from really has a program named "stkeys" in the sub-directory "stkeys".

---

### Post by psychok7 on 2010-08-26
> **Zugzwang said:**
> The file name of the program you are trying to execute starts with a "/", thus your Java application searches in **the root folder of the file system**. So try "stkeys/stkeys" instead and check that the directory from which you start your application from really has a program named "stkeys" in the sub-directory "stkeys".

thanks that was it... by the way how can i input some arguments coming from my Java to the C program??

---

### Post by Zugzwang on 2010-08-26
> **psychok7 said:**
> thanks that was it... by the way how can i input some arguments coming from my Java to the C program??

What do you mean by "arguments" - command line arguments or "terminal input/output"? The former you can simply append to the name of the program to run, the latter you can perform using the InputStream and the OutputStream offered by Java's process class. Google for details if this is what you want.

---

### Post by psychok7 on 2010-08-26
i was able to put everything working, clean and built the .jar using netbeans and when i try to execute my program the main GUI opens up but when i press the button that will execute the external command nothing happens. On the other hand if i open everything using the terminal everything works fine.. any ideas?

---

### Post by Zugzwang on 2010-08-29
> **psychok7 said:**
> any ideas?

If "nothing happens" in a Java program, then it is not entirely unlikely that some exception isn't caught. I do suspect that Netbeans runs the .jar file from a different directory (it's in the project settings) and you don't catch the exception that the executable is not found properly or discard it somehow like this:
```

try {
   ....
} catch (Exception e) {
  // Do nothing
}

```

When executing something from Netbeans, there's a terminal that will print the Exceptions that you didn't catch. Look if there's an exception popping up if you press the button! If you have some code like the one above in your program, at least put some "JOptionPane.showMessageDialog(...)" line in the "catch" part in order to get notified about exceptions.

---

