---
title: "rdf_reader_subs.o: file not recognized"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by doktorinjh on 2012-08-01
I'm a new Ubuntu/Linux user, so please bear with my ignorance. I'm attempting to install a program using the make -f command and I've been able to suss out several errors, but now I'm stuck on this one:

@ubuntu:~/mdx$ make -f Makemdx_gfortran
gfortran mdx.o  graphx_mdx.o rdf_reader_subs.o -o mdx  -force_flat_namespace -I/usr/X11R6/include/ -I/sw/include/ -L/sw/lib  -lXm -L/usr/X11R6/lib -lXt -lX11 -lm  
rdf_reader_subs.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make: *** [mdx] Error 1

My programming knowledge is limited (but improving), so any help would be appreciated. 

As a side note, there is also a g77 version of this installation, but I haven't been able to find a version to install. If there's a way to use gcc or another compiler for the g77, that may work as well, but from what I've read, compiling through gfortran is better in the long run. 

Thanks for any help!

---

### Post by levlaz on 2012-08-01
Are you just trying to install gfortran?

If so .. it is in the repo. 

```
 sudo apt-get install gfortran 
```

No need to compile anything. 

Then when you are ready to run a program, this is what I do. 

1. Write the program in gedit 
2. Save the file as filename.f90 
3. In a terminal go to the directory where the file is and run 

```
 gfortran filename.f90 
```

4. This will output a file titled "a.out" 
5. In order to run the file in the same terminal window type 

```
 ./a.out 
```

6. The program will run.

---

### Post by doktorinjh on 2012-08-02
I have gfortran up and running, it's a graphics program (MDX) that I'm having problems loading/compiling.

Is it that this .o file is not being recognized by gfortran? 

Thanks!

---

### Post by steeldriver on 2012-08-02
since you said you had several previous errors I wonder whether one of your previous compile attempts created a 'bad' rdf_reader_subs.o file (e.g. wrong architecture?) which nevertheless appears to be up-to-date to 'make'

is there a 'clean' target in the makefile? something you can invoke like

```
make -f Makemdx_gfortran clean
```

if so I suggest running that first - if not you could move the rdf_reader_subs.o file out of the build dir and see if 'make' recompiles it

---

### Post by doktorinjh on 2012-08-03
Unfortunately, there's no clean target and that command resulted in a "No rule to make target 'clean'" error.

I tried to remove the references to that object in the Makemdx_gfortran file, but it looks like it's heavily referenced and results in many undefined reference errors.

There are other .o files referenced in the Makemdx_gfortran file and they seem to be behaving fine. 

I also tried to start again from scratch (from the .tar) and it compiles up to that point (none of the previous errors) and returns the same "file not recognized" error. Is there a way to verify that the .o file isn't corrupt?

Thanks again!

---

### Post by spjackson on 2012-08-03
```

file *.o

```
Does this show something for rdf_reader_subs.o that is different from all the others?

---

### Post by doktorinjh on 2012-08-06
Thanks for the help, I think I may have been able to fix the problem by deleting all of the old .o files and replacing them with newly compiled object files. The program executable now appears, but I think I need to link it in order for the other programs that call on it to find the executable ("which mdx" does not link to the program file).

---

