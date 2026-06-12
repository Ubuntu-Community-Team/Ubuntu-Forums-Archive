---
title: "How to run a java program using eclim?"
date: 2009-12-22
forum: Programming Talk
---

### Post by Ubu-freak on 2009-12-22
I can't seem to run a simple Hello World program using eclim. I followed the install guide at[ http://eclim.org/guides/install.html#guides-install]("http://eclim.org/guides/install.html#guides-install") and the tutorial at [http://eclim.org/gettingstarted.html#gettingstarted](http://eclim.org/gettingstarted.html#gettingstarted), but when I try to run the program (using :Java) I get 
```
java.lang.RuntimeException: Required setting 'org.eclim.java.run.mainclass' has not been set.
    at org.eclim.plugin.jdt.command.src.JavaCommand.execute(JavaCommand.java:107)
    at org.eclim.command.Main.main(Main.java:89)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.martiansoftware.nailgun.NGSession.run(NGSession.java:334)

```And I don't know how to set whatever it says I didn't set. The program successfully compiles, and I can run it regularly in terminal, I am using Ubuntu 9.10, jdk 1.6, eclim 1.5.4.

---

### Post by ervandew on 2009-12-23
If eclim doesn't find your main class/method automatically, then you can set the setting that the stack trace references using :ProjectSettings (which will open a buffer where you can edit settings and then save the buffer (:w) to persist them).

Can you send a tar of your project to the [eclim-users]("http://groups.google.com/group/eclim-user") mailing list?  I'd like to get a look at your test project to see why eclim couldn't find your main class.

Also, if you run into any more eclim issues, please post them in the [eclim-users]("http://groups.google.com/group/eclim-user") group since I don't actively monitor other forums (I just stumble on these sometimes).

---

### Post by Ubu-freak on 2010-02-22
I got it now.  According to [http://eclim.org/vim/java/java.html](http://eclim.org/vim/java/java.html) you should be able to do it by setting the **org.eclim.java.run.mainclass** property of your project. 
Thanks for the eclim-users link =)

---

### Post by B@byD33 on 2011-09-25
I am running into the same issue. I successfully run `:Javac` however `Java` returns the following:

java.lang.RuntimeException: Required setting 'org.eclim.java.run.mainclass' has not been set.
	at org.eclim.plugin.jdt.command.src.JavaCommand.execute(JavaCommand.java:136)
	at org.eclim.command.Main.nailMain(Main.java:92)
	at sun.reflect.GeneratedMethodAccessor5.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.martiansoftware.nailgun.NGSession.run(NGSession.java:336)

I understand from the previous posts that java cannot find my class method and that u can use :ProjectSettings to edit the settings, however, as a new user it would be great to have step by step (i.e. which setting should be change, value). I really appreciate the help!

---

