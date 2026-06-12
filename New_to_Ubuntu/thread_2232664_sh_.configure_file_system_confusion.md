---
title: "sh ./configure file system confusion"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by Elliott_Kandler on 2014-07-03
Okay so I am using Linux for the first time trying to install some apparently complicated software. There is a configure.h file in my directory /Desktop/cfd/fun3d, so I used cd to take the terminal to that directory. I need mpi and parmetis with the install of fun3d, mpi is in the directory /usr/local and parmetis is in the directory /usr/bin. To install this I use the command "sh ./configure --with-mpi=/usr/local --with-parmetis=/usr/bin" which I get through mpi fine but when I get to parmetis it says "Configure: error: parmetis.h not found in /usr/bin/include"... why did it add the include at the end? I didn't tell it to look there and I know it's in the file location I told it to look it, but of course it's not in /usr/bin/include because I told it to look somewhere else. I really am a beginner to Linux and have been teaching myself for the past few days while trying to get this software installed so if someone could lead me in the right direction I would really appreciate it.

---

### Post by steeldriver on 2014-07-03
Hello and welcome to the forums

A ./configure script is usually only interested in the locations of **development** files (header files and libraries) - it shouldn't be necessary to tell it about **binary** programs that are already in your default path, such as those in /usr/bin. In particular, because it's looking for parmetis headers it appends the /include directory to the path you gave it.

Do you have parmetis development files installed (the libparmetis-dev package, or its local equivalent installed from source)?

---

### Post by Elliott_Kandler on 2014-07-03
Okay honestly I don't know. I spoke to NASA and they sent me a .tar file that I extracted the files to my desktop and then moved them to the /usr/bin directory because that's what my boss told me to do. Also I have no idea what I am doing so every command I am typing either was given to me by NASA, the sh ./configure, or by my boss, --with-mpi..... So honestly I have no clue what I am doing, just trying to do what other people are explaining to me and it's failing.

Also I am using the ./configure because in the fun3d folder there is a configure terminal link, but I was told to open a new terminal, take it to the directory where the configure file is and fun ./configure instead of just double clicking on the configure terminal directly.

---

### Post by steeldriver on 2014-07-03
Well I suspect your boss intended for you to build fun3d and then move the resulting binary file or files to /usr/bin

Since fun3d does not appear to be available to non-US persons, all I can suggest is you try with the simplest configuration and post the exact errors you get so that we can see exactly which pre-requisites are missing from the standard locations on your system i.e. unpack the tar file again, to a location made in your home directory e.g. 

```

mkdir -p ~/src/nasa && cd ~/src/nasa

tar xvf psth/to/tarfile

```

then cd into the top level directory of the unpacked archive (probably called fun3d) and run ./configure from there. You should not need to invoke it via sh explicitly - although you may need to make it executable i.e.

```

cd fun3d

chmod +x configure

./configure

```

---

### Post by Elliott_Kandler on 2014-07-03
Okay I can try that, but why does it randomly add the include on the end? I give it a directory to look in and it just tells me it cannot find the file, in a different location than I told it to look.... That really confuses me

---

