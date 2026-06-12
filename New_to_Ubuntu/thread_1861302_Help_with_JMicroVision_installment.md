---
title: "Help with JMicroVision installment"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by RoastedBeef on 2011-10-15
I followed the installation steps in the website
(These)
Linux Instructions:
Right-click on the link and select "Save Target As..."
After downloading, extract the archive
Then, set the execute permissions to the directory: type chmod -R u+x JMicroVision-v127-linux in a Terminal screen
Uninstall: Delete the directory of JMicroVision 1.2.7.

Launch JMicroVision: In the directory of JMicroVision 1.2.7, double-click JMVision or type ./JMVision in a Terminal screen. If the launcher does not start, type ldd JMVision to show the dependencies with the shared libraries and add to your system the missing packages. It is also possible to launch JMicroVision by using the Java command (see Generic or Other Platforms Instructions).

Start the Configuration Wizard: In the directory of JMicroVision 1.2.7, type ./JMVision -config in a Terminal screen.

So I extracted it to Desktop. My problem goes with the terminal, I type chmod.. etc and this appears:

chmod: cannot access `JMicroVision-v127-linux': No such file or directory

Anyone knows resolve this? Much appreciated.

---

