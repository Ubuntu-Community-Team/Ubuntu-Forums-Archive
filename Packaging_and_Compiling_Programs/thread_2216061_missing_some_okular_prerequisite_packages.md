---
title: "missing some okular prerequisite packages"
date: 2014-04-09
forum: Packaging and Compiling Programs
---

### Post by juanuni on 2014-04-09
Hello, I don't know if I write in the right subforum. I'm on Trusty Beta-2 (minimal) with latest KDE. I try install okular, but this message appears

> 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe libokularcore3abi1 i386 4:4.12.95-0ubuntu1  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe okular i386 4:4.12.95-0ubuntu1
  404  Not Found [IP: 91.189.91.15 80]
E: Imposible obtener [http://us.archive.ubuntu.com/ubuntu/pool/universe/o/okular/libokularcore3abi1_4.12.95-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/o/okular/libokularcore3abi1_4.12.95-0ubuntu1_i386.deb)  404  Not Found [IP: 91.189.91.15 80]


I suspect the prerequisite packages are missing. I open muon and the prerequisite package are
[LIST]
[*]libkscreen1
[*]libokularcore3abi1
[*]libspectre1
[/LIST]
but in [HTML]https://launchpadlibrarian.net/162544435/libkscreen_1.0.2-0ubuntu2.dsc[/HTML] the related ubuntu package no download ... same situation for libspectre1, see [HTML]http://archive.ubuntu.com/ubuntu/pool/main/libs/libspectre/libspectre_0.2.7-2ubuntu1.dsc[/HTML]

For libokularcore3abi1 (in [HTML]https://launchpad.net/ubuntu/trusty/+package/libokularcore3abi1[/HTML]) appears "No available description"

I suppose this is due beta version. I'm right?, Will this be corrected?

---

### Post by SeijiSensei on 2014-04-09
The current version of okular for Trusty is 4:4.12.97-0ubuntu2; it carries the date April 2 on my fully-updated Kubuntu 14.04 system.  There is no "libokularcore3abi1" package; the dependency listed in okular is called libokularcore4. I don't see anything called libkscreen1 in the okular dependency list either, but libspectre1 is there.

I take it you are not running Kubuntu.  My guess is that packaging of KDE apps for other platforms may not keep pace with Kubuntu releases still in development.

I'm using the repositories at mirrors.mit.edu, though I doubt that would matter.

---

### Post by juanuni on 2014-04-10
> **SeijiSensei said:**
> The current version of okular for Trusty is 4:4.12.97-0ubuntu2; it carries the date April 2 on my fully-updated Kubuntu 14.04 system.  There is no "libokularcore3abi1" package; the dependency listed in okular is called libokularcore4. I don't see anything called libkscreen1 in the okular dependency list either, but libspectre1 is there.

I take it you are not running Kubuntu.  My guess is that packaging of KDE apps for other platforms may not keep pace with Kubuntu releases still in development.

I'm using the repositories at mirrors.mit.edu, though I doubt that would matter.

Oh yeah, you are right. I just upgrade the distro and voilà. Thanks a lot.

---

