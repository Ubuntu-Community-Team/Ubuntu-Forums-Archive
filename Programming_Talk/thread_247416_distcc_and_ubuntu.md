---
title: "distcc and ubuntu"
date: 2006-08-30
forum: Programming Talk
---

### Post by geothenes on 2006-08-30
Hi,

I'm trying to use distcc to do distributed compilation across two machines both running Ubuntu.  To set this up I did the following on both machines:
1. Installed distcc from the repository
2. Opened /etc/default/distcc, changed STARTDISTCC="false" to STARTDISTCC="true", and changed ALLOWEDNETS="127.0.0.1" to ALLOWEDNETS="127.0.0.1" "192.168.1.58" (or "192.168.1.57" on the other machine).
3.  Opened /etc/environment and added a line that says:
DISTCC_HOSTS="localhost 192.168.1.58" (or "localhost 192.168.1.57" on the 192.168.1.58 machine).
4. Rebooted

I checked on the 192.168.1.58 machine and found the distccd daemon is running as follows:
/usr/bin/distccd --pid-file=/var/run/distccd.pid --log-file=/var/log/distccd.log --daemon --allow 127.0.0.1 --allow 192.168.1.57 --listen 127.0.0.1
In fact, 4 copies of the same process are running simultaneously... I'm not sure why.

So now went to compile my code on the 192.168.1.57 machine.  I ran make with:
make -j4
but I got an error saying it was unable to write to remote machine so it was compiling locally.  Here is the relevant verbose output from distcc:

distcc[5751] (dcc_get_hostlist) read hosts from environment
distcc[5751] (dcc_parse_hosts) found localhost token "localhost"
distcc[5751] (dcc_parse_hosts) found tcp token "192.168.1.58"
distcc[5751] (dcc_lock_host) /home/guyi/.distcc/lock/cpu_localhost_0 is busy
distcc[5751] (dcc_lock_host) got cpu lock on 192.168.1.58 slot 0 as fd3
distcc[5751] (dcc_strip_dasho) result: cc -DatirsaLibOf_EXPORTS -g3 -Wall -fPIC -I/atr/BIAS -I/usr/include/libxml2 -I/usr/local/lib/wx/include/gtk2-ansi-debug-2.6 -I/usr/local/include/wx-2.6 -I/atr/vxl/binDebug/vcl -I/atr/vxl/src/vcl -I/atr/vxl/binDebug/core -I/atr/vxl/src/core -I/atr/fltk -I/atr/atr-src -I/atr/atr-src/util -I/atr/vxl/src/contrib -I/atr/vxl/binDebug/contrib -c /atr/atr-src/CFI_AAB_AAB.cxx
distcc[5751] (dcc_spawn_child) forking to execute: cc -DatirsaLibOf_EXPORTS -g3 -Wall -fPIC -I/atr/BIAS -I/usr/include/libxml2 -I/usr/local/lib/wx/include/gtk2-ansi-debug-2.6 -I/usr/local/include/wx-2.6 -I/atr/vxl/binDebug/vcl -I/atr/vxl/src/vcl -I/atr/vxl/binDebug/core -I/atr/vxl/src/core -I/atr/fltk -I/atr/atr-src -I/atr/atr-src/util -I/atr/vxl/src/contrib -I/atr/vxl/binDebug/contrib -E /atr/atr-src/CFI_AAB_AAB.cxx
distcc[5755] (dcc_increment_safeguard) setting safeguard: _DISTCC_SAFEGUARD=1
distcc[5751] (dcc_spawn_child) child started as pid5755
distcc[5751] (dcc_strip_local_args) result: cc -g3 -Wall -fPIC -o CMakeFiles/atirsaLibOf.dir/CFI_AAB_AAB.o -c /atr/atr-src/CFI_AAB_AAB.cxx
distcc[5751] exec on 192.168.1.58: cc -g3 -Wall -fPIC -o CMakeFiles/atirsaLibOf.dir/CFI_AAB_AAB.o -c /atr/atr-src/CFI_AAB_AAB.cxx
distcc[5751] (dcc_note_state) note state 2, file "CFI_AAB_AAB.cxx", host "192.168.1.58"
distcc[5751] (dcc_connect_by_name) connecting to 192.168.1.58 port 3632
distcc[5751] (dcc_connect_by_addr) started connecting to 192.168.1.58:3632
distcc[5751] (dcc_select_for_write) select for write on fd4
distcc[5751] (dcc_note_state) note state 4, file "(NULL)", host "(NULL)"
distcc[5751] (dcc_x_token_int) send DIST00000001
distcc[5751] (dcc_writex) ERROR: failed to write: Connection refused
distcc[5751] (dcc_note_state) note state 3, file "(NULL)", host "(NULL)"


I've been trying to troubleshoot this now for several hours with no luck.  ](*,).  Any help would be appreciated.

Thanks,
Guy

---

### Post by hil on 2006-09-06
Have you checked your opened ports on the other machine? Use nmap to scan the other machine
```
nmap -v -sT 192.168.1.58
```
Run iptables on the other machine
```
sudo iptables -L
```
My ubuntu by default has iptables not loaded to the kernel.

Check if distcc has some test cases to troubleshoot your connection problem. Have you read about [gentoo distcc]("http://ubuntuforums.org/showthread.php?t=83186")?

---

### Post by hil on 2006-09-09
The distcc in ubuntu needs special care. It's difficult to configure it. I finally have 2 ubuntu PCs and 1 xubuntu PC running distcc successfully after 2 hours of stressed configuration. Here are some tips:

[LIST]
[*]/etc/default/distcc
Make sure you have the following 3 lines in the file. 192.168.12.0/24 should be replaced with the network where you have the compile servers running.
STARTDISTCC="true"
ALLOWEDNETS="127.0.0.1 192.168.12.0/24"
LISTENER=""
[*]~/.distcc/hosts
The file should have a list of hostnames for the compile servers seperated by new lines. Here is an example:
192.168.12.2
192.168.12.12
[/LIST]
Run a test to compile a program such as [gdm]("http://ftp.gnome.org/pub/GNOME/sources/gdm")
```
time make -j 3 CC=distcc >make.log
```
reference: [http://wiki.vpslink.com/index.php?title=HOWTO:_Install/Configure_Distcc](http://wiki.vpslink.com/index.php?title=HOWTO:_Install/Configure_Distcc)

---

