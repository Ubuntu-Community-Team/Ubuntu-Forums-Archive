---
title: "Installing Eclipse Visual Editor on Ubuntu"
date: 2009-08-24
forum: Programming Talk
---

### Post by Drood on 2009-08-24
Hi, I just installed eclipse 3.5 (downloaded from eclipse.org) but I do not know how to install the Visual Editor, for the class I am taking I need it, otherwise I would be open to other options for Java GUI.

I tried following the instructions here:
[http://wiki.eclipse.org/VE/Update#Install_VE_1.4_into_Eclipse_3.5_.2F_Galileo](http://wiki.eclipse.org/VE/Update#Install_VE_1.4_into_Eclipse_3.5_.2F_Galileo)

But when I am on the last step ( click next) I get a conflict error and cant finalize the installation.

```
Cannot complete the install because of a conflicting dependency.
  Software being installed: Java EMF Model 1.4.0.HEAD-7H-FPaAcggQleH8hJifHfUd (org.eclipse.jem.feature.group 1.4.0.HEAD-7H-FPaAcggQleH8hJifHfUd)
  Software currently installed: Eclipse IDE for Java Developers 1.2.0.20090619-0620 (epp.package.java 1.2.0.20090619-0620)
  Only one of the following can be installed at once: 
    Java EMF Model Utilities 2.0.200.v200905140200 (org.eclipse.jem.util 2.0.200.v200905140200)
    Java EMF Model Utilities 2.0.200.R3_1_maintenance (org.eclipse.jem.util 2.0.200.R3_1_maintenance)
  Cannot satisfy dependency:
    From: Eclipse IDE for Java Developers 1.2.0.20090619-0620 (epp.package.java 1.2.0.20090619-0620)
    To: org.eclipse.epp.package.java.feature.feature.group [1.2.0.20090619-0620]
  Cannot satisfy dependency:
    From: EPP Java Package 1.2.0.20090619-0620 (org.eclipse.epp.package.java.feature.feature.group 1.2.0.20090619-0620)
    To: org.eclipse.wst.xml_ui.feature.feature.group 0.0.0
  Cannot satisfy dependency:
    From: Java EMF Model 1.4.0.HEAD-7H-FPaAcggQleH8hJifHfUd (org.eclipse.jem.feature.group 1.4.0.HEAD-7H-FPaAcggQleH8hJifHfUd)
    To: org.eclipse.jem.util [2.0.200.R3_1_maintenance]
  Cannot satisfy dependency:
    From: WST Common Core 3.1.0.v200903021835-7B77FXTF7RZHITIwQkLs_V (org.eclipse.wst.common_core.feature.feature.group 3.1.0.v200903021835-7B77FXTF7RZHITIwQkLs_V)
    To: org.eclipse.jem.util [2.0.200.v200905140200]
  Cannot satisfy dependency:
    From: WST Common UI 3.1.0.v200903021835-7B5FREDhdMNPm7dkmBmpUJxRlMta (org.eclipse.wst.common_ui.feature.feature.group 3.1.0.v200903021835-7B5FREDhdMNPm7dkmBmpUJxRlMta)
    To: org.eclipse.wst.common_core.feature.feature.group [3.1.0.v200903021835-7B77FXTF7RZHITIwQkLs_V]
  Cannot satisfy dependency:
    From: Eclipse XML Editors and Tools 3.1.0.v200905240756-7H6FMVDxtkM-5OgPGKK4xQocS5AL (org.eclipse.wst.xml_ui.feature.feature.group 3.1.0.v200905240756-7H6FMVDxtkM-5OgPGKK4xQocS5AL)
    To: org.eclipse.wst.common_ui.feature.feature.group [3.1.0.v200903021835-7B5FREDhdMNPm7dkmBmpUJxRlMta]:confused:
```

---

### Post by Drood on 2009-08-24
I have to stop doing this (prematurely asking questions). The error message basically says the dependencies are installed and so all I had to do was uncheck everything except the actual Visual Editor.

---

### Post by animefan82 on 2009-11-05
Nevertheless, it's a good thing you did, because I've been having trouble with just that. I think I actually tried only installing the actual VE once before, but when I tried that now, it worked flawlessly. So thanks. Keep asking questions prematurely :p

---

### Post by Drood on 2009-11-06
Nice, I'm glad this helped someone.

---

### Post by size_XXM on 2009-12-07
Is there a way to add VE to the ubuntu repository-installed version? Looking into Eclipse's Help>Install New Software there's no eclipse repostory, there's no VE plugin for eclipse in ubuntu's repo and I haven't tried anything else yet. Any ideas?

---

### Post by size_XXM on 2009-12-08
Whoops, now **I'm** acting prematurely here. Acccording to [this bug report](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944), installing plugins using the Help>Install New Software **should work** and might only require some additional eclipse-* packages.

That said, I did run into problems trying to install VE, as there were absolutely no pre-loaded eclipse update sites and few obvious were suggested.
I'm not even sure how I managed to trick the program into installing the dependencies, but one site was necessary to provide the EMF, then another one needed to be added for GMF. As soon as it could find its dependencies, it worked fine.

---

