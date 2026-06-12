---
title: "how to set gedit for compiling and running java programs"
date: 2009-08-03
forum: Programming Talk
---

### Post by jndlsnl on 2009-08-03
hi, i m newbie here....and i m using ubuntu 9.04. can anyone tell me tht how can i set gedit for compiling and running java programs....i have some threads but not anyone working for me....i very begginner here so plz tell me step by step info to set gedit for compiling and running java programs


thnx in advance...

---

### Post by Sockerdrickan on 2009-08-03
Just run a separate terminal or you'll loose some precious lines of view!

---

### Post by .Maleficus. on 2009-08-03
Do you have the JDK installed?  To compile/run a Java program from the command line, this is the process you take.  Note - this is done from a terminal.
```
cd path/to/java/source
javac MyProgram.java
java MyProgram
```
javac (the compiler) takes [optional arguments]("http://java.sun.com/j2se/1.4.2/docs/tooldocs/windows/javac.html") and must be in your $PATH to work.  If you aren't sure if your $PATH variable is set correctly, go to a terminal and type 'echo $PATH' and post the output here.

---

### Post by jndlsnl on 2009-08-03
yeah i hve installed jdk. and from terminal i can compile and run the java programs...

but i want to do it with from gedit as i post......how to set gedit for compiling and running java programs

---

### Post by wojox on 2009-08-03
snip

---

### Post by Dullstar on 2009-08-03
I can't say about the compiling part, but I'd really like to know why they cannot be ran on my computer.

---

### Post by kayvortex on 2009-08-03
You can use a gedit plugin called "External Tools" to run any external command. To turn "External Tools" on, open gedit and go to *Edit* and Select *Preferences*. Go to the *Plugins* tab and check the box next to *External Tools* and then close the window. Now, you can go to *Tools* in gedit and select *External Tools...*. From there, you can see a few pre-made commands (there is one that runs the command "make" in the working directory), and you can also make your own. I don't know too much on how to make it do *exactly* what you want it to do as efficiently as possible (it looks like you just enter in shell commands as you would in a shell script), but a bit of research/googling should elucidate all the basics.

---

### Post by jndlsnl on 2009-08-05
i use gedit plugin named "external tools" for compiling and running java programs.....

i see somewhere else how to make a new tool to compile and run java programs...

i put these commnads in new tool..

#!/bin/sh
cd $GEDIT_CURRENT_DOCUMENT_DIR
if javac $GEDIT_CURRENT_DOCUMENT_NAME;
then
java ${GEDIT_CURRENT_DOCUMENT_NAME%\.java}
else
echo "Failed to compile"
fi



but when i run this tool...it couldn't find javac...

it says tht javac could not found....how can i fix it??????????

---

### Post by kayvortex on 2009-08-05
I've never used java, so do you have to do something special in order to compile with javac, such as setting environment variables like PATH?

Could you post the output of,

```
locate javac
```

and,

```
echo $PATH
```

---

