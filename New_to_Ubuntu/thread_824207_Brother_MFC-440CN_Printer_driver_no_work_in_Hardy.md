---
title: "Brother MFC-440CN Printer driver no work in Hardy"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by cwmoser on 2008-06-09
The Brother websites printer driver for the MFC-440CN printer does not work in Hardy -- in fact if you install it, it will result in a Crash Report if you do the following:

sudo dpkg -i mfc440cncupswrapper-1.0.1-1.i386.deb 

Works just fine with Gutsy -- but not so for Hardy.

Anyone have a driver procedure for the MFC-440CN printer for Hardy?

Thanks

Carl

---

### Post by plucky on 2008-06-10
> Brother MFC-440CN Printer driver no work in Hardy
The Brother websites printer driver for the MFC-440CN printer does not work in Hardy -- in fact if you install it, it will result in a Crash Report if you do the following:

sudo dpkg -i mfc440cncupswrapper-1.0.1-1.i386.deb

Works just fine with Gutsy -- but not so for Hardy.

Anyone have a driver procedure for the MFC-440CN printer for Hardy?

Thanks

Carl 




The Brother drivers are now Packaged in Hardy and are in the Repos.So you can now use Synaptic package manager to install the drivers.
See this [link for Brother packaging](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother)#head-b52beb1f51be6f0078abf48dc10a972420b233e2) to find which package to install for your printer.

Good Luck

---

