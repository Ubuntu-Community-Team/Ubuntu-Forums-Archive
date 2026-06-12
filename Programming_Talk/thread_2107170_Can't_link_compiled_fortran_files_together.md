---
title: "Can't link compiled fortran files together"
date: 2013-01-21
forum: Programming Talk
---

### Post by msgeo on 2013-01-21
hi!
I'm new to Ubuntu and working on a Fortran based program!
got some errors and I'm sure I'll find my answer here...
so...here is the problem:
I have some .f files that needed to be compiled and then linked together and create a single file.
I installed gfortran on my Ubuntu and compiled .f files using ```
gfortran -c filename.f
``` 
files compiled successfully with some warnings that aren't important!
now I need to link them together using
```
gfortran -o file1.o file2.o file3.o -o outputfilename
```
 
but I get this error:
 
```
 
lateralf.o: In function `MAIN__':
lateralf.f:(.text+0x6733b): undefined reference to `time_'
lateralf.f:(.text+0x72abb): undefined reference to `time_'
collect2: error: ld returned 1 exit status

```
 
 
what should i do?
thanks....

---

### Post by bouncingwilf on 2013-01-21
Not sure where time is defined or if it is an intrinsic but it looks as though you may need to add the appropriate library to the linker line i.e. append  -llibrary_where_time-_function_is


Bouncingwilf

---

### Post by msgeo on 2013-01-22
> **bouncingwilf said:**
> Not sure where time is defined or if it is an intrinsic but it looks as though you may need to add the appropriate library to the linker line i.e. append  -llibrary_where_time-_function_is


Bouncingwilf

thanks...
i should mention that I'm able to successfully compile and link those files on my old machine with fedora 2 .4.22 using gcc commands!
but on this one with Ubuntu 12.10 using gfortran i get this error!

---

### Post by steeldriver on 2013-01-22
if it's using the same linker backend (ld) as gcc, then the link order is significant i.e. if file3.o contains main and file1.o has symbols used by main then file1.o needs to be to the right of file3.o on the link line

---

### Post by msgeo on 2013-01-22
> **steeldriver said:**
> if it's using the same linker backend (ld) as gcc, then the link order is significant i.e. if file3.o contains main and file1.o has symbols used by main then file1.o needs to be to the right of file3.o on the link line


thanks.
don't know if it's using the same linker backend or not but changing orders didn't work.
can this happen because of some missing files?

---

### Post by sudodus on 2013-01-22
I think time is not included in pure fortran, but it is in C.

Can you compile and link it in Ubuntu with gcc as before?

Can you link it to a C library with time?

---

### Post by steeldriver on 2013-01-22
^^^ that's what google is telling me as well - it looks like under g77 it was available from libg2c but that's not part of the gfortran distribution... ?

---

### Post by msgeo on 2013-01-22
> **sudodus said:**
> I think time is not included in pure fortran, but it is in C.

Can you compile and link it in Ubuntu with gcc as before?

Can you link it to a C library with time?

> **steeldriver said:**
> ^^^ that's what google is telling me as well - it looks like under g77 it was available from libg2c but that's not part of the gfortran distribution... ?



thank you.
""Can you compile and link it in Ubuntu with gcc as before?""
I can compile with gcc but when i try to link files it gives me a list of errors like this:

```

...........
gheisha_2002d.f:(.text+0x5c86f): undefined reference to `_gfortran_st_write_done'
gheisha_2002d.f:(.text+0x5cc4e): undefined reference to `_gfortran_st_write'
gheisha_2002d.f:(.text+0x5cc5c): undefined reference to `_gfortran_st_write_done'
gheisha_2002d.f:(.text+0x5cd03): undefined reference to `_gfortran_st_write'
gheisha_2002d.f:(.text+0x5cd11): undefined reference to `_gfortran_st_write_done'
gheisha_2002d.f:(.text+0x5d04c): undefined reference to `_gfortran_st_write'
gheisha_2002d.f:(.text+0x5d05a): undefined reference to `_gfortran_st_write_done'
collect2: error: ld returned 1 exit status
```""Can you link it to a C library with time?"" 
sorry but I don't know how i should do that.


