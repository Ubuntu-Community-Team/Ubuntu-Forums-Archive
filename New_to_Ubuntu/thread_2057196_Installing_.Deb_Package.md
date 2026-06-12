---
title: "Installing .Deb Package"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Mitch12 on 2012-09-13
I am a newbie to ubuntu and have problems installing a package which I have downloaded. The package is called Google-Secure-Data-Connector. When I click on the downloaded package it starts to install through ubuntu software centre, reaches 100% then stops with this error;

Reading database ... 179262 files and directories currently installed.) 
Preparing to replace google-secure-data-connector 1.2-0 (using .../google-secure-data-connector_1.2.2-0_all.deb) ... 
Unpacking replacement google-secure-data-connector ... 
google-secure-data-connector --- package name 
Setting up google-secure-data-connector (1.2-0) ... 
Checking for Java... 
dpkg: error processing google-secure-data-connector (--install): 
 subprocess installed post-installation script returned error exit status 1 
Processing triggers for ureadahead ... 
Errors were encountered while processing: 
 google-secure-data-connector

Not sure what this means?

---

### Post by shreepads on 2012-09-13
Stupid question, do you have Java installed?

---

### Post by mips on 2012-09-13
Requirements are:
Java JDK 1.6 or later
Ant 1.7 (Ant includes jUnit 4.4)

So install JDK & Ant first and then try again, these packages are in the repos.

---

### Post by NikTh on 2012-09-13
Hi , 
nobody is absolutely sure what this error means. It can means a lot. 
>   subprocess installed post-installation script returned error exit status 1but based on the output > Checking for Java...  maybe java required to install this package. I mean java from Oracle. I am not sure though.
Can you give the link to the .deb package ? 

Another way to install a .deb package is to download it and install it via dpkg (package manager) from terminal. 

When you click download (DO NOT choose to Open With) click on SAVE file. File will be saved in Downloads. 
Then open a terminal (Ctrl+Alt+t combo keys) and give this commands 
```
cd Downloads 
sudo dpkg -i blahblahblah.deb
``` where blahblahblah.deb is the name of the .deb package .

**TIP:** you can write the first 2-3 letters and then let the "Tab" key to fill the rest of them. 

Thanks

---

### Post by newb85 on 2012-09-13
In the future, when you're asking about software you've downloaded in your browser, you should give a link to where you downloaded it.  People are a lot less likely to help if they have to hunt to figure out where you got it... (I assume you got it at [http://code.google.com/p/google-secure-data-connector/downloads/list]("http://code.google.com/p/google-secure-data-connector/downloads/list").)

The error messages sound like it's a problem with the *.deb.

Is there a reason you're installing the Pre-Release instead of the Release Candidate?

---

