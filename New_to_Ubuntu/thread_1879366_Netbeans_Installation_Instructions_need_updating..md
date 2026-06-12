---
title: "Netbeans Installation Instructions need updating."
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Randy Schilling on 2011-11-11
The communities instructions for installing Netbeans,
[https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans),
are out-dated.  I would suggest something like the following.

What works to install Netbeans to Ubuntu is the following three step process.
   1. Make sure your Java is up-to date at [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp).
    2. Install JDK from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
   3. Install Netbeans from [http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)
I found the instructions provided by Oracle and its community to be up-to-date, detailed and top-to-bottom.
Use them with the following clarifications. 
The instructions for Java suggest that removal of existing Java is necessary; that seems to be true for Windows but not Linux.
The Netbeans instructions include the url to the JDK installation.  
You'll have to create directories for Java and JDK.  
I created /user/local/java and /usr/local/jdk7.
The Netbeans installer at first did not find my jdk;  I manually entered /usr/local/jdk7/jdk1.7.0_01.
When my installation completed, I went to Dash (under my beautiful new Ubuntu 11.10) searched Netbeans, 
found it, clicked it and it exploded onto my desktop.
I tested my installation by running the welcome sample under C++/C.
I mclicked (menu click) its icon in the launcher and clicked Keep in launcher.  
I moved its icon to the top of my launcher's panel.
My original plan was to combine steps 2 and 3 and install the JDK + Netbeans bundle.  
That failed under Ubuntu (as described in an earlier post) but it works under Windows.
This should relieve any would-be developer of some tense guessing.

Regards  - Randy

---

### Post by Randy Schilling on 2011-11-11
I don't know why my post landed here.
I thought I was working Forum Feedback and Help.

---

### Post by Perfect Storm on 2011-11-11
It was moved here. I don't know why you would post a thread like that in Feedback forum. Forum Feedback and Help is regarding the forum itself.

---

### Post by Randy Schilling on 2011-11-11
Hello AI,

I'd like to improve the page [https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)
My post explains what works.

Perhaps you would be kind enough to  explain how one goes about
making contributions to community help pages.


Many thanks and regards - Randy

---

### Post by Perfect Storm on 2011-11-12
[https://help.ubuntu.com/community/WikiGuide/Registration](https://help.ubuntu.com/community/WikiGuide/Registration)

---

