---
title: "Problem Trying To Download Matlab"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by buenomalo on 2012-12-26
Hello,

I tried installing matlab recently, and I believe the installation was somehow interrupted. Subsequently, Matlab is stuck under the "In Progress" tab of Ubuntu Software Center, and has the caption "Applying Changes." The download has been hanging without progress in this section for more than an hour; I am also unable to download any other application. Whenever I try to download another app., it simply does not show up under the "In Progress" tab. I cannot seem to cancel the Matlab download, either. I've tried uninstalling and reinstalling Ubuntu Software Center, but to no avail. 

Any advice is appreciated! Thanks.

---

### Post by Frogs Hair on 2012-12-26
Hello and Welcome 

Close the software center and try the following command. ```
sudo dpkg --configure -a
``` This can help locate and install dependencies and finish configuring the installation.

---

