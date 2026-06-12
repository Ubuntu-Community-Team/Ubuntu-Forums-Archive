---
title: "Problem adding jar to class path"
date: 2007-09-29
forum: Programming Talk
---

### Post by Black Mage on 2007-09-29
I have a jar called BDJ.jar in my home directory and I tried to add it to the classpath by doing

java -classpath ~/workspace/BluRay/ BDJ.jar

But it seems its not reading it because it throws

Exception in thread "main" java.lang.NoClassDefFoundError: BDJ/jar

So how else am I suppose to add a jar to the class path in the command line?

---

### Post by Fixman on 2007-09-29
> **Black Mage said:**
> I have a jar called BDJ.jar in my home directory and I tried to add it to the classpath by doing

java -classpath ~/workspace/BluRay/ BDJ.jar

But it seems its not reading it because it throws

Exception in thread "main" java.lang.NoClassDefFoundError: BDJ/jar

So how else am I suppose to add a jar to the class path in the command line?

Try
```
java -classpath $HOME/workspace/BluRay/BDJ.jar
```

---

### Post by Black Mage on 2007-09-29
No, it still throws the same error, and the jar is in that directory. Here is the full command line:

john@ubuntu:~/workspace/BluRay$ java -classpath $Home/workspace/BluRay/ BDJ.jar

and then I tried
john@ubuntu:~/workspace/BluRay$ java -classpath $John/workspace/BluRay/ BDJ.jar


and a few other variations wihth no success.....any ideas?

---

### Post by Ramses de Norre on 2007-09-29
Delete the space between the "/" and the filename, so instead of "$Home/workspace/BluRay/ BDJ.jar" you type "$HOME/workspace/BluRay/BDJ.jar".

I've also change "$Home" to "$HOME" because only the latter exists (unless you manually defined the lowercase one).

The command line is picky on spaces and cases...

---

### Post by Black Mage on 2007-09-29
Ahhhh, thnx is compiles now using 
javac -classpath $HOME/workspace/BluRay/BDJ.jar MySecondXlet.java
but still no success getting the Xlet to actually run, exception because of no main method.

But thnx, thats problem down.

---

### Post by lamadredelsapo on 2007-10-01
next time add it to the .bashrc file, so you won't have to edit classpath whenever you want to use that jar

---

