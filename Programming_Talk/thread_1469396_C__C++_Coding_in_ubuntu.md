---
title: "C / C++ Coding in ubuntu"
date: 2010-05-02
forum: Programming Talk
---

### Post by Rushyang on 2010-05-02
Alright, this always happens with me. just before exam days, My windows will crash or my computer hardware will go kaput. 

Now, at this time, My windows is crashed. and I don't want to waste my time in formatting windows. I need to know how can I compile and run my .C and .CPP files in Ubuntu 10.04. 

Please provide a good guide with screenshots if available. It's very urgent. :(

---

### Post by lisati on 2010-05-02
Moved to ["Programming Talk"]("http://ubuntuforums.org/forumdisplay.php?f=39") - have a look at the "stickies"

---

### Post by Rushyang on 2010-05-02
Thank You it's all solved out.. Actually I got panicked.. didn't look around. Sorry for double post. 

it's all solved.

---

### Post by TheStatsMan on 2010-05-02
If you are use to Windows and it is urgent try codeblocks. It is an IDE so it will compile and link for you.

---

### Post by sunk8 on 2010-05-02
> **Rushyang said:**
> Alright, this always happens with me. just before exam days, My windows will crash or my computer hardware will go kaput. 

Now, at this time, My windows is crashed. and I don't want to waste my time in formatting windows. I need to know how can I compile and run my .C and .CPP files in Ubuntu 10.04. 

Please provide a good guide with screenshots if available. It's very urgent. :(

3 really good ways of getting this done:

1] Install DosBOX. It's a dos emulator. Simply run C or C++ for it.
2] Use gcc in the terminal itself...
3] Install Anjuta. They have help pages...

---

### Post by nvteighen on 2010-05-02
1. Open terminal. Type:
```

sudo aptitude install build-essential

```

2. To compile one or more C files into a single executable called "myapp". The -Wall flag will activate all compiler warnings; it's a very good practice. The compiler will create the executable in your current directory.
```

gcc -o myapp file1.c file2.c file3.c -Wall

```

2a. If your C program uses math.h, you'll have to use:
```

gcc -o myapp file1.c file2.c file3.c -Wall **-lm**

```

3. For C++ it's almost the same as above. 2a is unnecessary for C++.
```

g++ -o myapp file1.cpp file2.cpp file3.cpp -Wall

```

4. To run a compiled binary called "myapp" present in the current directory:
```

./myapp

```

This will serve for any basic program you may need. Ask here if something goes wrong.

---

