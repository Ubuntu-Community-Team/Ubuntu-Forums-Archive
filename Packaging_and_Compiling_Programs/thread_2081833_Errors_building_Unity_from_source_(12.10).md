---
title: "Errors building Unity from source (12.10)"
date: 2012-11-07
forum: Packaging and Compiling Programs
---

### Post by DvKrane on 2012-11-07
I'm trying to build unity from the source code by following the steps provided here:[ http://unity.ubuntu.com/getinvolved/development/unity/#developing-unity]("http://unity.ubuntu.com/getinvolved/development/unity/#developing-unity")
However, I keep getting compiling errors. Here's what the error looks like:
```
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:29:15: error: expected constructor, destructor, or type conversion before ‘(’ token
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp: In member function ‘void unity::BGHash::TransitionToNewColor(const nux::color::Color&)’:
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:107:3: error: ‘logger’ was not declared in this scope
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp: In member function ‘nux::color::Color unity::BGHash::MatchColor(const nux::color::Color&) const’:
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:154:5: error: ‘logger’ was not declared in this scope
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:161:5: error: ‘logger’ was not declared in this scope
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:184:3: error: ‘logger’ was not declared in this scope
make[2]: *** [unity-shared/CMakeFiles/unity-shared.dir/BGHash.cpp.o] Error 1
make[1]: *** [unity-shared/CMakeFiles/unity-shared.dir/all] Error 2
make: *** [all] Error 2
iiquinox@narkotikk:~/code/unity/trunk/build$ 
```I'm running Ubuntu 12.10 and building Unity from the latest launchpad trunk. I haven't modified any of the source code so it should be building without problems right? Any help as to why I'm getting this error?

---

### Post by jaaso on 2012-11-07
> **DvKrane said:**
> I'm trying to build unity from the source code by following the steps provided here:[ http://unity.ubuntu.com/getinvolved/development/unity/#developing-unity]("http://unity.ubuntu.com/getinvolved/development/unity/#developing-unity")
However, I keep getting compiling errors. Here's what the error looks like:
```
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:29:15: error: expected constructor, destructor, or type conversion before ‘(’ token
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp: In member function ‘void unity::BGHash::TransitionToNewColor(const nux::color::Color&)’:
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:107:3: error: ‘logger’ was not declared in this scope
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp: In member function ‘nux::color::Color unity::BGHash::MatchColor(const nux::color::Color&) const’:
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:154:5: error: ‘logger’ was not declared in this scope
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:161:5: error: ‘logger’ was not declared in this scope
/home/iiquinox/code/unity/trunk/unity-shared/BGHash.cpp:184:3: error: ‘logger’ was not declared in this scope
make[2]: *** [unity-shared/CMakeFiles/unity-shared.dir/BGHash.cpp.o] Error 1
make[1]: *** [unity-shared/CMakeFiles/unity-shared.dir/all] Error 2
make: *** [all] Error 2
iiquinox@narkotikk:~/code/unity/trunk/build$ 
```I'm running Ubuntu 12.10 and building Unity from the latest launchpad trunk. I haven't modified any of the source code so it should be building without problems right? Any help as to why I'm getting this error?

Had same error today, I hope they will fix this soon.

---

