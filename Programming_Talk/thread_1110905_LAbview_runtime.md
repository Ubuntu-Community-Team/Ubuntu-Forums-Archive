---
title: "LAbview runtime"
date: 2009-03-30
forum: Programming Talk
---

### Post by linuss83 on 2009-03-30
Anyone how to install Labview runtime on Ubuntu 8.10 with 64-bits.
I have tried many things but it will not work.

Any guides or things like that

---

### Post by alexandre_bastien on 2009-06-20
[http://ubuntuforums.org/showthread.php?t=726092](http://ubuntuforums.org/showthread.php?t=726092)

I was facing the same problem to install LabVIEW 8.5 on my AMD64 Ubuntu 8.04, alien complained about architecture difference.

After a whole night trying different methods I've came to a procedure that works. All you need are the LabVIEW RPM packages, rpm2cpio and cpio utils, here are the step-by-step instructions:

1 - mkdir ~/labview
2 - cd ~/labview
3 - cp LABVIEW_INSTALL_MEDIA_MOUNT_POINT/*.rpm
4 - for each of the RPMs run the following command:

rpm2cpio RPM_FILE | cpio -idv

Don't mind to try *.rpm in the above command, I doesn't work Unfortunately it must be file by file or you can automate the process using a script.

The above command complete unpacks the RPM, after all the RPMs are processed there will be an ~/labview/usr/local/ folder containing all LabVIEW's files.

6 - sudo mv usr/local/* /usr/local/

7 - It's already installed! Just create a launcher that points to /usr/local/natinst/LabVIEW-8.5/labview

OBS: If you need to remove LabVIEW just remove the /usr/local/natinst and the 5 libraries added to /usr/local/lib

---

### Post by alexandre_bastien on 2009-06-20
But there is a graphical problem on jaunty. But it still usable.

---

