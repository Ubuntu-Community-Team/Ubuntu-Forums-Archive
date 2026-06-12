---
title: "Printer drivers Brother MFC-J410"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by rubendecloedt on 2013-09-20
Hi,
For my Brother printer MFC-J410 I found and installed the printer drivers. But somehow I can not print anything.
For the record: I can't write in code. So keep the solution as simple as possible.

Greetings,
Ruben Decloedt

---

### Post by Kirboosy on 2013-09-20
Welcome to the forums!

I found this guide from a few releases ago. However it should be relevant as that model of printer is no longer made or supported by Brother.
[h=2][SIZE=1][ HOW TO ... Brother MFC-J410W Printer ... U/Xubuntu 11.04 - 12.04 				]("http://ubuntuforums.org/showthread.php?t=1961148")
[/SIZE][/h]Hope that helps!
~Caboose

---

### Post by kurt18947 on 2013-09-20
The printer driver is still available.  The installer script found here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

works very well but is not IMO intuitive, especially for someone not familiar with the CLI/terminal.  If your O.S. is 32 bit, you can download the .deb files from Brother found here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J410](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J410) 

and install using Ubuntu Software Center, gdebi (graphical installer) or follow the instructions for installing via terminal.  A 64 bit O.S. complicates things a bit; you must use the script or follow the terminal directions on Brother's site.  The drivers are 32 bit and require some 'massaging' to install on a 64 bit O.S.  I've had good luck with Brother's drivers but they assume fluency in terminal/'code'.  Copy/paste in terminal does work and Brother shows examples.  I've found it unnecessary to do most of the "pre-required" stuff on modern Ubuntu distros.  The install instructions are located underneath the box containing the drivers.

---

