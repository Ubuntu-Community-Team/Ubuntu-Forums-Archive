---
title: "How to compile FORTRAN 90? (what command)"
date: 2006-08-31
forum: Programming Talk
---

### Post by Strid on 2006-08-31
Hi,

I've been using FORTRAN 90 to make small programs that do mathmatical calculations for me. I've been using the compiler they've got at the university for a while (they have Enterprise Red Had Linux) machines. However, I would like to take my work home and do programming under Ubuntu. I've been using Pascal under a DOS enviroment previously, but now that I've moved on to Ubuntu, I might aswell get FORTRAN at home. 

Anyways, I went ahead and installed the Intel Fortran Compiler thing and the installation went fine, it seems.

My problem is .. what is the command that compiles the source code? I can't really find it. :)

Thanks alot!

---

### Post by bukwirm on 2006-09-01
Did you try f90 and f95?

Also, try "apropos fortran" and look though the results.

---

### Post by junglepeanut on 2006-09-02
ifort 

If you plan on doing more involved programming say need lapack or blas, you may find it a little complicated getting mkl to work. Also the ifort I am guessing is a trial version, so unless you are getting drastic performance gains I would stick with gfortran and g95. (I compile on gfortran, g95, ifort, and absoft, occasionaly for a friend on a salford.) Each has its own nuisances, and not all have well documented man pages so make sure to find the documentation. Ifortrans support is not very good unless you pay...you should have decent support for your trial, my prof called in, I did not bother. If you need additional help, post again. I cant promise but I check once a week for interesting things. Also you could pm me. I have dozens of makefiles, most are good enough to last you through your masters degree.

I am in the process of creating a very simple introduction to computational physics website, maybe I will post a link once it has enough work to keep somebody busy for at least a week. (I am really busy with my own thesis, so it is slow going.)

---

### Post by junglepeanut on 2006-09-02
Hmmm. Intersting, Denmark...any chance you can get me into NBI????

Just kidding (unless you can.)

I visit Copenhagen approx. once a year.

Good luck, feel free to pm me.

Jp

---

### Post by Strid on 2006-09-03
Hello, guys! Thank alot! I 'sudo apt-get'ed gfortran, and now it seems to work. It returned a couple of error messages from my code, which is a good sign - it what a compiler do when it doesn't compile! :)

By the way, junglepeanut, I actually study at NBI. What are your business in denmark?


EDIT: I got my program compiled properly via gfortran now. Works like a charm. It's nothing fancy, though. Atm, it's just a prompt where you input some data and then it bruteforces its way through some diffrential equations and outputs data to a file I can open in, say, GNUPlot or what I like. I might aswell use a dedicated mathmatics programming language (like Maple or MatLab) for things like that, but I have what I call 'house hold' programming as a hobby. And really - it's nothing fancy at all. :)

---

### Post by junglepeanut on 2006-09-03
Sounds like what many of us do. You will find that as the problems become more complex you will be very happy you chose to learn program in fortran instead of using mathematica or maple. But they will definetely, at least in my case, help to double check your results for some of the basic stuff.

---

### Post by Strid on 2006-09-04
PM'ed you back, junglepeanut! :)

I have another problem aswell, perhpaps you can help me with that?

If I wanted text to be written a specific place on the screen (80 characters by 24 lines), how do I do that? This is in the console or under DOS or other non-graphical enviroment. 
Lets say that I wanted a text string to be star at line 10, character 10. In, say, Pascal, I would do something like this:


```
Program XY;

Uses Crt;

Begin;
   GotoXY(10,10);
   Write('This text begins at line 10, character 10');
end;

End Program XY
```


Or in Qbasic:

```
LOCATE 10, 10: PRINT "This text begins at line 10, character"
```

Is there an equivalent to this in FORTRAN or am I left with no hope? I've been searching alot both on this forum and via Google, but I couldn't come up with anything useful.

Any input is appreciated!

Thanks alot,
Anders Christensen

---

### Post by junglepeanut on 2006-09-06
I would clear the screen (actually just basically is like hitting enter a bunch of times) and then using formatting options go down ten lines and over ten spaces.

I have to say though I normally don't bother making things look pretty, I just make my formatting so it is easy for gnuplot  to read.

I was guessing you wanted the screen cleared first if not you could probably do it simpler with some formatting option. Probably simpler even than this with formatting too. As there is a drop down formatter I just don't know it off my head. Just be careful with character counts as if they are to big then you run into pushing off the back, and it skips large spaces. Sorry I don't know more I just started Fortran 3 months ago. 

```
Program Star
Implicit None

    Integer :: k

	Do k=1,25

		Write(*,*)

	End Do

	Write(*,'(10X,A41)') 'This skips ten spaces before writing this'

	Do k=1,13
	
		Write(*,*)
	
	End Do

End Program Star
```

---

### Post by junglepeanut on 2006-09-06
Oh yeah and check your loop counts so it is just right place, I just wrote this quick thinking about the numbers you said for the size, but I could make easy mistakes etc.

---

### Post by Strid on 2006-09-10
Thank you for your reply! I found this way of doing it - its a pretty clever approach to the problem, actually.

```

      subroutine ClearScreen
      character*4 seq
      seq = char(27) // '[2J'
      print *, seq
      return
      end subroutine

      subroutine printat (x,y,str)
      integer x, y
      character*(*) str
      character*4 xstr, ystr
      write (xstr, '(I4)') x
      write (ystr, '(I4)') y
      print *, char(27), '[', trim(adjustl(ystr)),';',trim(adjustl(xstr)),'H',str
      return
      end

      program main
      call ClearScreen
      call printat (15, 22, 'botlft')
      call printat (60, 5, 'toprgt')
      call printat (10, 5, 'toplft')
      call printat (60, 20, 'botrgt')
      stop
      end
```

It's not particularly pretty, but it works very well. Your screen must support ANSI sequencing to do this, though. But Ubunutu does that, furtunately. :)

---

### Post by junglepeanut on 2006-09-11
:eek: 

I would have never have even looked into stuff like that, wow. 

I think yours makes mine look childish. Oh well. 

Very cool.

Back to Jackson ](*,)

---

