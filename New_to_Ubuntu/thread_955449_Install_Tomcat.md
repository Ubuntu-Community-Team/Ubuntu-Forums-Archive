---
title: "Install Tomcat"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by DFHIII on 2008-10-22
I am using Synaptic Package Manager to install Tomcat.  I get the following message:

E:tomcat5.5: subprocess post-installation script returned error exit status 1

When I checked the details it said:

... please set JAVA_HOME...

How do I set JAVA_HOME?  I am Administrator, but can't assign a system variable.  I have created a Root account with password, but don't know how to login as root.

I am new to Linux, but not to programming.  I would appreciate any help to get by this problem.

Thanks,

Dan H.

---

### Post by greg@localhost on 2008-10-22
Have a look at this:

[http://ubuntuforums.org/showthread.php?t=44006](http://ubuntuforums.org/showthread.php?t=44006)

It's probably installing OK, but the post install config script is falling over.

---

### Post by rolnics on 2008-10-22
Take a look at [this Tomcat thread]("http://ubuntuforums.org/showthread.php?t=901990&highlight=set+JAVA_HOME") and there is also a [Tomcat HOWTO here]("http://ubuntuforums.org/showthread.php?t=44006&highlight=set+JAVA_HOME")

As for how to how to log into root you can use the command sudo, it will then ask for a password, which is the password of your user account. Ubuntu doesn't have a root account setup as standard.

---

