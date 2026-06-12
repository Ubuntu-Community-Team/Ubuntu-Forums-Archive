---
title: "Boost application build fails in precise."
date: 2016-09-03
forum: Packaging and Compiling Programs
---

### Post by ueter on 2016-09-03
Builds of Boost applications tend to blow out with
 
 ```
configure: error: Could not find a version of the library!

``` 
 

 The stock solution for this is  
 
 ```
./configure --with-boost-libdir=/usr/lib/x86_64-linux-gnu

``` 


This can be made more generic with

 ```
./configure --with-boost-libdir=/usr/lib/$(DEB_HOST_MULTIARCH)  

``` 
 
 
 
 This is working for me with trusty, xenial & yakkety, but in precise, I still get this error.
 Does anyone know how to fix this in precise?
 
 
 
 My rules file  commands are  
 
 ```

export DH_VERBOSE = 1
export DEB_BUILD_MAINT_OPTIONS = hardening=+all
include /usr/share/dpkg/default.mk
 
%:
     dh $@  --with autotools_dev
  
override_dh_auto_configure:
     dh_auto_configure -- --with-boost-libdir=/usr/lib/$(DEB_HOST_MULTIARCH)
 
``` 
 
 
The reported error, (only for precise) is
 
 ```
….
  checking build system type... x86_64-pc-linux-gnu
  checking whether the Boost::Thread library is available... yes
  configure: error: **Could not find a version of the library!**

``` 
 
 
 
 The other builds, with the same source, all proceed like this
 
 ```
….
 checking build system type... x86_64-pc-linux-gnu
 checking whether the Boost::Thread library is available... yes
 checking for exit in -lboost_thread... yes
 checking whether the Boost::IOStreams library is available... yes
 checking for exit in -lboost_iostreams... yes
 checking whether the Boost::System library is available... yes
 checking for exit in -lboost_system... yes
 checking host system type... x86_64-pc-linux-gnu
....

``` 
 
 
 
 Regards,
 Peter
 ….

---

