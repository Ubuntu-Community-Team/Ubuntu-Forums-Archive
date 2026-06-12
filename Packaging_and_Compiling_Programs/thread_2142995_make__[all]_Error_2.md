---
title: "make: *** [all] Error 2"
date: 2013-05-07
forum: Packaging and Compiling Programs
---

### Post by ammoula on 2013-05-07
please can you help me!
After running the follwing commands to compile ( toulbar2) mkdir build ; cd build ; cmake .. ; make package
but when i write cmake ..  an error  like " Could NOT find Doxygen (missing:  DOXYGEN_EXECUTABLE)"
and when i write make package an error  like this 
make[2]: *** [CMakeFiles/toulbar2.dir/src/tb2main.cpp.o] Error 1
make[2]: Leaving directory `/home/dell/Bureau/toulbar2/build'
make[1]: *** [CMakeFiles/toulbar2.dir/all] Error 2
make[1]: Leaving directory `/home/dell/Bureau/toulbar2/build'
make: *** [all] Error 2

---

### Post by schragge on 2013-05-07
It cannot find doxygen, so install doxygen
```
sudo apt-get install doxygen
```

---

### Post by dino99 on 2013-05-07
i suppose you still have not doxygen installed yet  [https://launchpad.net/ubuntu/+source/doxygen](https://launchpad.net/ubuntu/+source/doxygen)

---

### Post by ammoula on 2013-05-07
After running the follwing commands to compile make package ;
an error 

CPackRPM:Debug: *** error: No compatible architectures found for build
 ***
CPackRPM:Debug:    - /home/dell/Bureau/toulbar2/_CPack_Packages/Linux/RPM/rpmbuild.out
CPackRPM:Debug: *** error: No compatible architectures found for build
 ***
CPack Error: Problem copying the package: /home/dell/Bureau/toulbar2/_CPack_Packages/Linux/RPM/toulbar2.0.9.5.0-Release-x86_64.rpm to /home/dell/Bureau/toulbar2/toulbar2.0.9.5.0-Release-x86_64.rpm
CPack Error: Error when generating package: toulbar2
make: *** [package] Error 1

can one help me? thanks

---

### Post by oldos2er on 2013-05-07
Threads merged and moved to Packaging & Compiling Programs. Please don't open more than one thread for the same or similar questions.

---

### Post by schragge on 2013-05-07
Are you trying to generate an [RPM](http://en.wikipedia.org/wiki/RPM_Package_Manager) package on Ubuntu? Why? Doesn't the *cmake* script for the software you're building has an option not to generate it? To find it out, try to run *cmake* interactively:
```
ccmake ..
``` or ```
cmake -i ..
```

---

