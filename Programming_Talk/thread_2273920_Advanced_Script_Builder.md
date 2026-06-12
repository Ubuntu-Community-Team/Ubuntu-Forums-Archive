---
title: "Advanced Script Builder"
date: 2015-04-16
forum: Programming Talk
---

### Post by jecker on 2015-04-16
I am new to building scripts. I am hoping, instead of me learning from scratch how to build a script to do everything I need that there is an application that would build one for me. I am looking for a script builder that has options like check system/application requirements, install missing application requirements, change conf files, and copy files to specified directories. 

Does anyone know of an application that fits this build?

---

### Post by ian-weisser on 2015-04-16
Everything you have described seems fairly trivial to do in shell, perl, python, etc, without a helper application.

What kind of system/application requirements?

---

### Post by jecker on 2015-04-17
Yep I am sure it is fairly trivial. 

I would like a script to prompt the user for information, use that information and information obtained from the OS to configure the server. For example is Apache, PHP, MySQL or MariaDB installed and configured correctly? If those programs are not installed, install said programs and dependent programs.  Determine what version of Apache is installed, so a virtual host can be configured. Executing a script to create a database and setting permissions. Verifying MySQL or MariaDB was setup with the built in secure DB script. Prompting the user for the DB Server's root password, the hosted server's FQDN, etc...

---

