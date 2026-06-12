---
title: "simple question about java packages"
date: 2007-11-16
forum: Programming Talk
---

### Post by raeb on 2007-11-16
After a bit of searching, I can't really find an answer for this.  I'm highly inexperienced with creating my own java packages and have tried several different attempts at compiling my program to no avail.  I'm making a asteroids clone in java for the hell of it.  I'm attempting to organize the source into packages, and keeping it very simple to start with.  My root package (asteroids) has all of the game files except for commands, they are in the subpackage asteroids.command.  This is where I'm screwing up.  Classes in the asteroids package need to use the classes in the command package, but I've tried a few variations of import statements (and even no import of the command package) and always end up with the same error:

```
// When using something similar to import a4.command.*;
Game.java:67: package asteroids.command does not exist
```

That followed by a list of 'cannot find symbol' errors for all of the command classes.  Can anyone give me a hint as to what I'm missing?  Hopefully I'm just tired and it's something really simple.

---

### Post by rfreedman on 2007-11-16
Java packages have to be placed in a directory structure that mirrors the package structure. 

So, if your packages are a4.asteroids and a4.commands, then you will have to have a directory named 'a4', which contains directories 'asteroids' and 'commands'. Then, the source files for the asteroids package go in the 'asteroids' directory, and the source files for the commands package go in the 'commands' directory.

Then, to compile the code, set your classpath to the directory above 'a4', and compile. For example, you might have a 'src' directory that contains the 'a4' directory. Using the command line to compile, you might do the following:

cd src
set classpath=.
javac a4/commands/*.java
javac a4/asteroids/*.java

If one or more classes in the a4.asteroids package use the classes in the a4.commands package, then you can just invoke javac on the a4/asteroids directory, and the compiler will figure out the dependencies.

Of course, all of this is much easier with a good IDE, such as Eclipse, which will take care of organizing the source files for you.

---

