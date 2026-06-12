---
title: "Matlab7 R14 with Dapper"
date: 2006-11-30
forum: Programming Talk
---

### Post by Seinfeld on 2006-11-30
Hello

Does someone have Matlab7 R14 installed on Dapper??

I have 3 problems so I really appreciate your help

1. There is a problem in the Symbol Math tool. I cannot compile or run any file. The error message is :

Unable to load mex file: /home/mydir/matlab7_R14/toolbox/symbolic/maplemex.mexglx.

2. I cannot associate the .m files so as to open with Matlab when I click them..
Should I open them from Matlab ??. I doubt it, it should be fine as I did make the nautilus setting for these files (<file_name>.m) to open with matlab not with the text editor.. They never do..

3. The browser cannot be set from Matlab.. I did edit the "docopt" file line 51 and put mozilla as directed (Type help docopt on matlab prompt to see what I mean)  


Any help please ??

Thanks a lot

---

### Post by jeffers@bu.edu on 2007-03-02
Regarding the Symbolic Math problem, I've run into the same one but found a NEAR-solution for the Unable to load mex file problem:

[http://www.mathworks.com/support/solutions/data/1-1BDU5.html](http://www.mathworks.com/support/solutions/data/1-1BDU5.html)


HOWEVER, when I follow Mathworks' advice and put in the export command,

export LD_ASSUME_KERNEL=2.2.5,

Matlab or anything else won't execute at ALL. I get 

/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Does this work for you? Can anybody offer a tip on this?

---

