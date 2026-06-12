---
title: "Xen Xl command to fetch Host UUID"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by Veerabhadra_Kota on 2014-08-06
Hi,

I am looking for the below information on the Xen Host using XL or any other commands. Could anyone help me to retrieve below details:

1. Host UUID
2. Number of Physical Processors
3. Number of Physical Cores
4. Processor Manufacturer
5. Processor type
6. Processor Model
7. Chasis Serial Number.

I tried the below command but it is not providing me above required information:

command: sudo xl info

Your help is highly appreciated.

Thanks,
Veerabhadra

---

### Post by TheFu on 2014-08-06
I don't know, but there is a manpage that should explain everything.

**man xl**

Normally, I would try to avoid telling someone to [RTFM]("http://en.wikipedia.org/wiki/RTFM") - but you're doing virtualization and need to know about manpages.

---

### Post by Veerabhadra_Kota on 2014-08-06
Hi,

Thanks for sharing the command. I went through this link "[http://xenbits.xen.org/docs/unstable/man/xl.1.html](http://xenbits.xen.org/docs/unstable/man/xl.1.html)" which is the same. But I don't find any command to retrieve the above required information. 

Thanks,
Veerabhadra

---

### Post by TheFu on 2014-08-07
I'm sorry - didn't read your post carefully enough.

To learn about the hardware on a physical system use the **sudo lshw** command.
The xl command is specific to setting up VMs.

Wouldn't know how to get the chassis serial number except to look for the tag on the back. In the linux world, we don't worry much about that stuff except the asset management guys. Certainly NOT for licensing.

---

