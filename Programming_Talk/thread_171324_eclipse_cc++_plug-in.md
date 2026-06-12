---
title: "eclipse c/c++ plug-in"
date: 2006-05-06
forum: Programming Talk
---

### Post by chiarapat83 on 2006-05-06
Hi :KS 
I tried to install eclipse c/c++ plug-in.
First I installed eclipse 3.1.1 with apt command and after I download org.eclipse.cdt-3.0.2-linux.x86.
I copied c/c++ plug-in in the right directory (eclipse in /usr/share/eclipse and tar.gz c/c++ plugin in /usr/share)and uncopress with tar -zxvf... The output said that all the files where copied correctly in eclipse/features and eclipse/plug-ins directories...
But when I open eclipse Help -> About Eclipse -> Plug-in Details there isn't the new plug-in. I also tried Window -> Preference -> Plug-in Development -> Target Platform -> Reload and nothing happens :confused: 

Someone can help me please? :KS

---

### Post by unbuntu on 2006-05-06
never installed CDT the hard way you just described.  What I did was following the guide from the CDT website and let CDT install itself automatically.  

This might be what you are looking for:
> 
CDT 3.0.0, 3.0.1 (for use only with Eclipse Platform 3.1.X)

Use the following URL in a Site Bookmark in the update manager:

[http://download.eclipse.org/tools/cdt/releases/eclipse3.1](http://download.eclipse.org/tools/cdt/releases/eclipse3.1)

To install CDT from the update site, in the Help menu select Software Updates and then Find and Install, Select Search for new features to install and click Next. Click New Remote Site to add an update with the URL provided above, and then expand the site node to reveal the available downloads. 


---

