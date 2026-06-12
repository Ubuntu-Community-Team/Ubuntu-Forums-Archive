---
title: "Turning .bat into .sh"
date: 2016-10-31
forum: Packaging and Compiling Programs
---

### Post by radioactivesquirrel on 2016-10-31
Hello guys, I'm trying to run a RSPS server but they only have .bat run files, it uses java this is the .bat file can someone please make a working .sh file from this?

@echo off
title runserver
"C:/Program Files/Java/jre1.8.0_77/bin/java.exe" -Xmx815m -cp bin;lib/*; com.rs.Launcher true true false
pause

---

### Post by reegz on 2016-10-31
Try this.

```
java -Xmx815m -cp "bin/*:lib/*" com.rs.Launcher true true false
```

This assumes that Java is on your path.

---

### Post by radioactivesquirrel on 2016-11-01
I did this, and now I get : Error: Could not find or load main class com.rs.Launcher

---

### Post by reegz on 2016-11-01
It's basically saying that it cannot find the jar that contains the Java class that launches the application. So either the required libraries are missing (unlikely if you haven't moved files around) or that the command is being executed from the wrong directory.

Are you running this command from the same location as where the bat file is located?

---

### Post by radioactivesquirrel on 2016-11-02
yes, I run the .sh from the directory where the .bat and .sh are located, I can run it on windows, but ubuntu gives me errors

---

### Post by reegz on 2016-11-02
Have you validated that the files in the bin and lib directories have copied over? The command will work if all the required files are present.

---

