---
title: "gfortran doesnt work"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by Robinho45 on 2013-01-23
Hey guys,

i trying to set up a program for seismic wave propagation called SPECFEM. For adjusting the settings the program requires a fortran compiler. 

As far as i can tell from the synaptic package manager a fortran 95 compiler is installed on my system. 

When i start the file which sets up the system setting for the program the terminal tells me that fortran doesnt work. ("checking whether the Fortran compiler works... no")

When i typ "gfortran" i get "fatal error: no input files".

How can i get the compiler running?


Best regards,

Robin

---

### Post by tgalati4 on 2013-01-23
```
apt-cache search fortran
```

Shows there is gfortran4.4 (compatible with FORTRAN95), 4.5, 4.6, 4.7.  Perhaps you have a newer version that is not compatible with FORTRAN95

```
apt-cache policy gfortran
``` 

to determine what you have currently installed.

---

### Post by GordThompson on 2013-01-23
Wow, FORTRAN! *That *takes me back to my mis-spent youth!

I just had to give this a try. All I did was follow the "Hello World" example posted [here]("http://www.thegeekstuff.com/2009/11/fortran-hello-world-example-how-to-write-and-execute-fortran-program-on-linux-os/"). It worked fine for me. Give it a try and let us know how it turns out.

---

### Post by Warren Hill on 2013-01-23
I'm not surprised
```
gfortan
```Will not work because you have not told it what to compile.  Take a look here
[http://gcc.gnu.org/wiki/GFortranGettingStarted](http://gcc.gnu.org/wiki/GFortranGettingStarted)

---

### Post by sudodus on 2013-01-23
Look at this thread

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2107170[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2107170")

where you can find typical command lines to compile and or link scientific fortran programs.

Obviously fortran refuses to die ;-)

---

### Post by Robinho45 on 2013-01-24
hey guys,

thank you for your quick replies. Unfortunately i still couldn't get gfortran going so i made a short screencast that way you get a better idea about what is going on. Its to big to be uploaded here so i put it on youtube, i hope thats allowed here.

[http://youtu.be/DsycqFz_P6A](http://youtu.be/DsycqFz_P6A)

Thank you in advance.


Best regards.

---

### Post by sudodus on 2013-01-24
First we need to check if gfortran works at all.

Make a file named [FONT="Courier New"][SIZE="3"]prtime.f[/SIZE][/FONT] of the small fortran source code in this link.

[[COLOR="Red"]http://ubuntuforums.org/showpost.php?p=12468573&postcount=13[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12468573&postcount=13")

Try to compile and link it with the following command
```
 gfortran -o prtime prtime.f
```

That works for me in Ubuntu 12.04. It creates the executable file [FONT="Courier New"]prtime[/FONT], that you can run with the command
```
./prtime
``` (and it prints the current time to terminal and to the file [FONT="Courier New"]printed-time.txt[/FONT]).

Does this work for you?

If yes, gfortran works. If no you have to repair/reinstall gfortran.
--
Next we can try to make it work with your particular program package.

---

### Post by sudodus on 2013-01-24
I suggest that you search for help at the ***geodynamics.org*** web site.Maybe you can find someone to help you at its community via this link. Otherwise you need help by someone with experience teaching how to compile and link software packages using makefiles etc and maybe even debuggers.

[[COLOR="Red"]http://www.geodynamics.org/cig/community[/COLOR]]("http://www.geodynamics.org/cig/community")

Anyway, you need to set up the environment, and to perform all the steps successfully according to the manual

***manual_SPECFEM3D.pdf*** chapter 2.

---

### Post by GordThompson on 2013-01-24
> **Robinho45 said:**
> hey guys,

thank you for your quick replies. Unfortunately i still couldn't get gfortran going so i made a short screencast that way you get a better idea about what is going on. Its to big to be uploaded here so i put it on youtube, i hope thats allowed here.

[http://youtu.be/DsycqFz_P6A](http://youtu.be/DsycqFz_P6A)

Thank you in advance.


Best regards.
That was a good idea. Notice that in the installation instructions, in the paragraph immediately before the `./configure` command you copied-and-pasted, it says:

"This script will attempt to guess the appropriate configuration values for your system. However, at a minimum, it is recommended that you explicitly specify the appropriate command names for your Fortran compiler and MPI package"

Your FORTRAN compiler isn't `ifort`, it's `gfortran`. Also, you'll want to check if you have the `mpi-default-dev` package installed (that's where `mpif90` comes from).

FWIW, this just worked for me:

```
./configure FC=gfortran MPIFC=mpif90
```Finally, as sudodus said, you should read the rest of the instructions again and make sure you have followed all of the other recommended steps.

---

