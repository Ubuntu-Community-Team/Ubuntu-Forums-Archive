---
title: "Google Earth"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-07-10
Since last update I can't get google earth to work. I have tried all the posted fixes. I am running 12.04 64 bit. I downloaded the .deb here and software center thinks it's installed but it won't open from terminal or menu. I don't even get a splash screen.I get this error. I can't find libGL.so.1 in synaptic.I got the 64 bit ,deb file here
[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html")

```
cmcanulty@Darcy25:~$ google-earth
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
cmcanulty@Darcy25:~$ 
```

---

### Post by kimda on 2012-07-10
Google earth is in the repository multiverse. You can enable this by selecting the restricted sources in software center: 
start software center > select software sources from menu option edit and enable multiverse repo (restricted). Now you can install google earth from software center.

---

### Post by cmcanulty on 2012-07-10
it is installed but won't run so I uninstalled in synaptic then looked in software center and it doesn't show up and I have all sources enabled.

---

### Post by sudo smith on 2012-07-11
Did you try just getting it from the google earth website?

---

### Post by cmcanulty on 2012-07-11
yes did you read my first post with the link where I downloaded it? I have done the web site, synaptic, software center. The error no libGL.so.1 seems significant but how to fix I have no idea.I also have tried this directions
[http://www.tuxtree.com/2012/04/how-to-install-google-earth-6-2-in-ubuntu-12-04.html]("http://www.tuxtree.com/2012/04/how-to-install-google-earth-6-2-in-ubuntu-12-04.html")
Here is the terminal output nothing happens when I try it from menu

```
cmcanulty@Darcy25:~$ google-earth
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
cmcanulty@Darcy25:~$
``` 

and some other info  

```
cmcanulty@Darcy25:~$ google-earth
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
cmcanulty@Darcy25:~$ locate googleearth
The program 'locate' can be found in the following packages:
 * mlocate
 * locate
Try: sudo apt-get install <selected package>
cmcanulty@Darcy25:~$ path/to/googleearth
bash: path/to/googleearth: No such file or directory
cmcanulty@Darcy25:~$
```

---

### Post by kimda on 2012-07-11
I 've just installed this package. 

Do you have a nvdia graphics card? libGL.so.1 is installed in: nvidia-current package and in the libgl1-mesa-glx package. Try installing these packages to fix dependencies. The last mentioned package is independed of your graphics card so that would be the first one to install to get this fixed.

---

### Post by cmcanulty on 2012-07-11
here is my graphics card

---

### Post by codingman on 2012-07-11
Integrated graphics may not be able to work with google earth.

---

### Post by cmcanulty on 2012-07-11
this laptop worked fine until the latest update. Also I run 10 of the same model at our library and they do google earth fine also running ubuntu 12.04 classic.Can someone explain how to fix the error mentioned above:
```
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open 
```

---

