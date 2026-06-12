---
title: "Java explained"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by i,bigfoot on 2008-05-17
Hi All,

I am a "reasonably" experienced java developer yet all my experience has been in a totally windoze environment.  I am new to ubuntu and am trying to get a couple of things going yet finding it all rather confusing.

It seems that java libraries etc are spread throughout the entire distro rather than the drop a jdk on your filesystem and use it windows approach. 

So I was hoping someone could point me to some reading on how java lives in ubuntu? How would I install / use multiple jdk's (some projects are 1.4, some 1.5, even still maintain a 1.3 project). 

Also, does anyone know where I could get some install instructions for Eclipse 3.3 on Ubuntu 8.04? I am not entirely sure why hardy ships with 3.2, but I much prefer 3.3 and would like to understand how to get this to work.  

Cheers,

---

### Post by Sef on 2008-05-17
> Also, does anyone know where I could get some install instructions for Eclipse 3.3 on Ubuntu 8.04? I am not entirely sure why hardy ships with 3.2, but I much prefer 3.3 and would like to understand how to get this to work.


[Eclipse]("http://www.eclipse.org/") website.

---

### Post by Inxsible on 2008-05-17
you can install different jdk by simply choosing the right packages. You will have to search the Synaptic to get the appropriate version that you want to install. 

Installing Eclipse is pretty easy. You can simply download the appropriate version (depending on the architecture of your OS 32 bit or 64 bit) and then simply exploding the downloaded file where ever you like. I have it under /mnt/Shared/Eclipse. You may want to create a shortcut in the main menu for Eclipse.

---

### Post by txcrackers on 2008-05-18
Since I've been using Java/Linux since 1.3, I think I can help a bit...

Firstly, the Java versions available from the repositories only cover Java 5 and 6. If you're absolutely sure you need 1.3 and 1.4, then I would suggest downloading **all** your JDK's from the Sun site. Get the "tarball" versions. Create a directory where these should live (*/usr/local/java* is typical) and and un-archive each of them there. Then I'd suggest doing some research on the "alternatives" system (the command in Hardy is "update-alternatves") - this will allow you quickly switch JVM's on the fly and not have to do other strange things with the PATH, etc.

If you're using the repository versions, they get installed in */usr/lib/jvm*. Stick with the Sun JVMs - I never liked GCJ and OpenJDK is definitely "beta." Use the command "update-java-alternatives" to select which JDK to use (see above).

Note that these hints require you to be "root" (use the "sudo" command).

---

