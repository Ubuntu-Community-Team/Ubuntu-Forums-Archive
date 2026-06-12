---
title: "Error in ns-bgp integration with ns2.34"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by mageshbabuj on 2013-03-06
I try to integrate ns-bgp_2.0 with ns-2.34. But it showing following question. I dont know what to do. Pls help me anybody.


mageshbabu@mageshbabu:~/magesh/ns-allinone-2.34$ patch -p0 < ns-bgp_2.0_patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|
|diff -rc ns-2.27.orig/common/node.cc ns-2.27/common/node.cc
|*** ns-2.27.orig/common/node.cc    2004-01-12 16:57:44.000000000 -0800
|--- ns-2.27/common/node.cc    2004-06-22 12:47:03.000000000 -0700
--------------------------
File to patch:

---

### Post by Mark_in_Hollywood on 2013-03-06
Have you read this?

[http://www2.ensc.sfu.ca/~ljilja/cnl/projects/BGP-ns-2.34/rs_ensc_891_directed_studies_presentation_final.pdf](http://www2.ensc.sfu.ca/~ljilja/cnl/projects/BGP-ns-2.34/rs_ensc_891_directed_studies_presentation_final.pdf)

if this solves your problem, please mark this post as "Solved" by changing the post's prefix from Ubuntu to Solved.

---

