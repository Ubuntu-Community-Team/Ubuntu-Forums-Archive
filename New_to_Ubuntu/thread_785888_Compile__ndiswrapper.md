---
title: "Compile  ndiswrapper"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by hellomoto on 2008-05-07
ok i have read the HOWTO page on this and on 
got ndiswrapper to work on my old system but having upgraded am unable to compile ndiswrapper.

I compile it from source because i need the latest version to get my wifi card to work (having done this on the old system) and because I can't conect my ubuntu box to the net yet to do apt-get.

i get the following error when trying to compile:

```

mark@mark-desktop:~$ cd ndiswrapper-1.52
mark@mark-desktop:~/ndiswrapper-1.52$ sudo make
make -C driver
make[1]: Entering directory `/home/mark/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/mark/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/mark/ndiswrapper-1.52/driver/crt.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/hal.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/iw_ndis.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/loader.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/ndis.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/ntoskernel.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/ntoskernel_io.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/pe_linker.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/pnp.o
  CC [M]  /home/mark/ndiswrapper-1.52/driver/proc.o
/home/mark/ndiswrapper-1.52/driver/proc.c: In function &#8216;wrap_procfs_init&#8217;:
/home/mark/ndiswrapper-1.52/driver/proc.c:538: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/mark/ndiswrapper-1.52/driver/proc.c:538: error: (Each undeclared identifier is reported only once
/home/mark/ndiswrapper-1.52/driver/proc.c:538: error: for each function it appears in.)
/home/mark/ndiswrapper-1.52/driver/proc.c: In function &#8216;wrap_procfs_remove&#8217;:
/home/mark/ndiswrapper-1.52/driver/proc.c:565: error: &#8216;proc_net&#8217; undeclared (first use in this function)
make[3]: *** [/home/mark/ndiswrapper-1.52/driver/proc.o] Error 1
make[2]: *** [_module_/home/mark/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mark/ndiswrapper-1.52/driver'
make: *** [all] Error 2
mark@mark-desktop:~/ndiswrapper-1.52$ sudo make install
make -C driver install
make[1]: Entering directory `/home/mark/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/mark/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/mark/ndiswrapper-1.52/driver/proc.o
/home/mark/ndiswrapper-1.52/driver/proc.c: In function &#8216;wrap_procfs_init&#8217;:
/home/mark/ndiswrapper-1.52/driver/proc.c:538: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/mark/ndiswrapper-1.52/driver/proc.c:538: error: (Each undeclared identifier is reported only once
/home/mark/ndiswrapper-1.52/driver/proc.c:538: error: for each function it appears in.)
/home/mark/ndiswrapper-1.52/driver/proc.c: In function &#8216;wrap_procfs_remove&#8217;:
/home/mark/ndiswrapper-1.52/driver/proc.c:565: error: &#8216;proc_net&#8217; undeclared (first use in this function)
make[3]: *** [/home/mark/ndiswrapper-1.52/driver/proc.o] Error 1
make[2]: *** [_module_/home/mark/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mark/ndiswrapper-1.52/driver'
make: *** [install] Error 2
mark@mark-desktop:~/ndiswrapper-1.52$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
mark@mark-desktop:~/ndiswrapper-1.52$ 



```

Thankyou!

---

### Post by spiderbatdad on 2008-05-07
usually make is not run as root...make install is.

How about: ```
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by hellomoto on 2008-05-07
i can't really do any apt-get installs as the ubuntu box isn't able to connect to the net yet...

i will try run make not as root but wouldnt have thought it a problem if you did run it as root?

---

### Post by spiderbatdad on 2008-05-07
I believe you can install ndiswrapper-common ndiswrapper-utils-1.9 and ndisgtk all using the live cd as a source.

---

### Post by hellomoto on 2008-05-07
hmmm ty for your help, I will have a play and see were I get to!

---

### Post by miwaypet on 2008-05-07
I needed the ndiswrapper on my old machine (no hard line connection) and was surprised to find no ndiswrapper in the cd repos. So there are some work around's.

1) If you have the 7.10 disk, install and upgrade to 8.04.

2) Failing that, if you can get access to someone elses machine you have two options:

  a) if they are running ubuntu transfer the .deb packages from there file system to USB stick and then to your machine. I did this from laptop to old desktop. Opened file system (packages ndiswrapper-common and ndiswrapper-utils should be installed first) and did a search for ndiswrapper. It brought up the .deb packages.

  b) other machine is MS or MAC then go here: [ ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and download the packages for gutsy. Transfer to USB stick and install from that.

Best I've got. Hope it helps.

---

### Post by hellomoto on 2008-05-07
woop, got it working!  --- was there ever any doubt!

Now talking to you from the ubuntu box! 


I ended up fixing this problem by just using the synaptic package manager and getting ndiswrapper and utils off the hardy CD. many thanks

---

### Post by hellomoto on 2008-05-07
were has the solved option for threads gone?

---

