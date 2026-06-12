---
title: "[SOLVED] help building algoscore"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-18
I've just grabbed the latest version of algoscore and untar-ed it.  In the read me it says to install CMake and do
```
cd src
./make_build
```
which seemed to work.  I've tried to click on the AppRun file but it does not load the program and the algoscore binary at the top of the directory seems to be missing.  Does anyone know how I would go about getting the program to run?
Here's the link to the program:  [http://www.bitminds.net/kymatica/index.php/Software/AlgoScore](http://www.bitminds.net/kymatica/index.php/Software/AlgoScore)

---

### Post by fontenot_1031 on 2008-05-18
Ok so this will yield this.
```
david@laptopish:/usr/local/share/AlgoScore$ ./AppRun
[: 10: ==: unexpected operator
exec: 10: ./algoscore: not found

```

---

### Post by EXCiD3 on 2008-05-18
Made sure you have all the dependencies installed? It mentions to make sure you also install the packages with -dev.

---

### Post by fontenot_1031 on 2008-05-18
> **EXCiD3 said:**
> Made sure you have all the dependencies installed?

Went through the list of dependencies and double checked that before hand.  I wish I could find that algoscore binary file the installation instructions were talking about.

---

### Post by Xiong Chiamiov on 2008-05-18
It seems that they have something odd in their shell script.  I changed the brackets in the if statement to parens, and that got that part working, but then
...
err, let me get back to you in a moment, but try that in the meantime.  You may need to chmod +x AppRun after editing it.

---

### Post by fontenot_1031 on 2008-05-18
> **Xiong Chiamiov said:**
> It seems that they have something odd in their shell script.  I changed the brackets in the if statement to parens, and that got that part working, but then
...
err, let me get back to you in a moment, but try that in the meantime.  You may need to chmod +x AppRun after editing it.
Thanx man I'll give that a go.

---

### Post by EXCiD3 on 2008-05-18
> **fontenot_1031 said:**
> Went through the list of dependencies and double checked that before hand.  I wish I could find that algoscore binary file the installation instructions were talking about.

The binary file they are mentioning is what you are compiling. You have the source code and are creating the binary so that you can run it on your system. Unfortunately i'm on a windows box and probably cant help any further for the time being. :( Good luck!

---

### Post by fontenot_1031 on 2008-05-18
> **EXCiD3 said:**
> The binary file they are mentioning is what you are compiling. You have the source code and are creating the binary so that you can run it on your system. Unfortunately i'm on a windows box and probably cant help any further for the time being. :( Good luck!


Ahh hah it was my bad.  Woah I found it in my root directory for some reason.
Ok so I did Xiong's edit and chmod-ed it.  Changed permissions and the program should be good to go after an X11 restart.  Marked as solved thanx everybody for your help.

---

### Post by fontenot_1031 on 2008-05-18
...well not entirely solved.  AlgoScore insists that I'm on a Macintosh.
```
cd: 2: can't cd to /Applications/Utilities/X11.app/Contents/MacOS

```

---

