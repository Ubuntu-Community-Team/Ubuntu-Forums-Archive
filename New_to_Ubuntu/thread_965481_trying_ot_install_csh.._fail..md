---
title: "trying ot install csh.. fail."
date: 2008-10-31
forum: New to Ubuntu
---

### Post by silentvisual on 2008-10-31
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.27-7-generic to initrd.img.

dpkg: dependency problems prevent configuration of dkms:
 dkms depends on linux-image; however:
  Package linux-image is not installed.
  Package linux-image-2.6.27-7-generic which provides linux-image is not configured yet.
dpkg: error processing dkms (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-177-kernel-source:
 nvidia-177-kernel-source depends on dkms; however:
  Package dkms is not configured yet.
dpkg: error processing nvidia-177-kernel-source (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx-177:
 nvidia-glx-177 depends on nvidia-177-kernel-source (>= 177.80); however:
  Package nvidia-177-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-177 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because MaxReports is reached already
                                                                         Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 dkms
 nvidia-177-kernel-source
 nvidia-glx-177



i been trying a lot of things didn't work..
i think is the live cd thing i am using the 8.10 create a usb startup disk.. 

thankyou

---

### Post by stephanvaningen on 2008-10-31
With csh you mean the C-Shell I suppose?
What is your exact problem please? You say 'csh won't install'? What is all the other nvidia info in the post?

---

### Post by silentvisual on 2008-11-02
idk what i did i just install all the thing it was recommend and required thats all.. i just need fix that

update-initramfs is disabled since running on a live CD 

if now i can always reformat it.. cuz all i wanted to do is install it on my usb drive so i can take it to school and installed some software on it. thats it..

---

