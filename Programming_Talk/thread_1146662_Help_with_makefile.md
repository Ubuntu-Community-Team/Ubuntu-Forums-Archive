---
title: "Help with makefile"
date: 2009-05-02
forum: Programming Talk
---

### Post by 2Real on 2009-05-02
Hi, I'm trying to write a make file for my project for my class and I'm running into a problem and I'm not sure how to fix it.

the structure of my program is as follows


[LIST=1]
[*]src - source folder
[LIST=1]
[*]instructions - package
[*]sparcInstructions - package
[*]src - package (our sources files this was originally default package but we soon realized that was a bad idea)
[/LIST]
[/LIST]
our makefile is in the src package and when we try to run it we get these errors

make                                                                                                                                 
 rm -f -R *.class antlr.generated*                                                                                                                                               
 java org.antlr.Tool Evil.g                                                                                                                                                      
 java org.antlr.Tool EvilTree.g                                                                                                                                                  
 java org.antlr.Tool EvilCFG.g                                                                                                                                                   
 touch antlr.generated.evil                                                                                                                                                      
 touch antlr.generated                                                                                                                                                           
 javac *.java                                                                                                                                                                    
 BasicBlock.java:4: package instructions does not exist                                                                                                                          
 import instructions.Instruction;                                                                                                                                                
                    ^                                                                                                                                                            
 BasicBlock.java:6: package sparcInstructions does not exist                                                                                                                     
 import sparcInstructions.SparcInstruction;

I'm trying to figure out why this works inside of Eclipse, but it explodes when we try to run the makefile.

btw this is our makefile

FILES=Evil.java
 
 
 Evil.class : antlr.generated ${FILES}
 
javac *.java
 
 antlr.generated: antlr.generated.evil
 
touch antlr.generated
 
 antlr.generated.evil : clean Evil.g
 
java org.antlr.Tool Evil.g
 
java org.antlr.Tool EvilTree.g
 
java org.antlr.Tool EvilCFG.g
 
touch antlr.generated.evil
 
 safe:
 
\cp *.g *.java ~/.431
 
 clean:
 
rm -f -R *.class antlr.generated*

This is my first big project so I'm pretty noob when it comes to all of this.

Thanks

---

### Post by dwhitney67 on 2009-05-02
There are at least 1001 things one can do with a Makefile.  What is it that you are attempted to do?

If it merely to compile a Java file, then the following, basic Makefile, may satisfy your needs:
```

SRCS = $(wildcard *.java)

all:
        javac $(SRCS)

clean:
        $(RM) *.class

```

---

### Post by 2Real on 2009-05-02
> **dwhitney67 said:**
> There are at least 1001 things one can do with a Makefile.  What is it that you are attempted to do?

If it merely to compile a Java file, then the following, basic Makefile, may satisfy your needs:
```

SRCS = $(wildcard *.java)

all:
        javac $(SRCS)

clean:
        $(RM) *.class

```

i'm trying to compile my whole project but i can't figure out how to "tell" javac where my instruction packages are

---

### Post by Neheb on 2009-05-02
the -sourcepath option for javac *might* be what you are looking for to get javac to know where the stuff is, but I haven't used makefiles for java.

You could also take a look at the VPATH variables in makefiles.

---

### Post by dwhitney67 on 2009-05-02
Since I do not have your project to experiment with, trying see if either the -classpath or the -sourcepath options will work for your 'javac' statement.

These options require the path for your additional code (instructions?).

So in your top-level src directory, something like the following may work:
```

javac -classpath . `find src -name *.java`

```
Note, if the low-level src directory does not have subdirectories, then this may suffice:
```

javac -classpath . src/*.java

```

---

### Post by 2Real on 2009-05-02
> **Neheb said:**
> the -sourcepath option for javac *might* be what you are looking for to get javac to know where the stuff is, but I haven't used makefiles for java.

You could also take a look at the VPATH variables in makefiles.
i'll fool around with sourcepath and see what i get

---

### Post by 2Real on 2009-05-02
> **dwhitney67 said:**
> Since I do not have your project to experiment with, trying see if either the -classpath or the -sourcepath options will work for your 'javac' statement.

These options require the path for your additional code (instructions?).

So in your top-level src directory, something like the following may work:
```

javac -classpath . `find src -name *.java`

```Note, if the low-level src directory does not have subdirectories, then this may suffice:
```

javac -classpath . src/*.java

```

since my instructions and sparcInstructions need to be compiled also do i need to do

