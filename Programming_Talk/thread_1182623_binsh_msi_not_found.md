---
title: "/bin/sh: msi: not found"
date: 2009-06-09
forum: Programming Talk
---

### Post by agilor on 2009-06-09
I try to compile executing 'make' and I get the following error. Any ideas?

make[3]: Entering directory `/home/epics/base-3.14.9/EtraxTest/EtraxTestApp/Db/O.linux-x86'
Inflating database from ../RpcThreshold-S3TRB0--SubEventId822.substitutions 
msi   -I. -I.. -I../O.Common -S../RpcThreshold-S3TRB0--SubEventId822.substitutions  > msi.tmp
/bin/sh: msi: not found
make[3]: *** [../O.Common/RpcThreshold-S3TRB0--SubEventId822.db] Error 127

---

### Post by yota on 2009-06-09
Hi Agilor,

in order to make someone able to help you, you should give some more details:
[LIST]
[*]what are you trying to compile
[*]where have you downloaded it, in which form (tar.gz etc.)
[*]what system are you using
[*]what development tools/libraries have you installed/using
[*]what is the exact procedure you are following
[/LIST]

---

### Post by agilor on 2009-06-09
I am trying to compile my own program, that uses EPICS (Experimental Physics and Industrial Control System). I am using Ubuntu. I am using Ubuntu.
It is too much complicated to explain, and very specific (I use epics base, Axis SDK and gcc-cross) . But anyhow can anyone give me any ideas of what could be the problem. I thought that it could be that I should install a package called msi, but I think that it does not exist, I am right?.
 I think that the key is in this line:
/bin/sh: msi: not found

I saw somwhere else that someone had a similar problem:
/bin/sh: g++: not found
and the solution was:
 	Code:
 	aptitude show g++ | grep State: 
If this shows **not installed**, then  	Code:
 	sudo apt-get install g++ 


but this does not work for me. :(

---

### Post by perlluver on 2009-06-09
At last I checked, MSI was part of the Microsoft Installer.  Was this built in Microsoft?  Or is it designed to run on Windows?

---

### Post by agilor on 2009-06-09
completing the what I wrote before, I tried:
'sudo apt-get install msi'
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package msi

What is msi?

---

### Post by yota on 2009-06-09
Ok, MSI (Macro Substitution and Include Tool) is an extension of EPICS: [http://www.aps.anl.gov/epics/extensions/msi/index.php](http://www.aps.anl.gov/epics/extensions/msi/index.php)

It seems that you need it...

Have you read the fine documentation&wiki right? ;-)

Hope this helps!

> **agilor said:**
> I am trying to compile my own program, that uses EPICS (Experimental Physics and Industrial Control System). I am using Ubuntu. I am using Ubuntu.
It is too much complicated to explain, and very specific (I use epics base, Axis SDK and gcc-cross) . But anyhow can anyone give me any ideas of what could be the problem. I thought that it could be that I should install a package called msi, but I think that it does not exist, I am right?.
 I think that the key is in this line:
/bin/sh: msi: not found

I saw somwhere else that someone had a similar problem:
/bin/sh: g++: not found
and the solution was:
 	Code:
 	aptitude show g++ | grep State: 
If this shows **not installed**, then  	Code:
 	sudo apt-get install g++ 


but this does not work for me. :(

---

### Post by blackxored on 2009-06-09
Install build-essential and then get the particulars of the package (README, INSTALL, 
COMPILING, etc.). Then you could try to compile. I agree you need to give more info.

---

### Post by agilor on 2009-06-09
I Installed the build-essential already and it did not work, but yota, regarding the MSI (Macro Substitution and Include Tool) I think that this makes sense. I will try to install this now (if I am able to...!)

---

### Post by agilor on 2009-06-09
Too many open files!!!!??

Im am trying to install the MSI (Macro Substitution and Include Tool) for EPICS, but when I try to compile using 'sudo make' it appears:

/home/epics/base-3.14.9/extensions$ sudo make
configure/CONFIG:5: configure/RELEASE: Too many open files
configure/CONFIG:13: configure/CONFIG: Too many open files
configure/CONFIG:17: configure/CONFIG_SITE: Too many open files
configure/RULES_TOP:3: configure/RULES_TOP: Too many open files
make: *** No targets specified and no makefile found.  Stop.

I did:
sudo sysctl -a | grep "fs.file-max"
rror: permission denied on key 'kernel.cap-bound'
error: permission denied on key 'kernel.cad_pid'
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
fs.file-max = 302305
error: permission denied on key 'dev.parport.parport0.autoprobe'
error: permission denied on key 'dev.parport.parport0.autoprobe0'
error: permission denied on key 'dev.parport.parport0.autoprobe1'
error: permission denied on key 'dev.parport.parport0.autoprobe2'
error: permission denied on key 'dev.parport.parport0.autoprobe3'

and I increased the fs.file-max to 1000000 with 'sudo sysctl -w fs.file-max=1000000' but I still get the same problem. Any ideas?

---

### Post by yota on 2009-06-10
Hi Agilor,

unfortunately is not simple to help you, the problem is complex and we have just a few details of what you're trying to do...

Anyway have you read the documentation? Are all the prerequisites met and required tools/libraries installed?

Moreover what is your level of experience? Are you already proficient with the GNU programming tools or is this a first time experience?

I looked at the README of the EPICS extensions and found that the requirements are pretty broad; I paste here it's content so you can check if everything is fine:
> 
README,v 1.7 2007/06/22 21:15:21 jba Exp

                        EPICS Extensions Build Instructions

                                  EPICS base 3.14        
 
Extensions Directory Structure

  EPICS software is divided into <top> areas. Examples of <top> areas are EPICS 
  base itself, EPICS extensions, and simple or complicated EPICS IOC applications. 

  The EPICS extensions <top> area has the following directory structure:

  <top>/ 
     Makefile
     configure/
               Makefile
               os/
     src/
         Makefile
         extension1/
                    Makefile
                    <subdirectories and source files>
         extension2/
                    Makefile
                    <subdirectories and source files>
         .
         .
         .
      include/
      bin/
      lib/
      html/
      . 
      . 
      . 
  
  where the <top> directory is usually named "extensions", configure is a 
  directory containing build configuration files and a Makefile, os is a 
  directory containing os specific build configuration files, and where each 
  extension<n> is a directory tree structure containing source files and 
  makefiles for an EPICS extension. The directories include, bin, lib, html, 
  and other directories are created by the build.

EPICS extensions setup

  Download the extensionsTop.tar.gz file:

    Unzip and untar the extensionTop.tar.gz distribution file.  Use WinZip 
    on Windows systems.

    This will create the extensions directory structure including 
    all configure and configure/os build configuration files, this README
    and Makefiles in extensions/ and extensions/src/.

  Download desired extensions:

    Many extensions are available from WWW pages at various EPICS
    sites.

  Unzip and untar extensions:

    Unzip and untar the extension distribution files to the 
    extensions/src directory. Use WinZip on Windows systems.

Extension build software requirements:

        To build EPICS base and extensions you will need following items 
        installed.  Some items can be obtained via links from the APS EPICS 
        software distribution web page - 
                [http://www.aps.anl.gov/xfd/WWW/xfd/SoftDist/Welcome.html](http://www.aps.anl.gov/xfd/WWW/xfd/SoftDist/Welcome.html)

        You may not have to build extensions at your site. Built extensions for 
        Win32 are available via the EPICS software distribution web page.

          ANSI C compiler or GNU gcc compiler.
         
          EPICS base distribution, R3.14.8 or later, available
          from [http://aps.anl.gov/](http://aps.anl.gov/)...

          GNU make, V3.70 or later.

          Perl, version 5.003 or later
 
Known conditional software requirements:

        X11 is needed by the following extensions
          alh, adt, ar, burt, dp, gdct313, mdct, km, libUnix, medm, probe,
          probeII, stripTool, caTCL, tcl, xmca, xmseq, sga
          motifButton, medm_cebaf, adt, popup, namecapture, SDDS/SDDSaps

        Motif is needed by the following extensions
          alh, adt, ar, burt, dp, km, medm, probe, probeII, StripTool,
          xmca, xmseq, motifButton, medm_cebaf, adt, popup, sga
          namecapture, SDDS/SDDSaps

        openwin3 is needed by the following extensions
          ar/ar

        Wingz is needed by the following extensions
          wingz

        Mathematica is needed by the following extensions
          math

        Xrtgraph is needed by the following extensions
          medm, medm_cebaf

        Interviews (Unidraw) is needed by the following extensions
          gdct313

        Tk-tcl is needed by the following extensions
          ar/arrtk, caTCL, tcl, tcl_select, dct, casr

        Blt is needed by the following extensions
          ar/arrtk, caTCL

        Idl is needed by the following extensions
          pvwave, tcl/apswish, tcl/interpreters/tcl_it ezcaIDL

        Java is needed by the following extensions
          dbStaticJava, doubleLinkList, jca, Jdct, jca, jprobe

Extensions build prerequisites

        EPICS_HOST_ARCH

           You must properly set the environemnt variable EPICS_HOST_ARCH. The
          epics/startup/EpicsHostArch script file is provided with EPICS base
          to set EPICS_HOST_ARCH.
 
        EPICS base

            EPICS base must be configured and built prior to building any
          extension

        RELEASE file

          The EPICS_BASE definition in extensions/configure/RELEASE file must
          point to the <top> of your built EPICS base.

        configure/CONFIG_SITE files

          Your extensions/configure directory must be present and the 
          CONFIG_SITE* files properly configured prior to building an extension.

        Build in configure first

          You must do a build in the extensions/configure directory before
          building any extensions and you must rebuild in configure each time 
          the configure/RELEASE file is modified.

Extensions build commands 

        Build a single extension (e.g. extension xyz):

          NOTE: The extensions on which this extension depends must be built
          first. 

          cd epics/extensions/src/xyz
 
            gmake            - To build and install the extension.
            gmake install    - To build and install the extension.
            gmake clean      - To clean temporary object files.  Clean will
                               remove ALL O.<arch> subdirectoriess.
            gmake rebuild    - To clean, build and install the extension.

        "Partial" build commands:

            gmake clean.<epics_host_arch>   - Removes O.<epics_host_arch> and 
                                              O.Common directories.
            gmake install.<epics_host_arch> - Builds and installs <epics_host_arch>
                                              arch only.
        Building a specific object file

          While developing code in a specific source file e.g. abc.c, cd to
          the source dir's  O.<epics_host_arch> directory, and invoke 
          "gmake <target_filename>" e.g.
                  vi alh.c
                  cd O.solaris-sparc
                  gmake alh.o
          The above example instructs make to build only alh.o.

        Build all extensions present in your epics tree:

          cd epics/extensions

          gmake            - To build and install all extensions.
          gmake clean      - To clean temporary object files.  Clean will
                             remove ALL O.<host_arch> subdirectories.
          gmake rebuild    - To clean, build, and install all extensions.

          To build all extensions present in an extensions tree using one 
          gmake command the DIRS list definition in extensions/src/Makefile 
          needs to contain all your extension directory names.  Make sure 
          that the dependancy extensions names for an extension preceed that 
          extension name.

Extensions build notes 

        Install locations 

          Executables are installed into $(INSTALL_LOCATION)/bin/<arch>
          and libraries into $(INSTALL_LOCATION)/lib/<arch>. INSTALL_LOCATION
          defaults to <top> but may be changed in the configure/CONFIG_SITE
          file.

        Header file dependancies

          During a normal build (a "gmake" or "gmake install"), a file
          containing header file dependancies is automatically generated in
          the O.<host_arch> directory for each c/c++ source file. These files
          have the source file name with a ".depends" suffix.
     
        Object files

          Compiler output object files are stored in the created O.<host_arch>
          directories. This allows objects for multiple host architectures to 
          be maintained in the same tree structure at the same time.


---

### Post by yota on 2009-06-10
Googling around I've found this tutorial that should help get EPICS running on ubuntu:

[http://nibot-lab.livejournal.com/91787.html](http://nibot-lab.livejournal.com/91787.html)

I hope it can help you.

---

### Post by agilor on 2009-06-11
[LEFT]Thanks Yota, your link helped me a lot to **install MSI for EPICS**. It is working now. I summarize what I did to install it:
Since MSI (Macro Substitution and Include Tool) is an extension of EPICS, first I had to install the so called "extensions top" (download from [http://www.aps.anl.gov/epics/extensions/msi/index.php](http://www.aps.anl.gov/epics/extensions/msi/index.php)) file:extensionsTop_20070703.tar.gz

Go to the epics directory (I assume something like /home/epics) and
tar -zxvf extensionsTop_20070703.tar.gz

This creates the directory "extensions" which includes many subdirectories and files. Then

emacs /home/epics/extensions/configure/RELEASE

define the variables EPICS_BASE and EPICS_EXTENSIONS to the correct value. Ie:
EPICS_BASE=/home/epics/base-3.14.9/
EPICS_EXTENSIONS=/home/epics/extensions

 /home/epics/extensions/configure$ make

Download MSI file:msi1-5.tar.gz from the link above. You can use:
wget -N [http://www.aps.anl.gov/epics/download/extensions/msi1-5.tar.gz](http://www.aps.anl.gov/epics/download/extensions/msi1-5.tar.gz)
tar -zxvf msi1-5.tar.gz
It creates a directory called msi1-5, which you have to move to
 /home/epics**/**extensions/src/

emacs /home/epics**/**extensions/src/Makefile
and modify in the Makefile the EXTENSION_MSI variable to the name of the directory msi:
EXTENSION_MSI = msi1-5

/home/epics/extensions/src$ make

Thats it!
now, just to check that it works:
cd /home/epics/extensions/bin/linux-x86
msi --help

----------------------
Then I do not why it appears the message: "Too many open files", but doing the right installation procedure it does not appear anymore


[/LEFT]

---

### Post by agilor on 2009-06-11
Then the problem to my initial topic "/bin/sh: msi: not found"
was solved installing MSI(Macro Substitution and Include Tool), and extension of EPICS.

However, to be able to compile I still have to do first:
export PATH=$PATH:/home/epics/extensions/bin/linux-x86
to be able to see msi from any directory.

Thanks a lot to everybody for your help!

---

### Post by yota on 2009-06-11
Instead of extending the path you can also copy the msi binary to the "/usr/local/bin" which is the perfect place where the user can add it's own custom commands (and scripts).
It's a folder which is never touched by the package manager and it's already in path having precedence over other standard paths.

Anyway I'm happy that you managed to get it working :-)

> **agilor said:**
> Then the problem to my initial topic "/bin/sh: msi: not found"
was solved installing MSI(Macro Substitution and Include Tool), and extension of EPICS.

However, to be able to compile I still have to do first:
export PATH=$PATH:/home/epics/extensions/bin/linux-x86
to be able to see msi from any directory.

Thanks a lot to everybody for your help!

---

