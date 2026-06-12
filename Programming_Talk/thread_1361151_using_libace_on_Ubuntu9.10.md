---
title: "using libace on Ubuntu9.10"
date: 2009-12-21
forum: Programming Talk
---

### Post by stoval on 2009-12-21
Hi all,
 
I am trying to build an application using libace-5.6.3 but failed on Ubuntu9.10:
 
/usr/include/ace/OS_NS_dirent.inl:131: error: invalid conversion from 'int (*)(const void*, const void*)' to 'int (*)(const dirent**, const dirent**)'
/usr/include/ace/OS_NS_dirent.inl:131: error: initializing argument 4 of 'int scandir(const char*, dirent***, int (*)(const dirent*), int (*)(const dirent**, const dirent**))'
/usr/include/ace/OS_NS_dirent.inl: In function 'int ACE_OS::alphasort(const void*, const void*)':
/usr/include/ace/OS_NS_dirent.inl:152: error: invalid conversion from 'const void*' to 'const dirent**'
/usr/include/ace/OS_NS_dirent.inl:152: error: initializing argument 1 of 'int alphasort(const dirent**, const dirent**)'
/usr/include/ace/OS_NS_dirent.inl:152: error: invalid conversion from 'const void*' to 'const dirent**'
 
I searched and found [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=552899](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=552899)
It said the bug has been fixed on libace-5.6.3-6
 
apt said I alread have the latest verson, so what's the next step?
 
Thanks a lot for your help!
 
Stoval

---

### Post by flyingtux on 2010-01-08
Hi,
Same problem for me !
Can we install it from the debian testing repository or should we wait any update of the ubuntu repo !

is there a risk to include a debian repository in an ubuntu distro

regards,

Jean-Pierre

---

### Post by Zugzwang on 2010-01-08
> **flyingtux said:**
> Hi,
Same problem for me !
Can we install it from the debian testing repository or should we wait any update of the ubuntu repo !

is there a risk to include a debian repository in an ubuntu distro


Don't do it. Rather, download the .deb file of the new package version directly and install it using "sudo dpkg -i yourdebfile.deb". Do the same for the "-dev" package version. You may also want to uninstall the package before the next Ubuntu upgrade.

---

### Post by flyingtux on 2010-01-08
Thanks for answering,

I did :
  	 	 	 	 	 	  sudo dpkg -i libace-5.6.3_5.6.3-6_i386.deb
 sudo dpkg -i libace-dev_5.6.3-6_i386.deb
 sudo dpkg -i libace-doc_5.6.3-6_all.deb
 
and it works :-)

regards,

Jean-Pierre

---

