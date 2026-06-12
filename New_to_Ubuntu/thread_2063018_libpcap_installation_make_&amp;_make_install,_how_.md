---
title: "libpcap installation: make &amp; make install, how it works ,"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by xptional on 2012-09-26
Hi :), 

I tried to install the binary libpcap installation on my ubuntu, [http://www.tcpdump.org/#old-releases]("http://www.tcpdump.org/#old-releases") 
```
./configure 
``` works well,
but when I came to run the make command, its does not it show an error,
```
khan@khan:~/wireshark/libpcap-1.2.1$ make
VER=`cat ./VERSION`; \
	MAJOR_VER=`sed 's/\([0-9][0-9]*\)\..*/\1/' ./VERSION`; \
	gcc -shared -Wl,-soname,libpcap.so.$MAJOR_VER  \
	    -o libpcap.so.$VER pcap-linux.o pcap-usb-linux.o pcap-can-linux.o fad-getad.o pcap.o inet.o gencode.o optimize.o nametoaddr.o etherent.o savefile.o sf-pcap.o sf-pcap-ng.o pcap-common.o bpf_image.o bpf_dump.o  scanner.o grammar.o bpf_filter.o version.o   

```
I also tried to run as root but it does not work,
```
khan@khan:~/wireshark/libpcap-1.2.1$ sudo make
[sudo] password for khan: 
VER=`cat ./VERSION`; \
	MAJOR_VER=`sed 's/\([0-9][0-9]*\)\..*/\1/' ./VERSION`; \
	gcc -shared -Wl,-soname,libpcap.so.$MAJOR_VER  \
	    -o libpcap.so.$VER pcap-linux.o pcap-usb-linux.o pcap-can-linux.o fad-getad.o pcap.o inet.o gencode.o optimize.o nametoaddr.o etherent.o savefile.o sf-pcap.o sf-pcap-ng.o pcap-common.o bpf_image.o bpf_dump.o  scanner.o grammar.o bpf_filter.o version.o   
khan@khan:~/wireshark/libpcap-1.2.1$ 

```

I need this package to install the wireshark by source code. Not by command line . 
Thanks for your help§

---

### Post by xptional on 2012-09-26
Please you can also what is inside the directory of libpcap, as  below, 
I did not find any make file ... 

```
khan@khan:~/wireshark/libpcap-1.2.1$ ls
aclocal.m4        msdos                            pcap_findalldevs.3pcap           pcap_snapshot.3pcap
arcnet.h          nametoaddr.c                     pcap_freecode.3pcap              pcap-snf.c
atmuni31.h        nametoaddr.o                     pcap_geterr.3pcap                pcap-snf.h
bpf               net                              pcap_get_selectable_fd.3pcap     pcap-snit.c
bpf_dump.c        nlpid.h                          pcap.h                           pcap-snoop.c
bpf_dump.o        optimize.c                       pcap_inject.3pcap                pcap_stats.3pcap
bpf_filter.c      optimize.o                       pcap-int.h                       pcap_statustostr.3pcap
bpf_filter.o      org.tcpdump.chmod_bpf.plist      pcap_is_swapped.3pcap            pcap-stdinc.h
bpf_image.c       packaging                        pcap-libdlpi.c                   pcap_strerror.3pcap
bpf_image.o       pcap                             pcap_lib_version.3pcap           pcap-tstamp.manmisc
CHANGES           pcap.3pcap                       pcap-linktype.manmisc            pcap-tstamp.manmisc.in
chmod_bpf         pcap.3pcap.in                    pcap-linktype.manmisc.in         pcap_tstamp_type_name_to_val.3pcap
ChmodBPF          pcap_activate.3pcap              pcap-linux.c                     pcap_tstamp_type_val_to_name.3pcap
config.guess      pcap-bpf.c                       pcap-linux.o                     pcap-usb-linux.c
config.h          pcap-bpf.h                       pcap_list_datalinks.3pcap        pcap-usb-linux.h
config.h.in       pcap_breakloop.3pcap             pcap_list_datalinks.3pcap.in     pcap-usb-linux.o
config.log        pcap-bt-linux.c                  pcap_list_tstamp_types.3pcap     pcap-win32.c
config.status     pcap-bt-linux.h                  pcap_list_tstamp_types.3pcap.in  ppp.h
config.sub        pcap.c                           pcap_lookupdev.3pcap             README
configure         pcap-can-linux.c                 pcap_lookupnet.3pcap             README.aix
configure.in      pcap-can-linux.h                 pcap_loop.3pcap                  README.dag
CREDITS           pcap-can-linux.o                 pcap_major_version.3pcap         README.hpux
dlpisubs.c        pcap_can_set_rfmon.3pcap         pcap-namedb.h                    README.linux
dlpisubs.h        pcap_close.3pcap                 pcap-netfilter-linux.c           README.macosx
etherent.c        pcap-common.c                    pcap-netfilter-linux.h           README.septel
etherent.o        pcap-common.h                    pcap_next_ex.3pcap               README.sita
ethertype.h       pcap-common.o                    pcap-nit.c                       README.tru64
fad-getad.c       pcap_compile.3pcap               pcap-null.c                      README.Win32
fad-getad.o       pcap_compile.3pcap.in            pcap.o                           runlex.sh
fad-gifc.c        pcap-config                      pcap_offline_filter.3pcap        savefile.c
fad-glifc.c       pcap-config.1                    pcap_open_dead.3pcap             savefile.o
fad-null.c        pcap-config.in                   pcap_open_dead.3pcap.in          scanner.c
fad-sita.c        pcap_create.3pcap                pcap_open_live.3pcap             scanner.h
fad-win32.c       pcap-dag.c                       pcap_open_offline.3pcap          scanner.l
gencode.c         pcap-dag.h                       pcap_open_offline.3pcap.in       scanner.o
gencode.h         pcap_datalink.3pcap              pcap-pf.c                        sf-pcap.c
gencode.o         pcap_datalink.3pcap.in           pcap-savefile.manfile            sf-pcap.h
grammar.c         pcap_datalink_name_to_val.3pcap  pcap-savefile.manfile.in         sf-pcap-ng.c
grammar.o         pcap_datalink_val_to_name.3pcap  pcap-septel.c                    sf-pcap-ng.h
grammar.y         pcap-dlpi.c                      pcap-septel.h                    sf-pcap-ng.o
ieee80211.h       pcap-dos.c                       pcap_set_buffer_size.3pcap       sf-pcap.o
inet.c            pcap-dos.h                       pcap_set_datalink.3pcap          sunatmpos.h
inet.o            pcap_dump.3pcap                  pcap_setdirection.3pcap          SUNOS4
install-sh        pcap_dump_close.3pcap            pcap_setfilter.3pcap             tests
INSTALL.txt       pcap_dump_file.3pcap             pcap_setnonblock.3pcap           TODO
lbl               pcap_dump_flush.3pcap            pcap_set_promisc.3pcap           tokdefs.h
libpcap.a         pcap_dump_ftell.3pcap            pcap_set_rfmon.3pcap             VERSION
libpcap.so.1.2.1  pcap_dump_open.3pcap             pcap_set_snaplen.3pcap           version.c
LICENSE           pcap_dump_open.3pcap.in          pcap_set_timeout.3pcap           version.h
llc.h             pcap-enet.c                      pcap_set_tstamp_type.3pcap       version.o
Makefile          pcap_file.3pcap                  pcap_set_tstamp_type.3pcap.in    Win32
Makefile.in       pcap_fileno.3pcap                pcap-sita.c
missing           pcap-filter.manmisc              pcap-sita.h
mkdep             pcap-filter.manmisc.in           pcap-sita.html
khan@khan:~/wireshark/libpcap-1.2.1$ 

```

How could it be possible to install ? Thanks in advance for your suggestions.

---

### Post by drmrgd on 2012-09-26
I'm not sure I follow.  As you say, there were no errors running make, so you should be OK.  It looks like (from the INSTALL.txt file in that folder), that all you need to run next is:

```
sudo make install
```

to finish the build.  Seems there is a bunch of make and configure options, so you might have a second look to make sure you have everything in place.  But, try to run 'sudo make install' and see if you get any errors from there.  Often the build process is three steps (configure, make, and make install).

---

### Post by xptional on 2012-09-27
Thanks dmrdg, 

Now it has been installed with the follwoing command,
```
sudo make install
```

Now I have problem for wireshark installation. 

make does not work and also make install, ```
sudo make [CODE]
``` sudo make install[/CODE]
Output
> khan@khan:~/wireshark/wireshark-1.8.2$ sudo make
make: *** No targets specified and no makefile found.  Stop.
khan@khan:~/wireshark/wireshark-1.8.2$ sudo make install
make: *** No rule to make target `install'.  Stop.
khan@khan:~/wireshark/wireshark-1.8.2$

Please anyhelp ! Thanks in advance !

---

### Post by drmrgd on 2012-09-27
As the basic method is the same for source packages, there could be some details that are different.  The first thing to do is to look for a README or INSTALL file in the archive.  Usually that will outline the precise way they want you to build the package for your system.  I don't know much about that package, so I can't say exactly how to build it.  

I'll also say that the Wireshark package is in the Ubuntu repositories, and unless you have a specific reason for why you want a different version than what's available, it's always a better idea to install packages with the repositories rather than building from source.  Here are the details of the package:

```
Package: wireshark
Versions: 
1.6.7-1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
                  MD5: 205b792665989c3882b556e37286b93b
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
                  MD5: 205b792665989c3882b556e37286b93b


Reverse Depends: 
  wireshark:i386,wireshark
  wireshark-dbg,wireshark 1.6.7-1
  wireshark-common,wireshark 1.6.7-1
  python-scapy,wireshark
  chaosreader,wireshark
  bittwist,wireshark
Dependencies: 
1.6.7-1 - libc6 (2 2.15) libgdk-pixbuf2.0-0 (2 2.22.0) libglib2.0-0 (2 2.24.0) libgtk2.0-0 (2 2.18.0) libpango1.0-0 (2 1.14.0) libpcap0.8 (2 0.9.8) libportaudio2 (2 19+svn20101113) libwireshark1 (2 1.6.0-1) libwiretap1 (2 1.6.0-1) libwsutil1 (2 1.6.0-1) zlib1g (2 1:1.1.4) wireshark-common (5 1.6.7-1) ethereal (3 1.0.0-3) ethereal:i386 (3 1.0.0-3) ethereal (3 1.0.0-3) ethereal:i386 (3 1.0.0-3) wireshark:i386 (0 (null)) 
Provides: 
1.6.7-1 - 
Reverse Provides:
```

You can install it by just running:

```
sudo apt-get install wireshark
```

---

### Post by DanR01 on 2012-09-27
You seem to have installed libpcap.

Have you run ./configure to create the make file in the wireshark directory?

Also, running sudo checkinstall rather than sudo make install is probably better.

I agree that installing from the repos is probably better.

---

### Post by xptional on 2012-09-28
Thanks for your cooperations. 

I knew that we can install wireshark from ubuntu repositories. 

But I want to diagnose, why, I could not arrive to install by the source code ?? , 

Anyhow, I tried again to install by source code, but failed. 

Hence I successfully installed via 
```
sudo apt-get install wireshark
```

Thanks again for your suggestions & help.

---

### Post by drmrgd on 2012-09-28
No problem.  I completely understand the desire to understand how to compile packages from source.  It's a very good thing to know in the event that you do need to install a package that's not in the repos.  

In general, like I said, the first thing you should always do is to have a look through the source archive that you downloaded for a README or INSTALL text file.  These are almost always included and will outline exactly how to build a package with not only the default configurations, but also some custom configurations if your system requires it (or if you want something other than the default).  They will also outline any other packages or libraries that are required in order to get a successful build. 

Some times building a package requires you to run ./configure as the first step; sometimes (but not very often) this is not necessary.  I'm not sure if I got the same version as you, but I had a quick look at the source package for Wireshark v1.8.2, and there are OS specific README files in there, and an INSTALL file.  In the install file there are detailed instructions to help you make sure that you have a few packages already installed (Perl, GTK+ and GLib), some information on how to make sure the software will be compatible with libpcap and Tshark, and then detailed build instructions (in this case you do have to run ./configure followed by make and make install).  

In general it's a lot more difficult to build a package and can take a considerable amount of time and effort.  This is why most recommend just installing pre-built packages from the repositories, which will handle all of the dependency fulfillment and configuration for you.  However, with a little practice and careful reading, you can always build from source if you have to.

Hope that helps for future builds!

---

### Post by xptional on 2012-09-28
Thanks you so much again  drmrgd; for such a good explanation. ! 
Yes, Offcourse, it will help me for future for installation of any package.

---

