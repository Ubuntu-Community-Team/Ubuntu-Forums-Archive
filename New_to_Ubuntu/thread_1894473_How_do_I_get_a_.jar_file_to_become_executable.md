---
title: "How do I get a .jar file to become executable?"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-12-12
I have just downloaded DimSum onto my second laptop as I want to continue learning Mandarin Script.  

I swear that on Nubbin the Notebook running Maverick I can just right click and tell it to run in Java. On Jolinar the laptop, which is running Xubuntu Oneric, it claims it's 'not marked as executable' when I do the self same thing.

Help? I am not good with terminal commands (I forget them!).

---

### Post by epicoder on 2011-12-12
[http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/](http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/)
This article uses an older version of Ubuntu and a different theme, but it will still work.

---

### Post by kemtnbkr on 2011-12-14
Yes, as sh228's link says, ```
chmod +x file.jar
``` should make the file executable. 'chmod' is useful because you can do the same for read and write, plus being able to use a minus operator instead of a plus to remove read (r), write (w), and execute (x) file permissions.

---

### Post by hamstermoon on 2011-12-14
I have tried both of these; the terminal command just gets 'not recognised' and the actual .jar doesn even HAVE an option to make it executable. I am very confused :sad:.
 
What I AM going to do is go and get the other .jar file from my other computer and see if that behaves in the same way if I transfer it across!

---

### Post by Morbius1 on 2011-12-14
I have a slightly different perspective on this.

"How do I get a .jar file to become executable?" - You don't.

Java doesn't care or is even capable of determining if a given file is executable.

* Open up thunar as root:
```
gksu thunar
```and go to /usr/share/applications. 

* Right click on "OpenJDK Java 6 Runtime" > Launcher

* In the Command box you will see this:
> cautious-launcher %f /usr/lib/jvm/java-6-openjdk/bin/java -jarRemove the "cautious-launcher %f" so that it looks like this:
> /usr/lib/jvm/java-6-openjdk/bin/java -jarIt's cautious-launcher that's getting in the way not java.

---

### Post by Ma5abre on 2011-12-14
Hi there I have Ubuntu so I'm not 100% sure whether it will the same or not.

When you mention 'right clicking and telling it to run in Java'.

Do you mean that you have gone to 'properties' panel and clicked on the 'permissions' tab, then checked the box for 'allow executing file as program'?

---

### Post by hamstermoon on 2011-12-14
I have had a look at DimSum on Nubbin the Notebook running Maverick and yes, I could tick the box to make the .jar file executable.  On Xubuntu however, the window that opens when you click properties, does not have that option. What exactly is going on here, and why is there a difference?

---

### Post by gandaran on 2011-12-14
> **hamstermoon said:**
> I have had a look at DimSum on Nubbin the Notebook running Maverick and yes, I could tick the box to make the .jar file executable.  On Xubuntu however, the window that opens when you click properties, does not have that option. What exactly is going on here, and why is there a difference?
where is the file location, the file must be on a linux file system like you home folder.

---

### Post by hamstermoon on 2011-12-14
> **gandaran said:**
> where is the file location, the file must be on a linux file system like you home folder.

It is in my Documents folder both on the Notebook running Ubuntu and on this computer running Xubuntu.

---

### Post by pbrane on 2011-12-14
it's probably for security reasons that Ubuntu is not allowing jar files to be marked as executable. You can always run a jar file on the command line.
```

java -jar path/to/jarfile.jar

```

(Dimsum runs fine on my Xubuntu using the command line)

---

### Post by robgraves on 2011-12-14
> **pbrane said:**
> it's probably for security reasons that Ubuntu is not allowing jar files to be marked as executable. You can always run a jar file on the command line.
```

java -jar path/to/jarfile.jar

