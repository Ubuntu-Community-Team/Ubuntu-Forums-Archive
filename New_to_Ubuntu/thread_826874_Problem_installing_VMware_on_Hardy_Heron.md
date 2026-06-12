---
title: "Problem installing VMware on Hardy Heron"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by mchoo on 2008-06-12
Hi,

Almost a week ago, I posted a message about problems with installing VMware on Hardy Heron. Now, a kind forum user (quelx) pointed me to a URL ([http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)) on how to fix my problem. Which was fine and dandy. 

Unfortunately, I came across another problem installing VMware on another system. The problem is somewhat different this time. I followed the instructions given in the URL to the letter. But, when I ran vmware-install.pl, when it reached the stage when it was trying to create SSL certificate, it bombed out with an error that says: "Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key".

Has anyone come across this problem? How do I work around it?

Thanks muchly!

---

### Post by elgalloloco on 2008-06-12
Maybe this thread can help you.

```
http://ubuntuforums.org/showthread.php?t=337040
```

---

### Post by paulderol on 2008-06-12
is there a particular reason you need VMware? i.e.--can you use virtualbox for your purposes, and under a personal liscence? If so, i reccomend remaking your .vmdk files to .vmi files and running the better integrated virtualbox. 

I REALIZE THAT THIS MAY NOT REALLY BE USEFUL. 

If you need VMware, that's that, but if you can switch, i think virtualbox is simpler to use and setup, not to mention it plays more nicely with Open Source.

---

### Post by mchoo on 2008-06-13
> **paulderol said:**
> is there a particular reason you need VMware? i.e.--can you use virtualbox for your purposes, and under a personal liscence? If so, i reccomend remaking your .vmdk files to .vmi files and running the better integrated virtualbox. 

I REALIZE THAT THIS MAY NOT REALLY BE USEFUL. 

If you need VMware, that's that, but if you can switch, i think virtualbox is simpler to use and setup, not to mention it plays more nicely with Open Source.

I'm obviously an absolute beginner. I didn't know that there was an Open Source VMware-like product. I'm gonna try out VirtualBox. Thanks.

---

### Post by spiderbatdad on 2008-06-13
As far as I know vmware-server is open source and compliant with GPL: [http://www.vmware.com/download/eula/server.html](http://www.vmware.com/download/eula/server.html)

There are some tweaks necessary to run it on Hardy, but overall it is a superior virtual machine.

[http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware-server](http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware-server)

---

### Post by hyper_ch on 2008-06-13
the reason I chose vmware over vbox is because networking is really bad/difficult in vbox compared to vmware.

---

