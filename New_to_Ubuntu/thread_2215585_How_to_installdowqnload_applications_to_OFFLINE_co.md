---
title: "How to install/dowqnload applications to OFFLINE computer"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by john181 on 2014-04-07
Hi everyone !  I use xUbuntu on my offline desktop. I need to downoad some apps but none of the linux versions downloads of the apps on the internet work when I try installing it off a usb ( pop up about how to open the file, using fle extractor or something). Exe files dont open.  So can I download some files from ubuntu software centre on another computer, and transfer it by usb, how do I do that ?

---

### Post by Mark Phelps on 2014-04-07
>  Exe files dont open.These are most likely MS Windows apps -- and these don't install on Ubuntu.  If that's what you're trying to use, you need to tell us that.

While you can download .deb files to one machine and copy them to another machine, you're likely to run into problems with missing dependencies.  When you go to install from a .deb file, the package manager sees the dependencies and checks your PC to see if you already have them installed.  If you do not, it downloads those missing dependencies, as well.  The problem with installing offline is that it can not download those files.  So, you have to go back to the original machine, download that file, copy it to the other machine, try installing again -- and bump into another missing dependency --  and do this over and over until all the missing dependencies are downloaded.  The Linux application package installation process is designed to be used online.

---

### Post by sandyd on 2014-04-07
Moved to Absolute Beginners Section

---

### Post by Impavidus on 2014-04-07
Synaptic package manager can create nice download scripts to get all .deb files, including dependencies, on a different computer to transfer them by usb drive. The thing is, you still have to refresh the package information somehow and you first have to install synaptic.

Although **sudo apt-get install synaptic** should give you some error messages with all the URLs you need for installing synaptic and dependencies... I tried something like that once, shortly after first installing Ubuntu 6.06. It worked, but I'm not sure it's such a neat method.

---

