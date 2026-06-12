---
title: "manually install .tar.gz"
date: 2014-08-02
forum: New to Ubuntu
---

### Post by Bikerman114 on 2014-08-02
I installed KDE on a second account to use KDevelop IDE in Ubuntu, I'll probably switch to Kubuntu if I like it and get use to KDE. I was able to use apt-get to install Kdevelop however apt-get doesn't see the Python extention kdev-python, although it is in the apt-get repository for Kubuntu. Now I downloaded the .tar.gz and unzipped it with the arcive manager. The install instructions are:
 ```
To install, do this:
mkdir -p build
cd build
cmake ..
make parser
make install
```

I made the build dirrectory just fine and got the error
```
CMake Error: The source directory "/home/test" does not appear to conta
in CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
```

There is a "CMakeList.txt" in the kdev-python-v1.5.0 folder so I've moved that into the build dirrectory gone into and and then tried
```
test@Bob:~/build/kdev-python-v1.5.0$ cmake ..
CMake Error: The source directory "/home/test/build" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

```

is there some way for me to make it look in the kdev-python-v1.5.0. Since I was in it when I called cmake shouldn't it be looking in that folder instead of just the build dirrectory. Also, could anyone explain how the manually installing process works. I can only find posts with similar code to install different programs but no reasons why or atleast not enough for me to figure out what I need to point cmake at. 

If anyone could break down the installation process to idiot level it would be appriciated. I love apt-get and aptitiude but it seems like everytime they don't have something it takes me alteast 45 minutes to install something. Also, is it normal to have different repositories, I first tride it out on a Kubuntu-USB and just installed it using apt-get. Would there be an easy way to make apt-get see this file since it's alread in the Kubuntu repository. Any advice will be appriciated.

---

### Post by philinux on 2014-08-02
[https://launchpad.net/ubuntu/+source/kdev-python](https://launchpad.net/ubuntu/+source/kdev-python)
There's a deb file here.

---

### Post by sandyd on 2014-08-02
> **Bikerman114 said:**
> I installed KDE on a second account to use KDevelop IDE in Ubuntu, I'll probably switch to Kubuntu if I like it and get use to KDE. I was able to use apt-get to install Kdevelop however apt-get doesn't see the Python extention kdev-python, although it is in the apt-get repository for Kubuntu. Now I downloaded the .tar.gz and unzipped it with the arcive manager. The install instructions are:
 ```
To install, do this:
mkdir -p build
cd build
cmake ..
make parser
make install
```

I made the build dirrectory just fine and got the error
```
CMake Error: The source directory "/home/test" does not appear to conta
in CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
```

There is a "CMakeList.txt" in the kdev-python-v1.5.0 folder so I've moved that into the build dirrectory gone into and and then tried
```
test@Bob:~/build/kdev-python-v1.5.0$ cmake ..
CMake Error: The source directory "/home/test/build" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

```

is there some way for me to make it look in the kdev-python-v1.5.0. Since I was in it when I called cmake shouldn't it be looking in that folder instead of just the build dirrectory. Also, could anyone explain how the manually installing process works. I can only find posts with similar code to install different programs but no reasons why or atleast not enough for me to figure out what I need to point cmake at. 

If anyone could break down the installation process to idiot level it would be appriciated. I love apt-get and aptitiude but it seems like everytime they don't have something it takes me alteast 45 minutes to install something. Also, is it normal to have different repositories, I first tride it out on a Kubuntu-USB and just installed it using apt-get. Would there be an easy way to make apt-get see this file since it's alread in the Kubuntu repository. Any advice will be appriciated.

kdev-python should exist in ubuntu releases Trusty and beyond and should be installable from apt-get provided that the universe repos are enabled.

Anyways,
64bit: [http://launchpadlibrarian.net/158905252/kdev-python_1.6.0-0ubuntu1_amd64.deb](http://launchpadlibrarian.net/158905252/kdev-python_1.6.0-0ubuntu1_amd64.deb)
32bit: [http://launchpadlibrarian.net/158900299/kdev-python_1.6.0-0ubuntu1_i386.deb](http://launchpadlibrarian.net/158900299/kdev-python_1.6.0-0ubuntu1_i386.deb)

---

### Post by Bikerman114 on 2014-08-02
> **sandyd said:**
> kdev-python should exist in ubuntu releases Trusty and beyond and should be installable from apt-get provided that the universe repos are enabled.

Anyways,
64bit: [http://launchpadlibrarian.net/158905252/kdev-python_1.6.0-0ubuntu1_amd64.deb](http://launchpadlibrarian.net/158905252/kdev-python_1.6.0-0ubuntu1_amd64.deb)
32bit: [http://launchpadlibrarian.net/158900299/kdev-python_1.6.0-0ubuntu1_i386.deb](http://launchpadlibrarian.net/158900299/kdev-python_1.6.0-0ubuntu1_i386.deb)

I'm running Ubuntu 12.04 now. the link you gave got to the same point as the eirlier link of loading a file that pulls up the software center for kdev-python without an option to download it and an error across the top:
```
Dependency is not satisfiable:kdevplatform7-libs (>=1.6.0)
```
Is it a thing where I jsut have to upgrade to get it working or would there be some workaround

---

### Post by ian-weisser on 2014-08-02
> **Bikerman114 said:**
> Is it a thing where I jsut have to upgrade to get it working[?]

Well, yes.
Apt should only 'see' packages for the same release of Ubuntu. Anything else can cause a _lot_ of breakage.

---

### Post by Bikerman114 on 2014-08-03
Okay, thanks. I'll just upgrade tonight. I've been putting it off with my slow internet.

---

