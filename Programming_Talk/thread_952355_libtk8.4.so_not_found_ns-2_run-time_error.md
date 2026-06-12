---
title: "libtk8.4.so not found: ns-2 run-time error"
date: 2008-10-19
forum: Programming Talk
---

### Post by boz on 2008-10-19
I installed all of the dependencies for ns-2 individually, which include tcl/tk 8.4 (I probably could have used the debs, but oh well), otcl, and tclcl.  I checked out ns-2, nam-1, and xgraph anonymously from the CVS repository, and compiled ns-2 successfully.  Then I type ./ns and get the run-time error: 
```
./ns: error while loading shared libraries: libtk8.4.so: cannot open shared object file: No such file or directory
```
ldd reveals:
```
root@raziel:~/src/ns-2# ldd ns
	linux-gate.so.1 =>  (0xb7fc5000)
	libtk8.4.so => not found
	libtcl8.4.so => /usr/local/lib/libtcl8.4.so (0xb7f06000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7ef8000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e11000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7df9000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7df4000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7dcf000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7cdc000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7cd1000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b82000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b7f000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7b7c000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7b64000)
	/lib/ld-linux.so.2 (0xb7fc6000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b5f000)
```
And I've confirmed that the library is in the right place:
```
root@raziel:~/src/ns-2# ls /usr/local/lib/
libotcl.a     libtclstub8.4.a  python2.5     tk8.4
libtcl8.4.so  libtk8.4.so      tcl8.4        tkConfig.sh
libtclcl.a    libtkstub8.4.a   tclConfig.sh
```
Does anyone have any idea what's going on?  I'm still pretty new to development tools and troubleshooting on Linux.  Thanks in advance.

---

### Post by boz on 2008-10-19
Never mind.  If I exit from root user, the executable links to the library just fine.

---

