---
title: "Path funkiness compiling Matlab scripts"
date: 2008-01-09
forum: Programming Talk
---

### Post by tgrimley on 2008-01-09
Having some trouble getting compiling matlab apps setup on one of my gutsy machines.  I have matlab installed to my home dir and haven't had any problems before.  I think it's not finding the right gcc directory or something but I'm pretty green with compiling under matlab.  Here's the output when I try to compile it.  Any points would be much appreciated!

```

>> mcc -v -m magicsquare.m            
Warning: Cannot convert string "-b&h-lucidasans-medium-r-normal-sans-*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Duplicate directory name: /home/tgrimley/matlabr2007a/toolbox/local.
Compiler version: 4.6 (R2007a)
Processing /home/tgrimley/matlabr2007a/toolbox/matlab/mcc.enc
Processing /home/tgrimley/matlabr2007a/toolbox/database/mcc.enc
Processing include files...
2 item(s) added.
Processing directories installed with MCR...
The file mccExcludedFiles.log contains a list of functions excluded from the CTF archive.
0 item(s) added.
Generating MATLAB path for the compiled application...
Created 38 path items.
Begin validation of MEX files: Wed Jan  9 15:41:20 2008
Validating '/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deploywhich.mexglx'.
No conflicting M-file found.
Validating '/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/readline.mexglx'.
No conflicting M-file found.
End validation of MEX files: Wed Jan  9 15:41:20 2008
Deleting 2 temporary MEX authorization files.
Removing: '/tmp/filev8NqGW_5961.auth'.
Removing: '/tmp/fileUEsOC2_5961.auth'.
Parsing file "/home/tgrimley/Documents/matlab-test/magicsquare.m"
        (Referenced from: "Compiler Command Line").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m"
        (Referenced from: "Compiler Command Line").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/compiler/dirname.m"
        (Referenced from: "Compiler Command Line").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m"
        (Referenced from: "Compiler Command Line").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/printdlg.m"
        (Referenced from: "Compiler Command Line").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/elmat/magic.m"
        (Referenced from: "/home/tgrimley/Documents/matlab-test/magicsquare.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/strfun/str2num.m"
        (Referenced from: "/home/tgrimley/Documents/matlab-test/magicsquare.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/iofun/filesep.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/hgrc.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/codetools/initdesktoputils.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/local/initprefs.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/isdeployed.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/ispc.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/lang/lasterror.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/local/pathdef.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/pwd.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/recycle.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/local/reporterrorlogs.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/strfun/str2double.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/usejava.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/matlabrc.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/iofun/fileparts.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/dirname.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/timefun/datestr.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/graphics/getappdata.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/datatypes/isfield.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/uitools/msgbox.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/timefun/now.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/datatypes/num2cell.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/strfun/num2str.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/graphics/orient.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/graphics/print.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/iofun/tempname.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/deployprint.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/path.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/printdlg.m").
Parsing file "/home/tgrimley/matlabr2007a/toolbox/matlab/general/rmpath.m"
        (Referenced from: "/home/tgrimley/matlabr2007a/toolbox/compiler/deploy/printdlg.m").
Generating file "magicsquare_main.c".
Generating file "run_magicsquare.sh".
Generating file "readme.txt".
Generating file "magicsquare_mcc_component_data.c".
Executing command: mbuild -O -v -output "magicsquare" "magicsquare_main.c" "magicsquare_mcc_component_data.c" -link exe
----------------------------------------------------------------
-> mbuildopts.sh sourced from directory (DIR = $HOME/.matlab/$REL_VERSION)
   FILE = /home/tgrimley/.matlab/R2007a/mbuildopts.sh
----------------------------------------------------------------
->    TMW_ROOT              = /home/tgrimley/matlabr2007a
->    CC                    = gcc
->    CC flags:
         CFLAGS             = -I/home/tgrimley/matlabr2007a/extern/include -DUNIX -DX11 -ansi -D_GNU_SOURCE -pthread -fexceptions
         CDEBUGFLAGS        = -g
         COPTIMFLAGS        = -O -DNDEBUG
         CLIBS              = -Wl,--rpath-link,/home/tgrimley/matlabr2007a/bin/glnx86 -L/home/tgrimley/matlabr2007a/bin/glnx86  -lmwmclmcrrt -lm -lstdc++
         arguments          = 
->    LD                    = gcc
->    Link flags:
         LDFLAGS            = -pthread
         LDDEBUGFLAGS       = -g
         LDOPTIMFLAGS       = -O
         arguments          = 
----------------------------------------------------------------

-> gcc -c  -I/home/tgrimley/matlabr2007a/extern/include -DUNIX -DX11 -ansi -D_GNU_SOURCE -pthread -fexceptions  -O -DNDEBUG magicsquare_main.c

magicsquare_main.c:8:19: error: stdio.h: No such file or directory
In file included from magicsquare_main.c:9:
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:68:20: error: string.h: No such file or directory
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:69:19: error: wchar.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from /home/tgrimley/matlabr2007a/extern/include/tmwtypes.h:40,
                 from /home/tgrimley/matlabr2007a/extern/include/matrix.h:316,
                 from /home/tgrimley/matlabr2007a/extern/include/mclmcr.h:70,
                 from magicsquare_main.c:9:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /home/tgrimley/matlabr2007a/extern/include/mclmcr.h:70,
                 from magicsquare_main.c:9:
/home/tgrimley/matlabr2007a/extern/include/matrix.h:882:20: error: stdlib.h: No such file or directory
/home/tgrimley/matlabr2007a/extern/include/matrix.h:1264:22: error: assert.h: No such file or directory
In file included from magicsquare_main.c:9:
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:224: error: expected specifier-qualifier-list before \u2018int32_t\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:240: error: expected declaration specifiers or \u2018...\u2019 before \u2018int32_t\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:241: error: expected declaration specifiers or \u2018...\u2019 before \u2018int32_t\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:244: error: expected \u2018=\u2019, \u2018,\u2019, \u2018;\u2019, \u2018asm\u2019 or \u2018__attribute__\u2019 before \u2018utf16_strlen_fcn\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:247: error: expected declaration specifiers or \u2018...\u2019 before \u2018int32_t\u2019
In file included from magicsquare_main.c:9:
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:431:24: error: stdint.h: No such file or directory
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:432: error: expected \u2018=\u2019, \u2018,\u2019, \u2018;\u2019, \u2018asm\u2019 or \u2018__attribute__\u2019 before \u2018mxInt64\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:433: error: expected \u2018=\u2019, \u2018,\u2019, \u2018;\u2019, \u2018asm\u2019 or \u2018__attribute__\u2019 before \u2018mxUint64\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:1212: error: expected declaration specifiers or \u2018...\u2019 before \u2018mxInt64\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:1212: error: expected declaration specifiers or \u2018...\u2019 before \u2018mxInt64\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:1215: error: expected declaration specifiers or \u2018...\u2019 before \u2018mxUint64\u2019
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:1215: error: expected declaration specifiers or \u2018...\u2019 before \u2018mxUint64\u2019
magicsquare_main.c: In function \u2018mclDefaultPrintHandler\u2019:
magicsquare_main.c:29: warning: incompatible implicit declaration of built-in function \u2018strlen\u2019
magicsquare_main.c: In function \u2018mclDefaultErrorHandler\u2019:
magicsquare_main.c:44: warning: incompatible implicit declaration of built-in function \u2018strlen\u2019

    mbuild: compile of 'magicsquare_main.c' failed.

Error: An error occurred while shelling out to mbuild (error code = 1).
Unable to build executable.
??? Error executing mcc, return status = 1.

>> 


```

