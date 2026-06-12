---
title: "i have problems in installing compiling package Gfortran77"
date: 2011-03-23
forum: Packaging and Compiling Programs
---

### Post by grandmonstre on 2011-03-23
Hello everyone
 
i'm a newbie and i need your help. I'm trying install compiling package fortran g77 (with ubuntu 10.10 64bit) .I tried to search and do flowing all tutors on internet but it doesn't work. I downloaded package gfortran-4.5_4.5.2-6ubuntu5_amd64.deb ,gcc-4.5-base_4.5.2-6ubuntu5_amd64.deb
 
in terminal, i typed : [COLOR=red]sudo dpkg -i gfortran-4.5_4.5.2-6ubuntu5_amd64.deb[/COLOR] 
it announce that package gcc-4.5-base_4.5.2-6ubuntu5 is not installed, and then i tried install gcc-4.5-base_4.5.2-6ubuntu5 ; this announcement appeared again .
 
my head is going to explode :( , please help me

---

### Post by MadCow108 on 2011-03-23
g77 is not maintained anymore and is thus not in ubuntu 10.10.
It has been replaced by gfortran which is a fortran 90 compiler but it should be quite compatible with fortran 77
```

$sudo apt-get install gfortran
$gfortran --version
GNU Fortran (Ubuntu/Linaro 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2010 Free Software Foundation, Inc.
```

4.5.1 version is called gfortran-4.5

do **not** install packages from natty into maverick like you tried (4.5.2)! that can end very badly if you don't know what you are doing!

---

### Post by grandmonstre on 2011-03-24
thanks for your answer :) , i tried to install version 4.5.1 ( i installed gfortran cause it's requirement from my tutor in enterprise) and sucessfully installed. this time, i'm in problem with compiling . 
Cause this is GNU fortran 95 , so i tried to compile with:
gfortran -o name_of_file.f name_of_file.o
and it says : command gfortran not found", then i typed 
sudo apt-get install gfortran 
but it says impossible to find package gfortran . I must have results before this friday but i can't compile files :( . Could u help me one more time?

---

### Post by deconstrained on 2011-03-24
> but it says impossible to find package gfortran
[IMG]http://i239.photobucket.com/albums/ff76/dcstrd/impossibru.jpg[/IMG]
Something's wrong with how apt is configured (repositories not enabled?) gfortran should be available!
[http://packages.ubuntu.com/maverick/gfortran](http://packages.ubuntu.com/maverick/gfortran)

If apt-get update fails, take a look at /etc/apt/sources.list. You can easily control enabling repos through Synaptic...

---

### Post by grandmonstre on 2011-03-25
thanks , i checked and tried with 
[COLOR=red]gfortran-4.5 name_of_file.f -o name_of_file.exe ([COLOR=black]not only gfortran[/COLOR])[/COLOR]
it worked very well

---

