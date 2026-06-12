---
title: "clamTK Help! please"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by candive on 2008-06-08
Hi all,

1.) do I have 4 infections according to Terminal??
2.) Is my clamTK up to date??
3.) How do I update? ("clamav-freshclam")
4.) Is my version the most recent & Stable.
5.) Am I Missing Anything??

Thank you.

chris@chris-laptop:~$ su 
Password: 
root@chris-laptop:/home/chris# clamav-getfiles 
/home/chris/clamav-data 
clamav-freshclam 
LibClamAV Error: Database Directory: clgf.nz8109 not locked 
connect(): No such file or directory 
-------------------------------------- 
ClamAV update process started at Sun Jun  8 09:43:08 2008 
WARNING: Your ClamAV installation is OUTDATED! 
WARNING: Local version: 0.92.1 Recommended version: 0.93 
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) 
Downloading main.cvd [100%] 
main.cvd updated (version: 46, sigs: 231834, f-level: 26, builder: sven) 
Downloading daily.cvd [100%] 
daily.cvd updated (version: 7402, sigs: 78179, f-level: 26, builder: guitar) 
Database updated (310013 signatures) from db.local.clamav.net (IP: 24.215.0.24) 
WARNING: Clamd was NOT notified: Can't connect to clamd through /var/run/clamav/clamd.ctl 
/usr/bin/clamscan -d /home/chris/clamav-data --recursive /usr/share/clamav-testfiles 
LibClamAV Warning: RAR code not compiled-in 
/usr/share/clamav-testfiles/clam-v3.rar: OK 
/usr/share/clamav-testfiles/clam.exe.bz2: ClamAV-Test-File FOUND 
/usr/share/clamav-testfiles/clam.zip: ClamAV-Test-File FOUND 
/usr/share/clamav-testfiles/clam.exe: ClamAV-Test-File FOUND 
LibClamAV Warning: RAR code not compiled-in 
/usr/share/clamav-testfiles/clam-v2.rar: OK 
/usr/share/clamav-testfiles/clam.cab: ClamAV-Test-File FOUND 

----------- SCAN SUMMARY ----------- 
Known viruses: 309171 
Engine version: 0.92.1 
Scanned directories: 1 
Scanned files: 6 
Infected files: 4 
Data scanned: 0.00 MB 
Time: 5.037 sec (0 m 5 s) 
Wrong number (4/5) of 'infected' files detected while scanning clamav test files 
Test of newly created database failed 
root@chris-laptop:/home/chris# clamav-freshclam 
root@chris-laptop:/home/chris#

---

### Post by Rhubarb on 2008-06-08
Somehow I don't think ClamAV-Test-File is actually a virus.
Looks to me it's a dummy virus used to make sure your AV is functioning properly.

---

### Post by the_doc on 2008-06-08
> **Rhubarb said:**
> Somehow I don't think ClamAV-Test-File is actually a virus.
Looks to me it's a dummy virus used to make sure your AV is functioning properly.

That's exactly what it is.

---

### Post by the_doc on 2008-06-08
AFAIK freshclam updates the virus definition database, that text dump you posted claims that the installation is out of date, so no you aren't running the most recent version.  Also ClamAV is mostly used for e-mail scanning on mail gateways and so may not be the best choice for desktop use.

---

### Post by bumanie on 2008-06-08
No you do not have the latest build - the latest build is 0.93. You can download the latest from the clamav site and compile it.

Known viruses: 309171 
Engine version: 0.92.1 
Scanned directories: 1 
Scanned files: 6 
[COLOR="Red"]Infected files: 4 [/COLOR]
[COLOR="Blue"]Data scanned: 0.00 MB [/COLOR]
Although it sys there are [COLOR="Red"]4 files infected[/COLOR], it also says [COLOR="Blue"]0mb [/COLOR]scanned - confused.

If you want to compile, I can probably help. I recently did the same on a friends ubuntu as well as my own. Have you done any compiling before? If not, to start with > sudo apt-get install build-essential - it is a "C" compiler that you will need. If you don't want to compile, go to synaptic and highlight entries to clamav and read the description, you may find what you are missing to allow the "LibClamAV Warning: RAR code not compiled-in" message to stop. I have no idea what it means - may be someone else will and we can both learn!
 
