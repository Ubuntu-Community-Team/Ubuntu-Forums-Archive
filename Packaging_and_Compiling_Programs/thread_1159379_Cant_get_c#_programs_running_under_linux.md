---
title: "Cant get c# programs running under linux"
date: 2009-05-14
forum: Packaging and Compiling Programs
---

### Post by Jusdogmatik on 2009-05-14
I am using Mono Develop and I cant seem to get any of the programs I've created to run under Linux. They are compiling as an exe. They will run through wine but that isn't what I'm going for. I'm pretty new to programing so these are all very basic applications.  I am running Mono Develop 2.0 and Ubuntu 9.04 if that means anything.  Thanks. 

n.b. They're all written in c#.

---

### Post by directhex on 2009-05-14
> **Jusdogmatik said:**
> I am using Mono Develop and I cant seem to get any of the programs I've created to run under Linux. They are compiling as an exe. They will run through wine but that isn't what I'm going for. I'm pretty new to programing so these are all very basic applications.  I am running Mono Develop 2.0 and Ubuntu 9.04 if that means anything.  Thanks. 

n.b. They're all written in c#.

.exe is the standard file extension for CLI assemblies. Producing .exe files is normal, and what you want - e.g. look at /usr/lib/f-spot/f-spot.exe or /usr/lib/tomboy/Tomboy.exe

Simply execute with "mono appname.exe"

---

### Post by Jusdogmatik on 2009-05-14
thanks I'll give it a shot

---

