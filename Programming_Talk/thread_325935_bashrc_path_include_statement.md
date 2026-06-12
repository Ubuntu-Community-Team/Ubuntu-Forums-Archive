---
title: "bashrc path include statement:"
date: 2006-12-26
forum: Programming Talk
---

### Post by newsman on 2006-12-26
I am trying to build omnetpp from source... i get the following message everytime:


/include -I. -DBUILDING_SIM   -I../nedxml -o distrib.o distrib.cc
opp_msgc -Xnc -Xns sim_std.msg
make[1]: opp_msgc: Command not found
make[1]: *** [sim_std_m.cc] Error 127
make[1]: Leaving directory `/opt/omnetpp-3.4b2/src/sim'
make: *** [sim] Error 2


I know why, opp_msg path should be included in bashrc file but i have done this as follows:

export PATH=$PATH:/opt/omnetpp-3.4b2/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/omnetpp-3.4b2/lib


Is there something wrong with the path statement above???

---

### Post by lnostdal on 2006-12-26
> **newsman said:**
> I am trying to build omnetpp from source... i get the following message everytime:


/include -I. -DBUILDING_SIM   -I../nedxml -o distrib.o distrib.cc
opp_msgc -Xnc -Xns sim_std.msg
make[1]: opp_msgc: Command not found
make[1]: *** [sim_std_m.cc] Error 127
make[1]: Leaving directory `/opt/omnetpp-3.4b2/src/sim'
make: *** [sim] Error 2


I know why, opp_msg path should be included in bashrc file but i have done this as follows:

export PATH=$PATH:/opt/omnetpp-3.4b2/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/omnetpp-3.4b2/lib


Is there something wrong with the path statement above???

have you tried to re-login or doing `source .bashrc' ..?

---

### Post by newsman on 2006-12-26
yep i tried relogin,,, reboot and relogin

is there any other way to specify the paths???

---

### Post by newsman on 2006-12-26
i typed printenv, it displays all the paths correctly but still i get errors and i don't know why??

TCL_LIBRARY=:/opt/ActiveTcl-8.4/lib:/usr/lib/tcl8.4
PATH=/opt/msp430/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/omnetpp-3.4b2/bin:/opt/ActiveTcl-8.4/bin


thus i don't know why i am getting errors

Even in my own directory if i call opp_msgc i get the following output,, so why is it not detecting during installation?

opp_msgc
opp_msgc - part of OMNeT++. (c) 2002-2005 Andras Varga
Translates .msg files into C++

Usage: opp_msgc [-s <cc-file-suffix>] [-t <h-file-suffix>]
                [-I <dir> -I ...] [-h] [-Xnc] [-Xnd] <nedfile>
  -I <dir>    add directory to include path
  -s <suffix> output C++ file suffix (defaults to: _m.cc)
  -t <suffix> output C++ header file suffix (defaults to: _m.h)
  -P <symbol> add dllexport/dllimport symbol to class declarations
  -h          output in current directory
  -Xnc        do not generate the classes, only object descriptions
  -Xnd        do not generate object descriptions
  -Xns        do not generate setters in object descriptions

I heard about doing a "symlink".. to the directory,, but i don't know what is that, how to do that and whether that may solve the problem???

---

### Post by newsman on 2006-12-26
i just did a symlink to opp_mspgc in the same directory as the error (src/sim) but it did not help.. it still exiting with same error

---

### Post by newsman on 2006-12-27
everytime i run configure i get this at the end:

WARNING: You selected shared libraries in configure.user, but your
LD_LIBRARY_PATH doesn't seem to contain /opt/omnetpp-3.4b2/lib!

So that the dynamic linker can find the OMNeT++/OMNEST shared libs, you either
have to create symbolic links from /usr/lib to the OMNeT++/OMNEST shared
libraries (you can do it as root), or better, set the LD_LIBRARY_PATH
environment variable.

Add the corresponding line to your startup file:
  export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/omnetpp-3.4b2/lib
         # into .(bash_)profile if you use bash or other sh-like shell
  setenv LD_LIBRARY_PATH $LD_LIBRARY_PATH:/opt/omnetpp-3.4b2/lib
         # into .cshrc if you use tcsh or other csh-like shell

If you prefer static libraries, edit configure.user and change the
build_shared_libs=yes line to build_shared_libs=no, then delete the shared
libraries, re-run configure and make.



however as i said, i have set the variables... as pasted above and checked them as follows:

$PATH
/opt/msp430/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:
/usr/bin/X11:/usr/games:/opt/omnetpp-3.4b2/bin:/opt/omnetpp-3.42b2:
/opt/ActiveTcl-8.4/bin

echo $LD_LIBRARY_PATH
/opt/omnetpp-3.4b2/lib

---

### Post by Amirhossein on 2007-12-18
***Istall Omentpp in your home directory instead of /opt/ and the you wont face this problem anymore.***

I also tried to install omnetpp in /opt/ and this caused lot of problems during compilation and running the program. The reason is, when you copy omnetpp in /opt/, in order for you to  compile it  you need to have root access. Maybe when you enter** sudo -i** or **sudo ./configure** or **sudo make** command your shell wont see some environment variables. I faced the same problem as you did. When I tried to install omnetpp in my home folder everything went fine.

Something else that is very important. when you want to run the program you must be the user that you have initially logged in with. So if you have entered **sudo -i** in the shell window, close it and open a new one.

---

