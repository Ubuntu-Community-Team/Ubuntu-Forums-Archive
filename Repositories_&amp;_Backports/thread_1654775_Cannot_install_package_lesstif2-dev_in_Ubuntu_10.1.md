---
title: "Cannot install package lesstif2-dev in Ubuntu 10.10 (Not connected to internet)"
date: 2010-12-28
forum: Repositories &amp; Backports
---

### Post by newubu123 on 2010-12-28
The following error occurred on a computer running Ubuntu Maverick (10.10), which I had installed using the Live CD. Please note that this problem occurred on a computer that is NOT connected to the Internet. In the following I will refer to it as the "Ubuntu" computer. Using a different computer, I had downloaded the file "lesstif2-dev_0.95.2-1_i386.deb" and its dependencies from https://launchpad.net/ubuntu/maverick/i386/lesstif2-dev/1:0.95.2-1, which I will call the "main" URL. (Actually, the file lesstif2-dev_0.95.2-1_i386.deb appears to be from the lucid version, not maverick. Is this really the intended link?) For the dependencies, I downloaded maverick files when available, and lucid files when maverick files were not available. (In an earlier attempt I had downloaded only the lucid versions, which are linked from the main URL, but that caused dependency errors.) Then I moved all these *.deb files to the Ubuntu computer (which is NOT connected to the internet). After getting all the dependencies to install, I doubleclicked on
	lesstif2-dev_0.95.2-1_i386.deb		
then clicked "install" in Ubuntu Software Center. Eventually a popup window appeared with the message: "An unhandlable error occured" and "There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at http://launchpad.net/aptdaemon/+filebug and retry." I retried installing lesstif2-dev several times in this way but the same thing happened. I restarted the computer and tried again but the problem still occurred.

To report the error, I directed the internet browser to http://launchpad.net/aptdaemon/+filebug, but it redirected to https://login.launchpad.net/NnRlxssnHZZLSZW2/+decide, which only said "Invalid OpenID transaction". Therefore I am reporting it here. 

I would appreciate any advice you may have on how to get lesstif2-dev to install. I look forward to using lesstif2-dev in Ubuntu. Thank you.

---

### Post by newubu123 on 2010-12-29
PROBLEM SOLVED

I solved the problem in the following way:

1. I ran "dpkg -i --simulate lesstif2-dev_0.95.2-1_i386.deb" and learned that installation of lesstif2-dev would try to overwrite '/usr/lib/libMrm.so', which is also in package openmotif 2.3.3-1.

2. I used Ubuntu Software Center to remove "openmotif-demos" and "openmotif".

3. I doubleclicked on the downloaded file "lesstif2-dev_0.95.2-1_i386.deb" then clicked "Install" in Ubuntu Software Center. This time Ubuntu Software Center ran without crashing, and eventually it said "lesstif2-dev" was installed.

Therefore, it now appears my earlier problem has been solved. However, I still need to run a test case that compiles and links with the include files and libraries from "lesstif2-dev". 

Hopefully I did the removal and installation of software in the "Ubuntu" way. As a suggestion, perhaps a future version of Ubuntu Software Center could identify the cause of such a problem automatically and recommend a solution.

---

