---
title: "Can't install some programs after xubuntu upgrade because of lib dependencies"
date: 2024-09-07
forum: New to Ubuntu
---

### Post by essedib14 on 2024-09-07
Hello I am trying to download Visual Studio Code but it won't install because of this error: Dependency is not satisifable libglib2.0-0 (>=2.37.3). 
I have tried various solutions online but I can't get it to work so I thought I'd try here please. 

I also had localWP installed before the upgrade and now I can't install anymore  because of this error: Dependency is not satisifable libaio1.

I am guessing they are not compatible with the upgrade but is there anything that I can do to install them anyway? What are my options? 
Thanks!

---

### Post by Dennis N on 2024-09-08
You could try the Flatpak version:

```

Visual Studio Code - Code editing. Redefined.

        ID: com.visualstudio.code
       Ref: app/com.visualstudio.code/x86_64/stable
      Arch: x86_64
    Branch: stable
   Version: 1.92.2
   License: LicenseRef-proprietary=https://code.visualstudio.com/license
Collection: org.flathub.Stable
  Download: 5.9*MB
 Installed: 14.9*MB
   Runtime: org.freedesktop.Sdk/x86_64/23.08
       Sdk: org.freedesktop.Sdk/x86_64/23.08


```

---

### Post by ActionParsnip on 2024-09-10
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

