---
title: "Trying to install Sense Board software for OU course, tracking dependencies?"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by t-julian101 on 2014-02-02
Hi all,

I used to be prehaps an intermediate Linux user (at a push) but have not been using Linux for sometime and seem to have returned to rank of newbie. I'm trying to install a peice of software on my Ubuntu 13.10 system. I seem to have run into some Dependency issues.

Rather than try and explain the suitation I'll give you the instructions, what I did and show the CL input and output. I should also mention there is a link for 'easy' 
download that opens in the software center however I can't install as "Dependency is not satisfiable: ia32-libs."

Instructions:

For the 64-bit option,  click the file name and the package installer  will launch and go through the installation process. This should take no  more than two minutes at most.

as mentioned above software center can't install.

Instructions for a manual install are as follows:

Download Zip file //I did and put it in documents.

As root:
unzip /path/to/sense-linux-install-b137.zip -d / 
chmod a+rx /usr/bin/sense.sh 
chmod a+rx /usr/bin/scratch_squeak_vm 
chmod a+rwx /usr/lib/Sense

had no problem


**Ubuntu additional steps**

Ubuntu 11.04 and later require two more packages to be installed. Give the command:
sudo apt-get install libssh2-1 libcurl3

Ubuntu 11.10 and later require an old version of libssl to be installed. Give the command:
sudo apt-get install libssl0.9.8

again followed with no problems.


You can now run Sense with 
/usr/bin/sense.sh

Didn't work.

```
tom@tom-HP-Pavilion-g6-Notebook-PC:~/Documents$ sudo /usr/bin/sense.sh
```


If Sense doesn&#8217;t work properly, try checking that all the plug-ins have their correct dependencies installed. Do

ldd /usr/lib/Sense/* | grep 'not found'

If any libraries are reported as not found, install them. You&#8217;ll need to find what they are.
As  more Linux distributions adopt OpenSSL 1.0 (and later), they&#8217;ll need to  be patched to pretend to OpenSSL 0.9.8 libraries, as above. If your  /usr/lib/libssl and /lib/libcrypto libraries are different versions than  1.0.0e, but still above 0.9.8, modify the instructions above.





```
tom@tom-HP-Pavilion-g6-Notebook-PC:~/Documents$ ldd /usr/lib/Sense/* | grep 'not found'
    libcurl.so.4 => not found
    libssl.so.0.9.8 => not found
    libssh2.so.1 => not found
    libcrypto.so.0.9.8 => not found
ldd: /usr/lib/Sense/Help: not regular file
ldd: /usr/lib/Sense/Media: not regular file
    libasound.so.2 => not found
ldd: /usr/lib/Sense/Projects: not regular file
ldd: /usr/lib/Sense/Sprites: not regular file
    libpangocairo-1.0.so.0 => not found
    libpango-1.0.so.0 => not found
    libcairo.so.2 => not found
    libgobject-2.0.so.0 => not found
    libgmodule-2.0.so.0 => not found
    libglib-2.0.so.0 => not found
    libXrender.so.1 => not found
    libSM.so.6 => not found
    libICE.so.6 => not found
    libasound.so.2 => not found
    libasound.so.2 => not found
    libpulse-simple.so.0 => not found
    libpulse.so.0 => not found


```

Thanks for reading, any help is greatly appreciated.

---

### Post by tgalati4 on 2014-02-02
ia32-libs is needed for running 32-bit software on a 64-bit installation.  

Open a terminal and see what is available for your distro:

```
apt-cache search ia32
```

---

### Post by t-julian101 on 2014-02-03
Its meant to be a 64-bit download. But I did try this. If I'm not mistaken nothing is relevent?

tom@tom-HP-Pavilion-g6-Notebook-PC:~$ apt-cache search ia32
grub-efi-ia32-dbg - GRand Unified Bootloader, version 2 (EFI-IA32 debug files)
grub-efi - GRand Unified Bootloader, version 2 (dummy package)
grub-efi-ia32 - GRand Unified Bootloader, version 2 (EFI-IA32 version)
grub-efi-ia32-bin - GRand Unified Bootloader, version 2 (EFI-IA32 binaries)
lsb-core - Linux Standard Base 4.1 core support package
lsb-cxx - Linux Standard Base 4.1 C++ support package
lsb-desktop - Linux Standard Base 4.1 Desktop support package
lsb-graphics - Linux Standard Base 4.1 graphics support package
lsb-languages - Linux Standard Base 4.1 Runtime Languages package
lsb-multimedia - Linux Standard Base 4.1 Multimedia package
lsb-printing - Linux Standard Base 4.1 Printing package
lsb-security - Linux Standard Base 4.1 Security package
microcode.ctl - Intel IA32/IA64 CPU Microcode Utility (transitional package)
primus-libs-ia32 - Shared libraries for primus (32-bit)
elilo - Bootloader for systems using EFI-based firmware
refit - graphical boot menu for ia32 and x64 EFI systems

---

