---
title: "cross comiler error while building android ROM"
date: 2016-01-21
forum: Packaging and Compiling Programs
---

### Post by jhajhria44 on 2016-01-21
I have been trying to build carbon rom for oneplus2 using Ubuntu 64bit but can't get past this error. so far i think mighthave found the solution but not sure how to use it. 

i re installed Ubuntu and everything just to be sure that it was not something because of what i did.

here is the error - [here]("http://pastebin.com/raw/bY8s1zcZ")

i think this is the main error 
 	Code: 
 	 	/usr/bin/as: unrecognized option '-mfloat-abi=softfp'
clang: error: assembler command failed with exit code 1 (use -v to see invocation) 
so i  searched and found something on this.  its related to compiler issue.

Solution -[ here]("https://falstaff.agner.ch/2015/03/03/cross-compile-linux-for-arm-using-llvmclang-on-arch-linux/")

-----------------------part from the above link ------------------------------------------------------

 	 		Quote:
 		 		Wrong assembler


 	Code: 
 	 	/usr/bin/as: unrecognized option '-mfloat-abi=soft'
clang: error: assembler command failed with exit code 1 (use -v to see invocation) 
To compile the kernel, clang does not use its internal assembler  but uses the GNU assembler (by using the -no-integrated-as option). In  this case the build system picked your hosts assembler (x86_64) instead  of the one provided by the cross compiler toolchain. The simplest way to  work around this is creating a symlink to clang in the cross compiler  toolchains directory:
 	Code: 
 	 	$ ln -s /usr/bin/clang ~/gcc-linaro-arm-linux-gnueabihf-4.9-2014.09_linux/bin/clang 
-----------------------------------------------part ends --------------------------------------------

	
	 
  i tried the solution but it said no such directories.
Conclusion i need to find the right directories.

 so is the solution that i found correct and if it is the right solution then how do i find out the directory which i should use??

---

