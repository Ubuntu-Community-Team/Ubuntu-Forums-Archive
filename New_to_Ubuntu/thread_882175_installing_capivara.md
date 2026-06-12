---
title: "installing capivara"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by myotis on 2008-08-06
Capivara downloads as a file called "capivara-installer-0.8.4.jar" which apparently installs on Windows if you double click on it.  But I could do with some help with installing on Ubuntu.

The instructions are:

t first make sure you have the Java Runtime environment installed on your system. On Windows, you can just double-click on capivara-<version>-installer.jar and the installation starts. You can also launch the installer from the command line.

Include the java runtime in your search path:

on Unix environments and bash
export PATH=/usr/local/jdk1.5.0_03/bin:$PATH

on Windows
set PATH=C:\Program Files\Java\jre1.5.0\bin;%PATH%
java -jar <PATH_TO_INSTALLER>/capivara-<version>-installer.jar

If your system does not support desktop icons or program list entries or you didn’t choose to install such, start Capivara by executing
java -jar <PATH_TO_CAPIVARA>/capivara.jar 

Can anyone help me out with this.

Thanks,

Graham

---

