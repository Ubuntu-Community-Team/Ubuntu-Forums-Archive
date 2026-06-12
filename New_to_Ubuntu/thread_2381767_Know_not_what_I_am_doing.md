---
title: "Know not what I am doing"
date: 2018-01-05
forum: New to Ubuntu
---

### Post by steven_scott on 2018-01-05
A couple of years ago, I partitioned this hard drive and successfully installed ubuntu 14.04 and allowed windows vista to reside in other partition. Then, when I booted, I would be asked which OS I wanted to load. It became necessary for me to install that drive into this computer which worked fine. However, I have encountered the following 2 problems. (Please note, I am not a tech guru and have no coding or programming experience, but I want to learn)

Problem 1: I cannot recall my authentication password. When I have tried to change passwd on the "terminal it asks for current passwd, which I do not have. Also I have tried "Recovery" and tried to change passwd, I get "authentication token error". Please guide me through the steps to fix this problem.

Problem 2: I can not access the vista partition and do not have installation disk or recovery disk. How can I solve that problem?

Thank You

---

### Post by sudodus on 2018-01-05
I suggest that you download a current version of Ubuntu (for example 16.04 LTS) and create a USB boot pendrive or DVD boot disk (maybe using another computer), and boot this computer into a live session. 

If the partitions of Ubuntu and Windows Vista are not mounted automatically, you can mount them manually with **mount**.

```

sudo mkdir /mnt/mp1
sudo mkdir /mnt/mp2
...
sudo mount /dev/sdxm /mnt/mp1
sudo mount /dev/sdyn /mnt/mp2

```

where x & y are drive letters and m & n are partition numbers, for example

```
sudo mount /dev/sda1 /mnt/mp1
```

If this works, you can save your personal files (anything that you want to keep), for example to an external drive or an internet cloud service.

Otherwise, ask for more help to access the files that you want to save.

Finally, you can install the current version of Ubuntu and forget about the old operating systems ;-)

---

### Post by Autodave on 2018-01-05
*Finally, you can install the current version of Ubuntu and forget about the old operating systems :wink:*

I agree: 14.04 is getting old and Vista is beyond old. IF there is a program in Vista that you can't live without, it will probably run under WINE in 16.04.

Also, since that machine has Vista on it, I am assuming that it is quite old and therefor you may want to consider a lighter version such as Xubuntu.

                        Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by Impavidus on 2018-01-05
> **steven_scott said:**
> 
Problem 1: I cannot recall my authentication password. When I have tried to change passwd on the "terminal it asks for current passwd, which I do not have. Also I have tried "Recovery" and tried to change passwd, I get "authentication token error". Please guide me through the steps to fix this problem.
Have you seen this link? [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
You probably missed that you have to remount the file system in read-write mode.
> 
Problem 2: I can not access the vista partition and do not have installation disk or recovery disk. How can I solve that problem?

In Linux it's usually no problem to move a hard drive from one computer to another, it still works (although proprietary drivers may make it a bit harder). Windows is not so easy. You probably can't boot Vista, but you should be able to access the Vista partition from Ubuntu to read or backup files. If the filesystem is unclean, you may have to add the -o ro option to the mount command:```
sudo mount -o ro /dev/sda1 /mnt/mp1
```

Ubuntu 14.04 LTS still has more than a year of support left, but is getting a bit old by now. Support for Windows Vista has ended. If you want Windows, you have to buy a Windows installation disk.

---

### Post by sudodus on 2018-01-05
> **Autodave said:**
> Also, since that machine has Vista on it, I am assuming that it is quite old and therefor you may want to consider a lighter version such as Xubuntu.

+1 for a lighter version such as **Xubuntu**.

There are also **Lubuntu**, **Ubuntu Budgie** and **Ubuntu MATE**. All these community flavours of Ubuntu have a lighter desktop environment and some lighter installed application programs than standard Ubuntu.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Impavidus on 2018-01-05
> **Autodave said:**
> *...* consider a lighter version such as Xubuntu.

                        Every 2 years, a long term service release is made. These LTSs have a service life of 5 years...

But the LTS releases of Xubuntu only live for 3 years. I don't know about all the other light flavours.

---

### Post by sudodus on 2018-01-05
Lubuntu LTS is also 3 years. I think all community flavours promise 3 years of support for LTS releases.

---

