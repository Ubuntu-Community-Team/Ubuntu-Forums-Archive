---
title: "Problems getting the Mono debugger to work under Jaunty"
date: 2009-04-27
forum: Programming Talk
---

### Post by schmendrick on 2009-04-27
hi,

i have updated to jaunty and tried to use the mono debugger (mdb).
i have the following additional mono packages installed:

mono-debugger
monodevelop
monodevelop-debugger-mdb


but i get the following error when i try to use it, (independent if i try it from commandline or from monodevelop):  

Cannot read symbol file `/usr/lib/mono/2.0/mscorlib.dll.mdb': Could not find file "/usr/lib/mono/2.0/mscorlib.dll.mdb".

when trying to debug a 1.0 project, i get the following error:

Cannot read symbol file `/usr/lib/mono/1.0/mscorlib.dll.mdb': Could not find file "/usr/lib/mono/1.0/mscorlib.dll.mdb"


in monodevelop, after i set a breakpoint, i can start the debugging session, but after the above error my helloworld application does not show any output, nor does the debugging session finnish.
there will be the following output on commandline (from where i started monodevelop):


---------------------------------------------------------
## DebuggerServer started
Cannot read symbol file `/usr/lib/mono/2.0/mscorlib.dll.mdb': Could not find file "/usr/lib/mono/2.0/mscorlib.dll.mdb".

WARNING: Got event 137f for unknown pid 1880
WARNING: Got event 137f for unknown pid 1881

** (MonoDevelop:1746): WARNING **: _wapi_handle_unref: Attempting to unref unused handle 0x4bb

---------------------------------------------------------


i then only can then press the "stop current build or application execution" :(

if i do not use the debugger, i can build and run mono apps normally.

the defined file mscorlib.dll.mdb is indeed not exisitng in /usr/lib/mono/2.0/, (mscorlib.dll can be found in that directory). anybody having an idea what i can do against that?


btw: this error is not only happening on my updated ubuntu machine but also on my FRESH kubuntu install on a second PC, so i have to guess this error is happening on every jaunty installation? anybody can confirm?


any ideas, how to get this working?

---

### Post by Zugzwang on 2009-04-27
> **schmendrick said:**
> 
the defined file mscorlib.dll.mdb is indeed not exisitng in /usr/lib/mono/2.0/, (mscorlib.dll can be found in that directory). anybody having an idea what i can do against that?


Yes. Use [http://packages.ubuntu.com](http://packages.ubuntu.com) to search for a package containing that file. You will see that you need to install the package "mono-dbg".

---

### Post by schmendrick on 2009-04-27
thanks zugzwang! 

i didnt know i could do that! after installing that package the "Cannot read..." error is gone.

but if that mono-dbg package is needed in some way shouldnt there be a dependency that you cannot install mono-debugger? 





I still have those 


WARNING: Got event 137f for unknown pid 9884
WARNING: Got event 137f for unknown pid 9885


warnings which prevent me from debugging. 
but after googling anew i now know: this is already known and a bug was reported yesterday:

[https://bugs.launchpad.net/ubuntu/+source/mono-debugger/+bug/367232](https://bugs.launchpad.net/ubuntu/+source/mono-debugger/+bug/367232)

so i'll wait for a new jaunty package.

---

### Post by schmendrick on 2009-04-30
mmmh, i'm not patient enough  :)

okay, i could also (try to) build everything i need from source, but i think ubuntu deserves a completely working mono+debugger out -of-the-box

on the above thread the responsible guy said that he'd do a backport to jaunty of a newer fixed version of the mono-debugger as soon as the package becomes available in karmic koala.

who and where can i kindly ask to add the needed mono packages to the karmic repositories? 

plus, is there maybe somebody willing to explain to me for what he needs the packages in karmic to get it running on jaunty anyway?

---

### Post by directhex on 2009-04-30
[https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

Add & wait.

---

### Post by thezman on 2009-05-02
Thank you so much directhex. That worked perfectly.

---

### Post by directhex on 2009-05-02
Oh, and usual rules apply - may crash, may wipe your disk, may eat your pony, IANAL, IDKFA, BBQ.

---

### Post by schmendrick on 2009-05-02
many many thanks directhex! 

all working now on both my ubuntu & kubuntu installs!

---

### Post by SKLP on 2009-05-05
Thanks, directhex.

---

