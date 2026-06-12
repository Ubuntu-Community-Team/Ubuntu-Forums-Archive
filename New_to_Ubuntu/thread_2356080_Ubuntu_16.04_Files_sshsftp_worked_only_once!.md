---
title: "Ubuntu 16.04 Files ssh/sftp worked only once!"
date: 2017-03-19
forum: New to Ubuntu
---

### Post by pingram3541 on 2017-03-19
I used the connect dialog in the "other locations" sidebar and connected to my virtual machine and was able to browse and manage the file system.  I needed to reboot my vm but after reboot I can no longer access the files via ssh.  It connects just fine, however when clicking on the drive it states "Oops! Something went wrong - unhandled error message: Location is already mounted" but there is only the one mount location I am trying to access visible in the Networks list which is the one giving me this error.

I can ssh into the machine using command line, putty or even another machine on my network no problem, just can't use the Ubuntu file browser any more =(

Any help is greatly appreciated.

---

### Post by Keith_Helms on 2017-03-20
Sounds like you connected to the VM's drive, then rebooted the VM while still connected.  Somewhere in the file manager options there should be a disconnect/unmount option which you would need to run before rebooting the VM.  Rebooting the system you're connecting to the VM from should also fix the problem.

---

### Post by pingram3541 on 2017-03-20
That's exactly what happened but I had a doozy of a time finding an explanation online and I'm glad I asked here.  After rebooting my host build I was able to connect again.  Thanks Keith!

---

