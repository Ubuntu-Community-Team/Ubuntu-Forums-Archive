---
title: "odd output from update"
date: 2018-03-03
forum: New to Ubuntu
---

### Post by micahpage on 2018-03-03
I just installed a fresh 16.04 LTS and when i run sudo apt-get update i get this...

```
sondra@ubuntu:~$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]            
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]             
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease               
Fetched 204 kB in 0s (248 kB/s)                              
*** Error in `appstreamcli': double free or corruption (fasttop): 0x0000000001a49b50 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x77725)[0x7f816af88725]
/lib/x86_64-linux-gnu/libc.so.6(+0x7ff4a)[0x7f816af90f4a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7f816af94abc]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_component_complete+0x439)[0x7f816b30cd19]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_data_pool_update+0x44a)[0x7f816b30df0a]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_cache_builder_refresh+0x1c2)[0x7f816b303272]
appstreamcli(ascli_refresh_cache+0x12e)[0x4049de]
appstreamcli(as_client_run+0x6fb)[0x403ceb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f816af31830]
appstreamcli(_start+0x29)[0x403519]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:06 17432626                           /usr/bin/appstreamcli
00607000-00608000 r--p 00007000 08:06 17432626                           /usr/bin/appstreamcli
00608000-00609000 rw-p 00008000 08:06 17432626                           /usr/bin/appstreamcli
00dbf000-02919000 rw-p 00000000 00:00 0                                  [heap]
7f8160000000-7f8160021000 rw-p 00000000 00:00 0 
7f8160021000-7f8164000000 ---p 00000000 00:00 0 
7f81656df000-7f8165715000 r-xp 00000000 08:06 17697647                   /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f8165715000-7f8165915000 ---p 00036000 08:06 17697647                   /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f8165915000-7f816591a000 r--p 00036000 08:06 17697647                   /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f816591a000-7f816591b000 rw-p 0003b000 08:06 17697647                   /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f816591b000-7f8165934000 r-xp 00000000 08:06 17826512                   /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f8165934000-7f8165b34000 ---p 00019000 08:06 17826512                   /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f8165b34000-7f8165b37000 r--p 00019000 08:06 17826512                   /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f8165b37000-7f8165b38000 rw-p 0001c000 08:06 17826512                   /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f8165b38000-7f8165b43000 r-xp 00000000 08:06 17826508                   /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7f8165b43000-7f8165d43000 ---p 0000b000 08:06 17826508                   /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7f8165d43000-7f8165d44000 r--p 0000b000 08:06 17826508                   /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7f8165d44000-7f8165d45000 rw-p 0000c000 08:06 17826508                   /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7f8165d45000-7f8166704000 r--p 00000000 08:06 17439521                   /usr/lib/locale/locale-archive
7f8166704000-7f8167fba000 r-xp 00000000 08:06 17441084                   /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7f8167fba000-7f81681b9000 ---p 018b6000 08:06 17441084                   /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7f81681b9000-7f81681ba000 r--p 018b5000 08:06 17441084                   /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7f81681ba000-7f81681bb000 rw-p 018b6000 08:06 17441084                   /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7f81681bb000-7f81681bf000 r-xp 00000000 08:06 6820373                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7f81681bf000-7f81683be000 ---p 00004000 08:06 6820373                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7f81683be000-7f81683bf000 r--p 00003000 08:06 6820373                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7f81683bf000-7f81683c0000 rw-p 00004000 08:06 6820373                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7f81683c0000-7f81684c8000 r-xp 00000000 08:06 6820259                    /lib/x86_64-linux-gnu/libm-2.23.so
7f81684c8000-7f81686c7000 ---p 00108000 08:06 6820259                    /lib/x86_64-linux-gnu/libm-2.23.so
7f81686c7000-7f81686c8000 r--p 00107000 08:06 6820259                    /lib/x86_64-linux-gnu/libm-2.23.so
7f81686c8000-7f81686c9000 rw-p 00108000 08:06 6820259                    /lib/x86_64-linux-gnu/libm-2.23.so
7f81686c9000-7f81686ea000 r-xp 00000000 08:06 6820256                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7f81686ea000-7f81688e9000 ---p 00021000 08:06 6820256                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7f81688e9000-7f81688ea000 r--p 00020000 08:06 6820256                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7f81688ea000-7f81688eb000 rw-p 00021000 08:06 6820256                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7f81688eb000-7f8168a6a000 r-xp 00000000 08:06 17441098                   /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7f8168a6a000-7f8168c6a000 ---p 0017f000 08:06 17441098                   /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7f8168c6a000-7f8168c7a000 r--p 0017f000 08:06 17441098                   /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7f8168c7a000-7f8168c7b000 rw-p 0018f000 08:06 17441098                   /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7f8168c7b000-7f8168c7f000 rw-p 00000000 00:00 0 
7f8168c7f000-7f8168c82000 r-xp 00000000 08:06 6820213                    /lib/x86_64-linux-gnu/libdl-2.23.so
7f8168c82000-7f8168e81000 ---p 00003000 08:06 6820213                    /lib/x86_64-linux-gnu/libdl-2.23.so
7f8168e81000-7f8168e82000 r--p 00002000 08:06 6820213                    /lib/x86_64-linux-gnu/libdl-2.23.so
7f8168e82000-7f8168e83000 rw-p 00003000 08:06 6820213                    /lib/x86_64-linux-gnu/libdl-2.23.so
7f8168e83000-7f8168e99000 r-xp 00000000 08:06 6820227                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f8168e99000-7f8169098000 ---p 00016000 08:06 6820227                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f8169098000-7f8169099000 rw-p 00015000 08:06 6820227                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f8169099000-7f816920b000 r-xp 00000000 08:06 17441544                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7f816920b000-7f816940b000 ---p 00172000 08:06 17441544                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7f816940b000-7f8169415000 r--p 00172000 08:06 17441544                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7f8169415000-7f8169417000 rw-p 0017c000 08:06 17441544                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7f8169417000-7f816941b000 rw-p 00000000 00:00 0 
7f816941b000-7f816944b000 r-xp 00000000 08:06 17441389                   /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7f816944b000-7f816964a000 ---p 00030000 08:06 17441389                   /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7f816964a000-7f816964b000 r--p 0002f000 08:06 17441389                   /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7f816964b000-7f816964c000 rw-p 00030000 08:06 17441389                   /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7f816964c000-7f8169840000 r-xp 00000000 08:06 17441749                   /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7f8169840000-7f8169a40000 ---p 001f4000 08:06 17441749                   /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7f8169a40000-7f8169a47000 r--p 001f4000 08:06 17441749                   /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7f8169a47000-7f8169a48000 rw-p 001fb000 08:06 17441749                   /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7f8169a48000-7f8169a65000 r-xp 00000000 08:06 17441803                   /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7f8169a65000-7f8169c65000 ---p 0001d000 08:06 17441803                   /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7f8169c65000-7f8169c66000 r--p 0001d000 08:06 17441803                   /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7f8169c66000-7f8169c67000 rw-p 0001e000 08:06 17441803                   /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7f8169c67000-7f8169e17000 r-xp 00000000 08:06 17441795                   /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7f8169e17000-7f816a016000 ---p 001b0000 08:06 17441795                   /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7f816a016000-7f816a01e000 r--p 001af000 08:06 17441795                   /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7f816a01e000-7f816a020000 rw-p 001b7000 08:06 17441795                   /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7f816a020000-7f816a021000 rw-p 00000000 00:00 0 
7f816a021000-7f816a028000 r-xp 00000000 08:06 17440789                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7f816a028000-7f816a227000 ---p 00007000 08:06 17440789                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7f816a227000-7f816a228000 r--p 00006000 08:06 17440789                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7f816a228000-7f816a229000 rw-p 00007000 08:06 17440789                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7f816a229000-7f816a240000 r-xp 00000000 08:06 6820341                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7f816a240000-7f816a440000 ---p 00017000 08:06 6820341                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7f816a440000-7f816a441000 r--p 00017000 08:06 6820341                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7f816a441000-7f816a442000 rw-p 00018000 08:06 6820341                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7f816a442000-7f816a444000 rw-p 00000000 00:00 0 
7f816a444000-7f816a463000 r-xp 00000000 08:06 6820347                    /lib/x86_64-linux-gnu/libselinux.so.1
7f816a463000-7f816a662000 ---p 0001f000 08:06 6820347                    /lib/x86_64-linux-gnu/libselinux.so.1
7f816a662000-7f816a663000 r--p 0001e000 08:06 6820347                    /lib/x86_64-linux-gnu/libselinux.so.1
7f816a663000-7f816a664000 rw-p 0001f000 08:06 6820347                    /lib/x86_64-linux-gnu/libselinux.so.1
7f816a664000-7f816a666000 rw-p 00000000 00:00 0 
7f816a666000-7f816a67f000 r-xp 00000000 08:06 6820380                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f816a67f000-7f816a87e000 ---p 00019000 08:06 6820380                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f816a87e000-7f816a87f000 r--p 00018000 08:06 6820380                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f816a87f000-7f816a880000 rw-p 00019000 08:06 6820380                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f816a880000-7f816a883000 r-xp 00000000 08:06 17440920                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7f816a883000-7f816aa82000 ---p 00003000 08:06 17440920                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7f816aa82000-7f816aa83000 r--p 00002000 08:06 17440920                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7f816aa83000-7f816aa84000 rw-p 00003000 08:06 17440920                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7f816aa84000-7f816aa9c000 r-xp 00000000 08:06 6820335                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7f816aa9c000-7f816ac9b000 ---p 00018000 08:06 6820335                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7f816ac9b000-7f816ac9c000 r--p 00017000 08:06 6820335                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7f816ac9c000-7f816ac9d000 rw-p 00018000 08:06 6820335                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7f816ac9d000-7f816aca1000 rw-p 00000000 00:00 0 
7f816aca1000-7f816ad0f000 r-xp 00000000 08:06 6820318                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7f816ad0f000-7f816af0f000 ---p 0006e000 08:06 6820318                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7f816af0f000-7f816af10000 r--p 0006e000 08:06 6820318                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7f816af10000-7f816af11000 rw-p 0006f000 08:06 6820318                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7f816af11000-7f816b0d1000 r-xp 00000000 08:06 6820189                    /lib/x86_64-linux-gnu/libc-2.23.so
7f816b0d1000-7f816b2d0000 ---p 001c0000 08:06 6820189                    /lib/x86_64-linux-gnu/libc-2.23.so
7f816b2d0000-7f816b2d4000 r--p 001bf000 08:06 6820189                    /lib/x86_64-linux-gnu/libc-2.23.so
7f816b2d4000-7f816b2d6000 rw-p 001c3000 08:06 6820189                    /lib/x86_64-linux-gnu/libc-2.23.so
7f816b2d6000-7f816b2da000 rw-p 00000000 00:00 0 
7f816b2da000-7f816b325000 r-xp 00000000 08:06 17440482                   /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7f816b325000-7f816b525000 ---p 0004b000 08:06 17440482                   /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7f816b525000-7f816b526000 r--p 0004b000 08:06 17440482                   /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7f816b526000-7f816b527000 rw-p 0004c000 08:06 17440482                   /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7f816b527000-7f816b579000 r-xp 00000000 08:06 17440944                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7f816b579000-7f816b778000 ---p 00052000 08:06 17440944                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7f816b778000-7f816b779000 r--p 00051000 08:06 17440944                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7f816b779000-7f816b77a000 rw-p 00052000 08:06 17440944                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7f816b77a000-7f816b8fa000 r-xp 00000000 08:06 17440906                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7f816b8fa000-7f816bafa000 ---p 00180000 08:06 17440906                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7f816bafa000-7f816bafe000 r--p 00180000 08:06 17440906                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7f816bafe000-7f816bb00000 rw-p 00184000 08:06 17440906                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7f816bb00000-7f816bb02000 rw-p 00000000 00:00 0 
7f816bb02000-7f816bc10000 r-xp 00000000 08:06 6820231                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7f816bc10000-7f816be10000 ---p 0010e000 08:06 6820231                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7f816be10000-7f816be11000 r--p 0010e000 08:06 6820231                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7f816be11000-7f816be12000 rw-p 0010f000 08:06 6820231                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7f816be12000-7f816be13000 rw-p 00000000 00:00 0 
7f816be13000-7f816be39000 r-xp 00000000 08:06 6820161                    /lib/x86_64-linux-gnu/ld-2.23.so
7f816bff1000-7f816c010000 r--s 00000000 08:06 17957138                   /usr/share/mime/mime.cache
7f816c010000-7f816c01e000 rw-p 00000000 00:00 0 
7f816c035000-7f816c038000 rw-p 00000000 00:00 0 
7f816c038000-7f816c039000 r--p 00025000 08:06 6820161                    /lib/x86_64-linux-gnu/ld-2.23.so
7f816c039000-7f816c03a000 rw-p 00026000 08:06 6820161                    /lib/x86_64-linux-gnu/ld-2.23.so
7f816c03a000-7f816c03b000 rw-p 00000000 00:00 0 
7ffe0a3ae000-7ffe0a3cf000 rw-p 00000000 00:00 0                          [stack]
7ffe0a3f5000-7ffe0a3f7000 r--p 00000000 00:00 0                          [vvar]
7ffe0a3f7000-7ffe0a3f9000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code


