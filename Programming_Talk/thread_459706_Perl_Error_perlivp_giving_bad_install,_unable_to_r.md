---
title: "Perl Error: perlivp giving bad install, unable to run perl command on perl scripts..."
date: 2007-05-30
forum: Programming Talk
---

### Post by cantormath on 2007-05-30
So I have some perl scripts that I have run on this and other machines, and now I am unable to run them.  I have recently, updated the kernel, uninstalled apache and nagios, I am not sure if this is related to the problem.

here is the error when trying to run perl script
```
:~$ perl somescript.pl 
Can't locate WWW/CheckSite/Spider.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at somescript.pl line 76.
BEGIN failed--compilation aborted at somescript.pl line 76.

```perlivp says:```

:~$ sudo perlivp
Password:
ok 1
ok 2
# Perl @INC directory `/usr/local/lib/perl/5.8.7' does not appear to exist.
# Perl @INC directory `/usr/local/share/perl/5.8.7' does not appear to exist.
# Perl @INC directory `/usr/local/lib/site_perl' does not appear to exist.
not ok 3
ok 4
ok 5
ok 6
# Perl header `stdio.ph' does not appear to be properly installed.
# Perl header `arpa/inet.ph' does not appear to be properly installed.
# Perl header `crypt.ph' does not appear to be properly installed.
# Perl header `db.ph' does not appear to be properly installed.
# Perl header `dbm.ph' does not appear to be properly installed.
# Perl header `dirent.ph' does not appear to be properly installed.
# Perl header `dlfcn.ph' does not appear to be properly installed.
# Perl header `float.ph' does not appear to be properly installed.
# Perl header `gdbm.ph' does not appear to be properly installed.
# Perl header `grp.ph' does not appear to be properly installed.
# Perl header `inttypes.ph' does not appear to be properly installed.
# Perl header `langinfo.ph' does not appear to be properly installed.
# Perl header `locale.ph' does not appear to be properly installed.
# Perl header `malloc.ph' does not appear to be properly installed.
# Perl header `math.ph' does not appear to be properly installed.
# Perl header `mntent.ph' does not appear to be properly installed.
# Perl header `ndbm.ph' does not appear to be properly installed.
# Perl header `netdb.ph' does not appear to be properly installed.
# Perl header `netinet/tcp.ph' does not appear to be properly installed.
# Perl header `netinet/in.ph' does not appear to be properly installed.
# Perl header `poll.ph' does not appear to be properly installed.
# Perl header `pthread.ph' does not appear to be properly installed.
# Perl header `pwd.ph' does not appear to be properly installed.
# Perl header `shadow.ph' does not appear to be properly installed.
# Perl header `stdlib.ph' does not appear to be properly installed.
# Perl header `string.ph' does not appear to be properly installed.
# Perl header `sys/dir.ph' does not appear to be properly installed.
# Perl header `sys/file.ph' does not appear to be properly installed.
# Perl header `sys/mman.ph' does not appear to be properly installed.
# Perl header `sys/mount.ph' does not appear to be properly installed.
# Perl header `sys/param.ph' does not appear to be properly installed.
# Perl header `sys/stat.ph' does not appear to be properly installed.
# Perl header `sys/statfs.ph' does not appear to be properly installed.
# Perl header `sys/statvfs.ph' does not appear to be properly installed.
# Perl header `sys/times.ph' does not appear to be properly installed.
# Perl header `sys/un.ph' does not appear to be properly installed.
# Perl header `sys/utsname.ph' does not appear to be properly installed.
# Perl header `sys/vfs.ph' does not appear to be properly installed.
# Perl header `termios.ph' does not appear to be properly installed.
# Perl header `unistd.ph' does not appear to be properly installed.
# Perl header `ustat.ph' does not appear to be properly installed.
# Perl header `utime.ph' does not appear to be properly installed.
# Perl header `values.ph' does not appear to be properly installed.
not ok 7
 2/7 subtests failed, 71.43% okay.
```Any ideas are welcome, I would like to know if anyone else has at least had the same problem, and I thank everyone in advance.

---

### Post by cantormath on 2007-05-31
I am now getting this when using perlivp:
```
:~$ perlivp
ok 1
ok 2
# Perl @INC directory `/usr/local/lib/perl/5.8.7' does not appear to exist.
# Perl @INC directory `/usr/local/share/perl/5.8.7' does not appear to exist.
# Perl @INC directory `/usr/local/lib/site_perl' does not appear to exist.
not ok 3
ok 4
ok 5
ok 6
# Perl header `stdio.ph' does not appear to be properly installed.
# Perl header `arpa/inet.ph' does not appear to be properly installed.
# Perl header `crypt.ph' does not appear to be properly installed.
# Perl header `db.ph' does not appear to be properly installed.
# Perl header `dbm.ph' does not appear to be properly installed.
# Perl header `dirent.ph' does not appear to be properly installed.
# Perl header `dlfcn.ph' does not appear to be properly installed.
# Perl header `float.ph' does not appear to be properly installed.
# Perl header `gdbm.ph' does not appear to be properly installed.
# Perl header `grp.ph' does not appear to be properly installed.
# Perl header `inttypes.ph' does not appear to be properly installed.
# Perl header `langinfo.ph' does not appear to be properly installed.
# Perl header `locale.ph' does not appear to be properly installed.
# Perl header `malloc.ph' does not appear to be properly installed.
# Perl header `math.ph' does not appear to be properly installed.
# Perl header `mntent.ph' does not appear to be properly installed.
# Perl header `ndbm.ph' does not appear to be properly installed.
# Perl header `netdb.ph' does not appear to be properly installed.
# Perl header `netinet/tcp.ph' does not appear to be properly installed.
# Perl header `netinet/in.ph' does not appear to be properly installed.
# Perl header `poll.ph' does not appear to be properly installed.
# Perl header `pthread.ph' does not appear to be properly installed.
# Perl header `pwd.ph' does not appear to be properly installed.
# Perl header `shadow.ph' does not appear to be properly installed.
# Perl header `stdlib.ph' does not appear to be properly installed.
# Perl header `string.ph' does not appear to be properly installed.
# Perl header `sys/dir.ph' does not appear to be properly installed.
# Perl header `sys/file.ph' does not appear to be properly installed.
# Perl header `sys/mman.ph' does not appear to be properly installed.
# Perl header `sys/mount.ph' does not appear to be properly installed.
# Perl header `sys/param.ph' does not appear to be properly installed.
# Perl header `sys/stat.ph' does not appear to be properly installed.
# Perl header `sys/statfs.ph' does not appear to be properly installed.
# Perl header `sys/statvfs.ph' does not appear to be properly installed.
# Perl header `sys/times.ph' does not appear to be properly installed.
# Perl header `sys/un.ph' does not appear to be properly installed.
# Perl header `sys/utsname.ph' does not appear to be properly installed.
# Perl header `sys/vfs.ph' does not appear to be properly installed.
# Perl header `termios.ph' does not appear to be properly installed.
# Perl header `unistd.ph' does not appear to be properly installed.
# Perl header `ustat.ph' does not appear to be properly installed.
# Perl header `utime.ph' does not appear to be properly installed.
# Perl header `values.ph' does not appear to be properly installed.
not ok 7
 2/7 subtests failed, 71.43% okay.

```

and the same error when I try and run a perl script..

---

### Post by cantormath on 2007-05-31
bump....

---

