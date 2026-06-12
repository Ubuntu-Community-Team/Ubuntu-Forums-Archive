---
title: "eclipse install and config on 6.06"
date: 2006-08-03
forum: Programming Talk
---

### Post by AllBuntu on 2006-08-03
Hey dear friends,

What is the best way to run eclipse on Ubuntu 6.06
a) using Ubuntu packages - gives you 3.1.2 and NOT all plugins
a1) and then add plugins using Help>Software Configuration

  or

b) download eclipse and install that to /usr/local/eclipse
b1) then just add whatever you want using eclipse.org

Considerations
* Ubuntu 6.06 seems to only offer 3.1.2
* Eclipse released 3.2 on 6/30 (a month ago)
* Some plugins are not available from the four Ubuntu repositories
* On one of my Ubuntu-package-installs eclipse, plugins installed broken. That makes you feel a little powerless (I got a slew of physical and virtual machines)
* Are there risks with using Ubuntu eclipse and then add-on stuff using eclipse, maybe even update eclipse itself?

Greatful for any insides,

Buntu-san

---

### Post by DeadEyes on 2006-08-04
Eclipse is pretty self contained, extract the tar and everything is there in one folder. So I would go with option B.

---

### Post by vdemeester on 2006-08-04
the b) solution is the best.

I use Eclipse 3.2 in /opt/eclipse/. You must have the sun-jdk installed if you don't want to have any bugs. You can see the [Callisto Project]("http://www.eclipse.org/callisto/").

> Callisto is about improving the productivity of the developers working on top of Eclipse frameworks by providing a more transparent and predictable development cycle. By releasing 10 projects at the same time, the goal is to eliminate uncertainty about version compatibility and make it easier to incorporate multiple projects into your environment.

---

### Post by Roland Bouman on 2006-08-09
Hi! 

I installed eclipse 3.2. too in /opt/eclipse. Alas, it eats up my processor (which should not be the case - my machine is powerful enough) and eventually it crashes with an out of memory error. 

I also installed the java 1.5 environment from sun. However, I can't find a way to have eclipse use that environment (jvm etc.) 

What must i do to have eclipse use the sun jvm?

Thanks in advance, 

Roland


[QUOTE=vdemeester;1336915]the b) solution is the best.

I use Eclipse 3.2 in /opt/eclipse/. You must have the sun-jdk installed if you don't want to have any bugs. You can see the

---

### Post by hod139 on 2006-08-10
> **Roland Bouman said:**
> 
I also installed the java 1.5 environment from sun. However, I can't find a way to have eclipse use that environment (jvm etc.) 

I wrote up a [howto]("http://ubuntuforums.org/showthread.php?t=201378") for setting up Sun's java and the repository version of eclipse.  You should be able to follow that howto, ignoring the steps for installing eclipse and looking at only the java instructions.  My guess is that you need to run the command
```

sudo update-java-alternatives -s java-1.5.0-sun 
```

---

### Post by javarunner on 2006-08-10
Eclipse 3.2 - latest release - is available for Ubuntu.  I just installed it and it seems to work just fine.  :D

---

### Post by [h2o] on 2006-08-11
I would do B as well. Some plugins (like pyDev) requires the latest Eclipse, which means having the one from the repositories is difficult.

---

### Post by groberts1980 on 2006-08-12
I am trying to install Eclipse using Synaptic, but I get this error when its downloading:

E: emacs21: subprocess post-installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfigured
E: eieio: dependency problems - leaving unconfigured
E: speedbar: dependency problems - leaving unconfigured

Any help or ideas? 

Also, I downloaded jdk-1_5_0_08-linux-i586.bin and decompressed it in the terminal, but it just created a folder on the desktop and unpacked it there. I'm not sure if its installed or not. When you download a bin or rpm.bin file, what is the correct way and place to install it?

Update: I tried installig jdk1.5 using Synaptec and got the same error message as the one above, when I tried installing Eclipse.

How can I get jdk1.5 and Eclipse installed?

Updated update: After all the errors whilst installing, jdk and Eclipse is up and running after all.

---

### Post by groberts1980 on 2006-08-13
I've tried installing a few other programs through Synaptec, but still get this error:

E: emacs21: subprocess post-installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfiguredlear
E: eieio: dependency problems - leaving unconfigured
E: speedbar: dependency problems - leaving unconfigured


Any idea how to clear this up?

---

### Post by Roland Bouman on 2006-08-16
Hi, 

and sorry for not posting back sooner - I just couldt get it to work any sooner (lack of time)

> **hod139 said:**
> I wrote up a [howto]("http://ubuntuforums.org/showthread.php?t=201378") for setting up Sun's java and the repository version of eclipse.  You should be able to follow that howto, ignoring the steps for installing eclipse and looking at only the java instructions.  My guess is that you need to run the command


Thanks! I first installed java 1.5 manually, but it did not seem to work. The, I used to automatix install, and that worked fine. 

> 
```

sudo update-java-alternatives -s java-1.5.0-sun 
```


Thanks! this works great!

After having done this, my manually installed eclipse 3.2 runs perfectly smooth. I Really appreciate it


Bye,
Roland

---

