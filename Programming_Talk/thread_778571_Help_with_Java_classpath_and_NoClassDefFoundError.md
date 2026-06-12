---
title: "Help with Java classpath and NoClassDefFoundError"
date: 2008-05-02
forum: Programming Talk
---

### Post by mattgaunt on 2008-05-02
Hey everyone

Im trying to run my program outside of netbeans - it's a group project and I'm trying to compile and hopefully jar it outside of netbeans.

Basically in the main directory (directory the terminal is in) there are a number of image files and other custom files the program uses, as well as three .jar files the program uses for api's, itext, translate and mail, and finally all the source files. Now when the source files compile the put into a package searchword (A new directory searchword/).

I can compile the program with -cp and the .jar file names but when i run it, it comes up with a NoClassDefFoundError.

Does anyone know what the correct classpath should be?

Gaunt

---

### Post by Zugzwang on 2008-05-02
> **mattgaunt said:**
> 
Does anyone know what the correct classpath should be?


Basically the same as for compiling. The "-cp" works for running the program as well.

Alternatively, you should also look into the Java documentation regarding the classpath-setting in the manifest-file of your "main" .jar.

---

### Post by mattgaunt on 2008-05-02
Well I've been compiling it as

javac  -cp ./iText-2.0.8.jar:./google-api-translate-java-0.30.jar:./mail.jar -d . *.java

and running the program as

java searchword.GUI

if I try

java  -cp ./iText-2.0.8.jar:./google-api-translate-java-0.30.jar:./mail.jar searchword.GUI

Then i get the following error message

Exception in thread "main" java.lang.NoClassDefFoundError: searchword/GUI

Soz if this seems stupid, I'm used to just programming with all sources files in one directory and not needing any API's.

Gaunt

---

### Post by Zugzwang on 2008-05-02
> **mattgaunt said:**
> 
javac  -cp ./iText-2.0.8.jar:./google-api-translate-java-0.30.jar:./mail.jar -d . *.java


Correct me if I'm wrong, but doesn't this only compile the sources in the current directory and not those in "searchword"? Check if the respective compiled class files are there.

If that doesn't work, you may try adding the current directory to the classpath by adding ":." to the -cp switch.

---

### Post by mattgaunt on 2008-05-05
Cheers for the help Zugzwang, we ended up putting the images inside the jar file and i played around until i got a classloader working with it so it seems to work now

---

