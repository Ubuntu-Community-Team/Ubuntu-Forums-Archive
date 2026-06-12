---
title: "command line arguements in java"
date: 2009-08-07
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-07
when is use javac compiler and then java to execute, i'm able to display and use command line arguements , how to do the same in eclipse?
if i just do the following code, ```

public static void main(String[] args) {
System.out.println("command line arg are " +args[0]+" "+args[1]+" "+args[2]);
}


```
where and how to pass command line arguements in eclipse??

---

### Post by Habbit on 2009-08-07
You mean how to make the Eclipse IDE pass arguments to your program when it's run through the "run" or "debug" commands in the IDE? Well, I don't know Eclipse itself, but in most IDEs the option is within the project properties, usually under some category called "runtime" or "execution".

---

### Post by lykeion on 2009-08-07
I'm no eclipse user either (I prefer IntelliJ), but a fast google search gives you the answer...

[http://www.eclipse-blog.org/java-se/java-command-line-arguments-in-eclipse-ide.html]("http://www.eclipse-blog.org/java-se/java-command-line-arguments-in-eclipse-ide.html")

Run > Run configurations... > Arguments Tab > and fill in the arguments (delimited by spaces) in the Program arguments box

---

### Post by abhilashm86 on 2009-08-08
yes thanks, now i found that tab for arguements......

---