---

### Post by evymetal on 2008-01-11
> **tgrimley said:**
> 

```

----------------------------------------------------------------
->    TMW_ROOT              = /home/tgrimley/matlabr2007a
->    CC                    = gcc
->    CC flags:
         CFLAGS             = -I/home/tgrimley/matlabr2007a/extern/include -DUNIX -DX11 -ansi -D_GNU_SOURCE -pthread -fexceptions
         CDEBUGFLAGS        = -g
         COPTIMFLAGS        = -O -DNDEBUG
         CLIBS              = -Wl,--rpath-link,/home/tgrimley/matlabr2007a/bin/glnx86 -L/home/tgrimley/matlabr2007a/bin/glnx86  -lmwmclmcrrt -lm -lstdc++
         arguments          = 
->    LD                    = gcc
->    Link flags:
         LDFLAGS            = -pthread
         LDDEBUGFLAGS       = -g
         LDOPTIMFLAGS       = -O
         arguments          = 
----------------------------------------------------------------

-> gcc -c  -I/home/tgrimley/matlabr2007a/extern/include -DUNIX -DX11 -ansi -D_GNU_SOURCE -pthread -fexceptions  -O -DNDEBUG magicsquare_main.c

magicsquare_main.c:8:19: error: stdio.h: No such file or directory
In file included from magicsquare_main.c:9:
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:68:20: error: string.h: No such file or directory
/home/tgrimley/matlabr2007a/extern/include/mclmcr.h:69:19: error: wchar.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from /home/tgrimley/matlabr2007a/extern/include/tmwtypes.h:40,
                 from /home/tgrimley/matlabr2007a/extern/include/matrix.h:316,
                 from /home/tgrimley/matlabr2007a/extern/include/mclmcr.h:70,
                 from magicsquare_main.c:9:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /home/tgrimley/matlabr2007a/extern/include/mclmcr.h:70,
                 from magicsquare_main.c:9:
/home/tgrimley/matlabr2007a/extern/include/matrix.h:882:20: error: stdlib.h: No such file or directory
/home/tgrimley/matlabr2007a/extern/include/matrix.h:1264:22: error: assert.h: No such file or directory 


```

I've not built from matlab > C myself, but it seems to have set it up fine for GCC. The (first?) problem is with your include path.

stdio.h, string.h, and wchar.h are all standard C headers - do you have the standard C headers installed?

sudo apt-get install libc-dev

If that doesn't work then try setting up the correct paths for GCC.

also, check the matlab readme to see if you need any other libraries.

---

### Post by Zugzwang on 2008-01-11
Also make sure you have build-essential installed:
```

sudo aptitude install build-essential

```

---