is there any way to have g77 compiler on my Ubuntu?



When i compile and link with f77 instead of gfortran it gives me the same error plus one interesting line:

```
lateralf.o: In function `MAIN__':
fort77-28275-1.c:(.text+0x584): undefined reference to `time_'
fort77-28275-1.c:(.text+0x8bae): undefined reference to `time_'
[B]lateralf.o: In function `prtime_':
fort77-28275-1.c:(.text+0x3428a): undefined reference to `date_and_time__'
collect2: error: ld returned 1 exit status[/B]
```
PRTIME is this:

    SUBROUTINE PRTIME( TTIME )

```
C-----------------------------------------------------------------------
C  PR(INT) TIME
C
C  PRINTS PRESENT DATE AND TIME AND GIVES IT IN A FORMAT SUITED FOR THE
C  RUNHEADER AND EVENTHEADER.
C  THIS SUBROUTINE IS CALLED FROM AAMAIN AND START.
C  ARGUMENT:
C   TTIME  = TIME (YYMMDD)
C
C  IF OUR DATE ROUTINE DOES NOT FIT TO YOUR COMPUTER, PLEASE REPLACE
C  IT BY A SUITABLE ROUTINE OF YOUR SYSTEM
C  FOR COMPILERS WITH NEWER DATE FUNCTIONS, INCLUDING DEC UNIX f77
C  AND RECENT GNU g77 >0.5.21 (egcs 1.1.x, gcc 2.95, ...)
C  IF YOR COMPUTER DOES NOT KNOW SUBROUT. DATE_AND_TIME
C  REPLACE THIS CALL BY A CALL TO YOUR SYSTEM ROUTINES TO
C  FILL THE INTEGERS: IYEAR, MONTH, IDAY, IHOUR, IMINU, ISEC
      CALL DATE_AND_TIME( YYYYMMDD, HHMMSS )
      READ(YYYYMMDD,'(I4,2I2)') IYEAR,MONTH,IDAY
      READ(HHMMSS,'(3I2)') IHOUR,IMINU,ISEC
      write(7,100) IDAY,MONTH,IYEAR,IHOUR,IMINU,ISEC
      TTIME = MOD(IYEAR,100)*10000 + MONTH*100 + IDAY
 100  FORMAT(' PRESENT TIME : ',I2.2,'.',I2.2,'.',I4,I4.2,':',I2.2,
     *       ':',I2.2)

      RETURN
      END

