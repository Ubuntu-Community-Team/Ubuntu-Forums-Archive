---
title: "eclipse CDT"
date: 2009-11-05
forum: Repositories &amp; Backports
---

### Post by yuriyb on 2009-11-05
Hi everyone! 

I tried to install eclipse CDT, but got following message:

E: Couldn't find package eclipse-cdt

Is it possible to install CDT via apt-get ???

---

### Post by RaptorJesus on 2009-11-05
The eclipse CDT needs to be installed via eclipse's plugin manager. Got to the Add Plugins window, and add the repository:
[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
to the eclipse source list (Galileo Update Site as it is known) and check the CDT main features box.

---

### Post by yuriyb on 2009-11-06
> **RaptorJesus said:**
> The eclipse CDT needs to be installed via eclipse's plugin manager. Got to the Add Plugins window, and add the repository:
[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
to the eclipse source list (Galileo Update Site as it is known) and check the CDT main features box.

Thanks a lot! All works fine.

---

### Post by RaptorJesus on 2009-11-06
No problem, glad I could help.

---

### Post by snakdoc on 2009-11-09
Thanks been trying to figure this out :)

---

### Post by freevryheid on 2009-11-09
Anyone know when the Karmic cdt will be ready? I'd rather wait for this than install via eclipse. Also the subversion and pydev eclipse plugins.

thx

---

### Post by RaptorJesus on 2009-11-12
Unknown. You may find this useful, however: [https://code.launchpad.net/~ubuntu-branches/ubuntu/karmic/eclipse-cdt/karmic](https://code.launchpad.net/~ubuntu-branches/ubuntu/karmic/eclipse-cdt/karmic)

---

### Post by dakira on 2009-11-15
They pulled it shortly before the release because the package they had was incompatible with the eclipse package they shipped. Here's the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/eclipse-cdt/+bug/461995](https://bugs.launchpad.net/ubuntu/+source/eclipse-cdt/+bug/461995)

---

### Post by ktiniatros on 2010-02-20
> **RaptorJesus said:**
> The eclipse CDT needs to be installed via eclipse's plugin manager. Got to the Add Plugins window, and add the repository:
[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
to the eclipse source list (Galileo Update Site as it is known) and check the CDT main features box.

can someone help me where to find this option?? I have ubuntu 9.10 and eclipse 3.5.1

I', totally newb, cant find the Add Plugins window!!

---

### Post by coefws on 2010-02-21
The following link worked for me:
[http://zedstar.org/blog/2009/11/24/adding-back-cdt-support-to-eclipse-karmic-koala/](http://zedstar.org/blog/2009/11/24/adding-back-cdt-support-to-eclipse-karmic-koala/)

However, you should first install eclipse plugin development environment (sudo apt-get install eclipse-pde) in order to avoid problems described in link below:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944)

---

### Post by iampat on 2010-05-27
> **RaptorJesus said:**
> The eclipse CDT needs to be installed via eclipse's plugin manager. Got to the Add Plugins window, and add the repository:
[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
to the eclipse source list (Galileo Update Site as it is known) and check the CDT main features box.


I tried it to install CDT, whoever I could not. here it the message 

> 
Cannot complete the install because one or more required items could not be found.
  
Software being installed: Eclipse C/C++ Remote Launch 6.0.0.201002161416 (org.eclipse.cdt.launch.remote.feature.group 6.0.0.201002161416)

Missing requirement: Eclipse C/C++ Remote Launch 6.0.0.201002161416 (org.eclipse.cdt.launch.remote.feature.group 6.0.0.201002161416) requires 'org.eclipse.rse.ui [3.0.0,4.0.0)' but it could not be found


Thanks for your help :)

---

### Post by nfrik on 2010-05-28
I have same problem. Using Eclipse 3.5.1 JDK and JRE are properly installed. What is wrong, please help!!!!!

---

### Post by dakira on 2010-06-07
I'm not exactly sure, what your problems are. But here is how I did it:

I installed the Eclipse version from the repositories (all packages) and in Eclipse under "Help -> Install new Software" I added these repositories:

[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
[http://download.eclipse.org/modeling/emf/updates/releases/](http://download.eclipse.org/modeling/emf/updates/releases/)

The latter might might not be needed. I'm not sure if it is a requirement of the CDT or of some other plugins I have installed. So try the first repo, and if that doesn't suffice add the second and try again.

Now from the CDT-Repo I added these packages:
Eclipse C/C++ Development Platform
GNU Toolchain Build Support for CDT
GNU Toolchain Debug Support for CDT
and CDT Utilities

That's it. Worked for me. If you get errors. maybe you're missing some Eclipse packages.

---

### Post by hnkulkarni on 2011-07-27
> **RaptorJesus said:**
> The eclipse CDT needs to be installed via eclipse's plugin manager. Got to the Add Plugins window, and add the repository:
[http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
to the eclipse source list (Galileo Update Site as it is known) and check the CDT main features box.

Thanks that worked for me.

---

