---
title: "How to delete all Java from my system."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-10-03
Due to complications, I need to do this... is there a certain command I could use to do this.

I have Version 6 AND Version 5 JREs installed.

---

### Post by kansasnoob on 2008-10-03
Go to synaptic and search java. Remove everything you see.

Don't know why you'd want to though.

---

### Post by Warpster Buntu on 2008-10-03
How can I check to make sure I eradicated it all?

---

### Post by Paqman on 2008-10-03
> **Warpster Buntu said:**
> How can I check to make sure I eradicated it all?

If it doesn't show up in Synaptic, it's gone.

If you still don't believe it, go to the Java site and see if [their tests](http://java.com/en/download/installed.jsp?detect=jre&try=1) run.

---

### Post by aimpau on 2008-10-03
Try also:

```

sudo apt-get autoremove

```

To remove the cached packages. Also, when removing from synaptic, make sure you choose remove AND purge.

---

### Post by iponeverything on 2008-10-03
> **Warpster Buntu said:**
> Due to complications, I need to do this... is there a certain command I could use to do this.

I have Version 6 AND Version 5 JREs installed.


Were they installed from a .deb?  if so try this to get the package names

dpkg -l |grep jre

and this to remove them

dpkg -r <package name>

If you they were not installed via dpkg cd to install directory where
sun hides (type: env) there jre and run:

find . -type f -name "uninstall*" 

to find the uninstall program that came with the jre

As a last resort you could tar up the install directories and remove them,
if that brute force method worked without any bad side effects then delete the tar file you made for backups.

found this link with google:
[http://cybernetnews.com/2008/08/09/helpful-tip-remove-old-versions-of-java-jre/](http://cybernetnews.com/2008/08/09/helpful-tip-remove-old-versions-of-java-jre/)

---

### Post by Warpster Buntu on 2008-10-03
Alright, I just install Java 6 bin... in which, and how, directory should it be placed in?

I'm sorry for all the questions... just not to great with all this stuff.

---

### Post by Paqman on 2008-10-03
> **Warpster Buntu said:**
> Alright, I just install Java 6 bin... in which, and how, directory should it be placed in?

You should be installing through Synaptic or Add/Remove. You won't need to specify the directory, the package manager takes care of all that for you.

---

