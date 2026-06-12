---
title: "Creating a package without makefile"
date: 2010-12-06
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2010-12-06
Is there a way to create a proper deb package **without** writing a makefile?

I have recently created [PHPmake]("http://projects.andreaferretti.it/phpmake"), which is a build tool alternative to make. It is not perfect yet, but I'm improving it.

I'd like to build a deb package for it, but the point is that I created my own build tool exactly because I was sick of using make. It does not feel righ to write a makefile to package it!

I know I can create basic packages with the ```
dpkg-deb -b
``` command, but these is not considered the proper way to create a package. Is there a way to create a proper package without makefiles, or is the use of make intrinsic to the apt system?

---

### Post by SevenMachines on 2010-12-06
The easiest way is to follow the packaging guide using cdbs and then override your build options. for example, if you had a binary package called 'hello' in your debian/control file, then you could put something like
> build/hello::
     # Put my custom build command in here...in your debian/rules file

---

### Post by surfer on 2010-12-06
did you have a look at [scons]("http://www.scons.org/")? and you still felt the need to write something on your own? respect! ;)

---

### Post by Nonno Bassotto on 2010-12-06
> **SevenMachines said:**
> The easiest way is to follow the packaging guide using cdbs and then override your build options. for example, if you had a binary package called 'hello' in your debian/control file, then you could put something like
in your debian/rules file

As far as I understand, debian/rules is a makefile to be used by make, so this is the way I was trying to avoid. Maybe I did not understand well.

---

### Post by Nonno Bassotto on 2010-12-06
> **surfer said:**
> did you have a look at [scons]("http://www.scons.org/")? and you still felt the need to write something on your own? respect! ;)

Actually I did not know Scons, I will have a look. The advantage of PHPmake (as well as Rake) is that makefiles are written in a standard programming language, namely PHP (Ruby for Rake). Hence it is very easy to extend them to allow for any functionality that may be missing.

In any case, it seems to me that anything is better than make, and it is somehow sad that the very build system of many Linux distributions might depend so tightly on this tool. I mean, I'm sure it was a revolution when it was born, but that was some 30 years ago and counting...

I should also add that PHPmake is in its infancy, but I plan to expand it. Some things to add/fix are:
- shell output is not in real time, in particular interactive shell commands do not work;
- there are no built-in rules as yet
- there is no automatic removal of intermediate files.
But apart from these deficiencies it is working fine for me right now.

---

### Post by SevenMachines on 2010-12-06
debian/rules is not used by make, its an essential file used by package building tools that tell it how to build the package from the source. typically you might have a 'Makefile' in your source that is used to compile your code. seperately, in debian packaging you would have a 'debian' directory that contains all the info needed to package up the code into a .deb archive, this is where the 'rules' file lives.

---

### Post by Nonno Bassotto on 2010-12-06
I know it lives there, but it is still a makefile, isn't it? For instance I can read [here]("http://www.debian.org/doc/debian-policy/ch-source.html"):
```

When make invokes a command in a makefile (including your package's upstream makefiles and debian/rules), it does so using sh.

```

---

### Post by surfer on 2010-12-06
> **Nonno Bassotto said:**
> The advantage of PHPmake (as well as Rake) is that makefiles are written in a standard programming language, namely PHP (Ruby for Rake). Hence it is very easy to extend them to allow for any functionality that may be missing.


oh, scons does the same with python. a nice addition for the club, then...

---

### Post by Simian Man on 2010-12-06
> **Nonno Bassotto said:**
> Actually I did not know Scons, I will have a look. The advantage of PHPmake (as well as Rake) is that makefiles are written in a standard programming language, namely PHP (Ruby for Rake). Hence it is very easy to extend them to allow for any functionality that may be missing.
Actually that is exactly the approach taken by scons, though it uses Python.  I am a big fan of scons, you should definitely take a look.

> **Nonno Bassotto said:**
> In any case, it seems to me that anything is better than make, and it is somehow sad that the very build system of many Linux distributions might depend so tightly on this tool.

Word.

---

### Post by SevenMachines on 2010-12-06
yes it is, but i thought you were looking to use phpmake as the build script for your source code. debian/rules is a packaging file only. if you use something like make, autotools, qmake, scons, etc, then the debian/rules file can consist only of a 'include' line that will automatically use these scripts to build your code. if you use something that debhelper doesnt know about then you need to tell debian/rules how to use this script by overriding the make target mentioned previously.
Incidentally, theres a debhelper addon called 'dh_make-php'  which may be useful to you depending on how your source build is set up

---

### Post by Nonno Bassotto on 2010-12-06
> **Simian Man said:**
> Actually that is exactly the approach taken by scons, though it uses Python.  I am a big fan of scons, you should definitely take a look.

I will definitely have a look. I initially thought about writing it in python, but finally chose PHP for the reason that its syntax is more similar to that of makefiles. For instance you can write
[PHP]
include('another_makefile.php');
$copy = 'copy.txt';
$original = 'original.txt';
target("distrib/$copy", $original,
    "cp $original ditrib/$copy"
);
[/PHP]

The use of double quotes " let you mix variables and commands, and as a result makefiles are more readable. Also, the include() syntax is as simple as it can be.

---

### Post by SevenMachines on 2010-12-06
+1 for scons. either way, using a build system recognised by debhelper makes packaging a doddle and would mean its unlikely you need to do anything complicated to build a package

---

### Post by Nonno Bassotto on 2010-12-06
> **SevenMachines said:**
> yes it is, but i thought you were looking to use phpmake as the build script for your source code. debian/rules is a packaging file only. if you use something like make, autotools, qmake, scons, etc, then the debian/rules file can consist only of a 'include' line that will automatically use these scripts to build your code. if you use something that debhelper doesnt know about then you need to tell debian/rules how to use this script by overriding the make target mentioned previously.
Incidentally, theres a debhelper addon called 'dh_make-php'  which may be useful to you depending on how your source build is set up

Thank you very much! It seems I am a bit confused about the whole process. I will have a look at dh_make and dh_make-php.

---

