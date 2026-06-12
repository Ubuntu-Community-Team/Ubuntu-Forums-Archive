---
title: "[SOLVED] Cannot load GIMP"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by stevebond001 on 2008-11-11
Hi
I have recently upgraded to Intrepid and all is well except for when I try to run GIMP from the Menu it will not launch (I get a box in the lower panel saying that GIMP is starting, but then disappears).
I have tried running GIMP from a terminal session running ***sudo gimp*** and I get the following error message:

***(gimp:26196): LibGimpBase-WARNING **: gimp: wire_read(): error***

Has anyone got any ideas on how to solve this?

Thanks very much

---

### Post by bscbrit on 2008-11-11
Good question - but you are not the only one with this problem.  One site has suggested the following:

```

> (gimp:1109): LibGimpBase-WARNING **: gimp: wire_read(): error
> /usr/lib/gimp/2.0/plug-ins/svg: error while loading shared libraries:  
> librsvg-2.                 so.2: cannot open shared object file: No such  
> file or directory
> 
find librsvg and install it.  without it you will not be able to import
and export paths.

```


But there are other suggestions : see [http://lists.xcf.berkeley.edu/lists/gimp-user/2005-November/006776.html](http://lists.xcf.berkeley.edu/lists/gimp-user/2005-November/006776.html) although it seems that this fault should have been corrected by now if it was around 3 years ago!

See if any of them help and, if not, come back and we will delve deeper.

I've checked and my version seems to work OK.  You might also try un-installing and re-installing gimp again.

---

### Post by stevebond001 on 2008-11-11
bscbrit
Thanks very much for the advice.

I have now solved the issue as follows:
When I re-ran **sudo gimp** I saw the following error:
***/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory***

I found a thread which discussed this ([http://ubuntuforums.org/showthread.php?t=825345](http://ubuntuforums.org/showthread.php?t=825345)) and one reply was to uninstall gimpshop.

I have now uninstalled gimpshop and hey presto, gimp now works correctly.

Hope this helps others with the same problem

Thanks once again.

---

### Post by bscbrit on 2008-11-11
Great! - see you around the forums.

bscbrit

---

