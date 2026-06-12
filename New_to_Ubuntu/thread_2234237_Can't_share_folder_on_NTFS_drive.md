---
title: "Can't share folder on NTFS drive"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by ian49 on 2014-07-13
I have a PC running Ubuntu 14.04 on an SSD as primary drive along with a Win 7 VM installed on the same drive. I also have a secondary (sdb1) drive which is NTFS so that both my Ubuntu host and my Win 7 VM can write to it. That's all working fine but despite various different attempts to get it working I can't get one of the folders on the NTFS drive to be shared on my local network such that my laptop also running Ubuntu 14.04 can have read/write access to it. I had assumed it was something to do with permissions and had tinkered with fstab but still can't get the folder to be shared. Can anyone help?

---

### Post by yancek on 2014-07-13
Is the second drive with the ntfs partition an internal drive on the PC or an external permanently attached to that PC?  Or is it an external drive which you plug in to the laptop and can't access it.  If the latter, it is likely a permissiions issue.  If the former, you need to install nfs on both, server on the PC and client on the laptop.  An explanation and details on installing are at the link below: 

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

---

### Post by ian49 on 2014-07-13
> **yancek said:**
> Is the second drive with the ntfs partition an internal drive on the PC or an external permanently attached to that PC?  Or is it an external drive which you plug in to the laptop and can't access it.  If the latter, it is likely a permissiions issue.  If the former, you need to install nfs on both, server on the PC and client on the laptop.  An explanation and details on installing are at the link below: 

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

Thanks for responding.

The second drive is internal.

I did take a look at the link you provided but it was too detailed for me to make any sense of. I have to admit that I wasn't expecting it to be so complex so now I'm wondering if there's a different approach I can take to avoid this problem. What I want to do is as follows:

I have a primary 120GB SSD with Ubuntu 14.04 and a Win 7 VM installed.

I want the Ubuntu host and the VM to be able to read and write to a shared folder on a secondary internal HDD.

I also want this shared folder on the secondary HDD to be available to my laptop via the network, also running Ubuntu.

It was suggested that I should make the secondary HDD NTFS so that the Win 7 VM could make use of it.

Is there a better way of doing this?

---

