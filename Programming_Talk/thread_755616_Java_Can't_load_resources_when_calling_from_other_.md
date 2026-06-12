---
title: "Java: Can't load resources when calling from other dir"
date: 2008-04-15
forum: Programming Talk
---

### Post by ayampanggang on 2008-04-15
PS: Sorry if my title is a bit misleading. Can't find another word to describe this.

I have created a java program that reads a textfile from its relative directory, (e.g. if i place it inside /home/derek, then the textfile it wants to read should be within the /home/derek/ directory)

the problem is that when i call the java program from the right directory then it works. if i call it from somewhere else it doesn't

/home/derek #] java EntryPoint --> works! because i call it from /home/derek

/home/derek/Movies #] java -classpath "/home/derek/" EntryPoint --> doesn't work. the program runs fine but it can't find the textfile. It seems like it searches for the textfile within the /home/derek/Movies (the current working dir) instead of the home dir.


The problem is that i want to make shortcut from my Gnome desktop, and the program won't load the textfile. And for now i have to open up terminal, switch to home dir, and run it from there.

anyone can tell me how to fix this?

Thank you very much!

---

### Post by CptPicard on 2008-04-15
Well, the thing is working perfectly right -- it's the current working directory that it should be looking for the file in. The Classpath is a whole different concept (it's where Java classes are to be found), and has nothing to do with the CWD.

You need to either hardcode the directory into your new File() call like new File("/home/derek/file.txt"), or preferably, pass the complete path to the file as a command-line parameter to your application.

---

### Post by Zugzwang on 2008-04-15
You *can* load your textfile using the CLASSPATH, but as CptPicard wrote, this is not the way it is intended to use. 


[LIST=1]
[*]If you just need your home path, you can use
the method getProperty("user.home") of the Properties object:

```

Properties props = new Properties();
String homeDir = props.getProperty("user.home");

```
[*] If you still want to use the class path, try something like:
```

MyClass.class.getResource("mytextfile.txt")

```
[*]However, using a command line argument as suggested by Mr.Picard is still the cleanest way to go
[/LIST]

---

### Post by ayampanggang on 2008-04-15
i see. So if i use command line argument, calling the program would look like:
java EntryPoint $CWD
right?

sounds neat, i'll try that

thank you for the lists of solution :)

---

