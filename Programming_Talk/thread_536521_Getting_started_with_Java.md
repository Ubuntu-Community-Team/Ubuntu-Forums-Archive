---
title: "Getting started with Java"
date: 2007-08-27
forum: Programming Talk
---

### Post by DeathOnJuice on 2007-08-27
I'm taking a computer science class this year on Java, and the teacher seems to assume that everybody uses Windows. I am strictly an Ubuntu user now. Before we get started in class, I want to know a few things about setting up Java in Linux.

1. Which packages do what? I believe I only need sun-java6-jdk, but I'm curious what the uses of gcj and gij are.

2. What additional configuration do I need to do after install sun-java6-jdk? I've seem some outdated guide that say I need to run update-java-alternatives, and those that say I need to add "/usr/lib/jvm/java-6-sun" to the top of /etc/jvm. Do these apply to Feisty?

3. Could someone give me a quick example of compiling a simple program, both from the command line and an IDE?

4. Last, will I have any trouble moving my code from my Linux box at home to the Windows school computers? I know Java is known for its portability.

Thanks so much!

---

### Post by pmasiar on 2007-08-27
did you checked sticky?

---

### Post by DeathOnJuice on 2007-08-27
Yes, but as I said, there are outdated guides (Java 5 on Dapper) and conflicting advice involving the post-install configuration.

---

### Post by ryno519 on 2007-08-27
I note, for the love of god don't use netbeans 5.5. I don't know if it was just its Windows implementation or not, but that thing was so buggy and inconsistant it zapped me of my will to live.

---

### Post by Ragazzo on 2007-08-27
sun-java6-jdk is the package for compiling and sun-java6-jre is needed to run Java programs. You can also install sun-java6-source so that you can open the source file for a Java API class in an IDE if you're curious.

gij and and gcj are the GNU implementations which are not nearly as good as Sun's and you don't need them if you install sun-java6-jdk. 

If you don't run update-java-alternatives, your computer will use the GNU Java instead of Sun's Java (I believe this is still true for Feisty). At least it shouldn't do any harm to run it.

And the simple program (you need to save this file as Test.java):
```

public class Test {
 public static void main(String[] args) {
  System.out.println("hello");
 }
}

```

To compile: **javac Test.java**
To run: **java Test**

How to compile in an IDE depends on the IDE but there's nothing wrong about NetBeans 5.5 as far as I know.

---

### Post by rharriso on 2007-08-27
don't be a wuss, forget the IDE's all the GUI text editors colorize code for you anyway.

---

### Post by kknd on 2007-08-27
Follow Ragazzo instruction.

Please, lets focus on simple and objective answers like Ragazzo did. No IDE bashing to people that are just beginning.

---

### Post by DeathOnJuice on 2007-08-28
Thanks, everyone.

---

### Post by samjh on 2007-08-28
Sun has an excellent set of tutorials about Java programming.

