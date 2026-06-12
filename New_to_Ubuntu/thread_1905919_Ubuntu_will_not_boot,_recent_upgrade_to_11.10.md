---
title: "Ubuntu will not boot, recent upgrade to 11.10"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by awol567 on 2012-01-08
Hello!  My Ubuntu has often had trouble starting on its own, and I eventually found that it would start reliably after I had booted into Windows, restarted the computer, and then booted into Ubuntu.  This wasn't a big issue for me, so I ignored it.  

Today, I updated to 11.10, and everything seemed to work as it did.  I attempted to install graphics drivers for my ATI HD 3870x2, but it didn't function how I would have liked it to, so I uninstalled it.  Now, it would seem as if Ubuntu will not boot at all, even after booting into Windows.  I've made note of the command line for booting up the kernels in GRUB.  

My question is: How can I fix Ubuntu so that I can boot without first booting into windows?

Thanks in advance.

---

### Post by fantab on 2012-01-08
WUBI is not meant as PERMANENT way of using UBUNTU. It is to TRY Ubuntu from Windows.

I suggest you make a DUAL BOOT by installing UBUNTU on its own separate Partition.
Here is an **[Illustrated Tutorial]("http://members.iinet.net.au/%7Eherman546/index.html")** to dual boot Ubuntu with Windows.
Also read [**Ubunu community dual boot**]("https://help.ubuntu.com/community/WindowsDualBoot") information.

---

### Post by awol567 on 2012-01-08
Hi fantab.  It seems that there's some misunderstanding about my setup, sorry about that.  I do have ubuntu in its own partition, however when I attempt to boot it first, it would normally produce an error: "Gave up waiting for root device...check rootdelay= ; root=".  I found that the error would be (somewhat) resolved if I booted first into Windows, then restarted the computer, then booted into Ubuntu.  

My situation has changed somewhat in that this little trick won't work anymore, although booting the recovery mode kernel still returns the error message.  What I've done in the past few days is update to 11.10 then install/uninstall ati drivers (after I found they did nothing of value). 

I am contemplating just reinstalling ubuntu on that partition, but is there any way I can repair the partition without losing all of my data?

EDIT: This morning I tried the workaround, and I successfully booted into Ubuntu.  What is it about booting into Windows first that allows Ubuntu to load properly?

---

### Post by fantab on 2012-01-09
There could be some problem with GRUB Boot Loader. 

Did you install Windows after installing Ubuntu? (I don't think you did, still making sure). 

Anyways, try [**repairing GRUB USING UBUNTU LIVE CD**]("http://www.webupd8.org/2009/05/fix-restore-grub-boot-loader.html").
Also see [**GRUB2-DOCUMENTATION**]("https://help.ubuntu.com/community/Grub2")

If you are still unable to solve it then post the output of [**BOOT INFO SCRIPT**]("http://bootinfoscript.sourceforge.net/") here.

---

### Post by bcbc on 2012-01-09
You could have an issue with the initrd.img which can be rebuilt manually (but this seems unlikely if it sometimes works).

Otherwise, here are some suggestions for follow up:
[http://dotancohen.com/eng/gave_up_waiting_for_root_device.html](http://dotancohen.com/eng/gave_up_waiting_for_root_device.html)

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

---

### Post by awol567 on 2012-01-10
I made sure to install ubuntu after I had already installed windows as per recommendations online.  

I will try bcbc's suggestions, and if that does not work I will try repairing GRUB as fantab suggested.  

Oddly enough, I began this session with no issues during booting.  I still don't know what the problem is but I don't think it is resolved yet.  I will have to try booting another time.  

Thank you for all your help, I will post when I have tested the solutions.

---

### Post by awol567 on 2012-01-27
Hello everyone, a little update since my last post.  I got the GRUB Customizer, and I disabled the quiet splash in the preferences, as well as changing the resolution, setting windows as the default operating system.  I have a feeling there was something up with the quiet splash, but I can't tell for sure what may have fixed the problem.  Thanks for your input!

---

