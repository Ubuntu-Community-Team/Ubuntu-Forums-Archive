---
title: "fortran77 problem on ubuntu(solved)"
date: 2013-05-19
forum: Programming Talk
---

### Post by adameye on 2013-05-19
Dear all:
   I can not compile the fortran program on ubuntu. please see attchement for next post, I tried to use f77,g77,ifort, but none of them work
I do not use fortran so I do not know how to debug the program, anyone can help me? it looks very easy,

```

f77 contour2d.f

/tmp/ccOQ8XAw.o: In function `MAIN__':
contour2d.f:(.text+0x1e4): undefined reference to `classify_'
contour2d.f:(.text+0x47d): undefined reference to `draw_'
contour2d.f:(.text+0x482): undefined reference to `sum_'
contour2d.f:(.text+0x487): undefined reference to `out_'
collect2: ld returned 1 exit status

```

I do have those files in the same directory, for example, a file classify2d.f:
"
CCCCC
CCCCC                             CLASSIFY 
CCCCC
c--- classify: classify cells as high or low density

      subroutine classify
      parameter (imax=256,jmax=256)
.........
"

I guess this is a different complier error? in my ubuntu, it can not recognize the subroutine classify?  
please let me know, thank you

---

### Post by adameye on 2013-05-19
please see attachment , thanks

---

### Post by alan9800 on 2013-05-19
Assuming that you have already installed [gfortran]("http://packages.ubuntu.com/precise/gfortran"), you could give a look to the [online documentation]("http://gcc.gnu.org/onlinedocs/gcc-4.6.3/gfortran/") about this compiler, especially to the [chapter 2]("http://gcc.gnu.org/onlinedocs/gcc-4.6.3/gfortran/Invoking-GNU-Fortran.html#Invoking-GNU-Fortran").

---

### Post by adameye on 2013-05-19
Hi:
  thanks for your reply, is this a complier problem, or a code problem? I don't use fortran, but only need a ./a.out to get what I want. So I am lost here, please help me

---

### Post by alan9800 on 2013-05-19
I gave a look to your attachments; could you please indicate the complete compilation command you used, so that we can see if there's something wrong?

---

### Post by adameye on 2013-05-19
Thanks, I cleared some stuff in attachment and attached the new original package here. I guess maybe library missing?
$ f77 contour2d.f
contour2d.f: In program `contour2d':
contour2d.f:128: warning:
         common /block1/ ni,nj,nk,deficit,flag,nvert,
                 ^
Padding of 2 bytes required before `delta' in common block `block1' at (^) -- consider reordering members, largest-type-size first
contour2d.f:158: warning:
           call sum
                ^
Reference to unimplemented intrinsic `SUM' at (^) (assumed EXTERNAL)
/tmp/ccwjFS69.o: In function `MAIN__':
contour2d.f:(.text+0x1e4): undefined reference to `classify_'
contour2d.f:(.text+0x47d): undefined reference to `draw_'
contour2d.f:(.text+0x482): undefined reference to `sum_'
contour2d.f:(.text+0x487): undefined reference to `out_'
collect2: ld returned 1 exit status

---

### Post by steeldriver on 2013-05-19
The zipfile you attached appears to contain a makefile - have you tried using it (instead of invoking f77 directly)? i.e.

```
make
```
or
```
make contour2d
```

---

