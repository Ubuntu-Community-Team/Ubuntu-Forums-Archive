---
title: "Missing packages in installing git Ubuntu 17.04"
date: 2018-03-02
forum: New to Ubuntu
---

### Post by ivessssssss on 2018-03-02
I tried using *sudo dpkg –configure -a *and [I]sudo apt-get update && sudo apt-get upgrade to fix the broken packages. However, the terminal still shows this:
```
[/I]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 git : Depends: libpcre2-8-0 but it is not installable
       Depends: liberror-perl but it is not installable
E: Unable to correct problems, you have held broken packages.
[I]
```

[/I]Can anyone help? 
Thanks heaps!!

---

### Post by deadflowr on 2018-03-02
17.04 hit end of life and support several months ago and the package archives have been removed.
You need to update to a newer or supported release such as Ubuntu 16.04 or Ubuntu 17.10.

---

### Post by ivessssssss on 2018-03-04
Thanks a lot!! I worked it out by using the 17.10 version

---

