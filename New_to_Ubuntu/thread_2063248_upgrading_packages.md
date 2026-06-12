---
title: "upgrading packages"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-26
Hello everyone,
 
As a true absolute beginner coming to Ubuntu/Linux from Windows I am bewildered by the vast array of packages and versions thereof.  Could someone explain to me the proper way to upgrade from one package to another.  For example, GTK+-2.0 depends on a Pango version.  Suppose Pango changes and a new version comes out.  If I want to upgrade to the new version two questions arise:
 
  1.  Will GTK+-2.0 continue to function correctly with the new Pango and how will I know this?
  2.  What is the correct procedure for installiong the new version of Pango.
 
I pick these as examples.  The question is very generic.
 
Regards and thanks,
Mark Allyn

---

### Post by sandyd on 2012-09-26
> **mark allyn said:**
> Hello everyone,
 
As a true absolute beginner coming to Ubuntu/Linux from Windows I am bewildered by the vast array of packages and versions thereof.  Could someone explain to me the proper way to upgrade from one package to another.  For example, GTK+-2.0 depends on a Pango version.  Suppose Pango changes and a new version comes out.  If I want to upgrade to the new version two questions arise:
 
  1.  Will GTK+-2.0 continue to function correctly with the new Pango and how will I know this?
  2.  What is the correct procedure for installiong the new version of Pango.
 
I pick these as examples.  The question is very generic.
 
Regards and thanks,
Mark Allyn

1. GTK+-2.0 will be compiled against the new Pango and will be uploaded to the new repos.

2. You see that software update window that comes out sometimes?
Click update.

Its automatic

---

### Post by snowpine on 2012-09-26
Welcome to the forums Mark!

The officially sanctioned upgrade method that most Ubuntu users is as follows:

Upgrade to a new release every 6 months (regular releases) or 2 years (long term support). This upgrades the kernel, libraries, applications, etc. all at the same time. It is like buying a new car that all of the parts are tested to work together.

Within the 6+ months that you are using each release, you get "patch" updates to the application and library versions you already have installed. These fix bugs, improve stability, and close security vulnerabilities, but do not (typically speaking) introduce new features or cause backwards compatibility problems for the user. 

Here is a great article explaining the concept, it is written by the Red Hat people but the concept applies equally to Ubuntu: [https://access.redhat.com/security/updates/backporting/](https://access.redhat.com/security/updates/backporting/)

The nice thing about Ubuntu is that it's "open source." This means that you never have to *guess* which version of something, you can always look "behind the scenes" and read about development, bugs, latest versions, etc. For example you may find these links helpful:

[http://packages.ubuntu.com/source/precise/pango1.0](http://packages.ubuntu.com/source/precise/pango1.0)
[https://launchpad.net/ubuntu/+source/pango1.0](https://launchpad.net/ubuntu/+source/pango1.0)

---

### Post by mark allyn on 2012-09-27
Thanks, snowpine.
 
I have found the community to be extremely helpful.  I'm still very green and still finding my way around Ubuntu.  
 
I will follow your advice on upgrades.  
 
Regards,
Mark

---

### Post by hypnot0ad on 2012-09-27
You can use the terminal to make sure you are only updating what you want when you feel you need to.

As @sandyd said when you see an update being prompted on your screen, simply click it and you should be OK.

I am sure that there are ways to get a more information on which packages you use and when they are updated so you can keep up.

---

### Post by HiImTye on 2012-09-28
packages in the official repos are checked to make sure that they don't fail any other package's dependency list. any packages from third party repositories (such as launchpad) obviously can't be guaranteed, so it's best to use only repositories that you know are reliable. the best methods for updating is to use the built in tools such as the 'Update Manager' or the console command:
```
sudo apt-get upgrade
```

---

