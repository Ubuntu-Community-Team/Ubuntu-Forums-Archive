---
title: "Error when try apt-get update - typora"
date: 2017-09-27
forum: New to Ubuntu
---

### Post by sed_faster on 2017-09-27
Hello folks,

How can I solve this error?
```

Hit:1 http://pt.archive.ubuntu.com/ubuntu zesty InRelease
Hit:2 http://pt.archive.ubuntu.com/ubuntu zesty-updates InRelease                                                                                                                                                 
Hit:3 http://pt.archive.ubuntu.com/ubuntu zesty-backports InRelease                                                                                                                                               
Hit:4 http://security.ubuntu.com/ubuntu zesty-security InRelease                                                                                                                                             
Hit:5 http://archive.canonical.com zesty InRelease                                                                                             
Hit:6 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu zesty InRelease              
Hit:7 https://typora.io ./linux/ InRelease                              
Hit:8 https://typora.io linux/ InRelease         
Ign:9 http://repo.vivaldi.com/stable/deb stable InRelease
Hit:10 http://repo.vivaldi.com/stable/deb stable Release
Reading package lists... Done
W: Conflicting distribution: https://typora.io ./linux/ InRelease (expected ./linux/ but got )
W: Conflicting distribution: https://typora.io linux/ InRelease (expected linux/ but got )

```

Thanks

---

### Post by ajgreeny on 2017-09-28
Let's see your **/etc/apt/sources.list** file contents with command ```
cat /etc/apt/sources.list/etc/apt/sources.list
``` and copy the output back here.

I have not been able to find a lot about installing typora, and certainly do not know it personally, so you will probably need to wait for someone with experience of using and updating it.

---

### Post by tim-timschroeder on 2017-10-07
> **Edgar_Oliveira said:**
> Hello folks,

How can I solve this error?
[..]
```

W: Conflicting distribution: https://typora.io ./linux/ InRelease (expected ./linux/ but got )
W: Conflicting distribution: https://typora.io linux/ InRelease (expected linux/ but got )

```



You see this warning because the instructions on the Typora website for how to include the Typora repository, which you have probably followed, are slightly inaccurate. You see the warning two times probably because you have included the Typora repository more than once in your /etc/apt/sources.list file.

Please 

1) change the repository path in your file /etc/apt/sources.list (or, should you have that, in a separate file in /etc/apt/sources.list.d) to this:

```

deb https://typora.io/linux ./

```

2) remove any other references to the Typora repository from your sources.list file.

When you now try apt-get update again, the warnings shouldn't show anymore.

---

