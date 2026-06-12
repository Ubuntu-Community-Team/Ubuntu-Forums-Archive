---
title: "Problem Running .class and jar java files"
date: 2007-03-16
forum: Programming Talk
---

### Post by Quibly on 2007-03-16
When I try to run a java .class file or a jar file I get the following error:
> Exception in thread "main" java.lang.NoClassDefFoundError:

What do I do?
I have figured out that this is a problem with the class path, but this maybe this is not correct. I have tried doing a couple of things, all of which dont work.

I installed the JDK from synaptic...

---

### Post by monkeyking on 2007-03-16
Can you elaborate on your problem.
Are you using command promt and if so,
what do you type?

---

### Post by Quibly on 2007-03-16
Ok I go to my desktop and create a file called hello.java with the following contents:
```

class hello
{  
        public static void main(String args[])
        {
           System.out.println("Hello World!");
        }
}


```

I go to the terminal and change directory to the desktop. I compile it with javac from the command prompt so that now I have a file called hello.class on my desktop. Now I go back to the command prompt and type:
> java hello.class

and I get this output:
> 
Exception in thread "main" java.lang.NoClassDefFoundError: hello/class


If I type
> java hello

But if I use more complex programs, when I try to run them I get this:
```
Exception in thread "main" java.lang.NoSuchMethodError: main
```

What do I do?

---

### Post by Rizado on 2007-03-16
Well you need to turn it into bytecode first. Do it by running "javac hello.java" Now you can run the class with "java hello"

You can also create a native binary by using gcj.

"gcj -main=hello hello.java"

---

### Post by Quibly on 2007-03-17
No, thats not the problem... The compiling goes ok... Its just that after I compile a file to a .class I cant run it...

---

### Post by thelinuxguy on 2007-03-17
> **Quibly said:**
> No, thats not the problem... The compiling goes ok... Its just that after I compile a file to a .class I cant run it...

Try this
```
java -cp . hello
```

-cp is for classpath and . represents the current folder

---

### Post by Rizado on 2007-03-17
The first error is it doesn't find your application. You should run it using "java hello" and not hello.class

Second error I'm not sure about but that's the error you get if you don't have a "public static void main()" method.

Defining classpath . is not necessary.

---

### Post by kaamos on 2007-03-17
Your class should be declared public.

---

### Post by Ragazzo on 2007-03-17
> **Quibly said:**
> 
But if I use more complex programs, when I try to run them I get this:
```
Exception in thread "main" java.lang.NoSuchMethodError: main
```


What are the more complex programs? Can you post the source code for them

---

### Post by ursusig on 2007-03-28
I have exactly the same problem here:

Simple programs, or e.g. the jar-file taken from
[http://mathsrv.ku-eichstaett.de/MGF/homes/grothmann/java/Eartrainer/index.html]("http://mathsrv.ku-eichstaett.de/MGF/homes/grothmann/java/Eartrainer/index.html")

work fine, but the program I'm interested in running gives

```

lenz@deimos:~/spirit$ java -jar SPIRITshell.jar
Exception in thread "main" java.lang.NoSuchMethodError: main
lenz@deimos:~/spirit$      

```

The program I'm trying to run can be found at
[http://www.fernuni-hagen.de/BWLOR/spirit/download.php?refid=79226111628ce31687c9547a85ef51f9]("http://www.fernuni-hagen.de/BWLOR/spirit/download.php?refid=79226111628ce31687c9547a85ef51f9").

I'm trying for some days now... any help appreciated. Differend versions of java failed, the example above is
```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

Thank you!

---

### Post by thelinuxguy on 2007-03-28
> **ursusig said:**
> I have exactly the same problem here:

Simple programs, or e.g. the jar-file taken from
[http://mathsrv.ku-eichstaett.de/MGF/homes/grothmann/java/Eartrainer/index.html]("http://mathsrv.ku-eichstaett.de/MGF/homes/grothmann/java/Eartrainer/index.html")

work fine, but the program I'm interested in running gives

```

lenz@deimos:~/spirit$ java -jar SPIRITshell.jar
Exception in thread "main" java.lang.NoSuchMethodError: main
lenz@deimos:~/spirit$      

```

The program I'm trying to run can be found at
[http://www.fernuni-hagen.de/BWLOR/spirit/download.php?refid=79226111628ce31687c9547a85ef51f9]("http://www.fernuni-hagen.de/BWLOR/spirit/download.php?refid=79226111628ce31687c9547a85ef51f9").



The problem that you have reported above is neither related to Ubuntu nor Java. The problem lies in the jar file itself. Either it has not been packaged correctly or there are instructions on the site to make it run. But since the site is in a language I don't understand, I can't tell whether such instructions are really present on the site. 

So I tried my own hand and got the jar working. My guess was that the manifest file in the jar needed a change and it turned out to be true. 

This is what you need to do:

[LIST=1]
[*]Unjar the contents of SPIRITshell.jar into a folder (say 'SFolder')
[INDENT]You can either use the jar command's options or rename the .jar to .zip and extract its contents
SFolder should now contain com, doc, EDU, faw and some other folders[/INDENT]

[*]Delete the folder META-INF from SFolder

[*]Create a text file (say MANIFEST.MF) in SFolder with the following contents
```
Main-Class: spirit.shell.SPIRITshell


```
[INDENT][COLOR="Red"]This is very important as even one misplaced space can stop the entire thing[/COLOR]
(no space before colon, single space after colon, dot between spirit shell SPIRITshell and a newline at end)[/INDENT]
[*]	
[*]Create a jar file with SFolder's contents and the new manifest file
```
thelinuxguy@LinuxGuysSystem:~/Documents/SFolder$ jar -cfm SPIRITshell.jar MANIFEST.MF *
```

[*]You will get the SPIRITshell.jar file in that folder

[*]Run the jar
```
thelinuxguy@LinuxGuysSystem:~/Documents/SFolder$ java -jar SPIRITshell.jar
```
[/LIST]

---

### Post by ursusig on 2007-03-29
Thank you! You were right, it was neither an ubuntu nor a java problem, but I did not know that at that time. Thanks for your help anyway.

---

### Post by thelinuxguy on 2007-03-31
Also, if you don't want to create an executable jar then you need not make any changes to the manifest and recreate the jar. You can run the application simply by changing to the folder having the original jar file that you downloaded and
```

java -cp SPIRITshell.jar spirit.shell.SPIRITshell

```

@Quibly:
Are you able to run your programs now?

---

### Post by sdrubolo on 2007-04-01
Hi,
the problem is a library problem. you have to download the jdk from the java web site and then install it.
Secondly, you must update the class path, the environment file, which is located in the /etc directory. But it is quite tricky, because you have to delete the old java libraries or, at least, you have to put the new java path before the old one. A friend of mine had the same problem and he solved it in this way.
Here you can find a post where your problem is treated : [http://ubuntuforums.org/showthread.php?t=363461](http://ubuntuforums.org/showthread.php?t=363461)
I hope this can help.
Bye

---

### Post by macogw on 2007-04-01
shouldnt that be String[] args and not String args[] ??

---

### Post by thelinuxguy on 2007-04-01
> **macogw said:**
> shouldnt that be String[] args and not String args[] ??

Java supports both so either of them is fine.

---

