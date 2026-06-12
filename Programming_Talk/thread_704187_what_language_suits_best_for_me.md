---
title: "what language suits best for me?"
date: 2008-02-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-02-22
I want some suggestions, 
that what language would suit best for me.

I want something like this:
 -not too difficult
 -free
 -able to make .exe files
 -good for game/gui development

My opinion is C++, but there aren't free
compilers for it. Thanks for any replies.

---

### Post by lnostdal on 2008-02-22
uh, yes .. there are free compilers for c and c++ (how do you think we built the c / c++ software running on ubuntu? - and the linux kernel?) ... just see the stickies at the top of the forum .. GCC is by far the most used compiler for c/c++

> 
-not too difficult

yes: python, java
no: c and c++

> 
-free

all of the ones mentioned in this post

> 
-able to make .exe files

this is not important -- ignore it (#1)

> 
-good for game/gui development


all of the ones mentioned in this post


#1: some might say that it is, but they are wrong .. it's an illusion .. it's like worrying about make-up when you're about to go scuba diving .. ignore them .. it is the wrong question .. you should instead be asking "how do i distribute my software written in xxxxx?"

---

### Post by Lster on 2008-02-22
Hi

From Wikipedia on .EXE:

[QUOTE=Wikipedia]EXE is the common filename extension for denoting an executable file (a program) in the OpenVMS, DOS, Microsoft Windows, ReactOS, and OS/2 operating systems.[/QUOTE]

So, what platform are you targeting?

You may want to look into Python (although it might not do everything you want) and read this:

[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

---

### Post by crazyfuturamanoob on 2008-02-22
Im targeting linux.
Why it isn't important to make exes?
Every prog I see is exe. I don't need to 
type "java program.class" or "python hello.py"
for every exe. I want to make apps that can be 
launched by a single mosue click.
Python would be my language, if I'd know how to use
cxFreeze.

---

### Post by stratavarious on 2008-02-22
.

---

### Post by Caduceus on 2008-02-22
If it's a .py file it's not an executable file per se. Only the OS's listed above can make literally ".exe" files, all others can execute but use different file extensions.

---

### Post by Lster on 2008-02-22
[QUOTE=Caduceus]Only the OS's listed above can make literally ".exe" files, all others can execute but use different file extensions.[/QUOTE]

[QUOTE=Wikipedia]The KDE and GNOME desktop environments associate a MIME Content-type with a file by examining both the filename suffix and the contents of the file, in the fashion of the file command, as a heuristic. They choose the application to launch when a file is opened based on the MIME Content-type, reducing the dependency on filename extensions. Mac OS X uses both filename extensions and mime types, as well as file type codes, to select a Uniform Type Identifier by which to identify the file type internally.[/QUOTE]

[http://en.wikipedia.org/wiki/File_extension#Relation_to_Internet_content_types](http://en.wikipedia.org/wiki/File_extension#Relation_to_Internet_content_types)

:)

---

### Post by lnostdal on 2008-02-22
> I want to make apps that can be launched by a single mosue click.

right, and why do you assume this is not possible?

for CLI:

```

lars@ibmr52:~/programming/java$ cat Hello.java
public class Hello {
  public static void main(String args[])
  {
    System.out.println("Hello World!");
  }
}


lars@ibmr52:~/programming/java$ javac Hello.java
lars@ibmr52:~/programming/java$ cat Hello
#!/bin/bash

java Hello
lars@ibmr52:~/programming/java$ chmod +x Hello
lars@ibmr52:~/programming/java$ ./Hello
Hello World!
lars@ibmr52:~/programming/java$ 

```

for GUI:

```

lars@ibmr52:~/programming/java$ cat HelloWorldSwing.java
/*
 * HelloWorldSwing.java requires no other files. 
 */
import javax.swing.*;        

public class HelloWorldSwing {
  /**
   * Create the GUI and show it.  For thread safety,
   * this method should be invoked from the
   * event-dispatching thread.
   */
  private static void createAndShowGUI()
  {
    //Create and set up the window.
    JFrame frame = new JFrame("HelloWorldSwing");
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    
    //Add the ubiquitous "Hello World" label.
    JLabel label = new JLabel("Hello World");
    frame.getContentPane().add(label);
    
    //Display the window.
    frame.pack();
    frame.setVisible(true);
  }
  
  public static void main(String[] args)
  {
    //Schedule a job for the event-dispatching thread:
    //creating and showing this application's GUI.
    javax.swing.SwingUtilities.invokeLater(new Runnable() {
        public void run()
        {
          createAndShowGUI();
        }
      });
  }
}
lars@ibmr52:~/programming/java$ javac HelloWorldSwing.java 
lars@ibmr52:~/programming/java$ cat HelloWorldSwing.desktop
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=HelloWorldSwing
Exec=java -cp /home/lars/programming/java HelloWorldSwing
Name=HelloWorldSwing
Icon=gnome-panel-launcher

```

place *HelloWorldSwing.desktop* in your *~/Desktop* folder if you wish (it can be placed anywhere of course) .. and click on it

edit: ..to get rid of the "magic-string" (/home/lars ... above) just pack your java-software in a jar..

---

### Post by lnostdal on 2008-02-22
.. and the same works for python also .. or *anything* really .. so reread my post above about ignoring people who goes "omg!!111!! it needzors to be an exefilz!!!11" ..... x)

---

### Post by LaRoza on 2008-02-22
If it is important to be an exe (for whatever reason), you can make exe's out of Python (and probably the others). (You can also use Freeze and probably others)

This is really not needed.

[http://www.py2exe.org/](http://www.py2exe.org/)

---

### Post by pmasiar on 2008-02-22
Pygame (and Python) is easiest way to program games using general programming language. Way simpler than any C/C++/Java. Only Game Maker or eToys are easier, but they use own way, not a common PL.

.EXE files run on Windows, but not on Linux. There are other ways to make cross-platform programs and make them executable by mouseclick. You will learn it later.

See wiki in my sig for links to learn Python.

---

### Post by a9bejo on 2008-02-24
Hi crazyfuturamanoob,

> **crazyfuturamanoob said:**
> 
I want to make apps that can be 
launched by a single mosue click.


That is the job of the operating system you run your program on, not the programming language. This means that **you can make executables that can be started with a mouse click out of any program you want**, no matter which programming language or even which software platform you used to create it. 

> 
Why it isn't important to make exes?


You mean executables. The filename extension .exe is only used on windows and only rarely seen on unix and linux systems.

> **crazyfuturamanoob said:**
> 
Every prog I see is exe. 


There is no .exe for this forum software you just used, or for the Google search application or the amazon.com application.  You do not double click on a exe file to make a phone call, right?  Well, there are a lot of software programs involved when making a phone call, and most of them are started by moving a zip file in a directory that is observed by an application server, not by clicking on a .exe file.  You do not start driving a car by double clicking on a .exe file.

**Only a fraction of the software you use runs on your desktop computer.**

> 
I don't need to 
type "java program.class" or "python hello.py"
for every exe.

if you put "java program" in a file and make that executable, you have an linux "exe".  If you put your java programs into an executable jar file, you can double click it in windows and gnome like an .exe file.  There is a tool that makes windows-executables (.exe) for java programs if you like. If you add a [shebang](http://en.wikipedia.org/wiki/Shebang_%28Unix%29) line to your python script, your users will not see any difference between your script and any other program they use.

If you want to start learning how to program, please don't think about how you gonna write you super useful game that you always wanted to play.  In the next few years, most of the code you produce will be ugly and unmaintainable, because you did not learn how to design good software yet.  You learn this by reading books and writing lots of very small programs that you will most likely never use again a year after you finished them.  

Start with a language that is **as abstract as possible**, so you can focus on learning how to write and design programs. On these forums, the preferred language for this is usually Python.  There are many other choices that are just as good, but I also know of no reason not to use Python.   The only really important thing is that you have fun coding in that language, because you will use it for quite some time.  Then learn C, so you see how to program close to  the machine.  Also learn about the different strategies to **design** software, and how to solve complex problems by building abstractions around them. 

Read [Teach Yourself Programming in Ten Years](http://norvig.com/21-days.html).  Read [SICP](http://mitpress.mit.edu/sicp/full-text/book/book.html). Read [Code Complete](http://cc2e.com/). Read [The Pragmatic Programmer](http://www.amazon.com/Pragmatic-Programmer-Journeyman-Master/dp/020161622X).

Then you can evaluate what tools you want to use to make your programs and learn them.

---

