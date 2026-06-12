---
title: "correctly using tar.gz files..."
date: 2011-11-04
forum: New to Ubuntu
---

### Post by WorldOfChaos 616 on 2011-11-04
Hi there ubuntu community, I have a begginer question on how to correctly install a tar.gz file. for example like flash player. I downloaded the tar file from the adobe website and extracted it to my desktop...however i am not sure on how to make the file install. any help or guidance on my current issue would be greatly appreciated. thanks clint clarkson

---

### Post by haqking on 2011-11-04
> **WorldOfChaos 616 said:**
> Hi there ubuntu community, I have a begginer question on how to correctly install a tar.gz file. for example like flash player. I downloaded the tar file from the adobe website and extracted it to my desktop...however i am not sure on how to make the file install. any help or guidance on my current issue would be greatly appreciated. thanks clint clarkson

First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

**Second for Flash, you should add the PPA and install via apt-get. or use [Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")**

You can also use Gdebi package installer or look at dpkg.

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set 

Have fun

Regards

haqking

---

### Post by oldos2er on 2011-11-04
Why not install flash from the repositories? ```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

You can install libflashplayer.so extracted from your tar.gz by copying it to /usr/lib/mozilla/plugins but you won't receive updates if you do it that way.

Yet another way to install flash is to click the FlashAid link in my sig.

---

### Post by WorldOfChaos 616 on 2011-11-04
thank you guys so much. I am not completely new to ubuntu. Just on certain installation issues. I am thinking that your guidance will help me to succeed. On a second thought. Every one starts out as a begginner. thanks clint clarkson

---

