---
title: "installing packages offline"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by natbob1 on 2008-08-11
I'm trying to compile a C application from source on a computer that does not have an internet connection, it gives the error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I have looked at other threads and found that the issue is solved by using:

sudo apt-get install linux-kernel-headers
sudo apt-get install build-essential

which I cannot do because It doesn't have an Internet connection. 
I do have another windows computer that does have an Internet connection. So I would like to know how to download the packages and install them from  a disk.

---

### Post by OffAxis on 2008-08-11
download the packages from here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)


Then, navigate to the folder where you downloaded them and...
```
sudo dpkg -i <package name>
```

---

### Post by unutbu on 2008-08-11
When you install build-essential, it will also try to install the following packages
if you don't already have them:
```

  dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev patch
```

To avoid the misery of downloading some debs and only later finding out you have unmet dependencies, go to Synaptic. Mark build-essential and linux-kernel-headers for installation. Then go to File>Generate package download script. Save the script and Quit synaptic. The script is a text file which will contain the complete list of packages (debs) you will need to download from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

Once you copy the debs over to the Ubuntu filesystem, put them in a directory all by themselves. To avoid dpkg from complaining about unmet dependencies, 

```
cd directory-with-the-debs
sudo dpkg -i *
```

(The * will list all the debs in one line, and when done this way dpkg can somehow decide the correct order the packages must be installed for you.)

---

### Post by natbob1 on 2008-08-11
Thanks,
I got the packages and have compiled!

---

### Post by zj3t3mju on 2008-08-12
second way
you can install it from liveCD, it have on install cd
or try [http://wapt-get.googlecode.com](http://wapt-get.googlecode.com)

---

