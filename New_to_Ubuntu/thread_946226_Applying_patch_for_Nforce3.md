---
title: "Applying patch for Nforce3"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Misko78 on 2008-10-13
Hello everyone,


I've have built second box and decided to use Ubuntu Hardy Heron as a operating system. So far i'm very satisfied but i have a hardware problem as my ASUS K8N board is not quite compatible with Linux, as it can't properly configure AGP port on this board thus making it 3D inoperable. Solution was to downgrade to earlier version of BIOS but unfortunately my CPU (Sempron E6) is not supported in only version of BIOS (Version 1006) that makes board compatible with Linux. I've found here in archives that one user managed to make it work with some kind of patch but i am total Linux and Ubuntu noob, so can you explain me how to apply this patch.

[Link to archived post.]("http://ubuntuforums.org/showthread.php?p=2333684")

---

### Post by Victormd on 2008-10-14
download his file, extract to your desktop, right click>properties>permissions and mark the option to make executable (if not already marked) then double click and select "run in terminal" or open a terminal and type:
```
cd Desktop
./k8agp.patch
```
If you get an error regarding permissions, then use
```
cd Desktop
sudo ./k8agp.patch
```

Right now I'm on windows and the file opens up as gibberish. When I get home I'll check it under ubuntu... but the above should get you going.

---

