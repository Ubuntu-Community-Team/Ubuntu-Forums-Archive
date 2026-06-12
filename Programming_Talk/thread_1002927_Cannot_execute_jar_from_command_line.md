---
title: "Cannot execute jar from command line"
date: 2008-12-05
forum: Programming Talk
---

### Post by sjmacewan on 2008-12-05
Hey folks,
I just finished a java swing app that works perfectly if I double-click on the icon. But if I try to run it from command line via the following command it loads but immediately hangs:

java -jar /pathToFile/fileName.jar 

Also, if I try dragging the icon to the panel (where I want it to be in the end) it just doesn't launch period. Any ideas why it would work on double-click but not by command?

Thanks!

---

### Post by Unterseeboot_234 on 2008-12-05
I don't how you did your java's development, but if you created with Notepad, without import package spiffycode; and then make a jar, the Manifest can't find main(); 

1. you can try: java -jar mySpiffyApp.main();

2. This can really be a can of worms for newbies using an IDE. The IDE will have a path into the project folder so it can look into the 'build' folder and the 'source' folder. Resources for the java program belong in both folders whilst in IDE.

If you have a data.txt file for persistence, you have to logically construct that path to the file with code. An image, no problem. URL url = getClass().getResource("pic.png"); Image originalImage = ImageIO.read( url ); -- now why! can't they do that with file?

My solution has been use NetBeans, set the project I want as Main Project, and when I build final, I go into config --> Custom and browse for main(); That way ANT makes manifest include the path to main();

Hope that helps. I've been down to the perfect working app in the IDE, only to go somewhere with the .jar and really look stupid because it won't launch.

---

### Post by sjmacewan on 2008-12-06
Hmmm, I used eclipse for an IDE, that's all I'm really comfortable with at this point. It's also my first time ever making a jar, so at first I though it could be something wrong in making the manifest. But like I said: the jar is created and if I double-click on the icon for the file, it opens up and runs perectly. It just hangs if I try to execute by command.

That item 1 in your reply, that's not to be typed in the console is it? It barks at the ( following main.

Thanks for your help so far.

---

### Post by sjmacewan on 2008-12-08
Sorry to bump, but does anybody else have any ideas what could be causing this?
Thanks,
Sjmacewan

---

### Post by tinny on 2008-12-08
First thing, do you have Sun Java setup on your machine? This is a must if you want to develop with Java on Ubuntu.

Whats the output of

```

> java -version

```

and

```

> javac -version

```

---

### Post by sjmacewan on 2008-12-10
oops, thought I subscribed to this, sorry for not answering

java version is:
java version "1.5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

javac is:
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.



I'm thinking maybe these should be something different? If so, how do I change it?
Thanks,
Sjmacewan

---

### Post by tinny on 2008-12-10
> **sjmacewan said:**
> oops, thought I subscribed to this, sorry for not answering

java version is:
java version "1.5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

javac is:
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.



I'm thinking maybe these should be something different? If so, how do I change it?
Thanks,
Sjmacewan

Yeah.

You should set yourself up with a Sun Java environment.

```

sudo apt-get install sun-java6-jdk

```

Then you will need to set this new environment up as default within eclipse.

Window > Preferences > Java > Installed JREs > Add

The path to the new JDK should be /usr/lib/jvm/java-6-sun-1.6.0.10

Then set this new JDK as default.

---

### Post by drubin on 2008-12-10
> **tinny said:**
> Yeah.

You should set yourself up with a Sun Java environment.

```

sudo apt-get install sun-java6-jdk

```

....

Agreed makes life much easier.

---

### Post by sjmacewan on 2008-12-11
I thought I remembered installing Sun's java, and sure enough I did. When I tried to install it, it said that I already have the newest version. Same with eclipse: it's using sun's java.

I think the problem is that when I type java and javac into a terminal, it's using the wrong java...how do I change which version Ubuntu uses?

UPDATE:
figured it out, used 
```
sudo update-alternatives --config java
```

Now, problem still holds :(


EDIT:

fixed! I forgot to recompile with the new javac, works fine. Thanks guys

---

### Post by drubin on 2008-12-12
> **sjmacewan said:**
> EDIT:

fixed! I forgot to recompile with the new javac, works fine. Thanks guys

You are compiling Suns java? as far as I know it is closed source so not 100% sure how you can compile it?

Do you perhaps me run it.. the .bin file

---

### Post by jespdj on 2008-12-12
> **drubin said:**
> You are compiling Suns java? as far as I know it is closed source so not 100% sure how you can compile it?
He wrote he recompiled **with** Sun's javac, i.e. he compiled his own source code with Sun's javac instead of the GNU Java compiler.

---

### Post by drubin on 2008-12-12
> **jespdj said:**
> He wrote he recompiled **with** Sun's javac, i.e. he compiled his own source code with Sun's javac instead of the GNU Java compiler.

heheh that explains a lot :)

---

