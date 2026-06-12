---
title: "How do I compile a program from source code in Ubuntu?"
date: 2011-09-18
forum: Programming Talk
---

### Post by sakibmoon on 2011-09-18
I have downloaded a tar file of Mplayer. I want to compile and install it on my system. I don't have any clue how can I do that. When I extracted, it created a folder with lots of folders and .h and .c files. (See the attached image) I have general programming knowledge in C. But how do I compile a big project like this. Which file I have to compile?

My main interest is with compiling from source, not about installing.

---

### Post by cgroza on 2011-09-18
Is there a file named Makefile, autogen.sh or ./configure?

The general steps for compiling are:
```

./configure
make
sudo make install # will install the compiled program.

```

---

### Post by sakibmoon on 2011-09-18
> **cgroza said:**
> Is there a file named Makefile, autogen.sh or ./configure?

The general steps for compiling are:
```

./configure
make
sudo make install # will install the compiled program.

```

Do you mean "configure" or "./configure" file. It has a file named Makefile and another named configure. In this case what I need to do

Do I need to copy the whole folder to home directory?

---

### Post by andrew.46 on 2011-09-18
Perhaps have a look here:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Hopefully this will get you started at least...

---

### Post by sakibmoon on 2011-09-18
I was looking for instruction on how to compile big C/C++ projects with compiler. In Windows it creates an .exe file. What happens in case of Ubuntu?

How can I compile the source on a IDE like netbeans? How do I import the project. Do I need to import a single Makefile or the whole project like java.

---

### Post by scitron on 2011-09-18
It basically is a three step process like someone already explained.

Open up a command prompt in the directory that you've extracted the files to.

Let's says the prompt at your command prompt is;

$

Then at the command prompt first type (only enter the stuff after the $)

$ ./ configure

Wait for that to finish and then;

$ make

When that's done, finally;

$ make install

That's it.

If you need more details read [here]("http://www.tuxfiles.org/linuxhelp/softinstall.html").

---

