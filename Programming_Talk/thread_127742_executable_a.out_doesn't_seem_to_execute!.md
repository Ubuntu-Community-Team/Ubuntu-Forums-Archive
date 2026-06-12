---
title: "executable a.out doesn't seem to execute!"
date: 2006-02-09
forum: Programming Talk
---

### Post by daviddoregan on 2006-02-09
I'm pretty much a beginner to both Linux and programming.

Using g77 compiler, build-essential installed on Breezy.
I compile .f files, which generate a.out a binary executable.
Double clicking on a.out doesn't have any effect!

If I enter

./a.out > file

and then read file, I can see the results of my program.
But I can't figure out a way to see the results of my program just using executing a.out. Should I open a.out with some specific program?
Please help!

---

### Post by Mlehliw on 2006-02-09
Did you try just typing './a.out' alone in a terminal.

The '>' symbol redirects the output of a command into a file. In your case, the output of your program that normally would display on a terminal was being redirected into file, which you then were able to read.

---

### Post by daviddoregan on 2006-02-10
Perfect thanks! this step was so obvious that it wasn't in any help file :rolleyes:

---

### Post by skirkpatrick on 2006-02-10
As a side note, double-clicking a command-line program from nautilus causes it to execute.  Now depending on whether you told Nautilus to just run it or run it in a console will depend on what you see.  Of course if the program doesn't wait for something to happen when you run it in console from Nautilus, the console will close as soon as the program is finished.

---

### Post by daviddoregan on 2006-02-10
yeah it was Nautilus I was trying to use.
Here is my first tiny little FORTRAN 77 program:

* *** COMPOUND INTEREST CALCULATION
      
      BALNCE = 1000
      RATE   = 0.09
      RINT   = RATE * BALNCE
      BALNCE = BALNCE + RINT
      PRINT*, 'NEW BALANCE IS', BALNCE
      STOP
      END

Is there a way I can alter this so that the answer stays on the screen when I run a.out by double-clicking on it in Nautilus? *beginner*

---

### Post by skirkpatrick on 2006-02-10
Not sure how to do it in Fortran.

---

### Post by engla on 2006-02-10
[QUOTE=daviddoregan]Is there a way I can alter this so that the answer stays on the screen when I run a.out by double-clicking on it in Nautilus? *beginner*[/QUOTE]
You can solve it in two ways basically: either in your FORTRAN code or in your terminal settings.

I. Insert an infinite loop at the end of your program. I have no idea how to write that in fortran, but it shouldn't be hard. When you want to quit the program, you can type ctrl-C to interrupt it.

II. Modify your terminal profile. Normally, it's set to close the terminal when a command exits. Set it to keep the window open.

---

### Post by mjh007 on 2006-02-24
[QUOTE=engla]II. Modify your terminal profile. Normally, it's set to close the terminal when a command exits. Set it to keep the window open.[/QUOTE]

I'm also new to Fortran programming in Linux. Have used VF in windows. How do you go about doing the above. 

e.g. if I have write(*,*) in my program, how do I see the results on my screen without the terminal closing immediately?

---

### Post by jerome bettis on 2006-02-24
we should really have a sticky thread on how to write, compile, and run hello world.  this comes up every day. \\:D/

---

