---
title: "Discrepancy in Xutil.h?"
date: 2007-11-14
forum: Packaging and Compiling Programs
---

### Post by lvirden on 2007-11-14
Recently on comp.lang.tcl, a user of Ubuntu posted a question about a problem he was having building code on his system.
He reported in thread [http://groups.google.com/group/comp.lang.tcl/browse_thread/thread/33976aaa02c7a766/#](http://groups.google.com/group/comp.lang.tcl/browse_thread/thread/33976aaa02c7a766/#)
that 
> And X11/Xutil.h certainly defines the function as a void:
>
>  extern void XEmptyRegion( 

On my local Linux and Solaris systems, this file defines XEmptyRegion as returning int. And in fact, when I check the docs over the past 10 years, this function was defined by the X  Consortium as returning int since at least 1998.

HOWEVER, I also found some red hat archives that mention that back in 2002, they were getting reports about needing to change the return value for this function from void to Bool (int) .

So, I was wondering if perhaps that old Linux bug was still remaining in the version of the X header files being distributed in Ubuntu, or if perhaps the user in the above thread was using some REALLY old version of Ubuntu.

I don't have a machine where I can easily check this out, and I haven't been able to locate a web accessible server to browse the  ubuntu sources to check this out for myself, so I thought I would ask for help from some of the developers here.

---

