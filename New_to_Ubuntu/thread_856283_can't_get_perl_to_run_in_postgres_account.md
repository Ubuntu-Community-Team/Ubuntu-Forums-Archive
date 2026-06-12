---
title: "can't get perl to run in postgres account"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by John@plectix on 2008-07-11
Hi,
  I'm new to ubuntu/linux and having problem getting perl to run when I'm logged in as my postgres user.

Why can't my postgres account find the shared library in /usr/lib?

The output from the command line is below.

Thanks
-John

```

**root@integration:~#** perl
print("root works\n");
root works
**root@integration:~#** which perl
/usr/bin/perl
**root@integration:~#** ldd /usr/bin/perl
        linux-vdso.so.1 =>  (0x00007fff9b9fe000)
        libperl.so.5.8 => /usr/lib/libperl.so.5.8 (0x00007fd8932d8000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007fd8930d4000)
        libm.so.6 => /lib/libm.so.6 (0x00007fd892e53000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007fd892c37000)
        libc.so.6 => /lib/libc.so.6 (0x00007fd8928d5000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0x00007fd89269d000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fd893616000)
**root@integration:~#** su - postgres
**postgres@integration:~$** which perl
/usr/bin/perl
**postgres@integration:~$** perl
perl: error while loading shared libraries: libperl.so.5.8: cannot open shared object file: Permission denied
**postgres@integration:~$** ldd /usr/bin/perl
        linux-vdso.so.1 =>  (0x00007fff7bffe000)
        libperl.so.5.8 => not found
        libdl.so.2 => /lib/libdl.so.2 (0x00007fd073b33000)
        libm.so.6 => /lib/libm.so.6 (0x00007fd0738b2000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007fd073696000)
        libc.so.6 => /lib/libc.so.6 (0x00007fd073334000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0x00007fd0730fc000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fd073d37000)
**postgres@integration:~$ set**
BASH=/bin/bash
BASH_ARGC=()
BASH_ARGV=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="3" [1]="2" [2]="33" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='3.2.33(1)-release'
COLUMNS=91
DIRSTACK=()
EUID=105
GROUPS=()
HISTFILE=/var/lib/postgresql/.bash_history
HISTFILESIZE=500
HISTSIZE=500
HOME=/var/lib/postgresql
HOSTNAME=integration
HOSTTYPE=x86_64
IFS=$' \t\n'
LANG=en_US.UTF-8
LINES=66
LOGNAME=postgres
MACHTYPE=x86_64-pc-linux-gnu
MAIL=/var/mail/postgres
MAILCHECK=60
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/bin:/usr/bin:/bin:/usr/games
PIPESTATUS=([0]="0")
PPID=11219
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
PS2='> '
PS4='+ '
PWD=/var/lib/postgresql
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=1
TERM=xterm-color
UID=105
USER=postgres
_=/usr/bin/perl
```

---

### Post by John@plectix on 2008-07-11
Problem was that the /usr/lib directory was not 755.  It was 744 permission.

Thanks
-John

---

