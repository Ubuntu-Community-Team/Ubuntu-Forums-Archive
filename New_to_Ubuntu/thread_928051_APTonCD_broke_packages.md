---
title: "APTonCD broke packages"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by lengo on 2008-09-23
I installed 8.04 from CD and was kindly informed that there were 252 updates (and as many or more MB ) waiting for me. Being as I am in a country where internet access is at a premium, I visited the network administrator at a local educational institution who kindly provided me with a CD of packages created with APTonCD. I loaded the packages to my cache (/var/cache/apt/archives) and, after a fairly long internet search, found that I could install them with:
```
sudo dpkg -i *.deb
```
Everything installed (be that good or bad) and I ended up with 32 broken packages. And then things started to unravel . . . The same icon that informed me that there were updates available now informed me that there were broken packages and that I could right-click to run Synaptic Package Manager, and run the 'Broken' filter to fix them. I did so, selected one of the broken packages to mark for 'complete removal', and clicked apply. Apparently, all these packages were related because I was informed that to remove the package I had selected I had to remove all 32 broken packages (is this normal?!) Thinking, naively, that Synaptic Package Manager accurately sorted through dependencies and provided the most robust update management around, I went ahead with it. And now I'm screwed . . . The first thing I noticed was my internet connection was gone (wireless managed with wicd). Then I noticed a 'muted' speaker in the upper right (sound packages are missing). Not knowing what else is broken (I have no idea what all the 'lib' files were), is there any way to get back to where I was? I thought Synaptic was meant to protect me from myself, sorting through dependencies that I cannot possible be expected to be aware of. I guess I was wrong. Anyway, wondering if there's any help available out there . . . Thanks.

---