Find it here: [http://java.sun.com/docs/books/tutorial/index.html](http://java.sun.com/docs/books/tutorial/index.html)

---

### Post by Tomosaur on 2007-08-28
You won't really need to worry about running your Java programs on Windows machines really.

In some cases, problems do present themselves, but these are mostly down to sloppy coding rather than inherent problems with Java. If and when you get onto file i/o, that's when you'll first have to actually think about cross-platform coding as a specific problem. Thankfully, Sun has recognised this, and so if you stick to the Java API rather than trying to build everything up from scratch, you'll have no trouble.

For the most part, a Java program written on Linux will run exactly the same on Windows as it does on the development machine. When you need to start doing stuff which depends on the platform (and, as I said before, the first time you're likely to come across this is when you start doing file i/o), then you should take a thorough read through of the API to find out whether there's already a solution available for you.

---

### Post by hod139 on 2007-08-28
> **DeathOnJuice said:**
> 
1. Which packages do what? I believe I only need sun-java6-jdk, but I'm curious what the uses of gcj and gij are.

gcj is the gnu java compiler.   It is not very good with its support of the java API (especially swing related API), and I suggest you stick with sun's implementation.

> 
2. What additional configuration do I need to do after install sun-java6-jdk? I've seem some outdated guide that say I need to run update-java-alternatives, and those that say I need to add "/usr/lib/jvm/java-6-sun" to the top of /etc/jvm. Do these apply to Feisty?

You still need to run ```

sudo update-java-alternatives -s java-6-sun
```
As for editing /etc/jvm, that depends.  Some java applications (e.g. eclipse) in the repositories do not obey the alternatives settings, and you must edit this file.  Some applications to obey the settings, and you do not have to edit it.

> 
3. Could someone give me a quick example of compiling a simple program, both from the command line and an IDE?

Ragazzo already showed how to compile from the command line.  If you want an IDE you can install eclipse.  Eclipse is one of those apps that is still disobeying the alternatives settings.  I have a howto though on how to install java and eclipse from the repositories: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

> 
4. Last, will I have any trouble moving my code from my Linux box at home to the Windows school computers? I know Java is known for its portability.

You should not have any problems, as long as the windows JRE is also version 1.6 (or 6.0 I never get Sun's versioning scheme).

---

### Post by Ramses de Norre on 2007-08-28
I've added this line in my ~/.bashrc :
```
export JAVA_HOME="/opt/java/jre/"
```
and all my java apps work flawlessly, this is not on ubuntu though so I'm not sure it'll work for you (and you'll probably need to change the path to somewhere in /usr/ too).

---

### Post by maxamillion on 2007-08-28
get a real editor ....  [http://www.vim.org/](http://www.vim.org/)

---

### Post by LaRoza on 2007-08-28
> **maxamillion said:**
> get a real editor ....  [http://www.vim.org/](http://www.vim.org/)

It is already installed, type vim in the terminal.

---

### Post by clem-vangelis on 2007-08-28
don't worry about portability , i'm actually doing some informatic studies and we were working on java , we do a project and my friend was using windows , the only problem you can have is the encoding of the source code... utf-8 for ubuntu and another thing for windows , just use something as notepad++ under windows

---

### Post by pmasiar on 2007-08-28
then learn [first vim session](http://bash.org/?795779) :-)

```

^C^C^X^X^X^XquitqQ!qdammit[esc]qwertyuiopasdfghjkl;:xwhat

```

---

### Post by CptPicard on 2007-08-28
That's nothing.

```

"Ed is the standard text editor."

Let's look at a typical novice's session with the mighty ed:

golem$ ed

?
help
?
?
?
quit
?
exit
?
bye
?
hello? 
?
eat flaming death
?
^C
?
^C
?
^D
?

---
Note the consistent user interface and error reportage.  Ed is
generous enough to flag errors, yet prudent enough not to overwhelm
the novice with verbosity.

```

---

### Post by aitorcalero on 2007-08-29
3. I will strongly recommend Eclipse as IDE
4. javac command is what you need to compile, but if you use an IDE you do not need to worry about that.

---

### Post by Xanderfoxx on 2007-11-23
I'm used to the Redmond implementation of Java SE with an IDE called [[COLOR="Blue"]JCreator LE[/COLOR]]("http://www.jcreator.com/"), so I'm definitely used to ease and convenience of use, and a decent GUI eye-candied development platform.

I just want to let you guys know, I haven't yet lost faith in Ubuntu's superiority as a Java SE development platform.

I want to learn how!

Teach me to way of the Jed - I mean -  Ubuntu Java development!

---

### Post by LaRoza on 2007-11-23
> **maurin.alex@gmail.com said:**
> 
Teach me to way of the Jed - I mean -  Ubuntu Java development!

Since Java runs in the JVM, there should be no difference. You can use Eclipse, Netbeans or other IDE's, although I prefer not to.

Compiling and running is exactly the same.

```

sudo aptitude install sun-java6-jdk

```

---

