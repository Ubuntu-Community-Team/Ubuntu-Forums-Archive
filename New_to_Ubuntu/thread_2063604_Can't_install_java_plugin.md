---
title: "Can't install java plugin"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by kmegamind on 2012-09-27
My google chrome says that my java plugin is out of date so i installed the new version as instructed [here]("http://java.com/en/download/help/linux_install.xml"), but chrome still asks for the update.
my system is 32-bit ubuntu 12.04.
plz help :)

---

### Post by cottfcfan on 2012-09-27
I would use Java from here:
[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)
Works fine in Chrome.

---

### Post by QIII on 2012-09-27
**WARNING: Yet another severe vulnerability has been found in Java (which affects Java 5, 6 and 7; Sun, Oracle and OpenJDK). You should be sure that you have an apparmor profile for the browser plugin (one exists by default in Firefox, I'm told, but be sure apparmor is turned on) and by application for every Java application you run. Because Oracle was so embarrassed by the last big hole that was found, they moved to release a security update outside of their quarterly security update cycle a few weeks ago. It may be they will do the same with this one.**
 
cottcfan is in the right direction, but *how *to get it done may be difficult to discerne from his link. And don't use the Beta for Oracle Java 8 unless you are willing to deal with the headaches. Use Oracle Java 7 Update 7.
 
If I am not mistaken, Chrome will look in the .mozilla directory for the plugin if it needs to.
 
The method of installation you used is a generic Linux installation and far, far too complicated for the Ubuntu user. There is a means tailor made for Ubuntu that will keep Oracle Java 7 updated as Oracle releases updates and keep you from having to reinstall all the time. It uses a PPA and apt, so your normal Ubuntu updates will catch new updates without a thought on your part.
 
webupd8.org has produced a package that will download and install Oracle Java 7 for you. They can't maintain the actual files because Oracle no longer licenses anyone to keep the files in their repositories. webupd8.org simply has a package that will automate the process of downloading and installation as any other package would be installed via apt.
 
Please have a look at the Java wiki link in my signature. Under "Oracle Java 7", "Command line methods", click the link "Using webupd8.org's strikingly simple method."
 
Multiple Java installations can coexist happily on one machine. Unless you are an experienced user, I would suggest just leaving what you have alone and using the webupd8.org installation. It will take care of setting your alternative to the new installation directory if it differs from the one you used. Setting the alternative is discussed in the wiki if you decide to change it later.

---

### Post by kmegamind on 2012-09-27
Thnx cottfcfan and thnx QIII for this nice illustration, The  webupd8.org method worked perfectly :D

---

### Post by Rebelli0us on 2012-10-17
Thank you, [webupd8team]("https://launchpad.net/~webupd8team/+archive/java") works. 

I was googling for an hour trying to install java plugin in firefox!

---