javac -classpath . src/instructions/*.java . src/sparcInstructions/*.java . src/src/*.java

i've never done this before. Does that makes sense at all?

---

### Post by dwhitney67 on 2009-05-02
> **2Real said:**
> since my instructions and sparcInstructions need to be compiled also do i need to do

javac -classpath . src/instructions/*.java . src/sparcInstructions/*.java . src/src/*.java

i've never done this before. Does that makes sense at all?

Everything looks good, except for the repeat dots (.); you only require one after the -classpath.

---

### Post by 2Real on 2009-05-02
> **dwhitney67 said:**
> Everything looks good, except for the repeat dots (.); you only require one after the -classpath.


i changed the line of my makefile to this

javac -classpath . ../instructions/*.java ../sparcInstructions/*.java *.java


i put in the ..'s because those folders are 1 dir up and the makefile is current in my src/src folder

however it seems i've broken more in my code now


javac -classpath . ../instructions/*.java ../sparcInstructions/*.java *.java
DottedTree.java:3: package org.antlr.runtime does not exist
import org.antlr.runtime.*;
^
DottedTree.java:4: package org.antlr.runtime.tree does not exist
import org.antlr.runtime.tree.*;
 
do i need to include things now that should have been in my classpath?

---

### Post by dwhitney67 on 2009-05-02
Forget the Makefile for now; try to see if you can run that javac command from the command-line.

And furthermore, try running the command from the top-level src directory.

I just want to know if it works before trying anything more elaborate.

---

### Post by 2Real on 2009-05-02
> **dwhitney67 said:**
> Forget the Makefile for now; try to see if you can run that javac command from the command-line.

And furthermore, try running the command from the top-level src directory.

I just want to know if it works before trying anything more elaborate.


  here are some of the errors i get from just running the command 


javac -classpath ./instructions/*.java ./sparcInstructions/*.java ./src/*.java
./src/DottedTree.java:3: package org.antlr.runtime does not exist
import org.antlr.runtime.*;
^
./src/DottedTree.java:4: package org.antlr.runtime.tree does not exist
import org.antlr.runtime.tree.*;
^
./src/DottedTree.java:7: cannot find symbol
symbol: class CommonTree
   extends CommonTree

---

### Post by dwhitney67 on 2009-05-02
I just experimented with a setup like the following:

```

                     src
                      +
                      |
    +-----------------+----------+
    |                 |          |
instructions         src      Makefile
    |                 |
 One.java          Two.java

```

Here, Two.java instantiates a One object, and calls a One method.

The Makefile looks like:
```

SRCS = $(wildcard instructions/*.java src/*.java)
CLS  = $(SRCS:.java=.class)

all:
	javac -classpath . $(SRCS)

clean:
	$(RM) $(CLS)

```
... and it works.

To run Two.class:
```

cd src
java -classpath ../instructions:../src Two

```

---

### Post by 2Real on 2009-05-02
> **dwhitney67 said:**
> I just experimented with a setup like the following:

```

                     src
                      +
                      |
    +-----------------+----------+
    |                 |          |
instructions         src      Makefile
    |                 |
 One.java          Two.java

```Here, Two.java instantiates a One object, and calls a One method.

The Makefile looks like:
```

SRCS = $(wildcard instructions/*.java src/*.java)
CLS  = $(SRCS:.java=.class)

all:
    javac -classpath . $(SRCS)

clean:
    $(RM) $(CLS)

```... and it works.

To run Two.class:
```

cd src
java -classpath ../instructions:../src Two

```


ok that seemed to work for my java files but i still have trouble with my ANTLR files

import org.antlr.runtime.*;
^
src/DottedTree.java:4: package org.antlr.runtime.tree does not exist
import org.antlr.runtime.tree.*;

---

### Post by dwhitney67 on 2009-05-02
Sorry, you have not mentioned where you keep your ANTLR code (specifically the jar file, if any).

Anyhow, if you have an ANTLR jar file (e.g. antlr.jar), then the path leading to this jar and the jar-filename itself, need to be added to the classpath.

For example:
```

javac -classpath .:/some/path/antlr.jar $(SRCS)

```

P.S.  I have never used ANTLR, so you may need to read the appropriate documentation on how to build your app with it.

---

### Post by 2Real on 2009-05-02
> **dwhitney67 said:**
> Sorry, you have not mentioned where you keep your ANTLR code (specifically the jar file, if any).

Anyhow, if you have an ANTLR jar file (e.g. antlr.jar), then the path leading to this jar and the jar-filename itself, need to be added to the classpath.

For example:
```

javac -classpath .:/some/path/antlr.jar $(SRCS)

```P.S.  I have never used ANTLR, so you may need to read the appropriate documentation on how to build your app with it.
  ah ok i'll play around with that

---

### Post by 2Real on 2009-05-03
what do i need to do to import a jar from /usr/share/java/

i have this for one of my jars

javac -classpath . /usr/share/java/antlr-runtime-3.13.jar $(SRCS)

but it's not working

---

### Post by dwhitney67 on 2009-05-03
> **2Real said:**
> what do i need to do to import a jar from /usr/share/java/

i have this for one of my jars

javac -classpath . /usr/share/java/antlr-runtime-3.13.jar $(SRCS)

but it's not working

Individual paths that are specified as part of the classpath are separate by a colon ':', not a white-space.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> Individual paths that are specified as part of the classpath are separate by a colon ':', not a white-space.

ok i have my makefile working except the clean part 
it doesn't seem to actually be deleting all my class files and i'm getting errors because of it 

it deletes the normal .class files but it's not deleting class files like these

EvilCFG$lvalue_return.class
EvilLexer$DFA6.class
EvilParser$arg_list_return.class
....
etc

this is my makefile now

FILES=Evil.java
SRCS = $(wildcard instructions/*.java sparcInstructions/*.java src/*.java ./*.java)
CLS = $(SRCS:.java=.class)

Evil.class : antlr.generated ${FILES}
    javac -classpath .:/usr/share/java/antlr-runtime-3.13.jar:/usr/share/java/antlrworks-1.2.3.jar:$(SRCS)

antlr.generated: antlr.generated.evil
    touch antlr.generated

antlr.generated.evil : clean Evil.g
    java org.antlr.Tool Evil.g
    java org.antlr.Tool EvilTree.g
    java org.antlr.Tool EvilCFG.g
    touch antlr.generated.evil

safe:
    \cp *.g *.java ~/.431

clean:
    $(RM) $(CLS)

---

### Post by dwhitney67 on 2009-05-03
It would be awesome if you would post your code (including Makefiles) within code-blocks.  The next time you reply or start a new post, highlight your code, then click on the # mark at the top of the edit-box.

As for your Makefile, it looks fine to me.  What value does it see for $(CLS).  To find out, insert this as your first entry-point in the Makefile... and then run 'make':
```

FILES=Evil.java
SRCS = $(wildcard instructions/*.java sparcInstructions/*.java src/*.java ./*.java)
CLS = $(SRCS:.java=.class)

foo:
        @echo $(CLS)
...

```

You should see a list of all of your .class files.

P.S.  ALWAYS perform the suggestion I show above when developing a Makefile.  It would royally suck if you screw something up and remove all of your .java files!

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> It would be awesome if you would post your code (including Makefiles) within code-blocks.  The next time you reply or start a new post, highlight your code, then click on the # mark at the top of the edit-box.

As for your Makefile, it looks fine to me.  What value does it see for $(CLS).  To find out, insert this as your first entry-point in the Makefile... and then run 'make':
```

FILES=Evil.java
SRCS = $(wildcard instructions/*.java sparcInstructions/*.java src/*.java ./*.java)
CLS = $(SRCS:.java=.class)

foo:
        @echo $(CLS)
...

```You should see a list of all of your .class files.

P.S.  ALWAYS perform the suggestion I show above when developing a Makefile.  It would royally suck if you screw something up and remove all of your .java files!


oh sorry about that 

i fixed the clean problem but i'm having trouble now running my file

i do 
```
java Evil <input file name>
```

and i get this error 

Exception in thread "main" java.lang.NoClassDefFoundError: Evil (wrong name: src/Evil)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: Evil.  Program will exit.


I see Evil.class in that folder.

---

### Post by dwhitney67 on 2009-05-03
The main issue when scattering your .java files all over the place is the configuring the CLASSPATH appropriately, which can sometimes be a pain.

Another alternative is to define your own class package, and then to collect all of the .class files into a jar file.  Then the CLASSPATH becomes a little easier to define.

Either way, it seems that you are not that familiar with the CLASSPATH, nor its importance when it comes to compiling java files, nor when it comes to running a java app.  This has got to change.

As an example, I have included a small/trivial project that contains two separate .java files.  They are organized into a directory structure that resembles their package name, which I conjured up; it is org.acme.project.  From there, there is a .app and a .util.

This is the typical layout for a company, in this case the Acme Non-Profit Organization, to organize their "special" project.

Anyhow, take a look at the tarfile which I have attached.  It contains a Makefile, which supports entry points for building the jar file, cleaning the mess when you are done, and running the app (which in this case, does nothing).  See if you can adopt this to your project.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> The main issue when scattering your .java files all over the place is the configuring the CLASSPATH appropriately, which can sometimes be a pain.

Another alternative is to define your own class package, and then to collect all of the .class files into a jar file.  Then the CLASSPATH becomes a little easier to define.

Either way, it seems that you are not that familiar with the CLASSPATH, nor its importance when it comes to compiling java files, nor when it comes to running a java app.  This has got to change.

As an example, I have included a small/trivial project that contains two separate .java files.  They are organized into a directory structure that resembles their package name, which I conjured up; it is org.acme.project.  From there, there is a .app and a .util.

This is the typical layout for a company, in this case the Acme Non-Profit Organization, to organize their "special" project.

Anyhow, take a look at the tarfile which I have attached.  It contains a Makefile, which supports entry points for building the jar file, cleaning the mess when you are done, and running the app (which in this case, does nothing).  See if you can adopt this to your project.

Am I not allowed to "concatenate" my different build paths when using javac?
I'm sorry about this this is the first time I've done this so it's all new.

This is my makefile now.

```
FILES=Evil.java
SRCS = $(wildcard instructions/*.java sparcInstructions/*.java src/*.java ./*.java)
ANTLR = $(wildcard /usr/share/java/antlr-runtime-3.1.3.jar /usr/share/java/antlrworks-1.2.3.jar)
CLS = $(wildcard instructions/*.class sparcInstructions/*.class src/*.class ./*.class)
APP = EVIL
JAR = $(APP).jar

all: $(JAR)

$(JAR) : antlr.generated ${FILES}
    javac -classpath . $(ANTLR):$(SRCS)
    jar -cf $(JAR) $(CLS);

antlr.generated: antlr.generated.evil
    touch antlr.generated

antlr.generated.evil : clean Evil.g
    java org.antlr.Tool Evil.g
    java org.antlr.Tool EvilTree.g
    java org.antlr.Tool EvilCFG.g
    touch antlr.generated.evil

safe:
    \cp *.g *.java ~/.431

clean:
    $(RM) $(CLS)
```

and this is the error it generates 

```
javac: invalid flag: /usr/share/java/antlr-runtime-3.1.3.jar
Usage: javac <options> <source files>
use -help for a list of possible options
make: *** [EVIL.jar] Error 2

```

---

### Post by dwhitney67 on 2009-05-03
I feel like the solution is digressing back to the state you left off yesterday.  Please fix this statement:
```

    javac -classpath . $(ANTLR):$(SRCS)

```
to be
```

    javac -classpath .:/usr/share/java/antlr-runtime-3.13.jar:/usr/share/java/antlrworks-1.2.3.jar $(SRCS)

```
In an effort to reduce typing mistakes, please copy/paste what you see above.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> I feel like the solution is digressing back to the state you left off yesterday.  Please fix this statement:
```

    javac -classpath . $(ANTLR):$(SRCS)

```to be
```

    javac -classpath .:/usr/share/java/antlr-runtime-3.13.jar:/usr/share/java/antlrworks-1.2.3.jar $(SRCS)

```In an effort to reduce typing mistakes, please copy/paste what you see above.

I fixed that line and now the jar generates but i only have 4 of my class files and it doesn't show the instructions or sparcInstructions folders.

Shouldn't this 

```
CLS = $(wildcard instructions/*.class sparcInstructions/*.class src/*.class ./*.class)
jar -cf $(JAR) $(CLS);
```

generate the jar with all the class files?

---

### Post by dwhitney67 on 2009-05-03
It should.  You can verify the contents of the jar file using the 'tvf' options.
```

jar tvf EVIL.jar

```

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> It should.  You can verify the contents of the jar file using the 'tvf' options.
```

jar tvf EVIL.jar

```


It doesn't. This is the output 

```
     0 Sun May 03 13:35:56 PDT 2009 META-INF/
    71 Sun May 03 13:35:56 PDT 2009 META-INF/MANIFEST.MF
 41656 Sun May 03 13:35:56 PDT 2009 EvilCFG.class
 15187 Sun May 03 13:35:56 PDT 2009 EvilLexer.class
 73215 Sun May 03 13:35:56 PDT 2009 EvilParser.class
 80337 Sun May 03 13:35:56 PDT 2009 EvilTree.class

```

2 folders of class files (instructions and sparcInstructions) are missing and the most important one (Evil.class) that has the main is missing.

---

### Post by dwhitney67 on 2009-05-03
The Evil.class may not be in the jar file, because it is generated after CLS is defined.  As for the class files in instructions and sparcInstructions, I do not have an answer for this.  Can you confirm that .class files exist in those folders?

Btw, this problem would have probably been solved yesterday had you posted your complete project.

Take a look at your Makefile; print out your variables to see if they contain what you expect at each stage.  Using 'echo' will help with this.

---

### Post by 2Real on 2009-05-03
Also, 

```
CLS = $(wildcard instructions/*.class sparcInstructions/*.class src/*.class ./*.class)
```

seems to ignore filed named like this

EvilParser$arguments_return.class
EvilParser$arg_list.class
EvilParser$assignment_return.class
....
EvilTree$types_return.class

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> The Evil.class may not be in the jar file, because it is generated after CLS is defined.  As for the class files in instructions and sparcInstructions, I do not have an answer for this.  Can you confirm that .class files exist in those folders?

Btw, this problem would have probably been solved yesterday had you posted your complete project.

Take a look at your Makefile; print out your variables to see if they contain what you expect at each stage.  Using 'echo' will help with this.


Oh is it ok if I post my complete project?

---

### Post by dwhitney67 on 2009-05-03
> **2Real said:**
> Oh is it ok if I post my complete project?

Take that back; please don't bother because I do not have the ANTLR stuff on my system.

Try using the 'find' command in your Makefile when generating the jar file.

Something like:
```

jar cf $(APP).jar `find . -name \*.class`

```
If you have other items you want in the jar file, just add it to the statement, with a white-space between each item.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> Take that back; please don't bother because I do not have the ANTLR stuff on my system.

Try using the 'find' command in your Makefile when generating the jar file.

Something like:
```

jar cf $(APP).jar `find . -name \*.class`

```If you have other items you want in the jar file, just add it to the statement, with a white-space between each item.

That seemed to add them all. Now how do I set the main so I can run this with an input file?

---

### Post by dwhitney67 on 2009-05-03
> **2Real said:**
> ... Now how do I set the main so I can run this with an input file?
You lost me with this statement.  Do you mean how does one pass command-line args to their java app?

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> You lost me with this statement.  Do you mean how does one pass command-line args to their java app?
well this is the error I get when trying to run my jar

```
java -jar EVIL.jar 1.ev
Failed to load Main-Class manifest attribute from
EVIL.jar

```

---

### Post by dwhitney67 on 2009-05-03
I have no idea; maybe the CLASSPATH needs to be defined in lieu of using the -jar option.

If you know the class name that contains the main() method, then try this:
```

export CLASSPATH=$(PWD)/EVIL.jar
java <YourMainClass> <args>

```
where <YourMainClass> is... well, you know, and <args> are your command-line parameters, if any.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> I have no idea; maybe the CLASSPATH needs to be defined in lieu of using the -jar option.

If you know the class name that contains the main() method, then try this:
```

export CLASSPATH=$(PWD)/EVIL.jar
java <YourMainClass> <args>

```where <YourMainClass> is... well, you know, and <args> are your command-line parameters, if any.
i think i just broke my classpath

nvm rebooting fixed it

---

### Post by 2Real on 2009-05-03
I needed to add 
```
Main-Class: Evil.class
```
into the manifest file but I still get the same error.

```
Failed to load Main-Class manifest attribute from
EVIL.jar

```

---

### Post by dwhitney67 on 2009-05-03
Did you define package(s) for your .java files?  Something like:

```

package instructions;

class Foo
{
}

```

Consider doing the same for sparcInstructions, and src, but using those names as the package name.

Then after building your jar file, the instructions I gave earlier wrt to setting the CLASSPATH and running the app should work.  If I had more information concerning the location of your main() function, that would help in offering you more detailed instructions.  For now, let's assume the main() in a src/MyClass.java.

```

export CLASSPATH=$PWD/EVIL.jar
java src.MyClass

```

If you screw the CLASSPATH again, just unset it using unset.
```

unset CLASSPATH

```

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> Did you define package(s) for your .java files?  Something like:

```

package instructions;

class Foo
{
}

```Consider doing the same for sparcInstructions, and src, but using those names as the package name.

Then after building your jar file, the instructions I gave earlier wrt to setting the CLASSPATH and running the app should work.  If I had more information concerning the location of your main() function, that would help in offering you more detailed instructions.  For now, let's assume the main() in a src/MyClass.java.

```

export CLASSPATH=$PWD/EVIL.jar
java src.MyClass

```If you screw the CLASSPATH again, just unset it using unset.
```

unset CLASSPATH

```

My main is in Evil.java which is in the folder above src so it's like this

src

[LIST=1]
[*]Evil.java (has main)
[*]instructions (package)
[*]sparcInstructions(package)
[*]src(package)
[/LIST]
and you're talking about doing the export in the terminal right? cause each time i do that it breaks my classpath

---

### Post by 2Real on 2009-05-03
[http://java.sun.com/docs/books/tutorial/deployment/jar/appman.html](http://java.sun.com/docs/books/tutorial/deployment/jar/appman.html)

i was looking at this but i can't get it to work

---

### Post by dwhitney67 on 2009-05-03
Take a look at the attachment; it contains a directory structure similar to what you have, although it lacks the ANTLR stuff.  Nevertheless, maybe it will give you an idea or two.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> Take a look at the attachment; it contains a directory structure similar to what you have, although it lacks the ANTLR stuff.  Nevertheless, maybe it will give you an idea or two.


ok this is my new makefile 

```
FILES=Evil.java
SRCS = $(wildcard instructions/*.java sparcInstructions/*.java src/*.java ./*.java)
CLS = $(wildcard instructions/*.class sparcInstructions/*.class src/*.class ./*.class)
APP = EVIL
JAR = $(APP).jar

all: run

$(JAR) : antlr.generated ${FILES}
    javac -classpath .:/usr/share/java/antlr-runtime-3.1.3.jar:/usr/share/java/antlrworks-1.2.3.jar `find . -name \*.java`
    jar -cf $(JAR) `find . -name \*.class`;

antlr.generated: antlr.generated.evil
    touch antlr.generated

antlr.generated.evil : clean Evil.g
    java org.antlr.Tool Evil.g
    java org.antlr.Tool EvilTree.g
    java org.antlr.Tool EvilCFG.g
    touch antlr.generated.evil

safe:
    \cp *.g *.java ~/.431

clean:
    $(RM) `find . -name \*.class`
    rm -f antlr.generated*

run: $(JAR)
    export CLASSPATH=$(PWD)/$(JAR) && java Evil
```
and it generates this error 

```
Exception in thread "main" java.lang.NoClassDefFoundError: Evil (wrong name: src/Evil)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: Evil.  Program will exit.
make: *** [run] Error 1

```Do you think I should try setting the manifest like it says on the Sun website?
What I'm saying is should I try to make it an executable jar now?

---

### Post by dwhitney67 on 2009-05-03
Please post the Evil.java file.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> Please post the Evil.java file.


```
package src;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.PrintStream;
import java.util.ArrayList;
import java.util.Arrays;

import org.antlr.runtime.ANTLRInputStream;
import org.antlr.runtime.CommonTokenStream;
import org.antlr.runtime.tree.CommonTree;
import org.antlr.runtime.tree.CommonTreeNodeStream;
import org.antlr.runtime.tree.DOTTreeGenerator;
import org.antlr.stringtemplate.StringTemplate;

public class Evil
{
   private static int printCounter = 0;
   
   public static void main(String[] args) throws FileNotFoundException
   {
      parseParameters(args);

      CommonTokenStream tokens = new CommonTokenStream(createLexer());
      EvilParser parser = new EvilParser(tokens);
      EvilParser.program_return ret = null;
      
      try
      {
         ret = parser.program();
      }
      catch (org.antlr.runtime.RecognitionException e)
      {
         error(e.toString());
      }

      CommonTree t = (CommonTree)ret.getTree();
      if (_displayAST && t != null)
      {
         DOTTreeGenerator gen = new DOTTreeGenerator();
         StringTemplate st = gen.toDOT(t);
         System.out.println(st);
      }

      /*
         To create and invoke a tree parser.  Modify with the appropriate
         name of the tree parser and the appropriate start rule.*/
      try
      {
         CommonTreeNodeStream nodes = new CommonTreeNodeStream(t);
         nodes.setTokenStream(tokens);
         EvilTree tparser = new EvilTree(nodes);
         StructTypes sTypes;
         
         tparser.program();
         
         CommonTreeNodeStream nodes2 = new CommonTreeNodeStream(t);
         nodes2.setTokenStream(tokens);
         
         EvilCFG cfg = new EvilCFG(nodes2);
         ArrayList<BasicBlock> blocks;
         
         blocks = cfg.program();
         
         if (_dumpIL){
             String fname = _inputFile;
             fname = fname.substring(0, fname.indexOf("."));
             fname+=".il";
             PrintStream buff = new PrintStream(new BufferedOutputStream(
                           new FileOutputStream(fname))); 
             printFuncs(blocks, buff);
             buff.close();
         }
         
         //translateIloc(blocks, sTypes);
      }
      catch (org.antlr.runtime.RecognitionException e)
      {
         error(e.toString());
      }
   }

   public static void translateIloc(ArrayList<BasicBlock> cfg, StructTypes sTypes)
   {
      for(BasicBlock block: cfg)
      {
         if(!block.getVisited3())
         {
            block.isVisted3();
            block.toSparc(sTypes);
            
            ArrayList<BasicBlock> children = block.getChildren();
            
            translateIloc(children, sTypes);
         } 
      }
   }
   
   public static void printFuncs(ArrayList<BasicBlock> in, PrintStream buff)
   {  
      for(BasicBlock block: in)
      {
         tSort(block);
         printCounter = 0;
      }
      
      for(BasicBlock blk: in)
      {
         ArrayList<BasicBlock> tmp = new ArrayList<BasicBlock>();
         buildArray(tmp, blk);
         
         BasicBlock[] tmp2 = new BasicBlock[tmp.size()];
         
         for(int i = 0; i < tmp.size(); i++)
         {
            tmp2[i] = tmp.get(i);
         }
         Arrays.sort(tmp2);
         
         for(int i = 0; i < tmp2.length; i++)
         {
            buff.println(tmp2[i].toString());
         }
         buff.flush();
      }
   }
   
   public static void tSort(BasicBlock block)
   {
      if(!block.getVisited())
      {
         block.isVisited();
         if(!(block.hasChildren()))
         {
            block.setPrintNum(new Integer(printCounter++));
         }
         else
         {
            ArrayList<BasicBlock> children = block.getChildren();
         
            for(int i = children.size()-1; i >= 0; i--)
            {
               BasicBlock blk = children.get(i);
            
               if(blk.getPrintNum() == null)
               {
                  tSort(blk);
               }
            }
         
            block.setPrintNum(new Integer(printCounter++));
         }
      }
   }
 
   public static void buildArray(ArrayList<BasicBlock> tmp, BasicBlock blk)
   {
      if(!blk.getVisited2())
      {
         blk.isVisited2();
      
         if(!(blk.hasChildren()))
         {
            tmp.add(blk);
         }
         else
         {
            for(BasicBlock block: blk.getChildren())
            {
               buildArray(tmp, block);
            }
            tmp.add(blk);
         }
      }
   }
   private static final String DUMPIL = "-dumpIL";
   private static final String DISPLAYAST = "-displayAST";

   private static String _inputFile = null;
   private static boolean _displayAST = false;
   private static boolean _dumpIL = false;

   private static void parseParameters(String [] args)
   {
      for (int i = 0; i < args.length; i++)
      {
         if (args[i].equals(DISPLAYAST))
         {
            _displayAST = true;
         }
         else if (args[i].equals(DUMPIL))
         {
             _dumpIL = true;
         }
         else if (args[i].charAt(0) == '-')
         {
            System.err.println("unexpected option: " + args[i]);
            System.exit(1);
         }
         else if (_inputFile != null)
        {
            System.err.println("too many files specified");
            System.exit(1);
         }
         else
         {
            _inputFile = args[i];
         }
      }
   }


   private static void error(String msg)
   {
      System.err.println(msg);
      System.exit(1);
   }

   private static EvilLexer createLexer()
   {
      try
      {
         ANTLRInputStream input;
         if (_inputFile == null)
         {
            input = new ANTLRInputStream(System.in);
         }
         else
         {
            input = new ANTLRInputStream(
               new BufferedInputStream(new FileInputStream(_inputFile)));
         }
         return new EvilLexer(input);
      }
      catch (java.io.IOException e)
      {
         System.err.println("file not found: " + _inputFile);
         System.exit(1);
         return null;
      }
   }
}
```

---

### Post by dwhitney67 on 2009-05-03
You indicated earlier that Evil.java was at the root-level of your directory structure (at the same level as the instructions, sparcInstructions, and src directories), yet with "package src;", it seems to imply that it is located in the src directory.

Could you please comment out that package statement, then rebuild your jar file, and then attempt to run it again.  I am curious if this makes a difference.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> You indicated earlier that Evil.java was at the root-level of your directory structure (at the same level as the instructions, sparcInstructions, and src directories), yet with "package src;", it seems to imply that it is located in the src directory.

Could you please comment out that package statement, then rebuild your jar file, and then attempt to run it again.  I am curious if this makes a difference.
i commented it out and it broke my java code

do you think i should move the Evil.java down to the src folder?

---

### Post by dwhitney67 on 2009-05-03
It can't hurt.

When you run it, I believe you will need to specify exactly where the Evil is.  So change the Makefile to have this:
```

