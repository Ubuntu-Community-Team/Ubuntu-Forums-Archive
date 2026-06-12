---
title: "unable to re-install g++"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by micahpage on 2013-11-07
I came across this error out of the blue
```
bash: /usr/bin/g++: No such file or directory
```

Now i am getting this error when installing g++
```
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

over the course of a couple hours i have tried removing g++ and reinstalling it serveral times, and some commands im not sure what they did, but i tried them as they were related to my problem. 

this is the error message i get when reinstalling:
```
micahpage@ubuntu:~/programs/cplusplus$ g++ -v
bash: /usr/bin/g++: No such file or directory

micahpage@ubuntu:~/programs/cplusplus$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-4.7-arm-linux-gnueabihf-base libsoil1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  g++-multilib
The following NEW packages will be installed:
  g++
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/1,448 B of archives.
After this operation, 34.8 kB of additional disk space will be used.
Selecting previously unselected package g++.
(Reading database ... 286707 files and directories currently installed.)
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Processing triggers for man-db ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: error: alternative path /usr/bin/g++ doesn't exist
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

here is the history of the commands i gave in trying to fix this problem.
```
 3663  g++ -std=c++11  -Wall -o "%e" "%f" -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system &&"./%e"
 3664  sudo apt-get install g++
 3665  sudo apt-get install g++-4.8
 3666  sudo apt-get install g++
 3667  g++ -std=c++11  -Wall -o "%e" "%f" -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system &&"./%e"
 3668  sudo apt-get install pentium-builder
 3669  g++ -std=c++11  -Wall -o "%e" "%f" -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system &&"./%e"
 3670  g++ -v
 3671  sudo apt-get update && sudo apt-get install build-essentials
 3672  sudo apt-get update && sudo apt-get install build-essential
 3673  cd programs/cplusplus
 3674  ls
 3675  g++ -std=c++11  -Wall -o "%e" "%f" -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system &&"./%e"
 3676  g++ -v
 3677  g++
 3678  sudo apt-get remove g++
 3679  g++ -v
 3680  sudo apt-get install g++
 3681  g++ -v
 3682  sudo apt-get install g++-4.8
 3683  sudo add-apt-repository ppa:ubuntu-toolchain-r/test
 3684  sudo apt-get update
 3685  sudo apt-get install gcc-4.8
 3686  sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50
 3687  gcc -v
 3688  g++ -v
 3689  sudo apt-get install g++ --reinstall
 3690  g++ -v
 3691  gcc -v
 3692  g++ -v
 3693  history
 3694  sudo apt-get remove g++
 3695  g++ -v
 3696  sudo apt-get install g++
 3697  sudo add-apt-repository ppa:ubuntu-toolchain-r/test
 3698  sudo apt-get update
 3699  sudo apt-get install gcc-4.8
 3700  sudo apt-get install g++-4.8
 3701  sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50
 3702  sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 50
 3703  sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 51
 3704  sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 49
 3705  gcc -v
 3706  g++ -v
 3707  sudo apt-get remove g++
 3708  sudo apt-get install g++
 3709  sudo dpkg -r g++
 3710  sudo apt-get -f install
 3711  sudo apt-get updatge
 3712  sudo apt-get update
 3713  sudo apt-get upgrade
 3714  gcc -v
 3715  g++ -v
 3716  sudo apt-get install g++
 3717  history


```

I am at a loss of why this happened. It happened just between compiling programs. No updates at that time, no changing config files, or removing g++ at that time. It seemed to jsut out of the blue have a problem?

---

### Post by squakie on 2013-11-08
did something happen to your $PATH variable such that it isn't searching correctly?

Also - it's just my preference - I have always installed synaptic package manager and used it except in the rare instance where I use apt.  I don't believe it's included by default anymore, so you must sudo apt-get install synaptic to install it.  After that you can just select it from the unity menu.  You can then graphically select packages for installation/removal - you may even find something listed there that you need installed.

---

### Post by micahpage on 2013-11-08
I havent changed anything regarding path

.profile
```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


```

I do have synaptic. It shows as g++-4.8 being installed, as well as 4.7, and libs, etc.


Somehow throughout tryng, apparently now i have 4.7 available. 
```
micahpage@ubuntu:~$ gcc --version
gcc (Ubuntu/Linaro 4.7.3-2ubuntu4) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

micahpage@ubuntu:~$ g++ --version
g++ (Ubuntu/Linaro 4.7.3-2ubuntu4) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

micahpager@ubuntu:~$ 


```

However when i try to revert to 4.8 i return the the previous error i had. At least with 4.7 i can compile. But now i seem to have a new problem from this.

when i try to compile a basic hello world i do not have a problem, 
```
micahpage@ubuntu:~$ g++ -std=c++11 test.cpp -o test
micahpage@ubuntu:~$ ./test
hello
micahpage@ubuntu:~$ 


```
but when i add SFML arguments, i get libgl errors

compiling with
```
g++  -std=c++11  -Wall -o "%e" "%f" -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system &&"./%e"
```
gives out this error:
```
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
```

compiling with:
```
g++  LIBGL_DEBUG=verbose -std=c++11  -Wall -o "%e" "%f" -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system &&"./%e"
```
gives out this error:
```
g++: error: LIBGL_DEBUG=verbose: No such file or directory

```

---

