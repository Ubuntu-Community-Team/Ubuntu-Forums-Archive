---
title: "Trying to create executables fails (c++ compiler not working)"
date: 2016-04-06
forum: Packaging and Compiling Programs
---

### Post by JustusHolmes on 2016-04-06
hi guys,

I was trying to set up this program called [http://sympler.org/#Configure&Compile](http://sympler.org/#Configure&Compile) but at the last step I am getting the error "c++ compiler cannot create executables".

I am new to Ubuntu and would be happy if anybody could help me :)

Greetings

---

### Post by steeldriver on 2016-04-06
Hello and welcome to the forums

Your system doesn't seem to have a C++ compiler installed - you can install just g++ (which may be enough) or to get a more comprehensive build environment, install the build-essential package - either from Software Center or via the command line using

```

sudo apt-get install build-essential

```

---

### Post by TheFu on 2016-04-06
a)  copy/paste of text from  the output would be nicer than an image. Not a big deal for many, but it saves bandwidth for people who pay by the bit.
b) compilers have usual dependencies and strict dependencies. On ubuntu, it is usually easiest to
[LIST=1]
[*]Ensure the system is up-to-date - [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) explains normal, weekly, system maintenance. update/upgrade
[*]install the **build-essential** pkg, then the compiler (if that isn't included)
[/LIST]
Then try to compile a simple "Hello World" program. Does that work?
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

This [https://unix.stackexchange.com/questions/146402/configure-error-c-compiler-cannot-create-executables](https://unix.stackexchange.com/questions/146402/configure-error-c-compiler-cannot-create-executables) may help too. I can't see the image now and don't recall the exact error.  32-bit vs 64-bit seems to be the common issue for that error.

Hope this helps.

---

### Post by JustusHolmes on 2016-04-06
Thanks for your quick replies. I have tested it and the c++ compiler executes "hello world"

here is the full source code maybe this helps you to see what the problem is:

> shb@shb-VirtualBox:~$ cd Schreibtisch
shb@shb-VirtualBox:~/Schreibtisch$ g++ -o helloworld helloworld.cpp
shb@shb-VirtualBox:~/Schreibtisch$ ./helloworld
Hello World!

shb@shb-VirtualBox:~/Schreibtisch$ cd Sympler
shb@shb-VirtualBox:~/Schreibtisch/Sympler$ libtoolize --force
libtoolize: putting auxiliary files in `.'.
libtoolize: linking file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: linking file `m4/libtool.m4'
libtoolize: linking file `m4/ltoptions.m4'
libtoolize: linking file `m4/ltsugar.m4'
libtoolize: linking file `m4/ltversion.m4'
libtoolize: linking file `m4/lt~obsolete.m4'
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
shb@shb-VirtualBox:~/Schreibtisch/Sympler$ aclocal
aclocal: warning: autoconf input should be named 'configure.ac', not 'configure.in'
configure.in:30: warning: macro 'AM_PATH_GSL' not found in library
configure.in:31: warning: macro 'AM_PATH_XML2' not found in library
shb@shb-VirtualBox:~/Schreibtisch/Sympler$ autoconf
configure.in:30: error: possibly undefined macro: AM_PATH_GSL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:31: error: possibly undefined macro: AM_PATH_XML2
shb@shb-VirtualBox:~/Schreibtisch/Sympler$ automake --add-missing
automake: warning: autoconf input should be named 'configure.ac', not 'configure.in'
configure.in:13: installing './compile'
configure.in:24: installing './config.guess'
configure.in:24: installing './config.sub'
configure.in:5: installing './install-sh'
configure.in:5: installing './missing'
src/Makefile.am:5: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/Makefile.am: installing './depcomp'
automake: warning: autoconf input should be named 'configure.ac', not 'configure.in'
src/basic/source/Makefile.am:108: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/boundary/source/Makefile.am:17: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/calculator/source/Makefile.am:8: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/force/source/Makefile.am:51: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/function_parser/source/Makefile.am:18: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/geometry/head/Makefile.am:10: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/geometry/source/Makefile.am:16: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/geometry/stl/source/Makefile.am:12: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/integrator/source/Makefile.am:28: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/meter/grid_meter/source/Makefile.am:27: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/meter/source/Makefile.am:25: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/particle_creator/source/Makefile.am:24: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/postprocessor/source/Makefile.am:14: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/reflector/source/Makefile.am:14: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/thermostat/source/Makefile.am:24: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/tools/Makefile.am:6: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/tools/Makefile.am:3: warning: source file '../basic/source/vtk_support.cpp' is in a subdirectory,
src/tools/Makefile.am:3: but option 'subdir-objects' is disabled
automake: warning: possible forward-incompatibility.
automake: At least a source file is in a subdirectory, but the 'subdir-objects'
automake: automake option hasn't been enabled.  For now, the corresponding output
automake: object file(s) will be placed in the top-level directory.  However,
automake: this behaviour will change in future Automake versions: they will
automake: unconditionally cause object files to be placed in the same subdirectory
automake: of the corresponding sources.
automake: You are advised to start using 'subdir-objects' option throughout your
automake: project, to avoid future incompatibilities.
src/weighting_function/source/Makefile.am:14: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')

shb@shb-VirtualBox:~/Schreibtisch/Build$ /home/shb/Schreibtisch/Sympler/configure [options] CXXFLAGS="[cxxflags]"
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: [options]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for [options]-g++... no
checking for [options]-c++... no
checking for [options]-gpp... no
checking for [options]-aCC... no
checking for [options]-CC... no
checking for [options]-cxx... no
checking for [options]-cc++... no
checking for [options]-cl.exe... no
checking for [options]-FCC... no
checking for [options]-KCC... no
checking for [options]-RCC... no
checking for [options]-xlC_r... no
checking for [options]-xlC... no
checking for g++... g++
checking whether the C++ compiler works... no
configure: error: in `/home/shb/Schreibtisch/Build':
configure: error: C++ compiler cannot create executables
See `config.log' for more details
shb@shb-VirtualBox:~/Schreibtisch/Build$ 



---

### Post by steeldriver on 2016-04-06
[options] and [cxxflags] are not meant to be typed literally: from the link you posted:

> 
Useful [cxxflags] are (for more see the g++ documentation):  
    -O3: for optimised compilation with g++ 
    -fopenmp: For compilation with OpenMP parallelisation (currently still inefficient)
  and useful [options] are:
    --with-tnt: use tnt library and jama libraries 
    --with-superlu: use superlu  
    --enable-all-static: for a statically linked stand alone executable not  requiring any dynamical linking of libraries (except the runtime  compiled expressions of course). Unfortunately this option currently  causes SYMPLER to crash very often. We have this bug on our list.  Further bug reports on this issue are welcome. A bug-fix is even more  welcome. 


---

### Post by JustusHolmes on 2016-04-06
oh ok thanks! So they are optional?
But what is missing in my code to use sympler?

---

### Post by steeldriver on 2016-04-06
Probably nothing's missing - by writing

```

configure [options] CXXFLAGS="[cxxflags]"

```

you are making it look for an architecture-specific cross compiler called [SIZE=4][FONT=courier new][options]-g++[/FONT][/SIZE] which obviously doesn't exist[SIZE=4][FONT=courier new][/FONT][/SIZE]

---

### Post by JustusHolmes on 2016-04-07
It finally worked.
There was only one xml2 library missing.

But there is one thing left where I need your help:
as you can see in this code
> <Simulation simName="sim" inputFromResults="yes"><Controller dt="0.005" timesteps="500"><IntegratorVelocityVerletX species="fluid" velocity="flatvel"/></Controller><PairParticleScalar symbol="Epot" expression="0.5*4*(((1/rij)^6-1)*(1/rij)^6-((1/2.5)^6-1)*(1/2.5)^6)" cutoff="2.5" species1="fluid" species2="fluid"/><ParticleVector symbol="flatvel" expression="[v]-uVecZ(zCoord([v]))" species="fluid" overwrite="yes"/><LJ forceName="LJ" species1="fluid" species2="fluid" cutoff="2.5"/><Phase><LinkedListCreator/><BoundaryCuboid boxX="20" boxY="20" boxZ="5" periodicX="yes" periodicY="yes" periodicZ="yes"><ReflectorStochastic/><ParticleCreatorStatic species="fluid" nStaticPX="10" nStaticPY="10" nStaticPZ="1" corner1="(0,0,0)" corner2="(20,20,5)" temperature="1"/><!--     density = "0.8442" -->
<!-- temperature = "2.275"--></
BoundaryCuboid></Phase><MeterPosVel measureEvery="1" species="fluid"><OutputVTK nameOutputFile="VTK2D/pos.vtk"/></MeterPosVel></Simulation>
nameOutputFile="VTK2D/pos.vtk" "sim2D.xml" wants to save the output file in the "VTK2D" folder. I created this folder in "/home/shb/Schreibtisch/Build" and execute this code with with "/home/shb/Schreibtisch/Build/src/sympler/sim2D.xml"... but it doesn't save the output file there. 

How and where do I have to create the "VTK2D" folder?

---

### Post by TheFu on 2016-04-07
The directory should be relative to the CWD where the program is run.  So, if you open a terminal and cd to /home/shb/Schreibtisch/Build ... then it would be /home/shb/Schreibtisch/Build/VTK2D/

Make sense? I would just put the full-path that I wanted into the config files if it wasn't working. PWD/CWD are very important for software developers.  pwd is "Present Working Directory" (for any lurkers).
Run 
* pwd
* echo $CWD
to see them.  $CWD may not be set - depends on your config, but it often is whenever the prompt gets updated for old-guys. ;)

---

### Post by JustusHolmes on 2016-04-07
@TheFu: Thanks for your reply
the file is  "/home/shb/Schreibtisch/Build/VTK2D/"

the src file is in Build and with executing it with "shb@shb-VirtualBox:~/Schreibtisch/Build$ ./src/sympler sim2D.xml" I get a "geometry.vtk" and "function_parser.log" but not the needed output file :(

I even tried to put the "src" folder into the "VTK2D" folder but it doesn't create "pos.vtk"

---

### Post by TheFu on 2016-04-07
What is your Linux/Unix knowledge level?
Could be something simple like permissions or case sensitivity or that the code is broken.  Check the config files, carefully.

I'd add a few debug lines to the code that opens the file for writing, recompile and run again.  That assumes there isn't a way to just increase the verbose-ness for logging of the tool. I'd do that first.  Seems this isn't an issue for getting a compiler working anymore - perhaps asking for help in the place where the program project happens makes more sense?  I don't see any open issues on the github project page. [https://github.com/kauzlari/sympler](https://github.com/kauzlari/sympler)

---

### Post by JustusHolmes on 2016-04-07
sorry I am total newbie :D just started one day ago. I know it does work... but yeah I will just ask the people from sympler.

Thanks :)

---

### Post by TheFu on 2016-04-07
Ok - so ... [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) is my best advice for learning Linux.  Start with the 1st link, it explains the biggest issues for people new to Unix/Linux - will save you lots of frustration.

Good luck and keep at it.  We were all new at some point. ;)  I try not to forget that ... er ... 23 yrs after I first started trying to learn Unix.

---