```

(Dimsum runs fine on my Xubuntu using the command line)

+1  This is what I use

---

### Post by hamstermoon on 2011-12-15
I will try that when I get home. Can you also possibly explain to me how to write a shell script for that so I don't have to keep tying into the Terminal??

---

### Post by Paqman on 2011-12-15
> **hamstermoon said:**
> I will try that when I get home. Can you also possibly explain to me how to write a shell script for that so I don't have to keep tying into the Terminal??

Easy peasy. Open a blank file and put:
```
#!/bin/bash
```
At the top. Then write your script, save and mark as executable. Job done.

---

### Post by pbrane on 2011-12-15
> **hamstermoon said:**
> I will try that when I get home. Can you also possibly explain to me how to write a shell script for that so I don't have to keep tying into the Terminal??

Like Paqman said. A shell script can simply be any shell commands you can type plus the 'sh-bang' at the top...

```

#!/bin/bash
  java -jar path/to/jarfile.jar

```

...would do it. You can add this to a menu or the desktop. Remember to mark your script as executable.

```

chmod u+x scriptname.sh

```

If you haven't done so already its handy to create a 'bin' directory in your $HOME directory. bash will look for that directory in it's path and if found can execute scripts in that directory without having to type the full path. Although inside a script you always want to use the full path to any files referenced.

---

### Post by hamstermoon on 2011-12-16
Having discussed this with a friend who knows more about Linux than I do I now understand it's a Nautilus versus Thunar problem. Nautilus allows you to change permissions via tick box and Thunar does not. I am going to talk to him a bit more about what to do! He said something about running somethign in the terminal that would make ALL .jar files executable.

---

### Post by Morbius1 on 2011-12-16
I'm going to try this one more time simply because I'm stubborn. 

jar files do not have to be executable to run. There is no way for Java to determine if a file has a Linux executable bit set. If you want to fix this so that you can run a jar file regardless of where it is located ( i.e., Linux filesystem, Windows filesystem. or CDROM ) then I would suggest fixing it at it's source by removing cautious-launcer from the java jar launcher. See post #5

---

### Post by pbrane on 2011-12-16
Making all jar files executable by defaultwill probably be a security risk. You should look into why jar files are not required to be marked as executable by default.

---

### Post by Morbius1 on 2011-12-16
"jar" is short for Java Archive. It is in itself not an executable entity. It contains files, libraries, meta-data and a bunch of other stuff. When run it starts the java runtime environment ( which is why there is a slight delay ) and everything at that point is passed to that environment.

Ubuntu created a launcher for the jar that contains "cautious-launcher" which checks to see if it has an executable bit set in an attempt at security. What they forgot is that this is Linux and the user will always find away around this impediment. You can run "java -jar" which will "execute" the jar even if it is not marked executable or you can fix it at it's source and remove "cautious-launcher" from the jar launcher.

---

### Post by hamstermoon on 2011-12-20
I seem to have got it to work. My friend suggest I put the .jar file in my home folder and then use 

> chmod +x file.jar

which had already been suggested.

It worked, now when I right click it executes, so I am going to have to write that down somewhere so I remember it!

---

### Post by bark50 on 2011-12-24
Thanks, Morbius, for being stubborn.  :lol:  Your solution worked for me.  Since I'm on Kubuntu, I had to use "kdesudo dolphin" to open the file manager and Kate to remove that cautious-launcher stuff.

---

### Post by UnbiasedMetal on 2013-04-19
> **Morbius1 said:**
> I have a slightly different perspective on this.

"How do I get a .jar file to become executable?" - You don't.

Java doesn't care or is even capable of determining if a given file is executable.

* Open up thunar as root:
```
gksu thunar
```and go to /usr/share/applications. 

* Right click on "OpenJDK Java 6 Runtime" > Launcher

* In the Command box you will see this:
Remove the "cautious-launcher %f" so that it looks like this:
It's cautious-launcher that's getting in the way not java.


after trying all the methods listed, this is the ONLY one that worked.  also, after searching other forums, and reading up on the Ubuntu Software Center, it is in fact, only  "cautious launcher" that is getting in the way.  however...  all that is needed is to remove the "cautious launcher" portion of the command line.
works just great now. 
this method places the control back into the users hands, where it ought to be.  excersize caution however, when opening untrusted, or previously unused files

---

### Post by QIII on 2013-04-19
Old thread.  Closed.

---

