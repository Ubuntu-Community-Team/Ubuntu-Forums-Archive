---
title: "Ubuntu Software Development"
date: 2011-08-20
forum: Packaging and Compiling Programs
---

### Post by Bob Thompson on 2011-08-20
I'm still kind of new to programming, but I'd like to know more about Ubuntu Software Development. I read that a lot of Ubuntu's  developers ( I think MOTU is the right term?) program code for Ubuntu in  various languages (Java, C++, etc.). If true, could someone explain how  this is possible? Is there a compiler maybe that can take various languages and convert them into machine code? AFAIK, there isn't one particular language MOTU's program in, or is there? I know that there is a section on it, but a lot of it still doesn't make sense to me at this time.  

If someone can just talk about the process in general that would be good too.

---

### Post by karlson on 2011-08-20
> **Bob Thompson said:**
> I'm still kind of new to programming, but I'd like to know more about Ubuntu Software Development. I read that a lot of Ubuntu's  developers ( I think MOTU is the right term?) program code for Ubuntu in  various languages (Java, C++, etc.). If true, could someone explain how  this is possible? Is there a compiler maybe that can take various languages and convert them into machine code? AFAIK, there isn't one particular language MOTU's program in, or is there? I know that there is a section on it, but a lot of it still doesn't make sense to me at this time.  

If someone can just talk about the process in general that would be good too.

The philosophy of UNIX and consequently Linux is to have small applications defined for a particular task and in view of this Ubuntu Software Development just as any other software development is done in the most appropriate language for the task.

That said there is no single compiler for all programming languages because some of them are not even compiled like Perl.

Languages most commonly used in development would probably be C, C++, Python, Java, and Perl you can choose whatever you want and that's the beauty of it.

---

### Post by Bob Thompson on 2011-08-20
Lets say I code a new calculator in C++ and a photo viewer in Java to be part of the next Linux distro. Does Linux have some method for detecting which language a piece of software was written in and compiling accordingly? or how would that work?

---

### Post by SevenMachines on 2011-08-20
You should probably look through this sticky at at the top of the programming forum.
[http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

In very, very general though you might want to think along the lines of something like this.

For some program included in the repository you would probably have,

* Source Code - The code for a project, written in whatever language, c, c++, python, java, etc, 100's of these! This will include a build system, which are instructions on how to turn your code into a program (including which compiler type, libraries will be needed and so on). Examples of this might be, Makefiles, cmake, scans, apache ant, etc, 100's of these too. This is the part done by the writer(s) of the sofware.

For source code to become part of a debian-based system like ubuntu it would then be packaged

* Debian Packaging - A set of files separate from the source code that detail how to take the associated source code and turn it into a debian package. This might tell the debian system which build system is used in the source code, which packages to create, what files each package should contain what licence to use. This might be done by the source code authors too, but often it'll be done by a maintainer in debian or ubuntu who knows how to package things.

It should be understood that people who package source code and fix bugs in ubuntu and generally maintain the health of repository packages (MOTU is a term for someone who does this for the 'universe' section of the repository) is usually not the author of the source code. They might be but more often than not they will be packaging someone elses code, applying bug fixes to a package, and keeping in contact with the author and/or a maintainer upstream in debian and so on to make sure the program can be installed and run properly.

---

