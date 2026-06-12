---
title: "Trying To Install OpenCV using the Cmake command"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by Lieske on 2013-05-31
I'm currently trying to install my first program, OpenCV. I'm using [this]("http://docs.opencv.org/doc/tutorials/introduction/linux_install/linux_install.html#linux-installation") user guide to help me.

I ran the following line and successfully downloaded OpenCV:

```
git clone https://github.com/Itseez/opencv.git
```

Now I'm trying to build/install the package. The guide says I need to run this line:

```
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ..
```

However, I get the error that the command cmake is not found. There is a directory in the downloaded OpenCV files entilted cmake but I'm not sure if any of the files in there are  related to my problem. I know cmake is a program to help build/install, is it possible that I don't have it?

---

### Post by steeldriver on 2013-05-31
Yes it's possible your system doesn't have cmake - in fact the standard system doesn't have a very complete build environment at all (the build-essential meta package is a good starting point)

You can easily check with either

```
dpkg -l | grep cmake
```

or

```
apt-cache policy cmake
```

Is there any particular reason you are building opencv from source instead of just installing the packaged version from the repository?

---

### Post by Lieske on 2013-05-31
I'm a user on a server (connected via ssh) and I believe don't have the permissions to download from the repository. I tried following [this guide]("http://opencv.willowgarage.com/wiki/Ubuntu_Packages") and got in trouble with the system admin. Very nasty email (I'm an intern so this for my job). So my mentor gave me the link to the other guide I posted above.

I just tried both the commands you suggested and terminal gives me the command not found option. I assume this means I don't have cmake?

I'm now trying to download/install cmake using [this]("http://www.cmake.org/cmake/help/install.html").

---

### Post by Cheesemill on 2013-05-31
If you don't have the permissions to download and install software from the repository then you are going to have a ***very*** difficult time installing software.

At the moment you're being asked to do a job but you're not allowed the correct tools to do it with. I'd have a polite word with your admin and let him know that you can't install OpenCV with your current access.

You could also ask someone else who does have the required permissions to install it for you.

---

### Post by Lieske on 2013-05-31
You're right, Cheesemill. Unfortunately the admin is very unfriendly (I'm fairly new to linux and he thinks I'm going to ruin everything) and the people I'm working with are out of town for the next week (vacation). 

I just downloaded the .tar.gz for cmake. I uncompressed it and and tried to install using the following. (As suggested by [the cmake webbsite]("http://www.cmake.org/cmake/help/install.html")).

```
 ./bootstrap
    make 
    make install 
```

I got the error: 

```
zsh: permission denied: ./bootstrap
```

Is this something else my admin has disabled me from doing or this is a problem with the permission of the files? (I downloaded them straight from the cmake website).

---