```

---

### Post by sudodus on 2013-01-22
Please post your link command line (or makefile)!

As an example, the -lm option solved the problem with undefined reference in another case (in an Ubuntu Forums thread)

```
cc -o sqrt sqrt.c -lm
```

---

### Post by sudodus on 2013-01-22
Read the following thread

[[COLOR="Red"]http://valhalla.fcaglp.unlp.edu.ar/~computacion/Manuales/Online/flinux/index.html[/COLOR]]("http://valhalla.fcaglp.unlp.edu.ar/~computacion/Manuales/Online/flinux/index.html")

>  The above examples should be enough to get you started making use of Fortran in Linux using f77. Of course, more flexibility is offered using the f2c/gcc combination because more options are available. (f2c and gcc have good man pages, so I don't need to describe them here.) For example, the command:

$ f2c f77demo.f

creates the file f77demo.c, and:

$ gcc -o demoexe f77demo.c -lf2c -lm

creates the demoexe executable, and together they are equivalent to the f77 command shown earlier. Notice that we had to include the f2c and m libraries explicitly this time--and they must be listed in this order. Failure to include these two libraries would cause the compiler to complain. For example, leaving off the -lm option for our example program produces the errors:

Undefined symbol _exp referenced from text segment
Undefined symbol _sin referenced from text segment

because the references to the sine and exponential functions in subroutine TRIG could not be resolved.

This web page looks old, but it is worth trying. If no go, search the internet for other link. I used this search string

[FONT="Courier New"][SIZE="3"]link time function into fortran linux[/SIZE][/FONT]

Good luck :-)

---

### Post by msgeo on 2013-01-22
> **sudodus said:**
> Please post your link command line (or makefile)!

As an example, the -lm option solved the problem with undefined reference in another case (in an Ubuntu Forums thread)

```
cc -o sqrt sqrt.c -lm
```

sorry but by link command line do you mean this?
```
gfortran -o cor69 lateralf.o qgsjet-II-03.o gheisha_2002d.o
```


there are a lot of make file...which one should i post here?

---

### Post by sudodus on 2013-01-22
> **msgeo said:**
> sorry but by link command line do you mean this?
```
gfortran -o cor69 lateralf.o qgsjet-II-03.o gheisha_2002d.o
```


there are a lot of make file...which one should i post here?

If you post your makefiles for this particular program (or links to them), it might be easier to help.

I have two questions before we continue to try other things:

1. Did you try to repeat (in Ubuntu) the method that worked with fedora 2 .4.22 using gcc commands?
2. Did you try using the f2c/gcc combination according to this link?

[[COLOR="Red"]http://valhalla.fcaglp.unlp.edu.ar/~computacion/Manuales/Online/flinux/index.html[/COLOR]]("http://valhalla.fcaglp.unlp.edu.ar/~computacion/Manuales/Online/flinux/index.html")

---

### Post by sudodus on 2013-01-22
I had some time to fix your program:

1. Declaration of character variables
2. Opening of file (not necessary, otherwise the program writes to the file [FONT="Courier New"]fort.7[/FONT])
3. Added a write statement to the terminal write(*,...)

And simply used
```
 gfortran -o prtime prtime.f
```
which compiled and linked a working program for me :-)

```
C-----------------------------------------------------------------------
C  PR(INT) TIME
C
C  PRINTS PRESENT DATE AND TIME AND GIVES IT IN A FORMAT SUITED FOR THE
C  RUNHEADER AND EVENTHEADER.
C  THIS SUBROUTINE IS CALLED FROM AAMAIN AND START.
C  ARGUMENT:
C   TTIME  = TIME (YYMMDD)
C
C  IF OUR DATE ROUTINE DOES NOT FIT TO YOUR COMPUTER, PLEASE REPLACE
C  IT BY A SUITABLE ROUTINE OF YOUR SYSTEM
C  FOR COMPILERS WITH NEWER DATE FUNCTIONS, INCLUDING DEC UNIX f77
C  AND RECENT GNU g77 >0.5.21 (egcs 1.1.x, gcc 2.95, ...)
C  IF YOR COMPUTER DOES NOT KNOW SUBROUT. DATE_AND_TIME
C  REPLACE THIS CALL BY A CALL TO YOUR SYSTEM ROUTINES TO
C  FILL THE INTEGERS: IYEAR, MONTH, IDAY, IHOUR, IMINU, ISEC

      character*8 YYYYMMDD
      character*6 HHMMSS

      open(7,file="printed-time.txt")

      CALL DATE_AND_TIME( YYYYMMDD, HHMMSS )
      READ(YYYYMMDD,'(I4,2I2)') IYEAR,MONTH,IDAY
      READ(HHMMSS,'(3I2)') IHOUR,IMINU,ISEC
      write(7,100) IDAY,MONTH,IYEAR,IHOUR,IMINU,ISEC
      write(*,100) IDAY,MONTH,IYEAR,IHOUR,IMINU,ISEC
      TTIME = MOD(IYEAR,100)*10000 + MONTH*100 + IDAY
 100  FORMAT(' PRESENT TIME : ',I2.2,'.',I2.2,'.',I4,I4.2,':',I2.2,
     *       ':',I2.2)

      RETURN
      END