> Downloading main.cvd [100%] 
main.cvd updated (version: 46, sigs: 231834, f-level: 26, builder: sven) 
Downloading daily.cvd [100%] 
daily.cvd updated (version: 7402, sigs: 78179, f-level: 26, builder: guitar) 
Database updated (310013 signatures) from db.local.clamav.net (IP: 24.215.0.24)The above entry indicates that clamav updated successfully.

---

### Post by candive on 2008-06-08
Bumanie, that is what I thought.
I will try later. (family)
Thank you to everyone.

---

### Post by candive on 2008-06-12
Bumanie,

Anytime you want to start with the install and update of clam.

Thank you.

---

### Post by bumanie on 2008-06-12
Hi candive, I'm at work on a windows computer at present, but that shouldn't be too much of a deterent to a successful clamav0.93.1 installation. If you have not already done so, install build-essential > sudo apt-get install build-essential Next go [here]("http://www.clamav.net/download/sources") which should refer you to a local download mirror. Download to desktop then right click and choose 'extract here'. there are two library files that you will probably need, but I can'rt remember the name of them off the top of my head, but they will be mentioned in an error message - so it's no real hassle really. After extracting in terminal > cd ~/Desktop > cd <name of package> (exactly what the extracted file reads. > ./configure At the end of the terminal read out there will be an error saying one ofr two files/libraries are missing - look them up in synaptic and install them. Then return to terminal repeat the above > cd ~/Desktop > cd clamav <package name> > ./configure it should compile this time. Then > [QUOTE]make then > sudo make install[/QUOTE]. Post back when you have done that. Before clam will work you have to edit two directories.

---

### Post by candive on 2008-06-12
Now that was fun! :guitar:
Where Do You Learn All These Cool Commands is there a place on the internet with all the commands and what they do?
Thank you

By the way first page of instructions completed.:)
I feel like a kid in a candy store.

---

### Post by candive on 2008-06-12
So now,
"Before clam will work you have to edit two directories."

/clamav-0.93.1/test' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1' 
make[2]: Nothing to be done for `all-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1' 
chris@chris-laptop:~/Desktop/clamav-0.93.1$ sudo make install 
[sudo] password for chris: 
Making install in libclamunrar 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar' 
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib" 
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libclamunrar.la' '/usr/local/lib/libclamunrar.la' 
/usr/bin/install -c .libs/libclamunrar.so.4.0.3 /usr/local/lib/libclamunrar.so.4.0.3 
(cd /usr/local/lib && { ln -s -f libclamunrar.so.4.0.3 libclamunrar.so.4 || { rm -f libclamunrar.so.4 && ln -s libclamunrar.so.4.0.3 libclamunrar.so.4; }; }) 
(cd /usr/local/lib && { ln -s -f libclamunrar.so.4.0.3 libclamunrar.so || { rm -f libclamunrar.so && ln -s libclamunrar.so.4.0.3 libclamunrar.so; }; }) 
/usr/bin/install -c .libs/libclamunrar.lai /usr/local/lib/libclamunrar.la 
/usr/bin/install -c .libs/libclamunrar.a /usr/local/lib/libclamunrar.a 
chmod 644 /usr/local/lib/libclamunrar.a 
ranlib /usr/local/lib/libclamunrar.a 
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/local/lib 

If you ever happen to want to link against installed libraries 
in a given directory, LIBDIR, you must either use libtool, and 
specify the full pathname of the library, or use the `-LLIBDIR' 
flag during linking and do at least one of the following: 
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable 
     during execution 
   - add LIBDIR to the `LD_RUN_PATH' environment variable 
     during linking 
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag 
   - have your system administrator add LIBDIR to `/etc/ld.so.conf' 

