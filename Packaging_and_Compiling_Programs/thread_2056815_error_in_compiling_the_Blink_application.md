---
title: "error in compiling the Blink application"
date: 2012-09-12
forum: Packaging and Compiling Programs
---

### Post by Narjess on 2012-09-12
I have installed tinyos-2.1.1 on Ubuntu 10.10.
When i trying to 
this is what happen:

mkdir -p build/micaz
  placing object files in build/micaz
  writing XML schema to app.xml
  compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o build/micaz/sim.o -g -O0 -tossim
-fnesc-nido-tosnodes=1000 -fnesc-simulate
-fnesc-nido-motenumber=sim_node\(\)   -finline-limit=100000 -Wall -Wshadow
-Wnesc-all -target=micaz -fnesc-cfile=build/micaz/app.c -board=micasb
-Wno-nesc-data-race BlinkAppC.nc   -fnesc-dump=components
-fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs
-fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
  compiling Python support and C libraries into pytossim.o, tossim.o, and
c-support.o
g++ -c  -shared -fPIC -o build/micaz/pytossim.o -g -O0
/opt/tinyos-2.x/tos/lib/tossim/tossim_wrap.cxx
-I/usr/include/python2.3 -I/opt/tinyos-2.x/tos/lib/tossim -DHAVE_CONFIG_H
make: g++: Command not found
make: *** [sim-exe] Error 127

Please help.

---

### Post by oldos2er on 2012-09-12
Moved to Packaging and Compiling Programs.

---

