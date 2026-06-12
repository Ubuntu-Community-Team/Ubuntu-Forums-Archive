---
title: "Netbeand IDE, C++ plugin......"
date: 2009-11-16
forum: Programming Talk
---

### Post by D3mon_Spawn on 2009-11-16
Hello all, I'm running x64 Ubuntu 9.10 and I just installed Netbeans from the Software Center. I need to do some C++ programming so I installed the C++ plugin within Netbeans, but now I'm a little confused as to which compilers and such I'm required to use that work with Netbeans. I navigated to the Netbeans support page ([http://netbeans.org/community/releases/67/cpp-setup-instructions.html#compilers_linux](http://netbeans.org/community/releases/67/cpp-setup-instructions.html#compilers_linux)) for C++ and they give a nice table of stuff but don't exactly specify which are required to download. I think I'm supposed to download the last four items. CAn anyone point me in the right direction?? I want to use whatever is compatible with Netbeans.

---

### Post by haTem on 2009-11-17
> **D3mon_Spawn said:**
> Hello all, I'm running x64 Ubuntu 9.10 and I just installed Netbeans from the Software Center. I need to do some C++ programming so I installed the C++ plugin within Netbeans, but now I'm a little confused as to which compilers and such I'm required to use that work with Netbeans. I navigated to the Netbeans support page ([http://netbeans.org/community/releases/67/cpp-setup-instructions.html#compilers_linux](http://netbeans.org/community/releases/67/cpp-setup-instructions.html#compilers_linux)) for C++ and they give a nice table of stuff but don't exactly specify which are required to download. I think I'm supposed to download the last four items. CAn anyone point me in the right direction?? I want to use whatever is compatible with Netbeans.

Installing the build-essentials package should give you all you need. It will install the g++ compiler which netbeans can use.

```

sudo aptitude install build-essentials

```

---

