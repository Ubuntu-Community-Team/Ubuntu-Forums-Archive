---
title: "How do I install compressed downloads"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by gpaul856 on 2011-11-25
This has to have been asked before, but I'll ask it again. How do I install compressed downloads. Can I use Synaptic Package Manager for installing compressed / downloaded programs?

---

### Post by haqking on 2011-11-25
> **gpaul856 said:**
> This has to have been asked before, but I'll ask it again. How do I install compressed downloads. Can I use Synaptic Package Manager for installing compressed / downloaded programs?

First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

You can also use Gdebi package installer or look at dpkg.

If you have to download it as a package (compressed) it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

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

### Post by sudodus on 2011-11-25
Normally in Ubuntu, software is installed from repositories with a command line from a terminal window for example
```
sudo apt-get install vlc
``` or from ***synaptic*** or ***software-center***  which are graphical user interfaces to apt-get. When you install this  way, you will also receive offers to update the software in the same way  as all system updates.

So if you have an internet connection, I strongly recommend that you use  this normal method to install programs. Use the manual download and  install (and if necessary compile) method only for programs that are not  included in the repositories or if you have no internet connection to  your computer.

---

### Post by gpaul856 on 2011-11-25
Thanks for helping. I did download a program that included README and INSTALL instructions, but I could not get it to work for me.

---

### Post by sudodus on 2011-11-25
> **gpaul856 said:**
> Thanks for helping. I did download a program that included README and INSTALL instructions, but I could not get it to work for me.
What program is it; can you find it in the repositories (for example browse with Synaptic)?

---

### Post by Frogs Hair on 2011-11-25
Some of the the programs in software center for decompressing archives are listed below . When installed they work as part of the file roller and the right click extract here option will usually open them . Installation method depends on the file type of the extracted archive  .

7zip - Handles multiple file types .
Zip 
RAR .rar files
Ark

---

