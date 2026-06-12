---
title: "Get Me Started with GTK and code::blocks-Linker missing a reference"
date: 2011-02-20
forum: Programming Talk
---

### Post by abpriest on 2011-02-20
Hi,

I would describe my c/c++ programming skills at Intermediate level, and I am looking to develop GTK applications with codeblocks as means of trying something new and as a practical way to develop my skills.  I already have codeblocks installed and running on my Ubuntu 10.10 machine. 

It has been a long road. I downloaded/installed libglib2.0-dev, then had to tell codeblocks where to look for all of the header files.

My problem when I compile the hello world application (from the GTK online manual [http://library.gnome.org/devel/gtk-tutorial/stable/c39.html )]("http://library.gnome.org/devel/gtk-tutorial/stable/c39.html") Now I get the error: "undefined reference to 'g_print'" and a slew of related errors for other functions.

:confused: What am I missing and where are those functions defined?

Thanks,

abpriest

---

### Post by GregBrannon on 2011-02-20
Have you already installed the build-essential stuff using:

```
sudo apt-get install build-essential
```

---

### Post by abpriest on 2011-02-21
No. What is contained in it?

---

### Post by mikejonesey on 2011-02-22
I found whenever the compiler don't work from ide, running it from command line usualy gives you a good clue as to what linker / include directories are missing from the ide...

what do you get when you build from command line...

---

### Post by abpriest on 2011-02-27
> **GregBrannon said:**
> Have you already installed the build-essential stuff using:



Yes. It is installed and running the newest version.

---

### Post by gmargo on 2011-02-27
Install the **libgtk2.0-dev** package to compile that example.

To configure **codeblocks** to find the required libraries see here: [http://ubuntuforums.org/showpost.php?p=10427712&postcount=4](http://ubuntuforums.org/showpost.php?p=10427712&postcount=4)  

Instead of "wx-config", you would use, for compiler settings:
```

`pkg-config --cflags gtk+-2.0`

```And for linker settings:
```

`pkg-config --libs gtk+-2.0`

```

---

### Post by abpriest on 2011-02-27
Solved! I had to tell code:blocks to add the directories with the header files to the project, the release, and the debug directories of the project. Need more details? Just ask!

---