```

---

### Post by cruzer001 on 2018-03-03
That's an old bug.  Are you using an old copy of 16.04?

[https://www.google.com/search?client=firefox-b-1&source=hp&ei=56SaWsr8IMnOjwOtgKiwBA&q=Error+in+%60appstreamcli%27%3A+double+free+or+corruption&oq=Error+in+%60appstreamcli%27%3A+double+free+or+corruption&gs_l=psy-ab.3..0.4432.4432.0.7704.3.2.0.0.0.0.122.122.0j1.2.0....0...1c.2.64.psy-ab..1.2.243.6..35i39k1.122.7SZMN7nce3k](https://www.google.com/search?client=firefox-b-1&source=hp&ei=56SaWsr8IMnOjwOtgKiwBA&q=Error+in+%60appstreamcli%27%3A+double+free+or+corruption&oq=Error+in+%60appstreamcli%27%3A+double+free+or+corruption&gs_l=psy-ab.3..0.4432.4432.0.7704.3.2.0.0.0.0.122.122.0j1.2.0....0...1c.2.64.psy-ab..1.2.243.6..35i39k1.122.7SZMN7nce3k)

[https://askubuntu.com/questions/943463/library-corruption-error-during-apt-get-update/949722#949722](https://askubuntu.com/questions/943463/library-corruption-error-during-apt-get-update/949722#949722)

---