export CLASSPATH=$(PWD)/$(JAR) && java src.Evil

```

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> It can't hurt.

When you run it, I believe you will need to specify exactly where the Evil is.  So change the Makefile to have this:
```

export CLASSPATH=$(PWD)/$(JAR) && java src.Evil

```
k i'll move the files around and then try that line of code

---

### Post by 2Real on 2009-05-03
I moved the Evil.java to the src folder and this is my new makefile


```
FILES=./src/Evil.java
APP = EVIL
JAR = $(APP).jar

all: run

$(JAR) : antlr.generated ${FILES}
    javac -classpath .:/usr/share/java/antlr-runtime-3.1.3.jar:/usr/share/java/antlrworks-1.2.3.jar `find . -name \*.java`
    jar -cf $(JAR) `find . -name \*.class`;

antlr.generated: antlr.generated.evil
    touch ./src/antlr.generated

antlr.generated.evil : clean ./src/Evil.g
    java org.antlr.Tool ./src/Evil.g
    java org.antlr.Tool ./src/EvilTree.g
    java org.antlr.Tool ./src/EvilCFG.g
    touch ./src/antlr.generated.evil

safe:
    \cp *.g *.java ~/.431

clean:
    $(RM) `find . -name \*.class`
    rm -f /src/antlr.generated*

