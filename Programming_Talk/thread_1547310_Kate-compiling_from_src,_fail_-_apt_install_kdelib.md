---
title: "Kate-compiling from src, fail - apt install kdelibs5-dev, cant find kde4_add_library"
date: 2010-08-06
forum: Programming Talk
---

### Post by pushkarajthorat on 2010-08-06
Greetings!
I am trying to compile kate([http://kate-editor.org/get-it/](http://kate-editor.org/get-it/) ). 

First problem:
  ```
sudo aptitude install kdelibs5-dev
```
error:

```
pushkaraj@laptop:~/kde/build$ sudo apt-get install kdelibs5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs5-dev: Depends: kdelibs5 (= 4:4.1.0-3) but 4:4.4.2-0ubuntu4 is to be installed
                Depends: libsoprano-dev (>= 2.1) but it is not going to be installed
                Depends: libphonon-dev (> 4:4.2.0) but it is not going to be installed
```

I have also tried with force-yes and something like =  apt-get install --force-yes kdelibs5=4:4.1.0-3 ; with hope to downgrade it.
but my every attempt was in vain, there is a tree of dependencies which requires to be satisfied by uninstalling/downgrade/install, and the list contains many *important* packages.

Now my question is, can I download(ofcourse I can with apt-get -d) the package, and also enable cmake/kate use it instead of the already installed one?

Second problem:
Running config process with cmake, and error was:

```
CMake Error at app/CMakeLists.txt:32 (kde4_add_library):
  Unknown CMake command "kde4_add_library".

```
to solve this I've tried to - add - ```
find_package (kde4 REQUIRED)
``` in CMakeLists.txt but it said not able to find kde4.cmake or its not in path.

Now question is- In which lib. does the kde4_add_library command is stored?

Thank you, for your time! Pushkaraj

---

### Post by pushkarajthorat on 2010-08-07
I am thru with installation of kdelibs5-dev, but still the cmake is failing as kde4_add_library was not found.
Please help I am in a problem!

---

### Post by pushkarajthorat on 2010-08-07
There is some problem with the code which is present in SVN repository 
svn co svn://anonsvn.kde.org/home/kde/trunk/KDE/kdesdk/kate/


when I switched to the git's code, this was successfully configured make & install!

---

