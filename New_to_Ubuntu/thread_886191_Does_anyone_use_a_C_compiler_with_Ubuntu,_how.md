---
title: "Does anyone use a C compiler with Ubuntu, how ??"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Windy Peaks on 2008-08-10
Ladies and Gentlemen:

I have downloaded many different C programming programs from the Applications->Add/remove but none of them recognize any of my header files.
Example #include <stdio.h> or #include <stdlib.h>
does anyone know why the libraries aren't there and do You know how I can enable them so that I don't have to go back to FEDORA 8. (great OS but it does not work with my wi-fi )

Thanks in Advance
Windy.

---

### Post by iaculallad on 2008-08-10
In your terminal, install the build-essential files:

```
sudo apt-get install build-essential
```

---

### Post by Separ on 2008-08-10
Have you tried compiling with gcc? It is run from the command line.

---

### Post by InfinityCircuit on 2008-08-10
If you want to figure out which packages contain your libraries, you can use apt-file:

```
sudo apt-get install apt-file
sudo apt-file update
```

Then if you do apt-file search blahblah. it will tell you which package to install.

Of course, build-essential is the first thing you need in order to compile.

---

### Post by HotCupOfJava on 2008-08-10
Use the Synaptic Package Manager to get your compilers. It will make sure you get all the packages you need for development (and even install and configure them for you). Go to System->Administration->Synaptic Package Manager. You will be prompted to enter your password. You can search for "C compiler" or something like that. Mark the package you want for installation. If additional packages are required, Synaptic will prompt you and mark those for you. Click "Apply Changes" and you've got it! If you are interested in using a great graphical IDE might I suggest NetBeans? It will do C, C++, Ruby and (my personal favorite) Java.

---

### Post by iaculallad on 2008-08-10
> **InfinityCircuit said:**
> If you want to figure out which packages contain your libraries, you can use apt-file:

```
sudo apt-get install apt-file
sudo apt-file update
```

Then if you do apt-file search blahblah. it will tell you which package to install.

Of course, build-essential is the first thing you need in order to compile.

apt-file? for figuring out which package contain libraries? Would it not be:

```
apt-cache search search_string
```

---

### Post by OutOfReach on 2008-08-10
like other people have said install build-essential by typing this into the terminal:

```
sudo apt-get install build-essential
```

Build-essential comes with gcc (correct?), a C compiler.

---

### Post by iaculallad on 2008-08-10
> **OutOfReach said:**
> like other people have said install build-essential by typing this into the terminal:

```
sudo apt-get install build-essential
```

Build-essential comes with gcc (correct?), a C compiler.

Yes, it comes with the build-essential file. GCC is the GNU compiler collection which includes front ends for Objective-C, C++, C, Java, Fortran,  and Ada, as well as libraries for these programming languages.

---

### Post by hyper_ch on 2008-08-11
> **iaculallad said:**
> apt-file? for figuring out which package contain libraries? Would it not be:

```
apt-cache search search_string
```

not really... apt-file builds a database of all files contained in a package. apt-cache search can't do this.

So if you get an error that file libWHATEVER is missing you can easily check in what packages this file is containd by using apt-file.

---

