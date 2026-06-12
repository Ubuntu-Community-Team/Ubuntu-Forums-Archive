---
title: "xubuntu - cant execute .jar file."
date: 2013-08-30
forum: New to Ubuntu
---

### Post by mike60 on 2013-08-30
Hi There.
so im running xubuntu 10.04 and i downloaded java and everything (java6) and i have a .jar file however when i double click it, NOTHING happens, nothing loads or no errors. when i try to open the .jar file through the terminal "java -jar /full/path/to/filename.jar" it gives me an error of "unable to access jar file" does anyone have any solutions for me please.

---

### Post by mike60 on 2013-08-30
P.S - i did try to run a chmod command butni dont think it worked, and i couldnt get the error message.

---

### Post by steeldriver on 2013-08-30
what do you get if you do 

```
ls -l /full/path/to/filename.jar
```

---

### Post by mike60 on 2013-08-30
ls: cannot access /home/Mike/Downloads/Virtue: No such file or directory

ls: cannot access V2.2/Virtue.jar: No such file or directory

---

### Post by steeldriver on 2013-08-30
Does the file path have a space in?

```
/home/Mike/Downloads/Virtue V2.2/Virtue.jar
```

If so you will need to quote it

```
java -jar **"**/home/Mike/Downloads/Virtue V2.2/Virtue.jar**"**
```

or 'escape' the space with a backslash

```
java -jar /home/Mike/Downloads/Virtue**\ **V2.2/Virtue.jar
```

---

### Post by newb85 on 2013-08-30
Brief comment:  Support for Ubuntu 10.04 officially ended April 2013.  I'll spare you the lecture/rant/long explanation.  If you don't know why you need to upgrade to a supported release, a little research is in order.

---

### Post by mike60 on 2013-08-30
i tried the first command, nothing loaded up but in the terminal under the command line (now a new command line) it only had
>
nothing else happened.
Second command you gave me i triedbbut it still said: unable to access jarfile /path/to/jarfile.jar

---

### Post by Impavidus on 2013-08-30
The > is a prompt, indicating that the shell is expecting more input. You probably forgot the closing quote. The second error means something is wrong with the path. Better check it again. Things like [space], [newline], $, \, {, }, ", ' may need to be escaped when not quoted.

---

### Post by nerdtron on 2013-08-30
> **mike60 said:**
> Hi There.
so im running xubuntu 10.04 and i downloaded java and everything (java6) and i have a .jar file however when i double click it, NOTHING happens, nothing loads or no errors. when i try to open the .jar file through the terminal "java -jar /full/path/to/filename.jar" it gives me an error of "unable to access jar file" does anyone have any solutions for me please.

Go to the file manager and see if you can even right click>properties and check the permissions of the file. Are you sure you have read access to it?
Try running the sudo chmod instead of just chmod. The file might be owned by the root or other user.

Also, please upgrade. Your system is no longer supported.

---

