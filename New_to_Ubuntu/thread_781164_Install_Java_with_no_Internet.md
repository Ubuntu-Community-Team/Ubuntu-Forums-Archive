---
title: "Install Java with no Internet"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by think13 on 2008-05-04
My friend recently installed Ubuntu.  Our university's internet system requires java in order to access the internet.  He cannot get internet access without the firefox java plugin, and I don't know how to install java without internet access.  

What is the easiest way to install java without internet access?

---

### Post by iSplicer on 2008-05-04
You will need to download the binaries from elsewhere and take it to your PC with a CD or USB drive and install it

---

### Post by think13 on 2008-05-04
OK, not very helpful.  I downloaded the binaries from Sun, but they are not .deb files.  I ran the binary they provided, didn't install the firefox plugin.

---

### Post by think13 on 2008-05-04
Ok, I did it by going to /var/cache/apt/archives and finding the .deb packages that it needed.  These were 
java-common, sun-java6-bin, sun-java6-jre, sun-java6-plugin, unixodbc, and odbcinst1debian.

I saved those package files to a flash drive and installed them on his machine.

---

