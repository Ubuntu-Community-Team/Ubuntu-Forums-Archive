---
title: "mounting iso"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by beew on 2011-11-06
Hi,

I have this 4.6 G iso which I somehow could not mount with the archive mounter. When I right click and choose open with archive mounter an icon appears but it is empty inside. 

On the other hand I can open the iso and browse the content with archive manager and it is definitely not empty. I can also mount it with furius iso mount and acetoneiso (a very nice app for manging isos btw)

I have tried to mount a few other isos (including some Linux live cd images) with the archive mounter and there was no problem. It seems that this iso is somehow special as far as the archive mounter is concerned.

Any idea? Thanks.

---

### Post by raja.genupula on 2011-11-06
[http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-mount-iso-images-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-mount-iso-images-in-ubuntu-linux/)

---

### Post by papibe on 2011-11-06
Hi beew.

What does the 'file' command tell you about the ISO? For example:
```
$ file ubuntu-11.04-server-i386.iso
ubuntu-11.04-server-i386.iso: # **ISO 9660** CD-ROM filesystem data 'Ubuntu-Server 11.04 i386       ' (bootable)

```
Regards.

---

### Post by beew on 2011-11-06
> **papibe said:**
> Hi beew.

What does the 'file' command tell you about the ISO? For example:
```
$ file ubuntu-11.04-server-i386.iso
ubuntu-11.04-server-i386.iso: # **ISO 9660** CD-ROM filesystem data 'Ubuntu-Server 11.04 i386       ' (bootable)

```Regards.

Hi

It says # ISO 9660 CD-ROM filesystem data

---

### Post by beew on 2011-11-06
> **raja.genupula said:**
> [http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-mount-iso-images-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-mount-iso-images-in-ubuntu-linux/)

Hi, 

I can mount it (acetoneiso, furius iso mount and command line all work), I am just wondering why archive mounter can't.

---

### Post by beew on 2011-11-07
Anyone?

---

### Post by beew on 2011-11-10
Re-extracted the iso (from a .rar) and tried it on Maverick. Same thing, mounting with the archieve mounter shows that content is empty, but mounting with acetoneiso and furius isomount shows all the content, as does simply opening with fille roller to browse the content.

---

### Post by MartyBuntu on 2011-11-10
Do you mind telling us what the ISO is and what you're looking to do with it?

---

### Post by beew on 2011-11-10
> **MartyBuntu said:**
> Do you mind telling us what the ISO is and what you're looking to do with it?

I just want to see the content. It consists of  data files. My problem is not that I can't mount and view it, like I said I could with the command line and other softwares,--without being root or anything fancy, just click and mount. I am  interested in finding out why I can't using the default method, it may be a bug in the file mounter.  I think the size may be the issue here as I can mount with the file mounter for smaller isos of various contents including programs such as Ubuntu live isos.

---

### Post by MartyBuntu on 2011-11-10
Why would strictly data files be in an ISO container?

---

### Post by beew on 2011-11-10
> **MartyBuntu said:**
> Why would strictly data files be in an ISO container?

I have no idea. It has some pictures and documents. But why should that matter?

---

### Post by MartyBuntu on 2011-11-10
> **beew said:**
> I have no idea. It has some pictures and documents. But why should that matter?

You can already mount the disk with acetoneiso. Why not just copy the data?
Problem solved.

---

### Post by beew on 2011-11-10
> **MartyBuntu said:**
> You can already mount the disk with acetoneiso. Why not just copy the data?
Problem solved.

The "problem" is not that I cannot access the data, I want to find out why archive mounter doesn't work and if others experience something similar. I try to determine if it is a bug on archive mounter's part.

---

