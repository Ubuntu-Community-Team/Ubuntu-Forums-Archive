---
title: "[SOLVED] Error message when opening Synaptic package manager"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by sanderella on 2008-06-26
I just tried to open Synaptic Package Manager, and I got the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone help please?

---

### Post by sharks on 2008-06-26
i think there is another synaptic running. i e . update via terminal, update manger.

---

### Post by rockerphil on 2008-06-26
it means you interupted somthing installing or uninstalling, just run this in terminal


sudo dpkg --configure -a

that should do the trick

---

### Post by erginemr on 2008-06-26
Please refer to:
[http://ubuntuforums.org/showthread.php?p=5264447](http://ubuntuforums.org/showthread.php?p=5264447)

---

### Post by sanderella on 2008-06-26
Thanks for the info. I have a follow-on from this problem, I get a message now saying, "You have 1 broken package on your system! Use the "Broken" filter to locate it."

What do I do now? Thanks, guys.

---

### Post by philinux on 2008-06-26
Open synaptic, choose custom filters, Select broken just to see what it was.

Then Edit >Fix broken packages.

---

### Post by sydbat on 2008-06-26
In Synaptic there are choices for viewing packages (on the lower left). Click 'Custom Filters' and a list will show in the left pane starting with 'Broken'. Click that and choose the package that is broken, then 'Apply'...it will fix your broken packages.

---

### Post by sanderella on 2008-06-26
Thanks, guys! :KS

---

### Post by Loyal on 2008-07-08
Hi,  I am having thisproblem too.  I think it happened when installing support for ttf.  When I do the dpkg --configure -a I gete told to  install x-ttcidfont -config package.  (Im new and probably stupid still) I tried apt-get x-ttcidfont -config and got no command found.  (it says the msttcoreefonts was the file I was getting)   I tried to figuree out  how to install via terminal.  Im lost.  Can you point me int he right direction to learn what to do?

---

### Post by zenzizenzizenzic on 2008-07-08
I think the package you want is called x-ttcidfont-conf.  If you ever think you know the first part of a package but can't remember the wording, try double-tapping the tab key to see all the possible completions.

Although sorry if you already knew this and had tried this package!

---

