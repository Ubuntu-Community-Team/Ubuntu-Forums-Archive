---
title: "Isuses during eclipse migration from 3.8 to 4.4.2 Luna"
date: 2015-06-11
forum: Packaging and Compiling Programs
---

### Post by vaibhav5 on 2015-06-11
I have migrated our product from 3.8 to 4.4.2 but when trying to launch the RCP application it is throwing null pointer exception at code 


PlatformUI.getWorkbench().getActiveWorkbenchWindow().getActivePage().showView(LIBRARY_VIEW_ID);


PlatformUI.getWorkbench().getActiveWorkbenchWindow() giving me null pointer . This code works fine in 3,8 and from years we are using this code . 


Attached full log file of error name errorRcp.txt


Java version we are using 1.7.0.45 . 


Also sometime it gives random exception also attaching that file with name error.txt

---

