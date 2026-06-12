---
title: "My Samsung SCX-4200 Isnt working! :("
date: 2008-09-15
forum: New to Ubuntu
---

### Post by vivekv3 on 2008-09-15
Hey Guys,

Im a COMPLETE nooby to ubuntu(hardy heron), and I tried reading the forum about installing the "unified linux driver" for the scx-4200 that I downloaded from the samsung site, but I still cannot figure out exactly how to do it.  Any help would be greatly appreciated.

Thanks

---

### Post by bumanie on 2008-09-15
Not sure if you've seen this step-by-step

[Ubuntu OS Installation]
> 1. Download and extract the driver
2. Open ”Root Terminal”
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer 
Also look at [this thread]("http://ubuntuforums.org/showthread.php?t=341621")

---

### Post by yahs on 2008-09-16
I have a Samsung SCX-4100 and I found it difficult to install correctly.

Ubuntu added the printer on installation but it did not have the driver for the SCX-4100, so printing did not work.
I downloaded and followed the instructions for installing the Samsung Unified Printer Driver and I had success, but in a different way to what was described.

After the installation an icon for the Unified Driver Configuration appears on the desktop showing 2 printers, scx-4100 (default) installed on mfp:/dev/mfp4 and SCX-4100_Series installed on usb://Samsung/SCX-4100%20Series

scx-4100 came from the unified driver download and installed on the first usb port.When I did a test everything appeared to be okay but nothing printed.
SCX-4100_Series was installed by ubuntu on installation and when I changed the printer driver (System, Administration, Printing, Make and Model)to SCX-4100 Series everything worked perfectly so I just deleted scx-4100 and I now have printing as normal with all features enabled.

If you're having difficulty with the instructions just follow the first couple of points

Download and extract the file to your home directory

Open a terminal and change the permissions

Change to the directory (cdroot/Linux)and run install.sh

This solves printing but scanning requires more fixes (however they do work)so I'd leave that till later.

---