```

---

### Post by msgeo on 2013-01-22
> **sudodus said:**
> I had some time to fix your program:
 
1. Declaration of character variables
2. Opening of file (not necessary, otherwise the program writes to the file fort.7)
3. Added a write statement to the terminal write(*,...)
 
And simply used
```
 gfortran -o prtime prtime.f
```
which compiled and linked a working program for me :smile:

 
Thank you so much for the time you spent on this. 
but the problem seems to be unsolved.
 
 
first to your previous question I should say that I used gcc/f2c combination but that one also gives  some errors like this:
```
 
 
/tmp/fort77-29566-1.c:17864:12: error: conflicting types for &#8216;fctcos_&#8217;
/tmp/fort77-29566-1.c:17302:33: note: previous declaration of &#8216;fctcos_&#8217; was here
/tmp/fort77-29566-1.c:26703:22: error: conflicting types for &#8216;rtmi_&#8217;
/tmp/fort77-29566-1.c:17296:33: note: previous declaration of &#8216;rtmi_&#8217; was here
/usr/bin/f77: aborting compilation

```
 
and about your correction on the PRTIME subroutine I should say that this a only a small part of the program and this is not my program.
this a scientific program for Simulating cosmic rays.
that one also comes with some errors:
 
```
 
      character*8 YYYYMMDD                                              
                          1
Error: Symbol 'yyyymmdd' at (1) already has basic type of CHARACTER
lateralf.f:19183.24:
 
      character*6 HHMMSS                                                
                        1
Error: Symbol 'hhmmss' at (1) already has basic type of CHARACTER
lateralf.f:35547.10:

```
 
 
here is the original file:
 
[http://sdrv.ms/Xwz3il](http://sdrv.ms/Xwz3il)
 
and here is some snapshots of the program directory:
[http://sdrv.ms/VRokm2](http://sdrv.ms/VRokm2)
[http://sdrv.ms/Uilgz3](http://sdrv.ms/Uilgz3)
 
also i mentioned earlier that I'm able to compile files with gcc just like fedora but when I try to link files it comes with some errors!

---

### Post by sudodus on 2013-01-22
> **msgeo said:**
> 
first to your previous question I should say that I used gcc/f2c combination but that one also gives  some errors like this:
```
 
/tmp/fort77-29566-1.c:17864:12: error: conflicting types for &#8216;fctcos_&#8217;
/tmp/fort77-29566-1.c:17302:33: note: previous declaration of &#8216;fctcos_&#8217; was here
/tmp/fort77-29566-1.c:26703:22: error: conflicting types for &#8216;rtmi_&#8217;
/tmp/fort77-29566-1.c:17296:33: note: previous declaration of &#8216;rtmi_&#8217; was here
/usr/bin/f77: aborting compilation

```

I see. That did not help :-(

Probably you had some other compiler or linker version or a library available in Fedora, that you don't have (yet) in Ubuntu.
>  
and about your correction on the PRTIME subroutine I should say that this a only a small part of the program and this is not my program.
this a scientific program for Simulating cosmic rays.
that one also comes with some errors:
 
```
 
      character*8 YYYYMMDD                                              
                          1
Error: Symbol 'yyyymmdd' at (1) already has basic type of CHARACTER
lateralf.f:19183.24:
 
      character*6 HHMMSS                                                
                        1
Error: Symbol 'hhmmss' at (1) already has basic type of CHARACTER
lateralf.f:35547.10:

```

Well, I had only the snippet you posted, and I needed declarations of the character variables to make the compiler happy. Obviously there are some kind of include statements or global statements, that declare the character variables.

***But I would like to know if you can create a working program of the fortran code in post #13 using the command line in the same post***. That will show if your compiler and linker have enough 'horsepower' to do that (for example if there is such a time function or subroutine).

I am running Ubuntu 12.04 LTS 32-bit with pae
```
uname -a
Linux ssd-grund 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686 i686 i386 GNU/Linux
```
> 
 
here is the original file:
 
[http://sdrv.ms/Xwz3il](http://sdrv.ms/Xwz3il)
 
and here is some snapshots of the program directory:
[http://sdrv.ms/VRokm2](http://sdrv.ms/VRokm2)
[http://sdrv.ms/Uilgz3](http://sdrv.ms/Uilgz3)
 
also i mentioned earlier that I'm able to compile files with gcc just like fedora but when I try to link files it comes with some errors!
I'll look at that later.

---

### Post by sudodus on 2013-01-22
> **msgeo said:**
> sorry but by link command line do you mean this?
```
gfortran -o cor69 lateralf.o qgsjet-II-03.o gheisha_2002d.o
```


there are a lot of make file...which one should i post here?

The .o files are compiled object code files. It might be enough, but you might need some kind of reference to the linker or some libraries (if more than the default ones are needed).

This could be possible to see in one of the makefiles.
--
With the snippet in post #13 it was possible for me to compile to an object file with
```
gfortran -c prtime.f
```
and to link with
```
gfortran -o prtime-from-o prtime.o
```
It created a file identical to the one created directly from the fortran source code file. So yes, it could be possible to link with the command you suggested, at least concerning the prtime subroutine.

---

### Post by sudodus on 2013-01-22
> **msgeo said:**
> ... 
 
here is the original file:
 
[http://sdrv.ms/Xwz3il](http://sdrv.ms/Xwz3il)
 
and here is some snapshots of the program directory:
[http://sdrv.ms/VRokm2](http://sdrv.ms/VRokm2)
[http://sdrv.ms/Uilgz3](http://sdrv.ms/Uilgz3)
 
also i mentioned earlier that I'm able to compile files with gcc just like fedora but when I try to link files it comes with some errors!
I looked at it. Yes, I could see the whole time subroutine
```
      SUBROUTINE PRTIME( TTIME )
```
with declaration of variables, that were not there in the snippet.

I also had a second look at the command line in post #1

```
gfortran -o file1.o file2.o file3.o -o outputfilename
```
I think you'd make the compiler/linker confused with the two -o options. First you tell it to write the final program to [FONT="Courier New"]file1.o[/FONT] and then to [FONT="Courier New"]outputfilename[/FONT]. The correct syntax should be

```
gfortran -o outputfilename file1.o file2.o file3.o
```

The command line in post #11 looks correct.
```
gfortran -o cor69 lateralf.o qgsjet-II-03.o gheisha_2002d.o
```
and I guess this is the real thing :-)

If you still have problems, maybe you should check, if you have double definitions or calls to the time subroutine, that there is another one, that cannot be resolved.

What about this one?

```

      INTEGER          ILEFTA,ILEFTB,TIME
      EXTERNAL         TIME
...
C  TIME AT BEGINNING

      ILEFTA = TIME()
...
...
C  TIME SINCE BEGINNING

      ILEFTB = TIME()

      TDIFF  = ILEFTB - ILEFTA

```
These are not calls to or via PRTIME

---

### Post by msgeo on 2013-01-23
> **sudodus said:**
> 

***But I would like to know if you can create a working program of the fortran code in post #13 using the command line in the same post***. 

yes.that file compiled and linked successfully with gfortran.

---

### Post by msgeo on 2013-01-23
I'm  really  grateful for your help...
this ""time"" function isn't really  important but  i don't know how to get rid of it!

just downloaded the fedora 18 to see if i can compile and link files on that

---

### Post by sudodus on 2013-01-23
> **msgeo said:**
> yes.that file compiled and linked successfully with gfortran.

Then I think the problem is the call of
```
TIME()
```
So you should make a function or subroutine instead of that to use the same time call as in PRTIME,

```
CALL DATE_AND_TIME( YYYYMMDD, HHMMSS )
```
or some other call to the system time that is supported, and use the output of that instead of the external TIME() call. You should also check what unit it is supposed to be (seconds?)

---

### Post by sudodus on 2013-01-23
> **msgeo said:**
> I'm  really  grateful for your help...
this ""time"" function isn't really  important but  i don't know how to get rid of it!

just downloaded the fedora 18 to see if i can compile and link files on that

First find it in the source code!

Then decide what to do: if you need it, or if you can simply 'comment it away' (putting a C in the first position of the lines where it is). Also look for

```

