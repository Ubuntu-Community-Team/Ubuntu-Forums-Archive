---
title: "[HOWTO] Execute java programs ala command-line utilities"
date: 2010-06-14
forum: Packaging and Compiling Programs
---

### Post by skytreader on 2010-06-14
When I run my java programs from the command line I'd use

```
java Main
```

Moreover, if I want to feed an input file to it I'd use

```
java Main <input
```

How do I do away with calling "java" and with the angled bracket (less than sign)? For example, if you'd call fmt with input you'd do something like,

```
fmt input
```

No "java" nor "<" (though I'm sure fmt isn't written in java).

Will making it a jar file help? Though, I think making it a jar file will require me to be in the same directory as the jar file to feed it with inputs. Of course, I can direct the input through directory navigation but that would be a lot of effort.

Any pointers will be appreciated thanks!

---

### Post by Kerubu on 2010-06-15
> **skytreader said:**
> When I run my java programs from the command line I'd use

```
java Main
```

Moreover, if I want to feed an input file to it I'd use

```
java Main <input
```

How do I do away with calling "java" and with the angled bracket (less than sign)? For example, if you'd call fmt with input you'd do something like,

```
fmt input
```

No "java" nor "<" (though I'm sure fmt isn't written in java).

Will making it a jar file help? Though, I think making it a jar file will require me to be in the same directory as the jar file to feed it with inputs. Of course, I can direct the input through directory navigation but that would be a lot of effort.

Any pointers will be appreciated thanks!

To execute a Java program, you first need to to start the Java runtime environment which is why you need to put 'java' in front of the name of your java program (which has been compiled into Java bytecode).

So you might ask why does the command 'java' execute and not my own java code straight from the command line. 

Well the program 'java' will have been compiled into the native MACHINE code of your computer. that is why your own java code will not execute if you just type the name of it on the command line. It's a bit like if your computer's NATIVE machine language was say 'French' yet Compiled java code is in a language called 'English'. Your computer will NOT understand English. However the program Java is written in French but it can *interpret* English.

You could however write a bash script which can contain several instructions you would normally type on the command line. the beauty of this is that you just type the name of you bash script and linux will execute ALL of the command instructions in it.... unfortunately you have to learn a little bit about bash scripting but that's not too difficult.

---

