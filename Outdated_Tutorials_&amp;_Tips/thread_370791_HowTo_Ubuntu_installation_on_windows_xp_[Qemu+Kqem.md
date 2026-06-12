---
title: "HowTo: Ubuntu installation on windows xp [Qemu+Kqemu]"
date: 2007-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by pe3no on 2007-02-26
Hi,

This is my first post here - I'm Piotr from Poland :-)
Sometimes we do not have the possibility to install Ubuntu,
for example at work, where the companies usually use m$ :-(
I had this problem and would like to share with the others my HowTo.
It describes the installation of Qemu + Kqemu on xp.
Having such a virtual machine, we can install and run our favourite Ubuntu :-)
This also gave me the possibility of presenting Ubuntu to my colleagues.
I tested this Guide several times and it worked without any problem.

Best regards~~Piotrek~~pe3no.

___________________________________________________________________


To install Ubuntu in m$ windows xp environment, using virtual machine Qemu + Kqemu (accelerator module), you need to follow the instructions below.
Generally, you need to copy+paste the code (without "C:\q>" of course) into the "cmd" windows terminal and press {enter} :-)



1.  Run "cmd" windows terminal session:
     Start > Run... > cmd  > OK


2.  Create a directory for Qemu+Kqemu installation:
```
c:\Documents...\...>     mkdir c:\q
```

3.  Go to this directory:
```
c:\Documents...\...>      cd c:\q
```


4.  Click the link below and save wget into c:\q or in case of problems find wget.exe somere else, using Google:
    [http://users.ugent.be/~bpuype/cgi-bin/fetch.pl?dl=wget/wget.exe](http://users.ugent.be/~bpuype/cgi-bin/fetch.pl?dl=wget/wget.exe)


5.  Download free unzip, using one of the locations below (or find with Google) - into c:\q  directory:
```
c:\q>      wget -c http://stahlworks.com/dev/unzip.exe
```


6.  Download Qemu from one of the locations or find with Google, using file name:
```
c:\q>      wget -c http://www.h6.dion.ne.jp/~kazuw/qemu-win/qemu-0.9.0-windows.zip
```

7.  Unzip Qemu into c:\q directory, which will create a subfolder:
```
c:\q>      unzip qemu-0.9.0-windows.zip
```

8.  Download tar into c:\q directory:
```
c:\q>      wget -c http://heanet.dl.sourceforge.net/sourceforge/gnuwin32/tar-1.13-1-bin.zip
```

9. Download package needed for tar:
```
c:\q>      wget -c http://heanet.dl.sourceforge.net/sourceforge/gnuwin32/tar-1.13-1-dep.zip
```

10. Unzip tar and its dependencies:
```
c:\q>      unzip tar-1.13-1-bin.zip
c:\q>      unzip tar-1.13-1-dep.zip
```

11. Download Kqemu - accelerator module:
```
c:\q>      wget -c http://www.nongnu.org/qemu/kqemu-1.3.0pre11.tar.gz
```

12. Change tarball's name to simplify your tasks :-)
```
c:\q>      move kqemu-1.3.0pre11.tar.gz kqemu.tgz
``` 

13. Download free gzip/gunzip:
```
c:\q>      wget -c ftp://ftp.uni-freiburg.de/pub/pc/msdos/archivers/gzip124.exe
```

14. Unpack gzip:
```
c:\q>      gzip124.exe
```

15. Create gunzip command:
```
c:\q>      copy gzip.exe gunzip.exe
```

16. Uncompress Kqemu &#8211; kqemu.tar will be created:
```
c:\q>      gunzip kqemu.tgz
```

17. Unpack kqemu.tar, which was created in bin subdirectory:
```
c:\q>      c:\q\bin\tar xvf  kqemu.tar
```

18. Using m$ file manager rightclick the file below:
      c:\q\kqemu-1.3.0pre11\kqemu.inf


19. Choose "install".


20. Come back to cmd and run Kqemu device, using command:
```
c:\q\>      net start kqemu
```

21. Create a virtual Qemu hard drive - with a size of a DVD disk for example:
```
c:\q>      c:\q\qemu-0.9.0-windows\qemu-img create c:\q\hdd.img 4450M
```

22. Run installation process of Ubuntu (with 768 MB of RAM) on Qemu + Kqemu, using a virtual CD/DVD installation disk.
You need to download it from Ubuntu home page - e.g. from [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/6.10/release/ubuntu-6.10-dvd-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/6.10/release/ubuntu-6.10-dvd-i386.iso)
    Modify running parameters if you need &#8211; look into documentation or use Google - most of the parameters are intuitive:
```
c:\q\>      c:\q\qemu-0.9.0-windows\qemu -boot d &#8211;nics 1 &#8211;user-net -localtime &#8211;enable-audio -cdrom c:\ubuntu-6.10-dvd-i386.iso -hda c:\q\hdd.img -m 768 -L  c:\q\qemu-0.9.0-windows
```

23. Run the sistem after installation process has finished and enjoy your Ubuntu on windows :-) :-) :-)
```
c:\q\>      c:\q\qemu-0.9.0-windows\qemu -boot c &#8211;nics 1 &#8211;user-net -localtime &#8211;enable-audio -cdrom c:\ubuntu-6.10-dvd-i386.iso -hda c:\q\hdd.img -m 768 -L  c:\q\qemu-0.9.0-windows
```

24. For your convenience put Kqemu startup string into autostart:
    Start > Programs > Autostart > (Rightclick)&#8230; Create shortcut...> (Rightclick the shortcut created)&#8230; properties > target:
    c:\windows\system32\net.exe start kqemu

25. To check if accelerator kquemu is working do as follow:
    Press: CTRL + ALT + 2 inside the window of Qemu
    type: info kqemu {Enter}
    you should receive: "kqemu support: enabled for user code"
    To come back into the Virtual Machine press: CTRL + ALT + 1


USEFUL LINKS:

[http://qemu-forum.ipi.fi/](http://qemu-forum.ipi.fi/)
[http://mypcquickref.110mb.com/qemu.shtml](http://mypcquickref.110mb.com/qemu.shtml)
[http://www.knoppmythwiki.org/index.php?page=QEMU](http://www.knoppmythwiki.org/index.php?page=QEMU)

----------

TO DO:

TODO1: Migration to newer quemu: [http://homepage3.nifty.com/takeda-toshiya/qemu/qemu-0.12.2-windows.zip](http://homepage3.nifty.com/takeda-toshiya/qemu/qemu-0.12.2-windows.zip)

---

### Post by 3doff on 2010-12-09
Hi, Piotr!

Found your HOWTO useful.

Did you manage to run kqemu with most recent qemu version (0.13)?

Because I think kqemu support was disabled and now only kvm is supported which needs Intel-VT or AMD-V processor technology.

---

