---
title: "&quot;Could not find 'path', starting '/bin/bash' instead. Please check your profile..."
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Tubba on 2011-11-27
So I've been trying to create an icon to launch a .jar file, namely GoMule.jar, because I got tired of doing it via terminal. First, I created a shell script, simply "java -jar GoMule.jar". This shell script works when launched via Konsole.

Second, I created a "Link to Application" that should launch the shell script (which, by the way, is marked as executable). The shell script is titled launcher.sh. First I tried just launcher.sh. Then sh launcher.sh. Then ./launcher.sh, then including the entire path from root, and so on. Nothing works. I've also tried every variant with or without a work path to the folder in question.

When I run the application link via Konsole, I get the lovely error message "Warning: Could not find '/home/leonard/.wine/dosdevices/c:/Program Files/Diablo II/GoMule/launcher.sh', starting '/bin/bash' instead.  Please check your profile settings." When I just try ./launcher.sh without a full path I get the same message, except the path is given as ~/Documents/GoMule.jar, for whatever reason. I've backslashed every space properly and it obviously recognizes the path.

So, how do I make it work!?

---

### Post by anewguy on 2011-11-28
Post a copy of your shell script - it's possible you're missing the directive at the front to tell it to use bash.

I'm also a little curious - are you trying to launch a Windows application in Wine via the script?

Dave ;)

---

### Post by Tubba on 2011-11-28
Oooh, that may be it. That would make sense. The script is just "java -jar GoMule.jar". And no, it's not trying to launch a Wine application, it's a java app in a Wine directory.

I searched around for the proper syntax but couldn't find anything but various irrelevant stuff.

---

### Post by anewguy on 2011-11-28
I can't say 100% this is correct, but this is what I would do:

Create a script file - like testme.sh with the following contents:


$! /bin/bash
$ java -jar /home/leonard/.wine/dosdevices/c:/Program Files/Diablo II/GoMule/GoMule.jar


Save the file, then be sure chmod the file to be executable.

Try:  ./testme.sh and see what happens.  Once it works from the command line then it can be made to be part of a launcher.

Also you may need to change the path to the jar file.  What does this the gomule.jar file actually do - start a game or some other type of gui program?  Is the program a Windows program?

Dave ;)

---

### Post by Tubba on 2011-11-29
Your code did not work, as it was, with a path modified down to GoMule.jar and put in the same directory, or moved to Home folder and run as it was, or any other variant I could think of. It quite literally seemed to do absolutely nothing. Not even a message from the Terminal.

GoMule is, basically, a java program for editing the binary (save) files of Diablo II, moving data between files, and create external files for item storage and such. It was specifically written to work cross-platform (originally for a program that'd work on OS X, I believe), and it works fine on Linux - I've used it. My only problem is to get it to run with a click rather than having to open a terminal and punch "java -jar /path/to/GoMule.jar" in.

---

### Post by anewguy on 2011-11-29
Wonder what would happen if:

- on the desktop create a new launcher
- for what to launch put in:

shell java -jar /path/to/GoMule.jar

- you may have to say run in terminal mode


Dave ;)

---

### Post by Tubba on 2011-11-30
Well launcher is a GNOME thing, I think? KDE has Link to Application, which I guess is the same thing. Anyway I created one with the command "shell java -jar /home/leonard/.wine/dosdevices/c:/Program Files/Diablo II/GoMule/GoMule.jar" on desktop. Terminal says:

Warning: Could not find 'shell', starting '/bin/bash' instead.  Please check your profile settings.

/usr/bin/java: /usr/bin/java: cannot execute binary file

---

### Post by anewguy on 2011-12-02
A couple of posts back I tried to create a shell script - I had something wrong there.  Remove the "$" at the start of each line, and replace the "!" on the first line with "#!".

I have no idea though if it will run or do what you want.

I'm starting to run out of ideas here - seems like it should be a simple task - create a launcher/link to application that contains the java statement itself.  I mean, right now it hasn't even gotten to the point of starting java, so it's something simple that I'm not seeing right now.

Sorry I haven't been able to figure this out - I'll keep trying.

Dave ;)

---

### Post by Tubba on 2011-12-05
Wait... apparently java -jar GoMule.jar works for the shell script, and simply clicking the shell script launches it.


Good enough for me. Thanks.

---

