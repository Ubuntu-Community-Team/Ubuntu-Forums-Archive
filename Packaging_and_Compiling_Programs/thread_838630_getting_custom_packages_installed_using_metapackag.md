---
title: "getting custom packages installed using metapackages"
date: 2008-06-23
forum: Packaging and Compiling Programs
---

### Post by udit99 on 2008-06-23
So we're trying our hands at making a custom Ubuntu distro from scratch and figured that one way of getting the package installed as part of the installation is to add it as part of the local mirror we created and then make the package a part of the xubuntu-desktop metapackage. We use the CDIMage scripts to ultimately make the ISO and we can get an ISO out of it fine. 


But the installation bombs with the error :


**xubuntu-desktop depends on neo-usplash; however: Package neo-usplash is not configured yet. dpkg: error processing xubuntu-desktop (--configure): dependency problems - leaving unconfigured Errors were encountered while processing: neo-usplash   xubuntu-desktop   **    

(neo-usplash is our custom package that we make ourselves and add to the metapackage)


Any ideas on what this configuration could be ?

Now im curious to know

---

### Post by inportb on 2008-07-27
Have you set it as a pre-dependency? These need to be installed and configured beforehand. You should instead make it a dependency.

---

