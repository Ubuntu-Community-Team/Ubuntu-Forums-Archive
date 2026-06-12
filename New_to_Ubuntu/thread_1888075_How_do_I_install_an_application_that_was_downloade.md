---
title: "How do I install an application that was downloaded as .tar.gz?"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by MooseMagnet on 2011-11-28
I downloaded gyachi-1.2.11.tar.gz

How do I install it?

Thanks

---

### Post by Elfy on 2011-11-28
Might be better using this - [http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html)

But if you prefer - [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by haqking on 2011-11-28
**First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

Or find a PPA.

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

### Post by MooseMagnet on 2011-11-28
Thanks tons!
Got it via forestpiskie's first link.

I knew there was an easier way other than compiling, etc. But wasn't able to find it.

I installed it so long ago, checked my notebook and those links were defunct.

But it's up and running again, and I appreciate your excellent direction.

Thank you !

---

### Post by haqking on 2011-11-28
> **MooseMagnet said:**
> Thanks tons!
Got it via forestpiskie's first link.

I knew there was an easier way other than compiling, etc. But wasn't able to find it.

I installed it so long ago, checked my notebook and those links were defunct.

But it's up and running again, and I appreciate your excellent direction.

Thank you !


Cool, yeah repos or PPA are always preferrable.

Glad you got it sorted.

Cheers

---

### Post by Elfy on 2011-11-28
wasn't sure if the ppa would _actually_ work (oh please not another failed update from a ppa :lol: )- the link being to a natty one, worked here so I assumed it would work for you too :p

---

