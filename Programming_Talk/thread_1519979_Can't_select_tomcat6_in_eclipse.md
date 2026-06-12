---
title: "Can't select tomcat6 in eclipse"
date: 2010-06-28
forum: Programming Talk
---

### Post by rmills1 on 2010-06-28
I've been searching all over for an answer to this and seem to have come across a lot of other people having the same issue but how they resolved it has not worked for me.

I installed tomcat6 and eclipse through apt-get.  I'm running ubuntu 10.04.  I'm able to open eclipse but when I try to run my web project I get the window in the attached screenshot.  It won't let me enter a server name or continue to the next step.  Not sure why.

---

### Post by sizha on 2011-12-11
Hi there rmils1. 
I'm new to ubuntu. I installed tomcat6 as you have & a year after you, l have the same problem on 11.10. I'm hoping you got an answer as to why you couldn't select tomcat6 in eclipse. Could share with me? 
Thanks heaps

---

### Post by r-senior on 2011-12-12
If you are trying to control Tomcat from Eclipse (or Netbeans), don't use apt-get to install Tomcat. It is configured for production server use and the IDEs don't understand the layout on the filesystem. In addition there are all sorts of permission problems to work around.

For development use, download the archive for Tomcat and unpack it somewhere under your home directory. You'll be able to configure it in the IDE and have the IDE control it.

---

