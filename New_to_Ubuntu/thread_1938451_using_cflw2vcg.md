---
title: "using cflw2vcg"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by newport_j on 2012-03-09
I do not know if this is a good place to ask this, but I will try. 
 
 
I am trying to use cflow and then cflow2vcg and finally xvcg. 
 
The first step is easy
 
The second step using cflow2vcg is not working.
 
I take the output from cflow and put it as the input to 
 
cflow2vcg.
 
But the program hangs with the partial output
 
graph: {
title: "TITLE"
color: lightray
classname 1: "Interne" classname 2: "Externe"
 
 
and the cursor hangs on the next line. Now if I put in
 
cflow2vcg --help
 
I get the help output-no problem. But if I type 
 
 
cflow2vcg out 
 
I get the output I showed above. It is also the same out if I just type 
 
cflow2vcg
 
It is as if the input file was never included in the command line. What am I doing wrong.
 
cflow and xvcg work fine. This connecting software 
 
cflow2vcg 
 
does not work at all.
 
Any help appreciated. Thanx in advance.
 
 
newport_j
 
 
 
where out is the out from cflow. I get what I typed about.

---

