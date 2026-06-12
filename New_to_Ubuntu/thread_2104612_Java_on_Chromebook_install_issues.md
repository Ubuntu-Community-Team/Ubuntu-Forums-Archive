---
title: "Java on Chromebook install issues"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by Nodak on 2013-01-13
I am completely new to all of this, so just bear with me. I was trying to install Java onto a chromebook running their chrome-os or whatever they call it, when I ran into a problem. The problem is that when I run the self install file, it keeps coming back permission denied. Here is the code.

>localhost opt # sudo bash jre-6u38-linux-i586.bin
>Unpacking...
>Checksumming...
>Extracting...
>jre-6u38-linux-i586.bin: line 86: ./install.sfx.12049: Permission >denied Failed to extract the files. Please refer to the >Troubleshooting section of the Installation Instructions on the >download page for more information.

I went to the page it recommends and found nothing. 
Thanks guys.

---

### Post by AG4EM on 2013-01-20
Please note that Chromebooks do not support Java, and it's also not possible to install software on them.  One way around that is to use the Ericom AccessNow HTML5 RDP client for Chromebooks.  AccessNow will allow you to connect to an RDP host like a Terminal Server, VDI virtual desktop or even a physical PC, and run Windows applications or desktops in a browser tab.  That means that you can open up an Internet Explorer session inside a Chrome browser tab, and then connect to the applications that require Java and run them on the Chromebook.

Click here for more information:
[http://www.ericom.com/AN4Chromebooks]("http://www.ericom.com/RDPChromebook.asp?URL_ID=708")

Please note that I work for Ericom

---

