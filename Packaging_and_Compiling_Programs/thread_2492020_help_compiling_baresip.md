---
title: "help compiling baresip"
date: 2023-10-27
forum: Packaging and Compiling Programs
---

### Post by bjlockie on 2023-10-27
I'm trying to compile [https://github.com/baresip/baresip](https://github.com/baresip/baresip)
I did sudo apt install libmosquitto-dev libopenaptx-dev libre-dev librem-dev (guess at the requirements).
The error I get now is:
```
$ cmake -B build
CMake Error at CMakeLists.txt:95 (find_package):
  Could not find a package configuration file provided by "re" with any of                               
  the following names:                                                                                   
                                                                                                         
    reConfig.cmake                                                                                       
    re-config.cmake                                                                                      
                                                                                                         
  Add the installation prefix of "re" to CMAKE_PREFIX_PATH or set "re_DIR" to                            
  a directory containing one of the above files.  If "re" provides a separate                            
  development package or SDK, be sure it has been installed.                                             
                                                                                                         
                                                                                                         
-- Configuring incomplete, errors occurred!
See also "/storage/programming/baresip/build/CMakeFiles/CMakeOutput.log".
```

---

### Post by #&amp;thj^% on 2023-10-27
I can't use it on my current system but, look here:[https://manpages.ubuntu.com/manpages/jammy/en/man1/baresip.1.html](https://manpages.ubuntu.com/manpages/jammy/en/man1/baresip.1.html)
Is that one not a good install?

---

### Post by TheFu on 2023-10-27
Did you look at CMakeOutput.log?

---

### Post by bjlockie on 2023-10-27
@1fallen that one is old, v3.6.0 is the latest.
I'm trying to track down a crash in the Android version and I'm hoping it also crashes in the Linux version.

---

### Post by bjlockie on 2023-10-27
The cmake log doesn't mean anything to me.
Here it is:

[ATTACH]292962[/ATTACH]

---

### Post by TheFu on 2023-10-27
> **TheFu said:**
> Did you look at CMakeOutput.log?

YOU, not me.  

Sorry, but my $dayjob is looking at stuff like this.  Usually, inside the log will be the error clearly spelled out. Sometimes it will recommend a solution.  YOU need to do the work.

---

### Post by bjlockie on 2023-10-27
I'm making progress.
I had to clone another repo it uses:
```
$ git clone https://github.com/baresip/re.git
```

Now I'm getting syntax errors from the source code. :-(

---

### Post by SeijiSensei on 2023-10-28
Is there some feature unique to this source version that you need? If not, I'd stick to the version in the repositories regardless of its age.

---

