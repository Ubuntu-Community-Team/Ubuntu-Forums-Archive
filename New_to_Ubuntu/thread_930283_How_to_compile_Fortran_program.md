---
title: "How to compile Fortran program"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by gulatiakshay on 2008-09-25
Hi, Well i had installed g77 through apt get now 
1.after writing a program in text editor i saved it on desktop...
2. OPen the Terminal Widnow and typing
     g77 hw.f -o hw
then i am getting now input directory

'''''
1. MY g77 is in usr/bin and my programe is on desktop....so tell me do i have to give the path for this like windows or it will automatically detect it on desk top

2. I also installed latex now how to open it usin terminal window......

---

### Post by Pro-reason on 2008-09-26
It's quite difficult to understand you.

Let's say you have a file located at *~/Desktop/hw.f*, and let's say that it contains the following code:

```

      program hw
         print *,"Hello World!"
      end program hw

```

To compile it, use the “g77” as you have already tried.  Obviously, you have to tell the command where to find your file.  It doesn't have telepathic powers.  To avoid having to include the full path, we shall use the “cd” command to change directory.

```

cd ~/Desktop
g77 **hw.f** -o **hw**
ls

```

We can then run the program you have just created:

```

./hello

```

It will print the message on the terminal.  The “./” at the beginning means “in the current directory”.

You sneaked in a question about LaTeX at the end.  Please only ask one question per thread.  Moreoever, a moment's Googling will give you all the answers you need (I have never used Fortran before).

---