run: $(JAR)
    export CLASSPATH=$(PWD)/$(JAR) && java src.Evil 1.ev
```

and I now I get this error

```
Exception in thread "main" java.lang.NoClassDefFoundError: org/antlr/runtime/RecognitionException
Caused by: java.lang.ClassNotFoundException: org.antlr.runtime.RecognitionException
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: src.Evil.  Program will exit.
make: *** [run] Error 1

```

Do I need to set the classpath for the ANTLR files now?

How would I do that with the method you showed earlier?

---

### Post by dwhitney67 on 2009-05-03
I started playing with the code I posted earlier, and I got it to break (exactly as you did with yours) when I specified all of my .java to be in the same package, even though they were in different directories.

The only thing I can suggest is that you edit each of the .java files to indicate that their package name corresponds with the directory name in which they reside, and as for Evil.java, it can live at the top-level but without a package name.

Evil.java will also need to import the appropriate packages (e.g. instructions, sparcInstructions, src) it requires, and ditto for each of the .java files in the subdirectories.

If you do not want to pursue this suggestion, then perhaps there is another way... but unfortunately, I do not know it.

I am accustomed to naming my packages with the name of the project, followed by the folder name.  For example, app.model, app.viewer, and app.controller, where the top-level directory is app, and the subdirectories are model, viewer, and controller.

The files in model would all have the package name app.model; for those in viewer, app.viewer; and so forth.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> I started playing with the code I posted earlier, and I got it to break (exactly as you did with yours) when I specified all of my .java to be in the same package, even though they were in different directories.

The only thing I can suggest is that you edit each of the .java files to indicate that their package name corresponds with the directory name in which they reside, and as for Evil.java, it can live at the top-level but without a package name.

Evil.java will also need to import the appropriate packages (e.g. instructions, sparcInstructions, src) it requires, and ditto for each of the .java files in the subdirectories.

If you do not want to pursue this suggestion, then perhaps there is another way... but unfortunately, I do not know it.

I am accustomed to naming my packages with the name of the project, followed by the folder name.  For example, app.model, app.viewer, and app.controller, where the top-level directory is app, and the subdirectories are model, viewer, and controller.

The files in model would all have the package name app.model; for those in viewer, app.viewer; and so forth.
I just checked the java files and all of the files are in the folders they are supposed to be in.
For example, all of package instruction is in folder instruction, all of package sparcInstruction is in folder sparcInstruction, and all of package src is in folder src.

Good idea with the package naming. I'll remember that for future projects I work on. This is my first major project I've worked on, so I'm trying to figure all this out as I go.

I think my next error is due to the CLASSPATH not getting the ANTLR classes when running right?

---

### Post by dwhitney67 on 2009-05-03
I've lost track (again).  Where is the ANTLR jar?  Append that path, with a separating colon-character to the CLASSPATH in your Makefile.

Btw, it is not typical to put the run instructions in the Makefile, but in this case, it sure beats typing all the time.  :)

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> I've lost track (again).  Where is the ANTLR jar?  Append that path, with a separating colon-character to the CLASSPATH in your Makefile.

Btw, it is not typical to put the run instructions in the Makefile, but in this case, it sure beats typing all the time.  :)


so 

```
export CLASSPATH=$(PWD)/$(JAR):/usr/share/java... etc && java Evi
```

right?

---

### Post by dwhitney67 on 2009-05-03
Yes.  It's the only thing I can think of at the moment.

P.S.  I just checked my system; I do have the antlr.jar files installed (in /usr/share/java).

---

### Post by 2Real on 2009-05-03
Omg i think it works

Thanks, for the help

---

### Post by dwhitney67 on 2009-05-03
> **2Real said:**
> Omg i think it works

Thanks, for the help

Whew!  After 6 pages of posts, it's great to know that everything worked out in the end.  Test your app to make sure that there are no more ClassNotFoundExceptions thrown.  If so, at least you know now it is the CLASSPATH that needs to be augmented.

---

### Post by 2Real on 2009-05-03
> **dwhitney67 said:**
> Whew!  After 6 pages of posts, it's great to know that everything worked out in the end.  Test your app to make sure that there are no more ClassNotFoundExceptions thrown.  If so, at least you know now it is the CLASSPATH that needs to be augmented.
the app ran but it's broken and that's another story :P
thanks for the help again

---