See any operating system documentation about shared libraries for 
more information, such as the ld(1) and ld.so(8) manual pages. 
---------------------------------------------------------------------- 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar' 
Making install in libclamunrar_iface 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar_iface' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar_iface' 
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib" 
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libclamunrar_iface.la' '/usr/local/lib/libclamunrar_iface.la' 
libtool: install: warning: relinking `libclamunrar_iface.la' 
(cd /home/chris/Desktop/clamav-0.93.1/libclamunrar_iface; /bin/bash ../libtool  --tag=CC --mode=relink gcc -g -O2 -thread-safe -version-info 4:3:0 -no-undefined -Wl,--version-script,../libclamunrar_iface/libclamunrar_iface.map -o libclamunrar_iface.la -rpath /usr/local/lib unrar_iface.lo ../libclamunrar/libclamunrar.la -lz )  
gcc -shared  .libs/unrar_iface.o  -L/usr/local/lib -lclamunrar -lz  -Wl,--version-script -Wl,../libclamunrar_iface/libclamunrar_iface.map -Wl,-soname -Wl,libclamunrar_iface.so.4 -o .libs/libclamunrar_iface.so.4.0.3 
/usr/bin/install -c .libs/libclamunrar_iface.so.4.0.3T /usr/local/lib/libclamunrar_iface.so.4.0.3 
(cd /usr/local/lib && { ln -s -f libclamunrar_iface.so.4.0.3 libclamunrar_iface.so.4 || { rm -f libclamunrar_iface.so.4 && ln -s libclamunrar_iface.so.4.0.3 libclamunrar_iface.so.4; }; }) 
(cd /usr/local/lib && { ln -s -f libclamunrar_iface.so.4.0.3 libclamunrar_iface.so || { rm -f libclamunrar_iface.so && ln -s libclamunrar_iface.so.4.0.3 libclamunrar_iface.so; }; }) 
/usr/bin/install -c .libs/libclamunrar_iface.lai /usr/local/lib/libclamunrar_iface.la 
/usr/bin/install -c .libs/libclamunrar_iface.a /usr/local/lib/libclamunrar_iface.a 
chmod 644 /usr/local/lib/libclamunrar_iface.a 
ranlib /usr/local/lib/libclamunrar_iface.a 
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/local/lib 

If you ever happen to want to link against installed libraries 
in a given directory, LIBDIR, you must either use libtool, and 
specify the full pathname of the library, or use the `-LLIBDIR' 
flag during linking and do at least one of the following: 
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable 
     during execution 
   - add LIBDIR to the `LD_RUN_PATH' environment variable 
     during linking 
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag 
   - have your system administrator add LIBDIR to `/etc/ld.so.conf' 

