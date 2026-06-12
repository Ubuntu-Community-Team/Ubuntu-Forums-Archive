---
title: "gFTP or SFTP"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by slickuser on 2008-08-23
Which one support by Ubuntu for SFTP (graphically)?

I am having problem installing gFTP.

> ./configure
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Can't find config.log though. Any help?

Thanks.

---

### Post by wgrant on 2008-08-23
You can use SFTP or FTP simply by typing a URL in Nautilus, the usual file browser. I'd highly recommend using that.

But if you do really want to use gFTP, just open up Applications->Add/Remove, search for, and install it. Much simpler.

---

### Post by Nepherte on 2008-08-23
Filezilla is another great client that supports sftp as well.

---

### Post by cozmicharlie on 2008-08-23
I would use sftp myself.  See this thread for a good discussion and easy how to ([http://ubuntuforums.org/showthread.php?t=596917&highlight=ftp+server](http://ubuntuforums.org/showthread.php?t=596917&highlight=ftp+server)).  If you have a Windows machine on your network you can use Tunnelier ([http://www.scribd.com/doc/20503/Bitvise-Tunnelier-V3-60](http://www.scribd.com/doc/20503/Bitvise-Tunnelier-V3-60)) - very easy to set up.

The message you are getting looks to be a compiler problem.  Make sure you have "build essential" (from Synaptic) installed and GCC (which should already be installed).  You may need to read the documentation and see if you are missing any dependencies also.

Good luck

---

### Post by wgrant on 2008-08-23
> **cozmicharlie said:**
> *snip*

The message you are getting looks to be a compiler problem.  Make sure you have "build essential" (from Synaptic) installed and GCC (which should already be installed).  You may need to read the documentation and see if you are missing any dependencies also.

Or one could just use the package, like one is meant to...

---

### Post by qstraza on 2008-08-23
if you want to install from source than install gcc
```
apt-get install gcc
```
you will probably need other packages, you will see what you need while configuring.

---

### Post by Oldsoldier2003 on 2008-08-23
> **Nepherte said:**
> Filezilla is another great client that supports sftp as well.

+1 I like filezilla a lot especially in mixed windows/linux environments. Having a standard program across platforms makes life much easier.

---

### Post by billgoldberg on 2008-08-25
I just tried gFTP to download something from my laptop (using ssh) and it's easy to use and works well.

---

### Post by pyromanic123boom on 2008-08-25
You could try FireFTP addon for firefox. Not the best FTP client, but it is nice to keep everything inside one window.

---

