---
title: "make a file persistently in linux"
date: 2014-09-08
forum: New to Ubuntu
---

### Post by mia3 on 2014-09-08
Hi,

I've added a file as follows:
"sudo cp /usr/local/etc/dnsmasq.conf.example /etc/dnsmasq.conf”
How can I make it persistent?

Thanks,

---

### Post by nerdtron on 2014-09-08
What do you mean persistent? Is the file /etc/dnsmasq.conf deleted after you reboot?

---

### Post by mia3 on 2014-09-08
Yes, if I reboot it, it will be removed

---

### Post by nerdtron on 2014-09-08
You using a desktop version right? Maybe a conflict on the GUI NetworkManager.
See here: [http://www.gwbasics.be/blog.nsf/dx/setup-dnsmasq-for-proof-of-concept-development-test-environments.htm](http://www.gwbasics.be/blog.nsf/dx/setup-dnsmasq-for-proof-of-concept-development-test-environments.htm)
> dnsmasq : on Ubuntu 12.10 (and higher), dnsmasq is actually already used  by NetworkManager.  So if you installl it, you'd have to disable it in  the NetworkManager configuration.

Why don't you make you changes on the /etc/NetworkManager/dnsmasq.d/dnsmasq.conf

---

### Post by yancek on 2014-09-08
Is this an actual installation to a hard drive or did you use software such as unetbootin or pendrivelinux to put the system on a flash drive?  If it is the latter, that is expected behavior as it is a read-only filesystem.  If it is an actual install, the file should be there on reboot.

---

### Post by mia3 on 2014-09-08
As I've searched more it seems I should add the file in /opt/.filetool.lst 
ok I will try [COLOR=#000000]GUI as well.
Thank you,[/COLOR]

---

### Post by SeijiSensei on 2014-09-09
I'll answer the question, though it's likely your problem is a symptom of something else.

Linux has file "attributes" beyond the normal permissions.  One of these is the "immutable" attribute.  Files with this bit turned on cannot be deleted or modified even by root unless the immutable switch is turned off.  You can use the "chattr" utility like this:
```
chattr +i /path/to/file
```
to make a file immutable.  Using the same command with "-i" turns that feature off.  To see more about these attributes, use "man chattr" for details.  The command "lsattr /path/to/file" will display a file's attributes.

---

