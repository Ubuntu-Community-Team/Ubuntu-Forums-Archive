---
title: "Setting up modulefile for Intel compilers by using environment-modules"
date: 2019-12-30
forum: New to Ubuntu
---

### Post by mdhfiz on 2019-12-30
I am trying to install `openmpi` (not from apt) into my HPC system. I want to use intel compilers (fortran, c and c++) for the compilation. When `./configure` my openmpi folder, **without** `module load intel`, compiler will not be found and the installation will fail. Once, I load intel module environment, I manage to at least configure it. However, when running `make all makefile`, the installation runs but in the end it fails. I've been attempting it ever since and can't figure out why. My guess is my intel modulefile. I am using *Intel Parallel Studio XE Cluster Edition* 2020. I'm not sure if I create my modulefile correctly. Could someone have a look at my modulefile and possibly point out my mistake and fix this problem. Thank you! 


This is my intel modulefile:  


```
     #%Module1.0#####################################################################
    ##")
    ## intel modulefile
    ##
    proc ModulesHelp { } {
        puts stderr "\tAdds Intel compilers to your environment variables,"
    
    }
    
    module-whatis "adds Intel compilers to your environment variables"
    
    
    set        main_root        /home/hafiz/intel
    
    prepend-path    PATH                  $main_root/bin
    prepend-path    PATH                $main_root/debugger_2020/gdb/intel64/bin
    
    prepend-path    LIBRARY_PATH        $main_root/lib/intel64
    prepend-path    LD_LIBRARY_PATH        $main_root/lib/intel64
    
    prepend-path    CPATH               $main_root/include
    prepend-path    CPATH               $main_root/include/intel64
    
    prepend-path    INTEL_LICENSE_FILE       $main_root/licenses
    
    setenv          INTEL_CC_HOME            $main_root
    setenv          INTEL_FC_HOME            $main_root
    setenv          INTEL_PYTHONHOME           $main_root/debugger_2020/python/intel64



```

---

