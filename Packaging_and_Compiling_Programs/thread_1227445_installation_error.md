---
title: "installation error"
date: 2009-07-30
forum: Packaging and Compiling Programs
---

### Post by denish_hp_6383 on 2009-07-30
I need to make browser for linux in gtkmm.
so I had download package gtkmozembedmm-1.4.2 from its official website.
than I had configure it using **./configure** command
after that I need to install it using **make** statement..
but after half of the installation it prompt error as....

[COLOR=SandyBrown][COLOR=DarkRed]/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_TraceChildren'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_CallTracer'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_ClearOperationCallback'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_GetOperationLimit'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_CallIteratorNext'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_NewObjectWithGivenProto'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_CloseIterator'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_PutCallObject'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_ThrowStopIteration'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_CallClass'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_ComputeThis'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_GetGlobalForObject'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_GetGCThingTraceKind'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_AlreadyHasOwnUCProperty'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_SetExtraGCRoots'
collect2: ld returned 1 exit status
make[2]: *** [generate_extra_defs] Error 1
make[2]: Leaving directory `/home/justdial/Desktop/web_browser/1.4.0/gtkmozembedmm-1.4.0/tools/extra_defs_gen'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/justdial/Desktop/web_browser/1.4.0/gtkmozembedmm-1.4.0/tools'
make: *** [all-recursive] Error 1


[COLOR=Black]Please Help me solve this......
thanks.....
[/COLOR][/COLOR][/COLOR]

---

### Post by Leslie Viljoen on 2009-08-06
You will need to look at the top half :-)
If you scan upwards, you'll probably see a line where it talks about a certain .h file that is missing. You then go over here: [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for that .h file. That will tell you which source package to install, something like "sudo apt-get install whatever-dev". Then try the compile again.

Often there is a README or an INSTALL file which tells you which packages to install in order to compile something - and normally you want the -dev versions of everything.

Also, if the thing you are compiling has a binary package in the repos, you can automatically install all the -dev packages it relies on using "sudo apt-get build-dep PACKAGE-NAME".

---

