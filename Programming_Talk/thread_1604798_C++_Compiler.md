---
title: "C++ Compiler"
date: 2010-10-24
forum: Programming Talk
---

### Post by Shibbir on 2010-10-24
How to compile and run a .cpp file in code::block ide? When I press press run button, the ide prompts that I have to build first. Press yes to build. But that didn't work. Any suggestion?

Another thing how to install Anjuta DevStudio?

---

### Post by SledgeHammer_999 on 2010-10-24
If you use Gnome then on the gnome-panel: System->Administration->Synaptic Package Manager. Search and install the package named "**build-essential**". 

Or open a terminal window and type:
```
sudo apt-get install build-essential
```

You can install anjuta the same way. The package name for it is "anjuta".

---

### Post by Jonas thomas on 2010-10-24
> **Shibbir said:**
> How to compile and run a .cpp file in code::block ide? When I press press run button, the ide prompts that I have to build first. Press yes to build. But that didn't work. Any suggestion?

Another thing how to install Anjuta DevStudio?

At what level are you? beginner or you know what your doing?
If you're a beginner I found this most excellent tutorial from a bronx public school... Unfortunately, it must have been taken down, or I'm not asking putting in the correct search terms.
(Sorry not being much help here)

---

### Post by Jonas thomas on 2010-10-24
> **Jonas thomas said:**
> At what level are you? beginner or you know what your doing?
If you're a beginner I found this most excellent tutorial from a bronx public school... Unfortunately, it must have been taken down, or I'm not asking putting in the correct search terms.
(Sorry not being much help here)

Hah...
I found it...
it was brooklyn not the bronx.. (hey I'm a midwesterner... it's all the same to me ;)

[http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/]("http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/")

---

### Post by mr clark25 on 2010-10-24
i am just starting to learn c++, and i like to write the code in the IDE, but compile it using the terminal.

the command is:
```

g++ somesourcecode.cpp -o outputfile

```

where "somesourcecode.cpp" is the source code, and "outputfile" is what you want to name the output file.

note: the above command will only work if you have cd'ed to the directory your source code is in.

you may need to install g++:
```

sudo apt-get install g++

```

---

### Post by worseisworser on 2010-10-24
> **mr clark25 said:**
> i am just starting to learn c++, and i like to write the code in the IDE, but compile it using the terminal.

the command is:
```

g++ somesourcecode.cpp -o outputfile

```

where "somesourcecode.cpp" is the source code, and "outputfile" is what you want to name the output file.

note: the above command will only work if you have cd'ed to the directory your source code is in.

you may need to install g++:
```

sudo apt-get install g++

```

It's a good idea to use the *-g* and *-Wall* options when compiling. See the GCC manual for information on as to what they do.

---