ILEFTA
ILEFTB
TDIFF

``` and see how they are used. No division by zero please ;-)

---

### Post by msgeo on 2013-01-23
it's impossible to get rid of Time....
its wide speared through all of the program!
may you please chack if you're able to link these file on your system or getting the same error like me?

[http://sdrv.ms/YmIQOS](http://sdrv.ms/YmIQOS)
[http://sdrv.ms/YmIzva](http://sdrv.ms/YmIzva)
[http://sdrv.ms/YmIDv3](http://sdrv.ms/YmIDv3)

these are the three files that i'm trying to link using:
```
gfortran -o hi  gheisha_2002d.o qgsjet-II-03.o lateralf.o
```

and getting some warnings + this error:
```

/tmp/ccIS2aMH.o: In function `MAIN__':
lateralf.f:(.text+0x6733b): undefined reference to `time_'
lateralf.f:(.text+0x72abb): undefined reference to `time_'
collect2: error: ld returned 1 exit status
```

---

### Post by sudodus on 2013-01-23
> **msgeo said:**
> it's impossible to get rid of Time....
its wide speared through all of the program!

No it is not wide spread. Only two instances in lateralf.f and there are also only a few TDIFF, ILEFTB and ILEFTA instances in that same file. So you can comment them away, and you'll get TDIFF=0 by this write sentence

```
write(7,201) ISHW,TDIFF,TDIFF/ISHW,IRECOR,IRECOR/ISHW,
```

This is a fairly big scientic program package with approx 70000 program lines (50000 real program code lines).

You need to know about fortran, or have someone who knows guiding your work, if you don't know about it. Otherwise you won't know if you succeed or not. You might compile and link it, but how would you know that it produces reasonable results?

You can disable the calls to time with
```
sed "s/.*TIME()/Csudodus&/" lateralf.f>lateralf.g
```
and check the result with
```
diff lateralf.f lateralf.g
```
Finally move the files
```
mv lateralf.f lateralf.f0
mv lateralf.g lateralf.f
```

I can compile and link the result. But the program stops early, because I have no input data files.

Good luck and please tell us a little about your work :-)

---

### Post by msgeo on 2013-01-23
> **sudodus said:**
> 
 
I can compile and link the result. But the program stops early, because I have no input data files.
 
Good luck and please tell us a little about your work :-)
 
 
 
Thank you so much!
 
yes...I can compile and link the result too but i should check the result with my supervisor to be confident!
 
and about this program I should say that I'm a postgraduate astrophysic student and this program help us to simulate the path of cosmic rays!
 
I just want to ask you to follow this thread in coming days if it's possible for you.
 
Thanks you so much!

---

### Post by sudodus on 2013-01-23
> **msgeo said:**
> Thank you so much!
 
yes...I can compile and link the result too but i should check the result with my supervisor to be confident!
 
and about this program I should say that I'm a graduate astrophysic student and this program help us to simulate the path of cosmic rays!
 
I just want to ask you to follow this thread in coming days if it's possible for you.
 
Thanks you so much!

You are welcome :-)

Yes, I'm subscribing to this thread, so I'll see if there will be new posts.

I'm glad that you will check the results with your supervisor, and I think it is important that you are open with the changes made to the program. Check with her/him, if it is OK to skip that time function. Otherwise you can make a new function via the subroutine call
```
CALL DATE_AND_TIME( YYYYMMDD, HHMMSS )
```

Good luck with your research project :KS

ps/
Long ago I wrote a master thesis about lab experiments shooting plasma towards magnetic and non-magnetic bodies (simulating for example northern and southern light and the corresponding interaction patterns at the moon). But I've been working with metallurgy and metal working to make a living.
/ds

---

