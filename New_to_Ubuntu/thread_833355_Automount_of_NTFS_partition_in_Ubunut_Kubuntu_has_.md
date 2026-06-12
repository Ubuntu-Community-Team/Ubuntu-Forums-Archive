---
title: "Automount of NTFS partition in Ubunut? Kubuntu has it but not Ubuntu?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-18
I find the following article about auto mounting NTFS partition in Kubuntu but I can not find similar system for ubuntu?

[http://ubuntusite.com/auto-mount-ntfs-drive-kubuntu-hardy-heron/](http://ubuntusite.com/auto-mount-ntfs-drive-kubuntu-hardy-heron/)

Do you know something similar for ubuntu?
Thanks

---

### Post by Hospadar on 2008-06-18
run the "ntfs-config" tool (I believe is the name, it's the frontend for the ntfs-3g driver which comes stock nowadays I think).  From a terminal, run "sudo ntfs-config" if nothing shows up, try installing it "sudo apt-get install ntfs-config"  Also in nautilus, if you go to "computer" (like Places->Computer) and right click the unmounted drive, go to properties or something I think you might be able to have it automount from there.

---

### Post by tamoneya on 2008-06-18
since the kubuntu guide you followed did it through a gui i found a howto that used a gui in ubuntu as well.  [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

However it is a very simple problem to solve just by editting the command line.  It takes 1 minute to do and you would learn more from doing it this way: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

