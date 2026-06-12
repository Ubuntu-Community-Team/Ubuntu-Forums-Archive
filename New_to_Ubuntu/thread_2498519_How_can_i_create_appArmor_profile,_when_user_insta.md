---
title: "How can i create appArmor profile, when user installs my app?"
date: 2024-06-17
forum: New to Ubuntu
---

### Post by vlabala on 2024-06-17
Hello guys, I'm new here. 
With the 24.04 ubuntu update appArmor profile became necessary for many applications, which include Discord, Chrome etc... ( I'm so new I can be wrong here already, but anyway )
I have an Electron application myself and noticed that my app just straight up crashes on launching, I can see that Discord and Chrome have their respectable profile files /etc/apparmor.d/chrome and /etc/apparmor.d/discord. 
Can anybody point me into right direction where can I create the same profile for my app? should I register it in ubuntu app store? or should I have some preloader that will create this profile for me? or is there some file I can ship with my electron build, like entitlements for MacOS? 
Thank you in advance!

---

### Post by vlabala on 2024-06-30
Figured that out, created a script that triggered by afterInstall field from electron-builder, in that I create the appArmor profile and refresh it, works like a charm, happy hacking!

---

### Post by ActionParsnip on 2024-07-02
Please mark as solved if there is no more issue

---

