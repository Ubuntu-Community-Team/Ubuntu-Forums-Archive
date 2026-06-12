---
title: "wsl ubuntu preview how update"
date: 2022-10-28
forum: New to Ubuntu
---

### Post by sucicf1 on 2022-10-28
This is a noob question.
I have got the wsl2 ubuntu preview. But how do I get the latest daily updates? If I try to update via ms store than I don't have updates since 5 days. Is it enough to make sudo apt update and sudo apt upgrade

Thank you

---

### Post by #&amp;thj^% on 2022-10-28
Ok I feel the need to Add>>>This app delivers the latest daily builds of Ubuntu WSL directly to your Windows machine. As amazing as that sounds, it should come as no surprise that this is not recommended for production development. It may be unstable and it will have bugs. But if you want a sneak peek at the future of Ubuntu, or to help identify issues and improvements, it might just be the app for you!
They have a special forum with help and information to browse through: [https://discourse.ubuntu.com/c/wsl2/27](https://discourse.ubuntu.com/c/wsl2/27)
I guess I should reply to your question though>>> "Is it enough to make sudo apt update and sudo apt upgrade"
Yes.
```
onefallen@x1:~$inxi -FzAzCz 
System: Kernel: 5.15.68.1-**microsoft-standard-WSL2 x86_64 bits**: 64 Desktop: N/A
Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)                                                            
```

---

