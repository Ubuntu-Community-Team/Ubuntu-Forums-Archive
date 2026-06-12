---
title: "How to run a command from Application launcher"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by madu on 2008-08-20
Hello,

I want to run a script from the application launcher (Application launcher is that button you can add to the panel).

What I want is to run a Java code. For example, I have my code in ~/Java folder. So I would normally go from terminal as follows:
$cd Java
Java$ java someProgram

I want to do this from the application launcher. I just tried putting 'cd ~/Java; java someProgram' in to a script and launching it. But gives the error "Failed to execute child process".

Is there any work around to get this done?

Thank you.

---

### Post by meindian523 on 2008-08-20
I think you need ```
cd ~/Java && java someProgram
```

---

### Post by madu on 2008-08-20
Thanks mate.
But still gives the same error. :(

---

### Post by meindian523 on 2008-08-20
Did you put that in a script and try to launch the script?I meant you to put that in the launcher program.

EDIT:On second thoughts,you should probably be putting ```
java ~/Java/someProgram
``` in the application launcher.

---

### Post by madu on 2008-08-20
> **meindian523 said:**
> Did you put that in a script and try to launch the script?I meant you to put that in the launcher program.

EDIT:On second thoughts,you should probably be putting ```
java ~/Java/someProgram
``` in the application launcher.

yes I put it in a script. And when I run the script on a terminal it works fine. But not with the application terminal. I'm trying to run the script from app launcher. 

I tried > java ~/Java/someProgram but it gives > Exception in thread "main" java.lang.NoClassDefFoundError error.

Thank you meindian.

---

### Post by meindian523 on 2008-08-20
Stupid workaround,try checking "Run in Terminal" in the app launcher.

---

### Post by madu on 2008-08-20
> **meindian523 said:**
> Stupid workaround,try checking "Run in Terminal" in the app launcher.

Thanks a lot mate.
But still didn't work.
Gives "Error creating child process for this terminal" error.

Thanks for the help man.

---

### Post by sdennie on 2008-08-20
Make your launcher read:

```

bash -c "cd ~/Java ; java someProgram"

```

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by madu on 2008-08-20
> **vor said:**
> Make your launcher read:

```

bash -c "cd ~/Java ; java someProgram"

```

Wow.. worked like a charm!
Thanks a lot mate!

Could you please tell me the difference between doing > bash -c "cd ~/Java ; java someProgram" and just [QUOTE"cd ~/Java ; java someProgram"[/QUOTE] with the 'Application in terminal" selection?

Thanks MarkieB.

---

### Post by sdennie on 2008-08-20
Both ~ and ; are shell operations.  A launcher just tries to execute what you've told it to execute but doesn't create a new shell to evaluate what are otherwise shell commands.  I hope that makes sense.

---

### Post by madu on 2008-08-20
> **vor said:**
> Both ~ and ; are shell operations.  A launcher just tries to execute what you've told it to execute but doesn't create a new shell to evaluate what are otherwise shell commands.  I hope that makes sense.

Thanks a lot Vor.
Think I got it.

---

### Post by meindian523 on 2008-08-21
Thanks Vor.This is why this the best forum out here.You learn something new everyday.I knew about the -c option,but didn't imagine this could be put to use in this manner.

---

### Post by seb_renaud on 2008-08-25
Got to this thread while trying to figure out how to launch an application that is provided as a .jar file. You need to send the following command in that case:

```
hacker@box:~$ java -jar myapp.jar
```

Failing to invoke in the above manner will generate a java.lang.ClassNotFoundException on the jar file.

All the above considerations for creating an actual launcher still applies I guess. I hope this helps someone!

---

