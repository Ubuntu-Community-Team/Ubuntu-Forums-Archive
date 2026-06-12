---
title: "(java) I don't know what this means......"
date: 2007-08-02
forum: Programming Talk
---

### Post by Immolatus on 2007-08-02
I hate to bother you guy's with something that is probably pretty simple, but can someone please explain the errors to me and what to do(I'm beginning to learn java). Thanks in advance.

rooster@kurgan:~$ javac hellojava.java
hellojava.java:2: cannot find symbol
symbol  : class string
location: class hellojava
public static void main(string[]args ) {
                        ^
hellojava.java:3: package system does not exist
      system.out.println("Hello, java!");
            ^
2 errors
rooster@kurgan:~$

---

### Post by Ramses de Norre on 2007-08-02
You should post the code....
I can tell you've written "system" instead of "System" (probably for println) and "string" instead of "String".
An example:
```

public class HelloWorld
{
    public static void main(String[] args)
    {
        System.out.println("Hello World!");
    }
}

```

---

### Post by pmasiar on 2007-08-02
i know Java is widely used in commercial programming... But for self-learner, IMNSHO you are *far* better off learn Python first. Much easier to learn basics, try expressions in Python shell, etc. *Then* you can switch to Java, most  basic concepts are the same (only more strict and complicated in Java).

Wiki in my sig has many resources, free online books, and training tasks

---

### Post by hod139 on 2007-08-02
Java is case sensitive.  For example, string should be String and system should be System.  It will be hard to debug other errors without showing some code.

---

### Post by Immolatus on 2007-08-02
Doh!! You guy's were exactly right. I'm coming from html, where everything now is lower case. I'll have to pay more attention to the examples.

Thanks.

I had another question though. I'm using the SDK from the repos as I couldn't figure out how to set up the JDK so that it would compile (javac not a command error).
I guess you have to put javac "in your path".

Sounds simple enough.....just install to /usr/local as root to make it system wide. Turns out all the how-to's I found were for wintrash.

All that having been said, Is there a simple enough solution to "putting it in my path"? I'd just like to know how. I don't like being Dependant on the repos.

Thanks again.

---

### Post by AlexThomson_NZ on 2007-08-03
> **Immolatus said:**
> All that having been said, Is there a simple enough solution to "putting it in my path"? I'd just like to know how. I don't like being Dependant on the repos.

Thanks again.

I'm the same in that I rather install the JDK manually rather than the repos.

If you have installed the JDK in the /usr/local directory, just add these lines to the end of your .bashrc file:
```

export JAVA_HOME=/usr/local/jdk1.5.0_12
export PATH=$JAVA_HOME/bin:$PATH

```

---

### Post by Immolatus on 2007-08-03
the jdk I'm using is jdk1.6.0_02 thats ok right?

---

### Post by jay019 on 2007-08-03
Yeah, should be fine. Just means your .bashrc should have...
```

export JAVA_HOME=/usr/local/jdk1.6.0_02
export PATH=$JAVA_HOME/bin:$PATH

```

Good luck learning java, I started this year and have found it to be a lot of fun.

---

### Post by steve.horsley on 2007-08-05
Personally, I add these two symlinks to /usr/local/bin which overrides whatever is in /usr/bin and doesn't get changed back again next time Ubuntu has a software update:
> steve@StevesPC:~$ ls -l /usr/local/bin/j*
lrwxrwxrwx 1 root root 24 2007-07-08 00:36 /usr/local/bin/jar -> /opt/jdk1.6.0_02/bin/jar
lrwxrwxrwx 1 root root 25 2007-07-08 00:36 /usr/local/bin/java -> /opt/jdk1.6.0_02/bin/java
lrwxrwxrwx 1 root root 26 2007-07-08 00:36 /usr/local/bin/javac -> /opt/jdk1.6.0_02/bin/javac

---

### Post by Immolatus on 2007-08-05
> **steve.horsley said:**
> Personally, I add these two symlinks to /usr/local/bin which overrides whatever is in /usr/bin and doesn't get changed back again next time Ubuntu has a software update:

Cool , I'll try this. Modifying .bashrc didn't fix anything for me, and I'm under the impression that gcc might interfere with javac, so this might fix that correct?

Either way i'll try it. For now I've got jdk-6u2 working with netbeans. So would your suggestion allow me to use the command line instead?

I'd really like to learn the bare bones technique first.

Thanks.

---

### Post by hesham87 on 2007-08-05
Guys i use java pretty good but in windows and in fact i cant use in Ubuntu ( Linux) so any help i can help in programming ?
but i need steps to start programming in Ubuntu i even get "Java Programming on Linux " book
but you know 
i need Some help

---

### Post by steve.horsley on 2007-08-06
> **hesham87 said:**
> Guys i use java pretty good but in windows and in fact i cant use in Ubuntu ( Linux) so any help i can help in programming ?
but i need steps to start programming in Ubuntu i even get "Java Programming on Linux " book
but you know 
i need Some help

I don't understand what your problem is here. Since this thread seems about finished, perhaps you should start a new thread with a good description of the problem.

---

### Post by Immolatus on 2007-08-06
Update....Modifying .bashrc did fix my problem, I just didn't know you had to log out and then back in for it to take effect. So yeah, it's working now ,thanks again.:guitar:

---

### Post by AlexThomson_NZ on 2007-08-06
> **steve.horsley said:**
> Personally, I add these two symlinks to /usr/local/bin which overrides whatever is in /usr/bin and doesn't get changed back again next time Ubuntu has a software update:

^ This is better practice than my hack ;)

---

