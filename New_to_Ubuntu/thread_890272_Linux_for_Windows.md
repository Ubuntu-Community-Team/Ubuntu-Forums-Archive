---
title: "Linux for Windows?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Gitanes on 2008-08-14
Hello everyone.  I'm a soon to be Ubuntu user.  Thus far I've only run Ubuntu in a virtual machine and I am gearing up for a full install.

I'm wondering if there is a Linux distribution out there with tools on it for dealing with a Windows partition - like BartPE - with anti-virus tools and a rootkit finder?

I've tried Insert, which came on a DVD that I got with _The Linux Bible_, but it didn't seem to find my Windows partition and I'm not sure that the chkrootkit would have worked with that file system anyway.

The problem with making a BartPE is that I've only an oem copy of Windows and it appears impossible to hack an oem into a BartPE disk.

Anyway, looking forward to leaving Windows and MS behind and have learned a lot from reading these forums already.

Thanks for any suggestions.

---

### Post by erickghint on 2008-08-14
Have you tried Knoppix?

---

### Post by jualin on 2008-08-14
The latest version of Ubuntu 8.04 (as of today) has NTFS support which will enable Linux to read and write the Windows partition just fine. Therefore any antivirus program that you run in Linux will be able to scan your Windows partition. I have used a program called ClamAv which runs on Linux and can scan your Windows Partition for viruses. I am not sure if this is what you are looking for. Good luck!

---

### Post by Gitanes on 2008-08-14
I have tried Knoppix (came with the Linux Bible DVD) though it didn't have a rootkit finder or anti-virus for Windows as I recall.  Yet, if I'm not mistaken Knoppix can be modified, like BartPE, by adding your own programs, etc.  I'm not sure if that would be beyond my level of ability at this point though.

---

### Post by jualin on 2008-08-14
> **Gitanes said:**
> I have tried Knoppix (came with the Linux Bible DVD) though it didn't have a rootkit finder or anti-virus for Windows as I recall.  Yet, if I'm not mistaken Knoppix can be modified, like BartPE, by adding your own programs, etc.  I'm not sure if that would be beyond my level of ability at this point though.

You should be able to install any programs on any Linux distribution using the "Package Managers" (something similar to Add and Remove in Windows). If your favorite distro doesn't include the program you like, you can always install it  later. In Ubuntu installing is very easy because it uses Synaptic Package Manager, which has a huge list of packages(programs) available for you to install with one click. And other programs such as Skype have their own Ubuntu packages ready to download and install with one click also. Hope this helps!

---

### Post by Gitanes on 2008-08-14
> **jualin said:**
> The latest version of Ubuntu 8.04 (as of today) has NTFS support which will enable Linux to read and write the Windows partition just fine. Therefore any antivirus program that you run in Linux will be able to scan your Windows partition. I have used a program called ClamAv which runs on Linux and can scan your Windows Partition for viruses. I am not sure if this is what you are looking for. Good luck!

Ah, maybe that's what I'll wind up doing then.  Makes sense, run a scan from my Ubuntu installation where I can install various programs.  Does chkrootkit do any good run against a Windows system though? Does it only find stuff in a Linux system?  Perhaps there's a rootkit finder for Windows?

---

### Post by jualin on 2008-08-14
I have never tried chkrootkit on Linux or Windows but I found this software online which claims to run on Windows NT and Higher.[Check it out]("http://www.rootkitfinder.com/rootkit_revealer.htm") to see if that's what you want. Maybe someone else can expand on my answer since I am not sure if chkrootkit checks both Windows and Linux.

---

### Post by jualin on 2008-08-14
Also check out this [link]("https://help.ubuntu.com/community/InstallingSecurityTools") which suggests other security tools that you can install on Ubuntu. Remember that when the [link]("https://help.ubuntu.com/community/InstallingSecurityTools") mentions installing a package, you need to open the Package Manager (Synaptic in Ubuntu) and search for the package name (chkrootkit for example) and then install it.

---

