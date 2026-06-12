---
title: "OpenCL in maverick doesn't see my GPU"
date: 2010-12-06
forum: Programming Talk
---

### Post by Elcid247 on 2010-12-06
hi guys, i've been writing programs in OpenCL for a while now and everything worked just fine with the last 2 ubuntu versions.

but ever since i installed maverick, OpenCL doesn't read my GPU, i can run code only on my CPU.

I have ati mobility radeon 4650 and using catalyst 10.11 driver from ati's website.

For OpenCL i'm using the packages from [here]("http://devforums.amd.com/forum/messageview.cfm?catid=390&threadid=125792&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear") (i've been using it in previous ubuntu versions too).

i also have the ati sdk v2.1 tarball (downloaded from ati's website and it worked on earlier versions). The samples are built but give this error when they run "clCreateContextFromType failed. Error code : CL_DEVICE_NOT_FOUND". and the CLInfo sample shows only CPU.

lspci and lshw both show my ATI Card just fine. and Compiz is working smooth with no problems

ideas?

---

### Post by Elcid247 on 2010-12-06
Updating my kernel headers fixed the problem

---

