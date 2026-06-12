---
title: "how to install PETSC 3.3 and petsc4py in UBUntu 64 bit, 12.04"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by astriedinger on 2012-11-14
Hello GUys,

I am totaly new, I Ahve only dealt with LInux UBuntu fro a bout a week or so, and some installation manuals or README files for programs I dont understand.  My situation is the following:

I am trying to install PETSC 3.3 or higer in my computer becasue the petsc4py seems to need it for the proper installation (according to the readme file). I downloades the file frm PETSC website (PETSC3.3-pa4) and try to install it.

After writing in the comand window what they indicated in quotes "   " I got the following in the comand window:

TESTING: checkFortranPreprocessor from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:634)
TESTING: checkFortranDefineCompilerOption from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:655)
TESTING: checkFortranLibraries from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:671)
TESTING: checkFortran90 from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:1047)
TESTING: checkFortran2003 from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:1060)
TESTING: checkFortran90Array from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:1080)
TESTING: checkFortranModuleInclude from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:1167)
TESTING: checkFortranModuleOutput from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:1233)
TESTING: setupFrameworkCompilers from config.compilers(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/compilers.py:1360)
.......
.......
......(MORE STUFF)...
.....
...

TESTING: configureLibrary from config.packages.MPI(/home/s117555/Downloads/petsc-3.3-p4/config/BuildSystem/config/packages/MPI.py:722)
*******************************************************************************
         UNABLE to CONFIGURE with GIVEN OPTIONS    (see configure.log for details):
-------------------------------------------------------------------------------
Downloaded package mpich from: [http://www.mcs.anl.gov/research/projects/mpich2/downloads/tarballs/1.4.1p1/mpich2-1.4.1p1.tar.gz](http://www.mcs.anl.gov/research/projects/mpich2/downloads/tarballs/1.4.1p1/mpich2-1.4.1p1.tar.gz) is not a tarball.
[or installed python cannot process compressed files]
* If you are behind a firewall - please fix your proxy and rerun ./configure
  For example at LANL you may need to set the environmental variable http_proxy (or HTTP_PROXY?) to  [http://proxyout.lanl.gov](http://proxyout.lanl.gov) 
* Alternatively, you can download the above URL manually, to /yourselectedlocation/mpich2-1.4.1p1.tar.gz
  and use the configure option:
  --download-mpich=/yourselectedlocation/mpich2-1.4.1p1.tar.gz
******************************************************************************
For which I deduced I need the mpich.... I downloaded it but I have no clue how  to install it, the guide lines in readme.pf from the mpchi file are... I dont get it.

Can some body  please tell me how to finaly get my PETSC 3.2, or 3.3 working in my computer.

I appreciate your help on this guys.

KInd regards,
Alberto Striedinger

---