See any operating system documentation about shared libraries for 
more information, such as the ld(1) and ld.so(8) manual pages. 
---------------------------------------------------------------------- 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar_iface' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamunrar_iface' 
Making install in libclamav 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamav' 
Making install in lzma 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamav/lzma' 
make[3]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamav/lzma' 
make[3]: Nothing to be done for `install-exec-am'. 
make[3]: Nothing to be done for `install-data-am'. 
make[3]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamav/lzma' 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamav/lzma' 
Making install in . 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamav' 
make[3]: Entering directory `/home/chris/Desktop/clamav-0.93.1/libclamav' 
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib" 
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libclamav.la' '/usr/local/lib/libclamav.la' 
libtool: install: warning: relinking `libclamav.la' 
(cd /home/chris/Desktop/clamav-0.93.1/libclamav; /bin/bash ../libtool  --tag=CC --mode=relink gcc -g -O2 -thread-safe -version-info 4:3:0 -no-undefined -Wl,--version-script,../libclamav/libclamav.map -o libclamav.la -rpath /usr/local/lib matcher-ac.lo matcher-bm.lo matcher.lo md5.lo others.lo readdb.lo cvd.lo dsig.lo str.lo scanners.lo textdet.lo filetypes.lo rtf.lo blob.lo mbox.lo message.lo table.lo text.lo ole2_extract.lo vba_extract.lo msexpand.lo pe.lo upx.lo htmlnorm.lo chmunpack.lo rebuildpe.lo petite.lo wwunpack.lo unsp.lo aspack.lo packlibs.lo fsg.lo mew.lo upack.lo line.lo untar.lo unzip.lo inflate64.lo special.lo binhex.lo is_tar.lo tnef.lo autoit.lo strlcpy.lo regcomp.lo regerror.lo regexec.lo regfree.lo unarj.lo bzlib.lo nulsft.lo infblock.lo pdf.lo spin.lo yc.lo elf.lo sis.lo uuencode.lo phishcheck.lo phish_domaincheck_db.lo phish_whitelist.lo regex_list.lo mspack.lo cab.lo entconv.lo hashtab.lo dconf.lo lzma_iface.lo explode.lo textnorm.lo ../libclamunrar_iface/libclamunrar_iface.la lzma/liblzma.la -lz -lpthread -lz )  
gcc -shared  .libs/matcher-ac.o .libs/matcher-bm.o .libs/matcher.o .libs/md5.o .libs/others.o .libs/readdb.o .libs/cvd.o .libs/dsig.o .libs/str.o .libs/scanners.o .libs/textdet.o .libs/filetypes.o .libs/rtf.o .libs/blob.o .libs/mbox.o .libs/message.o .libs/table.o .libs/text.o .libs/ole2_extract.o .libs/vba_extract.o .libs/msexpand.o .libs/pe.o .libs/upx.o .libs/htmlnorm.o .libs/chmunpack.o .libs/rebuildpe.o .libs/petite.o .libs/wwunpack.o .libs/unsp.o .libs/aspack.o .libs/packlibs.o .libs/fsg.o .libs/mew.o .libs/upack.o .libs/line.o .libs/untar.o .libs/unzip.o .libs/inflate64.o .libs/special.o .libs/binhex.o .libs/is_tar.o .libs/tnef.o .libs/autoit.o .libs/strlcpy.o .libs/regcomp.o .libs/regerror.o .libs/regexec.o .libs/regfree.o .libs/unarj.o .libs/bzlib.o .libs/nulsft.o .libs/infblock.o .libs/pdf.o .libs/spin.o .libs/yc.o .libs/elf.o .libs/sis.o .libs/uuencode.o .libs/phishcheck.o .libs/phish_domaincheck_db.o .libs/phish_whitelist.o .libs/regex_list.o .libs/mspack.o .libs/cab.o .libs/entconv.o .libs/hashtab.o .libs/dconf.o .libs/lzma_iface.o .libs/explode.o .libs/textnorm.o -Wl,--whole-archive lzma/.libs/liblzma.a -Wl,--no-whole-archive  -L/usr/local/lib -lclamunrar_iface -lpthread -lz  -Wl,--version-script -Wl,../libclamav/libclamav.map -Wl,-soname -Wl,libclamav.so.4 -o .libs/libclamav.so.4.0.3 
/usr/bin/install -c .libs/libclamav.so.4.0.3T /usr/local/lib/libclamav.so.4.0.3 
(cd /usr/local/lib && { ln -s -f libclamav.so.4.0.3 libclamav.so.4 || { rm -f libclamav.so.4 && ln -s libclamav.so.4.0.3 libclamav.so.4; }; }) 
(cd /usr/local/lib && { ln -s -f libclamav.so.4.0.3 libclamav.so || { rm -f libclamav.so && ln -s libclamav.so.4.0.3 libclamav.so; }; }) 
/usr/bin/install -c .libs/libclamav.lai /usr/local/lib/libclamav.la 
/usr/bin/install -c .libs/libclamav.a /usr/local/lib/libclamav.a 
chmod 644 /usr/local/lib/libclamav.a 
ranlib /usr/local/lib/libclamav.a 
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/local/lib 

