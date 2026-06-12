---
title: "can't open pipe on Karmic Koala"
date: 2009-12-31
forum: Programming Talk
---

### Post by v923z on 2009-12-31
Hello,

I have just switched over from fedora, and I was trying to use some code that I developed there. However, for some reason, I can't open a pipe from a C code. This is what I have and used to work on fedora

```
#include <stdio.h>
#include <stdlib.h>

FILE *fin;

int main() {
  fin = popen("gnuplot &>ttt.dat" ,"w");
  fflush(fin);
  fprintf(fin, "print 4*5");
  fflush(fin);
  pclose(fin);
  return(0);
}

```and this is how I compiled it
```

gcc test.c -o test

```When running ./test, ttt.dat is created, but remains empty. I must be missing something very trivial, I just don't know what. Could someone give me a pointer? My system is kubuntu 9.10, and here is the output of gcc -v
```

gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' 
--with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs 
--enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch 
--enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext 
--enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 
--enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all 
--disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release 
--build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8)

```Many thanks,
v923z

---

### Post by dwhitney67 on 2009-12-31
Augment the following printf() statement to appear as follows:
```

fprintf(fin, "print 4*5\n");

```
Note the \n character; this emulates the user pressing the <Enter> key when interfacing with gnuplot from the terminal.

P.S.  You should re-write your app as follows; the reason... 1) no need for global variables; and 2) check that the popen() succeeded.
```

#include <stdio.h>
#include <stdlib.h>

int main() {
  FILE* fin = popen("gnuplot &> ttt.dat" ,"w");
  if (fin) {
    fflush(fin);
    fprintf(fin, "print 4*5\n");
    fflush(fin);
    pclose(fin);
  }
  else {
     fprintf(stderr, "popen() failed.\n");
     return -1;
  }
  return(0);
}

```

---

### Post by v923z on 2009-12-31
Many thanks for your prompt reply!
> **dwhitney67 said:**
> Augment the following printf() statement to appear as follows:
```

fprintf(fin, "print 4*5\n");

```Note the \n character; this emulates the user pressing the <Enter> key when interfacing with gnuplot from the terminal.


This doesn't change the situation, while I admit that this could've been a possible error. If I do this on the command line, it works OK
```
echo "print 3*4" | gnuplot &> ttt.dat
```so I am sure that gnuplot is installed properly. 

> 
P.S.  You should re-write your app as follows; the reason... 
2) check that the popen() succeeded.
Yes, I agree. I was trying to post a minimal code here. On the other hand, it is good that you pointed this out, because your code doesn't return an error message, i.e., the pipe seems to have been opened properly, but for some reason, gnuplot doesn't process the command. However, I modified your code a bit, so I have a usleep immediately after flushing the pipe
```

...
    fprintf(fin, "print 4*5\n");
    fflush(fin);
    usleep(3000000);
...

```and if I run the code, and issue ps ax immediately after starting it, a broken pipe is reported
```

...
1912 pts/1    Ss     0:00 /bin/bash                                           
 2421 pts/1    R+     0:00 ps ax                                               
[1]+  Broken pipe             ./test3  

```So, why should a pipe be broken, if I create it from my code?
Thanks,
v923z

---

### Post by dwhitney67 on 2009-12-31
> **v923z said:**
> So, why should a pipe be broken, if I create it from my code?
Thanks,
v923z

I do not know why you are still having problems with your application.

As for the solution I proposed, I did not guess at it.  I inserted the change into your program, and tested it on my system.

Please repeat your testing, this time ensuring that you re-compiled your source code.

---

### Post by v923z on 2009-12-31
> **dwhitney67 said:**
> As for the solution I proposed, I did not guess at it.  I inserted the change into your program, and tested it on my system.

I think, you got me wrong there: I really wasn't implying that you didn't quite know what you were talking about:) All I meant was that it didn't work here, while I think it should have, and I was suspecting some permission issues, or something like that. I really have no idea. 

As for the problem at hand, I have made some headways, although, I don't know whether this will get us anywhere. But I hope it will. So, if I have this, 
```

FILE* fin = popen("gnuplot -persist" ,"w");

```then I can plot from my code without any problems, so, the following lines are executed properly
```

fprintf(fin, "p sin(x)\n");
fflush(fin);
usleep(100000);
fprintf(fin, "print 3*3\n");
fflush(fin);

```A sine will be shown in a separate window, and 9 will be printed to the console. But it will all break down, if I have this, instead:
```

FILE* fin = popen("gnuplot &> test.dat" ,"w");

```The file test.dat will be created at the beginning of the session, but the sine function is no longer shown, and test.dat will be empty. If I list the directory, a broken pipe will be reported. What on earth is going on here? Is there another way to redirect the output of gnuplot to a file? I need both stdout and stderr in my application, because I have to catch erroneous commands. Or is there some other application that I could use to test the glitch?
Cheers,
v923z

---

### Post by dwhitney67 on 2009-12-31
> **v923z said:**
> ...A sine will be shown in a separate window, and 9 will be printed to the console. But it will all break down, if I have this, instead:
```

FILE* fin = popen("gnuplot &> test.dat" ,"w");

```

I think that you have set your expectations too high.  How do you expect that the graphics of a separate window will show up in your text file, which is deriving its input from stdout (of gnuplot)?

As for capturing stdout and stdin of gnuplot into your file, you are doing exactly that.

For the external application that gnuplot launches to display graphics, that is not directed to stdout.  The only way I can think of to capture this is to use a window capture tool (eg. gnome-screenshot).

---

### Post by v923z on 2009-12-31
> **dwhitney67 said:**
> I think that you have set your expectations too high.  How do you expect that the graphics of a separate window will show up in your text file, which is deriving its input from stdout (of gnuplot)?

No, I don't want that. I am perfectly happy with having a separate window for the plot (in fact, I don't even need a separate window, for I can set the terminal in gnuplot, and re-direct the graph to an image file). The question is not that, but why should the pipe break, if I want to capture both stderr and stdout into the same file. As a matter of fact, that is what I try to point out in a previous post: if I simply echo the commands to gnuplot on the command line, everything works. But once I move that line into the code, all hell breaks loose. In the meantime, I have experimented with the code, and it turns out that the stderr re-direction causes the error. If I have this
```

FILE* fin = popen("gnuplot > test.dat" ,"w");
```then stdout will be in test.dat. But I would like to get stderr, too. So, is there a way to instruct the pipe to dump stderr to the same file? (Beyond what I have already tried.) 
Also, you say that it worked on your system. Is there a way to track down what is different between yours and mine?
Cheers,
v923z

---

### Post by v923z on 2009-12-31
As it turns out, the problem is that popen invokes the shell, an in particular, it invokes the sh shell, while my default shell is bash. I.e., when I echo the command on the command line, it is in the bash shell, but when I invoke it in the code, it is passed to the sh shell. So, using sh's syntax,
```

FILE* fin = popen("gnuplot > test.dat 2>&1 " ,"w");

```
does what it is supposed to do, writing both stderr and stdout into test.dat.
v923z

---

### Post by dwhitney67 on 2010-01-01
I'm glad you sorted the issue with your system/application.

I also employed Fedora before switching to Ubuntu.  One of my dislikes with Ubuntu is that it shipped with a watered-down version of 'Bash' called 'Dash'.  I think that /bin/sh was pointing to 'Dash' (or possibly something else), and that was contrary to how Fedora is set up.  So, as sudo, I removed /bin/sh, and then recreated its symbolic link to point to Bash (/bin/bash).

I think I did something like:
```

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

```

This probably indicates why your original app (with the minor fix) worked on my system.

---

