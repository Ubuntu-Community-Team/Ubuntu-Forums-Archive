---
title: "Running Java prog outside of eclipse"
date: 2006-03-24
forum: Programming Talk
---

### Post by Ron W on 2006-03-24
I have developed a Java programme using Eclipse. I now want to copy it to another directory so that I can use it in the new directory while keeping the original in the 'workspace' directory to use for further development.

I double click on the plan.class and plan$1.class files only to get the following messages - 
'Couldn't display "/home/ron/workspace/gard/plan/plan.class" ' and 
'Couldn't display "/home/ron/workspace/gard/plan/plan.class" ' 

What am I doing wrong? How can I run my programme in a new location? I am assuming that if I cannot get these working from this location (workspace directory) I cannot do so from another location.

Appreciating any help

Thanks

Ron

---

### Post by Keffin on 2006-03-25
[quote=Ron W]I have developed a Java programme using Eclipse. I now want to copy it to another directory so that I can use it in the new directory while keeping the original in the 'workspace' directory to use for further development.

I double click on the plan.class and plan$1.class files only to get the following messages - 
'Couldn't display "/home/ron/workspace/gard/plan/plan.class" ' and 
'Couldn't display "/home/ron/workspace/gard/plan/plan.class" ' 

What am I doing wrong? How can I run my programme in a new location? I am assuming that if I cannot get these working from this location (workspace directory) I cannot do so from another location.

Appreciating any help

Thanks

Ron[/quote] 
Well the error messages look like they are from GEdit trying to load them or something, so it is not even trying to run. Drop into the command line, cd to the base classes directory (for me this is ProjectPath/build/classes), and run the following:
```
java org.test.package.name.Test
``` Obviously your package name will be different, it is basically the path from the current directory to the class file but with dots instead of slashes, and no .class extension on the class name.

If you get a NoClassDefFound exception on the class you are trying to run then check you are in the right directory and using the correct package name etc. If you get a NoClassDefFound exception on any other class then you will need to add some things to your classpath. You should have a nice list of jar files that you depend on in eclipses Project Explorer tab. To include them from the command line, create an environment variable with a colon-seperated list of paths to all the jars you have in your project:
```
export CLASSPATH=/some/path/to/a/jarfile.jar:/some/other/path/to/a/jarfile.jar:/and/more/jars.jar
``` Then pass this to the first command like this:
 ```
java -cp $CLASSPATH org.test.package.name.Test
``` 
When you get this working, it should be trivial to copy the classes directory you are now in to anywhere else on the system and run it in exactly the same way. Don't use paths relative to the current directory in the CLASSPATH though, as they will be wrong when you move this directory.

The next step is to automate the above, by putting the commands to move to the correct directory, set the classpath, then run the program in a short script and attach a launcher to it. If you get that far then need help doing that just shout :).

---

