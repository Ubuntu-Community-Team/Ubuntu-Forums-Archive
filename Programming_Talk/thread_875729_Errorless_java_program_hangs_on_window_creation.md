---
title: "Errorless java program hangs on window creation"
date: 2008-07-31
forum: Programming Talk
---

### Post by The AlGorenator on 2008-07-31
Yeah, the program i'm trying to get Eclipse to interpret simply hangs as soon as it creates the window.

The program works properly under windows versions of eclipse, and i really need to work on it on this [kubuntu] computer.

Any help would be greatly appreciated.

---

### Post by Reiger on 2008-07-31
Sorry, but for a program to compile sucessfully; that's not the same as for it to be 'error-less'.

If it hangs, you may either be attempting too much for your system to chew (massive I/O operations, any?) or; more likely you may have the following issues:

1) An unexpected, uncaught exception ocurred -- especially true for Swing-applications that aren't thread safe. Also note that these exceptions may go rather 'unnoticed', that is to say: you may not be able to see they happened after you close your program.... So, try to figure out if you pass on objects/stuff which are still 'null'... You'd need to initialise your low-level menu-components before you pass them on to higher-level ones.
2) You have succesfully put your program in an infinite loop -- reviewe your for/while statements.

---

### Post by The AlGorenator on 2008-07-31
Yeah, i understand the issues you state, but in windows, the program functions.

That leads me to think it's a problem with kubuntu/eclipse since i know the code runs.

---

### Post by drubin on 2008-07-31
Are you running the same version of java and eclipse?

type ```
java -version
javac -version

```

---

### Post by The AlGorenator on 2008-07-31
java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)


javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

---

### Post by drubin on 2008-07-31
I would rather try the sun JDK.

Try uninstalling the version of OPEN jdk and install the sun version.

I am not sure but are you running OPEN jdk on your windows machine??...

---

### Post by The AlGorenator on 2008-07-31
No, i am not. Okay, i shall try this and report back.

---

### Post by The AlGorenator on 2008-07-31
java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

yeah.

I restarted eclipse and it still hung. Any other ideas?

---

### Post by The AlGorenator on 2008-07-31
It said it had some error installing now that i've tried again.

Never mind this, i'm just going to nab my roommate's computer and do my work on that.

Thanks, regardless. :)

---

### Post by Reiger on 2008-07-31
If you used the Java 6.xx compiler; try:

```

sudo aptitude install sun-java6-jdk

```

Also, check that your Eclipse is properly configured for this *new* run-time environment:

Window->Preferences;

[[IMG]http://img32.picoodle.com/img/img32/3/7/31/t_snapshotm_31d60ae.png[/IMG]](http://www.picoodle.com/view.php?img=/3/7/31/f_snapshotm_31d60ae.png&srv=img32)

And from there it should be self-explaining stuff...

---

### Post by dribeas on 2008-07-31
> **The AlGorenator said:**
> java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)


What is the java environment that eclipse is launching? (look into eclipse options)

---

