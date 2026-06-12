---
title: "Why can I access windows files while I am on Ubuntu?"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by babas87 on 2013-03-14
Hello, I just downloaded and installed Ubuntu 12.10 today along side with windows 7 so it's a dual boot. But I have a concern. I switched mainly to Ubuntu because of lack of security in Windows. I have heard that when it's a dual boot, the 2 operating system are separated and can't connect with each other so I was really happy about that. Then while playing (looking around) with Ubuntu I noticed an icon on the bar to the left called "285 GB Volume". When I open it, it's exactly like my C: drive from windows 7 and I can access every file in windows like: Users, Windows, System 32, Downloads... Why is that? Is there a chance I may be infected by windows files? Or infected files from Ubuntu tranfer to windows. I looked online everywhere to see why there is a link between Windows and Linux on my system. I also saw that to see windows files in Ubuntu, I had to install or do something I am not sure but the thing is I never done any of those and it's there automatically. Can somebody help me? Thanks for your help!

---

### Post by itrogers on 2013-03-14
Linux is recognizing the partition on your hard drive which happens to contain a Windows operating system. Linux can read the partition, the folder structure, the files, etc on that Windows partition (NTFS).

The reason why Windows can't "see" the linux partition is because Windows doesn't handle the Ubuntu file system well by default since the addon.

Any virus made for Windows is exactly that, made for Windows. They corrupt the file system, registry, system folder, etc. The base of Linux is far more different than Windows in that any virus or insecurity made for Windows won't affect linux.

---

### Post by babas87 on 2013-03-14
Ok thanks for the quick reply. I have one more question: What anti-virus software do you recommend for linux (the best one)? Thanks

---

### Post by ManamiVixen on 2013-03-14
You don't need one. Linux has no viruses, The only reason why you would want antivirus for linux is in a case where you send files to Windows PC's.

---

### Post by babas87 on 2013-03-14
Thanks. Linux is great... :)

---

### Post by babas87 on 2013-03-14
I have another question. I hope that you don't get annoyed. I am getting used to the system and I saw online to never run as root. But how to know that I am running as root. I am the administrator of the machine (I am the only one using it), I am running as root? Thanks

---

### Post by 3rdalbum on 2013-03-15
If you don't log in with the username "root" then you are not running as root.

---

### Post by DiabolicalClaptrap on 2013-03-15
> **ManamiVixen said:**
> You don't need one. Linux has no viruses, The only reason why you would want antivirus for linux is in a case where you send files to Windows PC's.

True but I strongly advise keeping up to date on vulnerabilities and exploits. Don't always assume the community will catch everything. Look into programs like noscript and apparmor. bodhi.zazen typed an [excellent tutorial]("http://ubuntuforums.org/showthread.php?t=1008906") on the latter. Try to have an understanding of what IS out there. Just because Linux was built to be resistant to viruses doesn't mean it's impervious to other types of malicious of code. A good defense can only be as good as the user wants it to be. Just my 2 cents.

---

### Post by itrogers on 2013-03-15
> **babas87 said:**
> I have another question. I hope that you don't get annoyed. I am getting used to the system and I saw online to never run as root. But how to know that I am running as root. I am the administrator of the machine (I am the only one using it), I am running as root? Thanks

You may be an administrator but you are not the ultimate administrator known as root. Typically you'll run commands with root privileges using "sudo" in the command line. This is good for the operating system and is one of the reasons for its great security, unlike Windows where you pretty much have full admin access all the time.

---

### Post by coldraven on 2013-03-15
I think that I'm correct in saying that Ubuntu mounts any connected drives as "Media". If you plug in a USB drive or stick it automatically appears in the file manager.
You can edit a file called fstab so that your Windows drive does not appear but I would leave it as it is for the following reasons.
While using Ubuntu if you download a file or image that needs a Windows program you can just copy it to C:\Downloads or wherever and work on it next time you boot into Windows.
If you install Clam anti-virus in Ubuntu you can scan your Windows drive and any files that you download in Ubuntu.

---

### Post by Warren Hill on 2013-03-15
The first user user created on a system is an **administrator** not **root.**  If you want to prove to your self you are not root open a terminal by pressing CTRL+ALT+T and enter

```
fdisk -l
```

This command lists the drives and partitions on your computer but its a privileged command so if you are not **root** you will not get an error but the command will just return with out any data. Now to check if you are an **administrator** try

```
sudo fdisk -l
```

You should see much more information.

To understand this better I suggest you take a look at [this question on Ask Ubuntu]("http://askubuntu.com/questions/257948/how-can-i-get-root-like-permissions-so-i-can-download-stuff-from-the-software-ce/258177#258177")[URL="http://askubuntu.com/questions/257948/how-can-i-get-root-like-permissions-so-i-can-download-stuff-from-the-software-ce/258177#258177"]

[/URL]

---

### Post by Warren Hill on 2013-03-15
If you don't want to be able to see the contents of your Windows partition that's easy too.  Just provide us with the output of the following commands and we can advise what you need to do

```
sudo fdisk -l; mount | grep ^'/dev'; cat /etc/fstab
```

All you need to do is edit  **/etc/fstab** and we can advise what changes to make.

---