If you ever happen to want to link against installed libraries 
in a given directory, LIBDIR, you must either use libtool, and 
specify the full pathname of the library, or use the `-LLIBDIR' 
flag during linking and do at least one of the following: 
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable 
     during execution 
   - add LIBDIR to the `LD_RUN_PATH' environment variable 
     during linking 
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag 
   - have your system administrator add LIBDIR to `/etc/ld.so.conf' 

See any operating system documentation about shared libraries for 
more information, such as the ld(1) and ld.so(8) manual pages. 
---------------------------------------------------------------------- 
test -z "/usr/local/include" || /bin/mkdir -p "/usr/local/include" 
 /usr/bin/install -c -m 644 'clamav.h' '/usr/local/include/clamav.h' 
make[3]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamav' 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamav' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/libclamav' 
Making install in clamscan 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamscan' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamscan' 
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin" 
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'clamscan' '/usr/local/bin/clamscan' 
/usr/bin/install -c .libs/clamscan /usr/local/bin/clamscan 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamscan' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamscan' 
Making install in clamd 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamd' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamd' 
test -z "/usr/local/sbin" || /bin/mkdir -p "/usr/local/sbin" 
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'clamd' '/usr/local/sbin/clamd' 
/usr/bin/install -c .libs/clamd /usr/local/sbin/clamd 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamd' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamd' 
Making install in clamdscan 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamdscan' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamdscan' 
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin" 
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'clamdscan' '/usr/local/bin/clamdscan' 
/usr/bin/install -c clamdscan /usr/local/bin/clamdscan 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamdscan' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamdscan' 
Making install in freshclam 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/freshclam' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/freshclam' 
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin" 
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'freshclam' '/usr/local/bin/freshclam' 
/usr/bin/install -c .libs/freshclam /usr/local/bin/freshclam 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/freshclam' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/freshclam' 
Making install in sigtool 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/sigtool' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/sigtool' 
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin" 
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'sigtool' '/usr/local/bin/sigtool' 
/usr/bin/install -c .libs/sigtool /usr/local/bin/sigtool 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/sigtool' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/sigtool' 
Making install in clamconf 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamconf' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamconf' 
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin" 
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'clamconf' '/usr/local/bin/clamconf' 
/usr/bin/install -c .libs/clamconf /usr/local/bin/clamconf 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamconf' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamconf' 
Making install in database 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/database' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/database' 
make[2]: Nothing to be done for `install-exec-am'. 
/bin/bash /home/chris/Desktop/clamav-0.93.1/config/install-sh -d /usr/local/share/clamav 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/database' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/database' 
Making install in docs 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/docs' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/docs' 
make[2]: Nothing to be done for `install-exec-am'. 
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1" 
 /usr/bin/install -c -m 644 './man/clamscan.1' '/usr/local/share/man/man1/clamscan.1' 
 /usr/bin/install -c -m 644 './man/freshclam.1' '/usr/local/share/man/man1/freshclam.1' 
 /usr/bin/install -c -m 644 './man/sigtool.1' '/usr/local/share/man/man1/sigtool.1' 
 /usr/bin/install -c -m 644 './man/clamdscan.1' '/usr/local/share/man/man1/clamdscan.1' 
 /usr/bin/install -c -m 644 './man/clamconf.1' '/usr/local/share/man/man1/clamconf.1' 
test -z "/usr/local/share/man/man5" || /bin/mkdir -p "/usr/local/share/man/man5" 
 /usr/bin/install -c -m 644 './man/clamd.conf.5' '/usr/local/share/man/man5/clamd.conf.5' 
 /usr/bin/install -c -m 644 './man/freshclam.conf.5' '/usr/local/share/man/man5/freshclam.conf.5' 
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8" 
 /usr/bin/install -c -m 644 './man/clamd.8' '/usr/local/share/man/man8/clamd.8' 
 /usr/bin/install -c -m 644 './man/clamav-milter.8' '/usr/local/share/man/man8/clamav-milter.8' 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/docs' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/docs' 
Making install in etc 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/etc' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/etc' 
make[2]: Nothing to be done for `install-exec-am'. 
/bin/bash /home/chris/Desktop/clamav-0.93.1/config/install-sh -d /usr/local/etc 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/etc' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/etc' 
Making install in clamav-milter 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamav-milter' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/clamav-milter' 
test -z "/usr/local/sbin" || /bin/mkdir -p "/usr/local/sbin" 
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8" 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamav-milter' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/clamav-milter' 
Making install in test 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1/test' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1/test' 
make[2]: Nothing to be done for `install-exec-am'. 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/test' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1/test' 
make[1]: Entering directory `/home/chris/Desktop/clamav-0.93.1' 
make[2]: Entering directory `/home/chris/Desktop/clamav-0.93.1' 
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin" 
 /usr/bin/install -c 'clamav-config' '/usr/local/bin/clamav-config' 
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig" 
 /usr/bin/install -c -m 644 'libclamav.pc' '/usr/local/lib/pkgconfig/libclamav.pc' 
make[2]: Leaving directory `/home/chris/Desktop/clamav-0.93.1' 
make[1]: Leaving directory `/home/chris/Desktop/clamav-0.93.1' 
chris@chris-laptop:~/Desktop/clamav-0.93.1$

---

### Post by candive on 2008-06-13
bump, does anyone know what files I need to change/remove and how do I do it?

---

