---
title: "native eclipse ?"
date: 2005-10-26
forum: Programming Talk
---

### Post by JOKe on 2005-10-26
i know that Fedora team has build Eclipse with GCJ .
will be nice to have it on ubuntu too.

---

### Post by tageiru on 2005-10-26
It is already in breezy universe.

apt-get install eclipse-sdk

---

### Post by JOKe on 2005-10-27
but is this native version of eclipse ? 
i mean it runs and compile apps without sun j2sdk or blackdown j2sdk ? and it use gcj ?

---

### Post by LorenzoD on 2005-10-28
It is.

---

### Post by JOKe on 2005-10-28
lol this rox :) ubuntu ROX :)

---

### Post by gururise on 2005-12-24
How do you execute the native version of eclipse?  After installing eclipse-sdk, eclipse still wants a vm to use.

---

### Post by asimon on 2005-12-26
I think you need to install the corrosponding -gcj packages, which contain the java compiled to native code.

```
$ apt-cache search eclipse|grep gcj
ecj-bootstrap-gcj - bootstrap version of the Eclipse Java compiler (native version)
eclipse-ecj-gcj - Native version of the Eclipse Java compiler
eclipse-jdt-gcj - Java Development Tools plug-ins for Eclipse (GCJ version)
eclipse-pde-gcj - Plug-in Development Environment to develop Eclipse plug-ins (GCJ version)
eclipse-platform-gcj - Eclipse platform without plug-ins to develop any language (GCJ version)
eclipse-rcp-gcj - Eclipse rich client platform (GCJ version)
libgcj6-src - libgcj java sources for use in eclipse
libgcj7-src - libgcj java sources for use in eclipse

```

---

### Post by cabezon on 2006-08-10
I got all the packages as well, but when i execute eclipse it still looks for the VM and doesnt work with gcj vm. 

I want to use the gcj version, but have been unable to, in amd64 ubuntu breezy.

It should work as the only thing i did is : 
```
aptitude install eclipse-rcp-gcj
```

ii  eclipse-base                                    3.1.1-1ubuntu3                       Eclipse distribution base
ii  eclipse-jdt                                     3.1.1-1ubuntu3                       Java Development Tools plug-ins for Eclipse
ii  eclipse-jdt-common                              3.1.1-1ubuntu3                       Java Development Tools plug-ins for Eclipse
ii  eclipse-jdt-gcj                                 3.1.1-1ubuntu3                       Java Development Tools plug-ins for Eclipse
ii  eclipse-pde                                     3.1.1-1ubuntu3                       Plug-in Development Environment to develop E
ii  eclipse-pde-common                              3.1.1-1ubuntu3                       Plug-in Development Environment to develop E
ii  eclipse-pde-gcj                                 3.1.1-1ubuntu3                       Plug-in Development Environment to develop E
ii  eclipse-platform                                3.1.1-1ubuntu3                       Eclipse platform without plug-ins to develop
ii  eclipse-platform-common                         3.1.1-1ubuntu3                       Eclipse platform without plug-ins to develop
ii  eclipse-platform-gcj                            3.1.1-1ubuntu3                       Eclipse platform without plug-ins to develop
ii  eclipse-rcp                                     3.1.1-1ubuntu3                       Eclipse rich client platform
ii  eclipse-rcp-common                              3.1.1-1ubuntu3                       Eclipse rich client platform (common files)
ii  eclipse-rcp-gcj                                 3.1.1-1ubuntu3                       Eclipse rich client platform (GCJ version)
ii  eclipse-sdk                                     3.1.1-1ubuntu3                       Extensible Tool Platform and Java IDE
ii  eclipse-source

---

