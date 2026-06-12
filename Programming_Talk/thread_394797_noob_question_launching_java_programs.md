---
title: "noob question: launching java programs"
date: 2007-03-27
forum: Programming Talk
---

### Post by mctk on 2007-03-27
So I've got my fancy little java program running from the terminal.  That's all working fine.  I move to my project's directory and run "java helloWorld".

Is there anyway to run this program without moving to the same directory that helloWorld is in?  For example, helloWorld.class is located in the folder: ~/Desktop/helloWorld/

Is there a way I can simply open a terminal and type something like:
```

java Desktop/helloWorld/helloWorld

```

rather than
```

cd Desktop/helloWorld; java helloWorld

```
Ultimately, I want my little java program to run on startup for all users and have an icon on the desktop.  How can I make that happen?  Thanks in advance!

---

### Post by Tomosaur on 2007-03-27
Yup, you need to use the classpath argument, like this:
```

java -cp <path containing class files> <command> <command args>

```

So in your case you would type:
```

java -cp ~/Desktop/helloWorld/ helloWorld

```

---