### Post by adameye on 2013-05-19
thanks, I did try 'make', looks ok, and got a 'contour2d' (put a rho.smooth date file here, then use './contour2d, it looks it is running, but it is actually silly stuck here, not running at all)
so I tried to only complier the contour2d.f.  From my experience of C and Matlab, I could only complier contour2d.f and corresponding subprogram, and get an executable ./a.out or contour2d, but I failed.

any helps appreciated!!!

---

### Post by adameye on 2013-05-19
Hi,
  To make sure I did not misunderstand the package, here I post all files I got from the Author,
top_package.tar is the main file (even I only need the included "Contour2d" folder), and the lib_test.tar.gz is provided by the author when he knew I had problem to run the program.
suppose this run is very simple, I only need to provide a data file, named with rho.smooth, and specify some parameters from contour2d.inp. detailed descriptions are included in this package.


because it looks it is a technique problem so I have to come to this forum for the help. One of my paper is almost published but the reviewer suggests me to verify something, which can be calculated by this damned contour2d.f. I do not use Fortran!

any suggestions appreciated, you can also contact me on adameye AT gmail.com

---

### Post by alan9800 on 2013-05-19
in the README file, contained in the top_package archive, the author of the software writes> The command "make everything" will compile and install of these programs.
The command "make thebasics" will compile and install the ones that are most likely to be useful, in particular contour3 and gsmooth.Have you tried to follow these instructions, especially to run the command```
make everything
```:?:

---

### Post by adameye on 2013-05-20
hi, for make everything, I got.. should I get an older ifort? thanks


"
ifort   -c -o contour2.o contour2.f
ifort  -o ../Bin/contour2 contour2.o 
make[1]: Leaving directory `/home/Package/Source'
make contour3
make[1]: Entering directory `/home/Package/Source'
ifort  -o ../Bin/contour3 contour3.o 
ipo: error #11033: Il version for contour3.o (1.31421.2.893) does not match compiler's il version (1.33188.2.934), please regenerate
ifort: error #10014: problem during multi-file optimization compilation (code 1)
make[1]: *** [contour3] Error 1
make[1]: Leaving directory `/home/Package/Source'
make: *** [everything] Error 2


actually I only need one contour2d.f in Countour2d folder, shall I continue to working on this "ipo: error #11033: Il version for contour3.o..."? but if installing the whole package is useful, I will do it..

---

### Post by King Dude on 2013-05-20
My goodness, it's been quite sometime since I've last seen a Fortran programmer.

---

### Post by alan9800 on 2013-05-20
gfortran provides backwards compatibility for Fortran 77 and nearly all of the GNU language extensions supported by g77; you might install it```
sudo apt-get install gfortran
```and then try to compile all the files as suggested by the author of the software by using```
makefile everything
```

---

### Post by adameye on 2013-05-21
thanks, I just upgraded to ubuntu 12 from 8.0, after installing fort77, I have to delete the -fast in Makefile (otherwise error) ,then...

$make everything
...
/tmp/fort77-8191-1.c:353:22: error: conflicting types for &#8216;cxfft3_&#8217;
/tmp/fort77-8191-1.c:173:33: note: previous declaration of &#8216;cxfft3_&#8217; was here
/tmp/fort77-8191-1.c:434:22: error: conflicting types for &#8216;cfft99_&#8217;
/tmp/fort77-8191-1.c:370:33: note: previous declaration of &#8216;cfft99_&#8217; was here
/usr/bin/f77: aborting compilation
make[1]: *** [src3ft.o] Error 25
...

---

### Post by alan9800 on 2013-05-21
I sincerely don't understand why you don't install gfortran; this compiler is able to manage all the versions of fortran, so what is the reason for which you don't install it?

---

### Post by adameye on 2013-05-22
hi:
  in ubuntu 8 i have gfortran, after re-installing ubuntu 12, I forgot gfortran, now I installed gfortran and got same error if I try to complie contour2d.f

now I am struggleing to install a fortran debug software on ubuntu, I hope I can get some tools like Visual C++ or Matlab, which I can load the fortran code, and set the break point, step by step to see what is the hell of the problem

I am trying gdb with emacs but I am totall confused

---

### Post by alan9800 on 2013-05-22
> **adameye said:**
> now I am struggleing to install a fortran debug software on ubuntu, I hope I can get some tools like Visual C++ or Matlab, which I can load the fortran code, and set the break point, step by step to see what is the hell of the problemfor this purpose, [geany](https://apps.ubuntu.com/cat/applications/precise/geany/) might be somehow helpful.

---

### Post by steeldriver on 2013-05-22
I unpacked the top_package.tar and was able to build the contents of both the Source and Contour2d subdirs using gfortran

The files in Source needed one edit to get them to compile - replacing 'iargc(0)' with 'iargc()'. I don't know if this preserves the original intended function (I *am* old enough to have been taught F77 in school but I don't remember any of it) but it allows it to compile and run.

```
sed -i 's/iargc(0)/iargc()/' *.f
```

Then the make command I used was

```
make "FC=gfortran" "FLINK=gfortran" "FFLAGS=" "CLIB=-lm"
```

in both Source and Contour2d

After that I was able to run the 2 shell scripts in the top level Package directory i.e.

```

$ chmod +x sh.*
$ 
$ export PATH=$PATH:./Bin
$
$ ./sh.simple 
 gsmooth>    using G+ filter definition
$ cat contour.out 
# npix =   32768  nsurvey =   32768  nactive =   32768
  -2.0000  -46.0000   8.35829E-01  0.977264
  -1.7320  -60.0000   8.54776E-01  0.958374
  -1.5000  -47.0000   8.71579E-01  0.933197
  -1.2000   -9.0000   8.93391E-01  0.884918
  -1.0000   20.0000   9.09512E-01  0.841339
  -0.7000   40.0000   9.34714E-01  0.758026
  -0.4000   77.0000   9.61896E-01  0.655426
   0.0000  102.0000   9.97170E-01  0.500000
   0.4000   87.0000   1.03328E+00  0.344574
   0.7000   36.0000   1.06094E+00  0.241974
   1.0000  -16.0000   1.08986E+00  0.158661
   1.2000  -20.0000   1.10875E+00  0.115082
   1.5000  -55.0000   1.13640E+00  0.066803
   1.7320  -56.0000   1.15858E+00  0.041626
   2.0000  -43.0000   1.18453E+00  0.022736
$ 
$ ./sh.data
 gsmooth>    using G+ filter definition
 gsmooth>    using G+ filter definition
$ 
$ cat contour.out 
# npix =   32768  nsurvey =   32344  nactive =   32055
  -2.0000  -36.3750   8.34702E-01  0.977245
  -1.7320  -47.5000   8.53996E-01  0.958354
  -1.5000  -36.3750   8.71194E-01  0.933187
  -1.2000    1.6250   8.93356E-01  0.884925
  -1.0000   25.2500   9.09548E-01  0.841331
  -0.7000   49.5000   9.34802E-01  0.758039
  -0.4000   78.3750   9.61851E-01  0.655423
   0.0000   98.3750   9.97076E-01  0.500000
   0.4000   71.2500   1.03292E+00  0.344577
   0.7000   24.6250   1.06056E+00  0.241961
   1.0000  -25.2500   1.08882E+00  0.158669
   1.2000  -37.8750   1.10725E+00  0.115075
   1.5000  -66.6250   1.13594E+00  0.066813
   1.7320  -62.6250   1.15836E+00  0.041646
   2.0000  -43.8750   1.18561E+00  0.022755
$ 

```

I didn't try to run the Contour2d/contour2d program because I don't know what inputs it expects.

Hope this helps

---

### Post by adameye on 2013-05-23
man! you saved my life !
I could repeat what you have mentioned above, very excited.
I am working further now...

---

### Post by adameye on 2013-05-23
thanks, geany looks awesome, I am searching websites to find how to set break points... looks need some plugins, 
i downloaded geany-plugins-1.23,
then it needs new intltool, got it, then it needs gtk+-2.0.pc, can not find it...., how to install this gtk from sudo apt-get install? thanks
"
configure: error: Package requirements (geany >= 1.23) were not met:

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gtk+-2.0', required by 'Geany', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GEANY_CFLAGS
and GEANY_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
"

---

### Post by steeldriver on 2013-05-23
Are you trying to build geany plugins from source? why? is the plugin that you want not available from the repository? 

What is the problem now for which you need to debug the code? did the sh.xxx examples not run for you?

If you *really* need to build an application that uses the gtk+-2.0 library, you will need to install the **libgtk2.0-dev** package - that should install the .pc file in the appropriate place for pkg-config

Sorry for all the questions - I just don't want you to spend time on unnecessary things

---

### Post by alan9800 on 2013-05-23
> **adameye said:**
> thanks, geany looks awesome, I am searching websites to find how to set break points... looks need some plugins, 
i downloaded geany-plugins-1.23,
then it needs new intltool, got it, then it needs gtk+-2.0.pc, can not find it...., how to install this gtk from sudo apt-get install? thanks
"
configure: error: Package requirements (geany >= 1.23) were not met:

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gtk+-2.0', required by 'Geany', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GEANY_CFLAGS
and GEANY_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
"if you have troubles with geany, you may try [Code::Blocks]("https://apps.ubuntu.com/cat/applications/precise/codeblocks/").

---

### Post by adameye on 2013-05-24
> **steeldriver said:**
> Are you trying to build geany plugins from source? why? is the plugin that you want not available from the repository? 

What is the problem now for which you need to debug the code? did the sh.xxx examples not run for you?

If you *really* need to build an application that uses the gtk+-2.0 library, you will need to install the **libgtk2.0-dev** package - that should install the .pc file in the appropriate place for pkg-config

Sorry for all the questions - I just don't want you to spend time on unnecessary things

thanks, The contour2d folder has no examples as the author suggests in the file, so I am trying to debug and see what is going on here.

I think the main contour2d.f misses "open(5,file='contour2d.inp',form='formatted',status='old')" at the beginning, so I added it and now
I can run ./contour2d with a rho.smooth borrowed from the sh.simple!!!  
Is this a huge humor from the author of this package?

But when I generate my own binary rho.smooth file (from matlab fwrite), it can not be used for this fortran program, as it shows
"At line 14 of file denread2d.f (unit = 9, file = 'rho.smooth')
Fortran runtime error: Unformatted file structure has been corrupted
"
So now I need to figure out what is the hell difference between the binary file of this package and my binary file, 
looks I could not call the following c program in Matlab due to no complier found...
"

#include <stdio.h>

int ftwrite(ptr,size,nitems,stream)
char *ptr ;
unsigned size, nitems ;
FILE *stream ;

{
    int nbytes, nitem1 ;
    int errno ;

    errno = 0 ;
    nbytes = size*nitems ;
    if ( fwrite(&nbytes,sizeof(int),1,stream) != 1 )  {
	errno = -10 ;
	fprintf(stderr,"write error, is the file open ? \n") ;
	}
    nitem1 = fwrite(ptr,size,nitems,stream) ;
    if ( nitem1 != nitems ) {
	errno = -20 ;
	fprintf(stderr,"write error, %d items requested, %d items written. \n",
		nitems,nitem1) ;
    }
    if ( fwrite(&nbytes,sizeof(int),1,stream) != 1 )  {
	errno = -30 ;
	fprintf(stderr,"write error on second byte label \n") ;
    }
    
    return(errno) ;

}"


Many thanks for all

---

### Post by steeldriver on 2013-05-24
Hi again

I don't think the omission of the file open() operation was a mistake - the comment block at the top of the contour2d.f file says

```

c* Input:
c
c  Input variables are read from unit 5.  This is convenient for Unix users,
c  who can pipe the input file of their choice to the standard input.
c  Users on other systems may wish to have the program open a named input file.

```

which I take to mean that the original usage was intended to be

```
contour2d < contour2d.inp
```

You have just done exactly what is suggested there i.e. modified it to open a named file - which is fine as well.

I'm not familiar with your field or the background to any of this work, but as far as I can see the various 'contour' executables that the package provides are divided into 2 quite distinct types:


[LIST=1]
[*][contour3, contour6] simplified routines that are expected to be run direct from the command line with 3 or 4 command line arguments (parameters), as in the sh.simple and sh.data examples 
[*][contour2, contour2d] full featured routines that require many parameters and are run by piping a parameter file (contour2.inp, contour2d.inp) via stdin (or, as you have done, by modifying the source to read from a named file) 
[/LIST]
 
When I tried to run *either* contour2 or contour2d with the corresponding .inp file I get a similar error as you i.e.

```

$ contour2 < contour2.inp
At line 44 of file contour2.f (unit = 7, file = 'rho.smooth')
Fortran runtime error: I/O past end of record on unformatted file
$ 
$ Contour2d/contour2d < Contour2d/contour2d.inp
 vi
 reading data
At line 14 of file denread2d.f (unit = 9, file = 'rho.smooth')
Fortran runtime error: I/O past end of record on unformatted file
$ 

```

However that appears to be just because both the sh.simple and sh.data script create rho.smooth files for a 32x32x32 case

```

poisson_den 32 32768 12 > rho.out
gsmooth 32 2 rho.out rho.smooth t
contour3 32 rho.smooth p > contour.out

```

whereas contour2.inp is expecting 64x64x64 data and Contour2d/contour2d is expecting 256x256 - is that correct?

```

$ head -2 contour2.inp 
ni   nj   nk
64   64   64
$ 
$ head -2 Contour2d/contour2d.inp 
ni   nj  
256  256

```

When I changed those numbers to 32 both cases appear to run OK, i.e.

```
$ diff contour2.inp contour2.myinp
2c2
< 64   64   64
---
> 32   32   32
$ 
$ contour2 < contour2.myinp
# npix =   32768  nsurvey =   32344  nactive =   32055
  -2.0000  -36.3750   8.34747E-01  0.977214
  -1.7320  -47.5000   8.53939E-01  0.958385
  -1.5000  -36.3750   8.71194E-01  0.933187
  -1.2000    1.6250   8.93363E-01  0.884894
  -1.0000   25.2500   9.09552E-01  0.841300
  -0.7000   48.5000   9.34811E-01  0.758008
  -0.4000   78.3750   9.61852E-01  0.655392
   0.0000   98.3750   9.97076E-01  0.500000
   0.4000   71.2500   1.03291E+00  0.344608
   0.7000   24.6250   1.06055E+00  0.241992
   1.0000  -25.2500   1.08880E+00  0.158700
   1.2000  -37.8750   1.10723E+00  0.115106
   1.5000  -66.6250   1.13594E+00  0.066813
   1.7320  -62.6250   1.15845E+00  0.041615
   2.0000  -44.8750   1.18549E+00  0.022786

```

and

```

$ diff Contour2d/contour2d.inp Contour2d/contour2d.myinp 
2c2
< 256  256
---
> 32  32
$ 
$ Contour2d/contour2d < Contour2d/contour2d.myinp
 vi
 reading data
 guess0 =    1.0086807       shift0 =   0.10267337    
 number of cells =         1024
 number of cells in survey volume =    1024.0000    
.
.
.

```

So are you sure you have the correct .inp data for your MATLAB-generated rho.smooth file?

---

### Post by adameye on 2013-05-25
> **steeldriver said:**
> Hi again

I don't think the omission of the file open() operation was a mistake - the comment block at the top of the contour2d.f file says

```

c* Input:
c
c  Input variables are read from unit 5.  This is convenient for Unix users,
c  who can pipe the input file of their choice to the standard input.
c  Users on other systems may wish to have the program open a named input file.

```

which I take to mean that the original usage was intended to be

```
contour2d < contour2d.inp
```

You have just done exactly what is suggested there i.e. modified it to open a named file - which is fine as well.


So are you sure you have the correct .inp data for your MATLAB-generated rho.smooth file?

thank you very much for your help, it looks "Input variables are read from unit 5" means using './contour2d < contour2d.inp'!!!
first I can not find "getarg" in contour2d.f so I thought the .inp is not read from the command line...
I even do not know I need to use "<" for the command line input, even sh.simple implies this format..

now I am sure my .inp file is correct, but I noticed the ftwrite.c is not simply using "fwrite" but a more complicated format, however, m matlab
just simply uses "fwrite", so now I need to figure out how to write same binary in Matlab with ftwrite.c in the package

---

### Post by steeldriver on 2013-05-25
Well 'unit 5' in FORTRAN-speak is the UNIX standard input stream, so you're just redirecting 'stdin': see --> [http://en.wikipedia.org/wiki/Standard_streams#1950s:_Fortran](http://en.wikipedia.org/wiki/Standard_streams#1950s:_Fortran)

You can find information on how to deal with FORTRAN unformatted binary files in MATLAB here: --> [http://www.mathworks.com/support/solutions/en/data/1-15RS7/?solution=1-15RS7](http://www.mathworks.com/support/solutions/en/data/1-15RS7/?solution=1-15RS7)

If you look at the places where ftwrite is called, you can see that the rho array is written out as a single FORTRAN binary record in the format described in that link i.e. a single 'int32' header representing the number of bytes in the record, followed by the array values as 4-byte (single-precision) reals, followed by the int32 number of bytes again. So at its most basic (no error checking! you should really add some) you should be able to do something like:

```

% open a binary file for writing
fid = fopen('rho.matlab', 'wb');

% write the FORTRAN record header ( = the number of BYTES in the record)
fwrite(fid, length(rho)*4, 'int32');

% write the record data - NB we know the data consists of 
% single-precision floats which are 4 byte objects
nr = fwrite(fid, rho, 'real*4');

% [optionally check the return value 'nr' here]

% write the FORTRAN record footer ( = the number of BYTES in the record)
fwrite(fid, length(rho)*4, 'int32');

fclose(fid);

```

I checked it by reading the original 'rho.smooth' file using: 
```

% open a binary file for reading
fid = fopen('rho.smooth', 'rb');

% read the FORTRAN record header ( = the number of BYTES in the record)
hr = fread(fid, 1, 'int32');

% read the record data - NB we know the data was written as 4 byte
% objects using C function ftwrite(&rho[0][0][0],4,n*n*n,stdout)
rho = fread(fid, hr/4, 'real*4');

% [at this point we should check that 'hr' bytes were actually read]

% read the FORTRAN record footer - this should confirm the record length
fr = fread(fid, 1, 'int32');

fclose(fid);

% [again we could check here that fr == hr == 4 * # objects read]

```

in and then writing it back out as 'rho.matlab'. The UNIX 'diff' command said that rho.matlab was identical to the original rho.smooth, and Contour2d/contour2d ran when I replaced rho.smooth by rho.matlab

So there should be no need to resort to calling the C ftwrite function - although if you ever do need to do that kind of thing, you would use MEX: --> [http://www.mathworks.com/help/matlab/matlab_external/introducing-mex-files.html](http://www.mathworks.com/help/matlab/matlab_external/introducing-mex-files.html) 

Good luck!

---

### Post by adameye on 2013-05-27
thank you very much, I think it works now so far

considering I may have more programs run on Ubuntu, I may still try to know how to set breaking point in Geany, otherwise I may consider Code::Blocks, as alan9800 suggest.

at least this fortran 77 problem solved! thanks for all kindness people!

---

### Post by alan9800 on 2013-05-28
I've made a little search with Google about how to set breakpoints in Geany and it seems not so easy to do, thus I suggest you to use Code::Blocks; here's the link for setting breakpoints in Code::Blocks:
[http://wiki.codeblocks.org/index.php?title=Debugging_with_Code::Blocks#Set_Breakpoints](http://wiki.codeblocks.org/index.php?title=Debugging_with_Code::Blocks#Set_Breakpoints)

---

