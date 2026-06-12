---
title: "How Does Ubuntu Recognize Packages?"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by ifben on 2011-09-22
Hello,

I am wondering how Ubuntu recognizes a package when you install it. For example, when you type, "apt-get install ruby-full" at the command line, how does Ubuntu know what "ruby-full" is?

Thank you,

Ben

---

### Post by alphacrucis2 on 2011-09-22
> **ifben said:**
> Hello,

I am wondering how Ubuntu recognizes a package when you install it. For example, when you type, "apt-get install ruby-full" at the command line, how does Ubuntu know what "ruby-full" is?

Thank you,

Ben

It has an index of all the packages that are in the enabled repositories. When you run **sudo apt-get update** you are updating your local copy of the index to bring it into sync with whatever is on the repository mirrors that you are using.

---

### Post by ifben on 2011-09-22
Few Questions now:

1. Is there some place you can see a list of the enabled repositories? 

2. When you do apt-get install, are you just grabbing a copy of a Github repository? 

3. Does this mean that you wouldn't be able to install these packages via Aptitude without an internet connection? 

4. How does one get his software in the list of enabled repositories? For example, let's say I made a package and I wanted it to be installed via Aptitude. How would I proceed?

Thanks for your time.

Ben

---

### Post by Lars Noodén on 2011-09-22
APT is probably the [single biggest advancement](http://ianmurdock.com/solaris/how-package-management-changed-everything/) that Linux has brought to the industry.

Ubuntu inherits APT from [Debian](http://www.debian.org/doc/FAQ/ch-pkg_basics).  There is a lot of material out there on how to use APT, though little to explain how it works.  Synaptic and the Software Center are also extensions of the same package manager.

---

### Post by oldos2er on 2011-09-22
> **ifben said:**
> 1. Is there some place you can see a list of the enabled repositories?

/etc/apt/sources.list and any files in /etc/apt/sources.list.d
Or run **gksu software-properties-gtk** to see the same info in a GUI.

> 2. When you do apt-get install, are you just grabbing a copy of a Github repository?

I don't think the repos use github; not sure. 

> 3. Does this mean that you wouldn't be able to install these packages via Aptitude without an internet connection?

Both aptitude and apt-get can install packages from a CD, see   [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
Otherwise, they look to the repos which require an internet connection.

> 4. How does one get his software in the list of enabled repositories? For example, let's say I made a package and I wanted it to be installed via Aptitude. How would I proceed?

If you've created a package on your own machine, you can install it with dpkg, **sudo dpkg -i foo.deb**
If you're asking how to submit your package to the Ubuntu repos, see 
[http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

---

### Post by Lars Noodén on 2011-09-22
> **oldos2er said:**
> 
If you've created a package on your own machine, you can install it with dpkg, **sudo dpkg -i foo.deb**
If you're asking how to submit your package to the Ubuntu repos, see 
[http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

You can also maintain your own [Personal Package Archive (PPA)](http://ubuntuforums.org/showthread.php?t=929498)

---

