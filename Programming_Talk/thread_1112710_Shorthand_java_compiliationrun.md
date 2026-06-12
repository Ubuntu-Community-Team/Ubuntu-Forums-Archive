---
title: "Shorthand java compiliation/run"
date: 2009-03-31
forum: Programming Talk
---

### Post by arod529 on 2009-03-31
So I have java jdk on my linux box.

Instead of using Terminal to compile and run my programs I created custom app. launchers. For compiliation I just pointed to */usr/local/jdk1.6.0_12/bin/javac*. Works great. I did the same for running the program(pointed to */usr/local/jdk1.6.0_12/bin/java*).

Problem: the java command uses the .class file name without the .class extention. Is there anyway to make the custom application launcher truncate the .class file extention?

Also doing the same(*/usr/local/jdk1.6.0_12/bin/javadoc*) for javadoc creates the documentation files in my */home/<username>* folder even though the .java file is on my desktop. Wierd.

Thanks for the help.

---

### Post by CptPicard on 2009-04-01
IMO the correct way to approach automating Java project builds, tests etc on the command line is to write an ant script :)

---

### Post by arod529 on 2009-04-03
I have no idea how to use ant script. I found this web page [[COLOR="RoyalBlue"]http://mindprod.com/jgloss/ant.html[/COLOR]]("http://mindprod.com/jgloss/ant.html"), but it looks like its alot more compicated than I'm looking for. As of right now, the only thing I am doing is compiling .java files. I don't do anyting with .jar files and the like.

Reason: I'm taking a beggining java class at the community collage.

If you can explain how to write and use the appropriate ant script, I'd be happy to learn.

---

### Post by myrtle1908 on 2009-04-03
> **arod529 said:**
> So I have java jdk on my linux box.

Instead of using Terminal to compile and run my programs I created custom app. launchers. For compiliation I just pointed to */usr/local/jdk1.6.0_12/bin/javac*. Works great. I did the same for running the program(pointed to */usr/local/jdk1.6.0_12/bin/java*).

Problem: the java command uses the .class file name without the .class extention. Is there anyway to make the custom application launcher truncate the .class file extention?

Also doing the same(*/usr/local/jdk1.6.0_12/bin/javadoc*) for javadoc creates the documentation files in my */home/<username>* folder even though the .java file is on my desktop. Wierd.

Thanks for the help.

What language is your "launchers" app written in?  It is simple to remove parts of string eg. '.class' but need to know what you are using.  For example, in Perl you could write ...

```
my $class_file = 'abc.123.class';
$class_file =~ s/\.class$//i;
print $class_file;
```

Which would print: 'abc.123'.

---

### Post by arod529 on 2009-04-07
> **myrtle1908 said:**
> What language is your "launchers" app written in?  It is simple to remove parts of string eg. '.class' but need to know what you are using.  For example, in Perl you could write ...

```
my $class_file = 'abc.123.class';
$class_file =~ s/\.class$//i;
print $class_file;
```

Which would print: 'abc.123'.

I'm not using a language.

Here is what I did:
Right click the file and click *open with*. At the bottom of the window click on the arrow next to *custom command*. Click *browse* and point to */home/usr/local/jdk<version number>/bin/javac*. Obvoiusly you replace *javac* with whatever command you wish to run.

---

### Post by The Cog on 2009-04-08
You might be able to do something with the program basename. Just a guess, but perhaps put in the launcher:
> java $(basename $1 .class)

but can I suggest you install geany - a nice syntax-highlighting editor with a compile button and error highlighting.

---

### Post by arod529 on 2009-04-11
Well, for some reason I couldn't get the *basename* keyword to work with the program launcher. But I conveintly discovered the *External Tools* plugin and can compile, run, and document my files all with a button. I basically turned gedit into a super simplistic IDE.

The only thing is it doesn't check whether the file has been changed so make sure the file is saved before running the javac command.

Even though any errors are not highlighted the comiler tells you what line they are on. With the line numbers enabled debugging isn't any harder(for comilation errors) than in an IDE.

The screenshots got kinda screwed unless you press the "Expand" button that appears when you hover over the picture.

By the way, I did try geany but the compiler and run commands wouldn't work. It gave me some weired error. I don't remmember what is was though. Besides, I absoulutly love the snippets plugin for gedit.

---

