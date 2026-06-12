---
title: "Source Compilation - can someone clarify?"
date: 2020-05-13
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-05-13
Hello all!

I've been looking at how to compile packages from source code and have compiled my first package, however I'm getting an error when trying to actually use it (it's a plugin for an emulator) and I'm not entirely sure I didn't do something slightly wrong, and would like to make sure before I go chasing other possibilities in case I need to remove and re-compile it.

[I was following this guide]("https://github.com/gonetz/GLideN64/wiki/Build-From-Source-(Linux)"), who's process differs slightly from the instructional I used to learn the basics. The part I am not sure about is the section titled "initial setup". What is the purpose of...```
./getRevision.sh
```My understanding is that it is a shell script. It returns a revision number, plus another piece of information which I can't remember, but it didn't seem to do anything of any great importance at the time.

The reason I ask is that when I ran "./getRevision" it returned the right info but also returned an error message (which again I cant remember - sorry) I then performed the workaround shown in italics at the bottom of the initial setup section, and ran ./getRevision once more, which then returned the exact same info as the first time just without the error message. I then carried on with the rest of the guide and it seemed to compile and install fine.

Can anyone shed some light on the purpose of ./getRevision and weather what I described could potentially cause errors when it come to using the program?

---

### Post by SeijiSensei on 2020-05-13
Did you do this?

> There is no easy solution to this other than to manually create a Revision.h file in the /src directory containing #define PLUGIN_REVISION "1". 

If so, and the code compiled, you should be fine.  Have you tried running it?  You'll know pretty quickly if it was built and installed correctly!

---

### Post by jcdenton1995 on 2020-05-13
Hello!

I did do, I cut & pasted the original "revision.h" file into my home folder for safe keeping (as there was already one present in /src) and then created a new one containing the string specified in the guide, ran "./getRevision" again and then carried on with the compiling process. The funny thing is the file I created now contains the exact same content as the original that I popped into my home directory, maybe ./getRevision updates the contents?

Anyway I don't seem to be able to use the plugin as it keeps returning an error (the emulator that I'm using it with has a command line interface so not much more to go on than that)  but I think from a quick search it's a OpenGL / driver thing so I'm not too worried at the moment, as long as the package compiled and installed correctly. I mean I know it's not a super high tech observation or anything but the compilation didn't throw up any errors and it all seemed to go smoothly so maybe it's okay?

---

### Post by SeijiSensei on 2020-05-14
It depends on whether you needed to include the missing OpenGL driver or code in the build process.

Did you run this step?

```
sudo apt-get install gcc g++ cmake libgl1-mesa-dev libfreetype6-dev libmupen64plus-dev zlib1g-dev
```

In particular, libgl1-mesa-dev might have some code you need. There's no mention in the instructions you linked to of the usual "./configure" step that most well-behaved source code uses.  Perhaps it is run during getRevision?  Usually running

```
./configure
```

in the main source directory will check for needed dependencies and complain if they are not there.  Running "./configure --help" will display a list of the possible compilation options.

---

### Post by jcdenton1995 on 2020-05-14
Yes, I installed the dependencies but used "apt" instead of "apt-get", most of them were already on my machine anyway and only a couple were fetched.

getRevision.sh is the only script within /src and it is pretty short, I cant claim to understand it but it looks like it is checking that the source code is the latest version before you compile it...```
SCRIPT_DIRECTORY=`dirname $0`
rev=\"`git rev-parse --short HEAD`\"
lastrev=$(head -n 1 $SCRIPT_DIRECTORY/Revision.h | awk -F'PLUGIN_REVISION ' {'print $2'$

echo current revision $rev
echo last build revision $lastrev

if [ "$lastrev" != "$rev" ]
then
   echo "#define PLUGIN_REVISION $rev" > $SCRIPT_DIRECTORY/Revision.h
   echo "#define PLUGIN_REVISION_W L$rev" >> $SCRIPT_DIRECTORY/Revision.h

```Furthermore there is no "./config" (I was expecting to find this based off of a guide I followed that outlined how to compile programs generally) however there is a file named "config.h" but I'm not sure if that's relevant...

---

### Post by monkeybrain20122 on 2020-05-14
> **SeijiSensei said:**
> It depends on whether you needed to include the missing OpenGL driver or code in the build process.


```
./configure
```



It uses cmake according to the instructions in OP's link

---

### Post by monkeybrain20122 on 2020-05-14
> **jcdenton1995 said:**
> 
Furthermore there is no "./config" (I was expecting to find this based off of a guide I followed that outlined how to compile programs generally) however there is a file named "config.h" but I'm not sure if that's relevant...

It uses cmake instead of autoconf so there is no configure file and the like

look at the build instruction from your link. Basically

```
cd into source folder

mkdir build && cd build

cmake -DMUPENPLUSAPI=On ..

make -j5 #say you have  quad core , you can change the number accordingly
```

---

