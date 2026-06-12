---
title: "Problem with cblas.h in package libblas3-dev"
date: 2009-11-10
forum: Packaging and Compiling Programs
---

### Post by hughbert on 2009-11-10
Hi all, I've posted something about this in the beginners forum because I didn't know really where to put it, but I'll try it here as well (if this is breaking the rules, I'm sorry, please let me know and I'll remove one of the threads or something).

*Note; I am something of a noob so be kind if what I say isn't 100% correct, it's just how I understand it at the moment.*

There is a problem with the file cblas.h which appears in /usr/include as part of libblas3-dev on ubuntu 9.10

Effectively the file has incorrect naming (based on the C language standard) and absence of some functions and as such won't work in association with other packages which call these functions.

We discovered this when I and my university supervisor were installing packages & software onto my laptop (ubuntu 9.10) and got error messages from a program trying to call functions from cblas.h.

We got round this by copying cblas.h from his computer, which runs a different distro and already had the file/package installed.

Is this the right place to post this? If not can you point me to the right place?

Thanks
Hugh

---

### Post by SevenMachines on 2009-11-11
dont know which forum is the right one for this, my advice would be to have a look at [atlas]("http://math-atlas.sourceforge.net/errata.html"), where blas comes from, and see if its a known issue, or something else. From a quick glance I would guess that missing functions/symbols seems to be a compiling issue and not an oversight. If its not a bug and its a compiling issue then this is the right place :) but it would need more imformation on what the problem you had was

---

### Post by hughbert on 2009-11-11
Thanks for the advice, I'll have a look. 
 
I'm not entirely sure what the extent of the problem is since my supervisor solved it pretty quickly but what tipped us off that something was wrong was that another file was trying to call the function **cblas_daxpby **(I think) and no such function existed in cblas.h. 
 
There *was *a function called **cblas_daxpy** in the file; but referring to the C standard (again, I think it was the C standard, my supervisor picked up a big yellow book and referred to it as 'the standard') showed that it should have been named as **cblas_daxp*b*y**.
 
Then we compared the file size of the cblas.h on his computer with that on mine, and they were different. So we copied the cblas.h from his to mine, and after that everything worked.
 
What I think is happening is the file cblas.h that comes with the libblas3-dev package (for ubuntu 9.10) has non-standard function names. I don't know to what extent, or what's causing it.
 
**Note; I downloaded/installed the package again on my home desktop through apt (ubuntu 9.10 again) and I get the same, non-standard-function-named version of the file.**

---

### Post by SevenMachines on 2009-11-11
to be honest, i think daxpy is the standard, certainly according to [netlib]("http://www.netlib.org/blas/"), which i thought was the home of the specification. i dont know what the big yellow book is though :) so i'd be happy to accept i was wrong on that

---

### Post by SevenMachines on 2009-11-11
although daxpby is part of [netlib linalg]("http://www.netlib.org/linalg/qmr/")

---

### Post by hughbert on 2009-11-12
Well I don't really know, I'm not exactly knowledgeable about this kind of thing (hence why I've posted it!)

After looking at the functions, I can understand why daxpby is the one I want for the software I'm using. But it looks like daxpy is in the standard as well, so maybe it's not a naming issue it's that some of the functions aren't included any more?

---

### Post by SevenMachines on 2009-11-12
i'll guarantee you know more about blas than i do! obviously libraries can change over time with things added/deprecated and so on, the Atlas people will know more on the wheres and whys of daxpby

---

### Post by hughbert on 2009-11-12
I've added an error tracker to the Atlas page, hopefully they'll know what to do.

It's likely that the function is missing from the package I installed in ubuntu 9.10 because it is a newer version and the files have change; however (how I understood it from my supervisor) the function we needed is included in the standard, and therefore should be included in the file... unless my supervisor needs a new big yellow book! 

Either way it's been reported and hopefully someone over there can tell us what's going on/why it's changed/what we need to do.

Thanks for your help & guidance!

---

### Post by alexserb on 2009-11-12
Hello!

To the best of my knowledge, the reference implementation of BLAS is the so called netlib BLAS, see [http://www.netlib.org/blas](http://www.netlib.org/blas)

This implementation does not contain any function called daxpby. Thus the C interface to BLAS (i.e. cblas.h also) is not supposed to contain any function called cblas_daxpby, please consider reading the file cinterface.pdf which is linked to from [http://www.netlib.org/blas](http://www.netlib.org/blas)

You may also consider reading the BLAS FAQ at:
[http://www.netlib.org/blas/faq.html#1.2](http://www.netlib.org/blas/faq.html#1.2)
and the references therein (if you can get access to the referenced articles).

I do not know what the yellow book of your supervisor is, but I suppose it is no secret and you can find out and let us know title and author(s). It would be also nice to know what exactly your supervisor uses as BLAS and on which operating system (or linux distribution).

I am also puzzled by the following assertion from your very first message: "Effectively the file has incorrect naming (based on the C language standard)..." If it would be like that a lot of other software works with ATLAS/netlib BLAS in spite of using something broken!? Moreover, it is unclear what you mean by the "C language standard", do you mean the programming language, or the C interface to BLAS.

Please note that the cblas.h provided by ATLAS (at least in version 3.8.3) contains a function called catlas__daxpby, which might be exactly what you need. I think that it is not called cblas_daxpby simply because daxpby does not exist in the reference implementation of BLAS. Changing the source(*) of your software to call catlas__daxpby should not be a big issue and is in my opinion better than replacing cblas.h.

Actually one can easily get the same result as with cblas_daxpby by calling first cblas_dscal to compute b*y and then cblas_daxpy to compute a*x+b*y without much overhead. This way you get around using what seems to be a non-portable function. Changing the source of the software this way may be the best solution.

I have the feeling that the cblas.h header file used by your supervisor is actually not conforming to the reference, i.e. extending it.

Best regards,

Serban

(*) I suppose you have access to the source since you need the header file, which is of no use if the software is already compiled.

---

### Post by hughbert on 2009-11-13
Hi Serban! Thanks for you input.

The assertion of "Effectively the file has incorrect naming (based on the C language standard)..." was what we thought at the time when it happened - which I now know is wrong, so I completely retract it.

I got a response from the ATLAS guys, effectively saying the same as you; that cblas_daxpby does not exist, but that catlas_daxpby does. 

So my current theory is this; I was mistaken about it being cblas_daxpby, and the file was trying to call catlas_daxpby. The error message was only on screen for a couple of seconds, so I'm not very sure. However, since the catlas_ functions are not in the BLAS standard, they have been removed from the cblas.h included in the debian/ubuntu release package. 

Comparing the cblas.h file we copied from my supervisors computer with that on my desktop (unchanged from the package install) this appears to be correct; there are no catlas functions in the ubuntu 9.10 package.

However I'm still confused about what the yellow book was as my lecturer found daxpby in it, which is what prompted the first (incorrect) assumption. I'll talk to my supervisor again and find out what that book actually is! 

Thanks very much for helping me understand what's going on here. If the catlas_ functions aren't being included in the package I guess that's not really an error? I don't know how much this affects other users of the package, or if it's pretty much just me :rolleyes:

Regards
Hugh

---

