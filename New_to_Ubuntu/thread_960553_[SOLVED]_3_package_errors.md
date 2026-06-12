---
title: "[SOLVED] 3 package errors?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by NoL618 on 2008-10-27
I'm trying to do updates from the update manager and I cannot because I get an error message telling me I have three broken pagages?  What does this mean?  There is also an icon in the top right corner that is shaped like an star with a down arrow and another one that is a red circle with a line in the middle.

When I scroll over the orange star it tells me this message:  
 Error:  BrokenCount > 0

What does all this mean??

---

### Post by NoL618 on 2008-10-27
Here's another error message i get when trying to update:


E: /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.42_amd64.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-restricted-modules-2.6.24-21-generic_2.6.24.14-21.51_amd64.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-headers-2.6.24-21_2.6.24-21.42_all.deb: failed in buffer_write(fd) (10, ret=-1)


no idea what this means....definitely need help fixing...

---

### Post by philinux on 2008-10-27
Open synaptic from the system>admin menu.

Click Broken, 

Then Edit>Fix Broken

---

### Post by NoL618 on 2008-10-27
I just tried to fix the errors from the synaptic manager and this is the error message I got:

E: /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.42_amd64.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-restricted-modules-2.6.24-21-generic_2.6.24.14-21.51_amd64.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-headers-2.6.24-21_2.6.24-21.42_all.deb: failed in buffer_write(fd) (10, ret=-1)

what should I do now?

---

### Post by philinux on 2008-10-27
Looks like your root partition could be full. 
Use this 

```
df -h
```

Post back the output.

---

### Post by porteclefs on 2008-10-27
i want to point out that this is also why your apt-get / sources.list issue is occurring.

---

### Post by NoL618 on 2008-10-27
ok, this is what I got:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.7G  2.7G     0 100% /
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   64K 1007M   1% /dev
devshm               1007M   24K 1007M   1% /dev/shm
lrm                  1007M   44M  963M   5% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon      2.7G  2.7G     0 100% /home/noelle/.gvfs


can I do anything?

---

### Post by dracayr on 2008-10-27
you can uninstall programs... you have to free disk space somehow

dracayr

---

### Post by NoL618 on 2008-10-27
Ok, I just went to the applications add/remove and I got this message and it did not let me continue:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


How do I remove applications and programs?  How do I know what to remove?

---

### Post by Elfy on 2008-10-27
go to the other thread - they are connected - do the clean and then you should be able to deal with this problem

---

### Post by NoL618 on 2008-10-27
thank you!

---

### Post by geektitude on 2008-10-30
> **philinux said:**
> Open synaptic from the system>admin menu.

Click Broken, 

Then Edit>Fix Broken

Thanks Philinux...your post helped me out.

---

