---
title: "[SOLVED] Problems with running .class files"
date: 2008-01-19
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-01-19
I tried to run HelloWorld.class, and that happened:
> arho@ohra-desktop:~$ java /home/arho/Asiakirjat/HelloWorld.class
Exception in thread "main" java.lang.NoClassDefFoundError: /home/arho/Asiakirjat/HelloWorld/class
arho@ohra-desktop:~$ 
What to do? Whats the error? And was my command even correct?
I tried to search other topics but there are no answers in them.
Edit: 
I forgot to tell you, that the HelloWorld thing has the following, 
in case that the problem is in the code:
> //helloworld application
public class HelloWorld
{
  public static void main(String[] args)
    {
    System.out.println("Hello World!");
    }
}
Thanks for your help.

---

### Post by Lord Illidan on 2008-01-19
Go into your /home/arho/Asiakirjat/HelloWorld/ directory from the console and type ls to see where is the location of the class file. Might be a good idea to run it from the current directory.

---

### Post by crazyfuturamanoob on 2008-01-19
How can I go to a certain directory in terminal?
I think it's: /folder/subfolder/destination
But Im not sure.
Edit:
I tried that, but I think it didn't work:
> 
arho@ohra-desktop:~$ /home/arho/Asiakirjat
bash: /home/arho/Asiakirjat: is a directory
arho@ohra-desktop:~$ Is
bash: Is: command not found
arho@ohra-desktop:~$ |s
bash: syntax error near unexpected token `|'
arho@ohra-desktop:~$ 

Edit2:
I also tried to run it on my cellphone, but it couldn't open it.

---

### Post by crazyfuturamanoob on 2008-01-19
I want to be able to run java app on my cellphone, how?

---

### Post by CptPicard on 2008-01-19
The "java" command doesn't run a "file" per se, it runs a class with a "main" method, and the class has to be on the classpath. So if we suppose that you've got the class in the current directory and there is no package  being used, the command is "java HelloWorld". The current directory is already automagically in the classpath... if you had packages in use, so from current directory the .class would be in something like your/package/here/HelloWorld, then the command would be "java your.package.here.HelloWorld".

---

### Post by crazyfuturamanoob on 2008-01-19
I didn't understand a sinlge word of that.
What is classpath? Could you say it in english, please?
Like whats wrong with "java HelloWorld"? It gives an error.
And how I can run java apps on my cellphone?
How can I create .jar files?

---

### Post by LaRoza on 2008-01-19
> **crazyfuturamanoob said:**
> I didn't understand a sinlge word of that.
What is classpath? Could you say it in english, please?
Like whats wrong with "java HelloWorld"? It gives an error.
And how I can run java apps on my cellphone?
How can I create .jar files?

Sounds like you want a lot.

For so many questions, I would check the documentation, the man pages, and the cellphone documentation.

---

### Post by CptPicard on 2008-01-19
> **crazyfuturamanoob said:**
> I didn't understand a sinlge word of that. ... Could you say it in english, please?

Ok, let's try it again... or maybe in Finnish, just noticed. Terve ;)

> What is classpath?

"Classpath" is a kind of abstract hierarchical namespace "directory structure" that the JVM uses to locate classes, as being multiplatform, it can't really rely on the filesystem to do that. You define the classpath (either explicitly giving the -cp switch to java or defining the CLASSPATH system variable), after which the JVM knows where to look to find the classes.

The current directory is always automatically on the classpath. The parameter of the java runtime is the *fully-qualified name* of the class *in terms of the classpath*, not a filename. So "java HelloWorld" should work here provided that your HelloWorld.class file is in the current directory. If you're getting an error I'd like to see it...

For the rest of the questions, figure those out in due time, learning about the Java classpath mechanism seems like the first thing you need to do :)

---

### Post by crazyfuturamanoob on 2008-01-20
I tried once again to check the classpath with that command:
> root@ohra-desktop:/home/arho# /home/arho/Asiakirjat/HelloWorld.class Is
bash: /home/arho/Asiakirjat/HelloWorld.class: Permission denied
root@ohra-desktop:/home/arho# /home/arho/Asiakirjat/HelloWorld.class
bash: /home/arho/Asiakirjat/HelloWorld.class: Permission denied

Didn't work. Note: I was on root user. What went wrong?

I want an exact command, how to run .class or .jar files, 
not complicated explanations.
edit:
Solved!
> arho@ohra-desktop:~$ cd /home/arho/Asiakirjat
arho@ohra-desktop:~/Asiakirjat$ Is
bash: Is: command not found
arho@ohra-desktop:~/Asiakirjat$ ls
HelloWorld.class  HelloWorld.java  HelloWorld.java~
arho@ohra-desktop:~/Asiakirjat$ java HelloWorld
Hello World!
arho@ohra-desktop:~/Asiakirjat$ Gee!

---

### Post by CptPicard on 2008-01-20
Uh, those commands are certainly nonsense. The Java classpath is a JVM parameter that tells where to find the classes. I really recommend you Google for the concept if I am not managing to make it clear, understanding it is pretty crucial for a Java programmer.

[http://www.kevinboone.com/classpath.html](http://www.kevinboone.com/classpath.html)

[http://mindprod.com/jgloss/classpath.html](http://mindprod.com/jgloss/classpath.html)

For your specific example... first, don't be root, it's Bad in general. Otherwise, from the exact situation you were in:

```

cd Asiakirjat
java HelloWorld

```

---

