---
title: "Missing Gimp directory path"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by carusoswi on 2013-11-10
Ok, I am running Ubuntu 13.10.  I installed the experimental version of Gimp, version 2.9.1 from the associated PPA.
Worked fine on a couple of new 16-bit tiffs (snappy performance, too!).

Then, on subsequent and new files started throwing the following error message:  Plug-in crashed: "file-tiff-load" 
                                                                                                                        /usr/lib/gimp/2.0/plug-ins/file-tiff-load

                                                                                                                       The dying plug-in may have messed up GIMP's internal state. 
                                                                                                                       You may want to save your images and restart GIMP to be on the safe side.

Searching the web for a solution, I came upon a suggestion to delete that plugin and that Gimp would rebuild it or some such thing upon the next restart.

So, I opened a terminal and tried to follow the path to the plugins folder.

I cannot get to /usr/lib/gimp/.  Terminal reports that no such file or directory exists.

Obviously, there is a gimp directory somewhere, or the application would not run at all, so, how would I go about finding it?

Incidentally, Gimp 2.9.1 happily continue to open those files it previously opened without a complaint, and 2.9.1 will open 8-bit files, also without a complaint.

The solution to this problem isn't an urgent need, I can still remove 2.9.1 and re-install 2.8.8.  

But, I am very curious to find a solution to the problem.

Any advice appreciated.

Thanks.

Caruso

---

### Post by Otto06127 on 2013-11-18
> **carusoswi said:**
> Ok, I am running Ubuntu 13.10.  I installed the experimental version of Gimp, version 2.9.1 from the associated PPA.
Worked fine on a couple of new 16-bit tiffs (snappy performance, too!).

Then, on subsequent and new files started throwing the following error message:  Plug-in crashed: "file-tiff-load" 
                                                                                                                        /usr/lib/gimp/2.0/plug-ins/file-tiff-load

                                                                                                                       The dying plug-in may have messed up GIMP's internal state. 
                                                                                                                       You may want to save your images and restart GIMP to be on the safe side.

Searching the web for a solution, I came upon a suggestion to delete that plugin and that Gimp would rebuild it or some such thing upon the next restart.

So, I opened a terminal and tried to follow the path to the plugins folder.

I cannot get to /usr/lib/gimp/.  Terminal reports that no such file or directory exists.


The path is /usr/lib/gimp/2.0/
> 
Obviously, there is a gimp directory somewhere, or the application would not run at all, so, how would I go about finding it?

Incidentally, Gimp 2.9.1 happily continue to open those files it previously opened without a complaint, and 2.9.1 will open 8-bit files, also without a complaint.


Please update to the current version from my PPA. IMHO the Gimp developers have done their work regarding TIFF with more than 8 Bit. Check it out.
[https://launchpad.net/~otto-kesselgulasch/+archive/gimp-edge](https://launchpad.net/~otto-kesselgulasch/+archive/gimp-edge)

>  

The solution to this problem isn't an urgent need, I can still remove 2.9.1 and re-install 2.8.8.  

But, I am very curious to find a solution to the problem.

Any advice appreciated.

Thanks.

Caruso

Caruso, please consider you're on the edge of development. :mrgreen:

Cheers

Otto

---

