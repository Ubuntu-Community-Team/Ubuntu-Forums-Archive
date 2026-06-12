---
title: "Which g++"
date: 2007-06-05
forum: Programming Talk
---

### Post by Greggle on 2007-06-05
Which g++ should I get? The latest, which I guess is 4.1? What's the most stable(subjective, I know)?

I'm trying to get Anjuta installed, but I get the 'C compiler cannot create executables' error. I've read a few places(including old posts here) that installing g++ will eliminate this problem.

I'm using 7.04 if it's relevant.

Thanks, gang.

---

### Post by WW on 2007-06-05
Unless you have a compelling reason to do otherwise, get the version provided with Ubuntu 7.04:
```

$ sudo apt-get install g++

```
Unfortunately that package is not really everything that you probably need.  Install the **build-essential** package (which includes g++):
```

$ sudo apt-get install build-essential

```

---

### Post by Greggle on 2007-06-05
Damn! Okay, I got a lot farther into the configure process after that install you suggested. It barfed up an error while searching for glib. The last output was 'No package glib-2.0 found'. Is there another spiffy command like the previous one to install glib without downloading anything?

This is day two of my first foray into Linux. All apologies...

---

### Post by WW on 2007-06-05
> **Greggle said:**
> 

I'm trying to get Anjuta installed, 


anjuta is available in the Ubuntu repository:
```

$ sudo apt-get install anjuta

```

---

### Post by KaeseEs on 2007-06-05
The above poster's advice is corect.  Some additional info for future reference may be useful to you, however; when numerous versions of a program are listed by APT in addition to the base program, it means that multiple concurrent branches are available.  For example: a search for 'gcc' will yield ```
i   gcc                             - The GNU C compiler                        
p   gcc-2.95                        - The GNU C compiler                        
p   gcc-2.95-doc                    - Documentation for the GNU compilers (gcc, 
p   gcc-3.3                         - The GNU C compiler                        
i   gcc-3.3-base                    - The GNU Compiler Collection (base package)
p   gcc-3.3-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-3.4                         - The GNU C compiler                        
p   gcc-3.4-base                    - The GNU Compiler Collection (base package)
p   gcc-3.4-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-4.0-locales                 - The GNU C compiler (native language suppor
i   gcc-4.1                         - The GNU C compiler                    
```Just installing 'gcc' will grab you the most recent stable version (which happesn to be gcc 4.1).  Grabbing gcc-3.3 will grab you the most recent version from the 3.3 branch.  Typically, multiple branches are distributed simultaneously if new versions introduce incompatibilities, so people need updated versions of older branches compatible with their old code/scripts/etc.  This phenomena can be observed with php4/5 and apache/2 as well, for example.  The best course of action, unless you have circumstances otherwise, is to just grab the basic package.  Good luck!

---

### Post by KaeseEs on 2007-06-05
> **Greggle said:**
> Damn! Okay, I got a lot farther into the configure process after that install you suggested. It barfed up an error while searching for glib. The last output was 'No package glib-2.0 found'. Is there another spiffy command like the previous one to install glib without downloading anything?

This is day two of my first foray into Linux. All apologies...

Try```
sudo aptitude install libglib2.0-0
```

---

### Post by Greggle on 2007-06-05
Negative, Kaes'. It ended by saying '0 packages upgraded, 0 newly installed, 0 removed and 46 not upgraded.'

---

### Post by WW on 2007-06-05
> **Greggle said:**
> 
This is day two of my first foray into Linux. All apologies...

No apologies necessary.  If this is day two, then you might not be aware of how the Ubunutu repository is divided into several components. One of them is the **universe** component, where you can find anjuta.  By default, this component is not enabled, so you won't be able to access these packages with the apt-get or aptitude command (nor with the GUI Synaptic).  The Ubuntu web pages have an explanation of [how to enable repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by Greggle on 2007-06-05
Thanks, WW.

Yeah, I've been searching through the Syanptic Package Manager, but a lot of the things I search for return pretty esoteric results, insofar as I don't know much about the lingo and suchlike. I still have a foot stuck in the Windows door, as it were.

Anyway, I did see in there that Anjuta was available, but is it the latest release? Will it install it for me, ala Windows? I'd kinda like to do it all through the terminal, by hand. I'm a DOS baby, so I'm not at all put out by the command line interface.

---

### Post by WW on 2007-06-05
Feisty has Anjuta version 1.2.4a, which, according to the Anjuta web page, is the latest stable release.

You can install it with Synaptic, or use the command that I showed earlier (assuming that you have enabled the universe repository).

If you really want to compile the source code--just for the fun of it, or to get the beta release version 2.1.3--then go for it.

---

### Post by Greggle on 2007-06-05
Thansk, WW!

I installed it with the command line per your post. Anjuta is a go.

I definitely want to learn how to compile a package from the command line, but I'll cross that bridge another day. Sleep beckons.

Again, thanks for the help. Bravo!

---

