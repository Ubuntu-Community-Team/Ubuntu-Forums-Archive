---
title: "can't find editor"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-06-16
I get this error and do have vim installed. I prefer to use gedit but how do I fix it? So I guess I want to get the editor issue fixed and also set gedit as the sudo editor.

```
mcanulty@Darcy25:~$ sudo visudo
[sudo] password for cmcanulty: 
visudo: no editor found (editor path = /usr/bin/editor)
cmcanulty@Darcy25:~$ 
```

---

### Post by papibe on 2012-06-16
Hi cmcanulty.

Try this first:
```
sudo update-alternatives --config editor
```
Regards.

---

### Post by Cheesemill on 2012-06-16
> **cmcanulty said:**
> I get this error and do have vim installed. I prefer to use gedit but how do I fix it? So I guess I want to get the editor issue fixed and also set gedit as the sudo editor.

```
mcanulty@Darcy25:~$ sudo visudo
[sudo] password for cmcanulty: 
visudo: no editor found (editor path = /usr/bin/editor)
cmcanulty@Darcy25:~$ 
```
```
sudo EDITOR=gedit visudo
```Should work as a one off, I can't remember where the EDITOR environmental variable is usually defined though.

---

### Post by cmcanulty on 2012-06-17
Still error I tried typing 1. Also I don't see gedit even on list

```
cmcanulty@Darcy25:~$ sudo update-alternatives --config editor
[sudo] password for cmcanulty: 
There are 9 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Path                 Priority   Status
------------------------------------------------------------
  0            /usr/bin/vim.gnome    60        auto mode
  1            /bin/ed              -100       manual mode
  2            /bin/nano             40        manual mode
  3            /usr/bin/cream        0         manual mode
  4            /usr/bin/emacs23      0         manual mode
  5            /usr/bin/vim.athena   50        manual mode
  6            /usr/bin/vim.basic    30        manual mode
  7            /usr/bin/vim.gnome    60        manual mode
  8            /usr/bin/vim.gtk      50        manual mode
  9            /usr/bin/vim.tiny     10        manual mode

Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /bin/ed to provide /usr/bin/editor (editor) in manual mode.
update-alternatives: error: error creating symbolic link `/etc/alternatives/editor.dpkg-tmp': No such file or directory
cmcanulty@Darcy25:~$ 

```

---

### Post by Cheesemill on 2012-06-17
This **may** work for adding gedit to the list:
```
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/gedit
```

I've never used it myself but Google threw it up.

---

### Post by cmcanulty on 2012-06-17
same error


```

cmcanulty@Darcy25:~$ sudo update-alternatives --install /usr/bin/editor editor /usr/bin/gedit
update-alternatives: --install needs <link> <name> <path> <priority>

Usage: update-alternatives [<option> ...] <command>

Commands:
  --install <link> <name> <path> <priority>
    [--slave <link> <name> <path>] ...
                           add a group of alternatives to the system.
  --remove <name> <path>   remove <path> from the <name> group alternative.
  --remove-all <name>      remove <name> group from the alternatives system.
  --auto <name>            switch the master link <name> to automatic mode.
  --display <name>         display information about the <name> group.
  --query <name>           machine parseable version of --display <name>.
  --list <name>            display all targets of the <name> group.
  --get-selections         list master alternative names and their status.
  --set-selections         read alternative status from standard input.
  --config <name>          show alternatives for the <name> group and ask the
                           user to select which one to use.
  --set <name> <path>      set <path> as alternative for <name>.
  --all                    call --config on all alternatives.

<link> is the symlink pointing to /etc/alternatives/<name>.
  (e.g. /usr/bin/pager)
<name> is the master name for this link group.
  (e.g. pager)
<path> is the location of one of the alternative target files.
  (e.g. /usr/bin/less)
<priority> is an integer; options with higher numbers have higher priority in
  automatic mode.

Options:
  --altdir <directory>     change the alternatives directory.
  --admindir <directory>   change the administrative directory.
  --log <file>             change the log file.
  --force                  allow replacing files with alternative links.
  --skip-auto              skip prompt for alternatives correctly configured
                           in automatic mode (relevant for --config only)
  --verbose                verbose operation, more output.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.
cmcanulty@Darcy25:~$ sudo update-alternatives --config editor
There are 9 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Path                 Priority   Status
------------------------------------------------------------
  0            /usr/bin/vim.gnome    60        auto mode
  1            /bin/ed              -100       manual mode
  2            /bin/nano             40        manual mode
  3            /usr/bin/cream        0         manual mode
  4            /usr/bin/emacs23      0         manual mode
  5            /usr/bin/vim.athena   50        manual mode
  6            /usr/bin/vim.basic    30        manual mode
  7            /usr/bin/vim.gnome    60        manual mode
  8            /usr/bin/vim.gtk      50        manual mode
  9            /usr/bin/vim.tiny     10        manual mode

Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /bin/ed to provide /usr/bin/editor (editor) in manual mode.
update-alternatives: error: error creating symbolic link `/etc/alternatives/editor.dpkg-tmp': No such file or directory
cmcanulty@Darcy25:~$
```

---

### Post by matt_symes on 2012-06-17
Hi

> **Cheesemill said:**
> This **may** work for adding gedit to the list:
```
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/gedit
```

I've never used it myself but Google threw it up.

This would need a priority to work.

```
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/gedit 10
```

I'm not sure if it will fix the error though.

Can you post the output of

```
cat /var/lib/dpkg/alternatives/editor
```

just to have a look.

Kind regards

---

### Post by chamber on 2012-06-17
> **Cheesemill said:**
> ```
sudo EDITOR=gedit visudo
```Should work as a one off, I can't remember where the EDITOR environmental variable is usually defined though.

The EDITOR variable can be defined in your .bashrc. Not sure if this will work for visudo though as this should generally be edited with vi. 

You can use nano in the terminal using EDITOR=nano visudo. If you don't want to type this each time then set an alias.

---

### Post by cmcanulty on 2012-06-17
Here is The results of both commands

```
cmcanulty@Darcy25:~$ sudo update-alternatives --install /usr/bin/editor editor /usr/bin/gedit 10
[sudo] password for cmcanulty: 
update-alternatives: using /usr/bin/vim.gnome to provide /usr/bin/editor (editor) in auto mode.
update-alternatives: error: error creating symbolic link `/etc/alternatives/editor.dpkg-tmp': No such file or directory
cmcanulty@Darcy25:~$ cat /var/lib/dpkg/alternatives/editor
manual
/usr/bin/editor
editor.1.gz
/usr/share/man/man1/editor.1.gz
editor.fr.1.gz
/usr/share/man/fr/man1/editor.1.gz
editor.it.1.gz
/usr/share/man/it/man1/editor.1.gz
editor.pl.1.gz
/usr/share/man/pl/man1/editor.1.gz
editor.ru.1.gz
/usr/share/man/ru/man1/editor.1.gz

/bin/ed
-100
/usr/share/man/man1/ed.1.gz




/bin/nano
40
/usr/share/man/man1/nano.1.gz




/usr/bin/cream
0
/usr/share/man/man1/cream.1.gz




/usr/bin/emacs23
0
/usr/share/man/man1/emacs.emacs23.1.gz




/usr/bin/vim.athena
50
/usr/share/man/man1/vim.1.gz
/usr/share/man/fr/man1/vim.1.gz
/usr/share/man/it/man1/vim.1.gz
/usr/share/man/pl/man1/vim.1.gz
/usr/share/man/ru/man1/vim.1.gz
/usr/bin/vim.basic
30
/usr/share/man/man1/vim.1.gz
/usr/share/man/fr/man1/vim.1.gz
/usr/share/man/it/man1/vim.1.gz
/usr/share/man/pl/man1/vim.1.gz
/usr/share/man/ru/man1/vim.1.gz
/usr/bin/vim.gnome
60
/usr/share/man/man1/vim.1.gz
/usr/share/man/fr/man1/vim.1.gz
/usr/share/man/it/man1/vim.1.gz
/usr/share/man/pl/man1/vim.1.gz
/usr/share/man/ru/man1/vim.1.gz
/usr/bin/vim.gtk
50
/usr/share/man/man1/vim.1.gz
/usr/share/man/fr/man1/vim.1.gz
/usr/share/man/it/man1/vim.1.gz
/usr/share/man/pl/man1/vim.1.gz
/usr/share/man/ru/man1/vim.1.gz
/usr/bin/vim.tiny
10
/usr/share/man/man1/vim.1.gz
/usr/share/man/fr/man1/vim.1.gz
/usr/share/man/it/man1/vim.1.gz
/usr/share/man/pl/man1/vim.1.gz
/usr/share/man/ru/man1/vim.1.gz

cmcanulty@Darcy25:~$ 

```

and here is the end of my bach.rc

```
export EDITOR="gedit"
alias visudo='-E visudo'
```

---

### Post by matt_symes on 2012-06-17
Hi

Can you try with the verbose switch please. Maybe that will give more information.

```
sudo update-alternatives --verbose --install /usr/bin/editor editor /usr/bin/gedit 10
```

Kind regards

---

### Post by cmcanulty on 2012-06-17
same error 


```

 cmcanulty@Darcy25:~$ sudo update-alternatives --verbose --install /usr/bin/editor editor /usr/bin/gedit 10
[sudo] password for cmcanulty: 
update-alternatives: setting up automatic selection of editor.
update-alternatives: using /usr/bin/vim.gnome to provide /usr/bin/editor (editor) in auto mode.
update-alternatives: error: error creating symbolic link `/etc/alternatives/editor.dpkg-tmp': No such file or directory
cmcanulty@Darcy25:~$
```

---

### Post by matt_symes on 2012-06-18
Hi

> **cmcanulty said:**
> same error 

```

 cmcanulty@Darcy25:~$ sudo update-alternatives --verbose --install /usr/bin/editor editor /usr/bin/gedit 10
[sudo] password for cmcanulty: 
update-alternatives: setting up automatic selection of editor.
update-alternatives: using /usr/bin/vim.gnome to provide /usr/bin/editor (editor) in auto mode.
update-alternatives: error: error creating symbolic link `/etc/alternatives/editor.dpkg-tmp': No such file or directory
cmcanulty@Darcy25:~$
```

I expected the same error. I was hoping for me error messages than that though.

I'm not sure if this is a bug in the code or a configuration problem and the error messages are not giving much clue.

I would sgeest running it through strace at this pointy to see what the code is doing.

```
sudo strace -o ~/t.txt update-alternatives --verbose --install /usr/bin/editor editor /usr/bin/gedit 10
```

This will create a file in your home directory called t.txt and it may potentially be quite large.

Post back the last 100 lines or so. Hopefully that will show what is going on.

Kind regards

---

### Post by cmcanulty on 2012-06-18
```
cmcanulty@Darcy25:~$ sudo strace -o ~/t.txt update-alternatives --verbose --install /usr/bin/editor editor /usr/bin/gedit 10
[sudo] password for cmcanulty: 
update-alternatives: setting up automatic selection of editor.
update-alternatives: using /usr/bin/vim.gnome to provide /usr/bin/editor (editor) in auto mode.
update-alternatives: error: error creating symbolic link `/etc/alternatives/editor.dpkg-tmp': No such file or directory
cmcanulty@Darcy25:~$
```

---

### Post by matt_symes on 2012-06-18
Hi

I think you missed this.

> This will create a file in your home directory called t.txt and it may potentially be quite large.

Post back the last 100 lines or so. Hopefully that will show what is going on.

From my previous post: look in your home directory. There should be a file there called t.txt. 

That contains a trace of the update-alternatives command. 

I am not interested in the output of the update-alternatives command but the contents of the t.txt file in your home directory.

Please post it back here the last (100 lines or so).

Kind regards

---

### Post by cmcanulty on 2012-06-18
Sorry I read that but forgot

```
(0)                                  = 0x2282000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe7000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=177226, ...}) = 0
mmap(NULL, 177226, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9839fbb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\30\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1802936, ...}) = 0
mmap(NULL, 3917016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9839a0a000
mprotect(0x7f9839bbd000, 2093056, PROT_NONE) = 0
mmap(0x7f9839dbc000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b2000) = 0x7f9839dbc000
mmap(0x7f983execve("/usr/sbin/update-alternatives", ["update-alternatives", "--verbose", "--install", "/usr/bin/editor", "editor", "/usr/bin/gedit", "10"], [/* 18 vars */]) = 0
brk9dc2000, 17624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9839dc2000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fba000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fb9000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fb8000
arch_prctl(ARCH_SET_FS, 0x7f9839fb9700) = 0
mprotect(0x7f9839dbc000, 16384, PROT_READ) = 0
mprotect(0x609000, 4096, PROT_READ)     = 0
mprotect(0x7f9839fe9000, 4096, PROT_READ) = 0
munmap(0x7f9839fbb000, 177226)          = 0
brk(0)                                  = 0x2282000
brk(0x22a3000)                          = 0x22a3000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=29689904, ...}) = 0
mmap(NULL, 29689904, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9837db9000
close(3)                                = 0
openat(AT_FDCWD, "/var/lib/dpkg/alternatives", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 3
getdents(3, /* 180 entries */, 32768)   = 5720
getdents(3, /* 0 entries */, 32768)     = 0
open("/proc/meminfo", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(4, "MemTotal:        3844700 kB\nMemF"..., 1024) = 1024
close(4)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
close(3)                                = 0
stat("/var/lib/dpkg/alternatives/appletviewer", {st_mode=S_IFREG|0644, st_size=188, ...}) = 0
open("/var/lib/dpkg/alternatives/appletviewer", O_RDONLY) = 3
open("/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(4, "# Locale name alias data base.\n#"..., 4096) = 2570
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
open("/usr/share/locale/en_US/LC_MESSAGES/dpkg.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/dpkg.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/dpkg.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/dpkg.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
fstat(3, {st_mode=S_IFREG|0644, st_size=188, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/appletviewer\napple"..., 4096) = 188
stat("/usr/lib/jvm/java-7-oracle/bin/appletviewer", {st_mode=S_IFREG|0755, st_size=7845, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/apt", {st_mode=S_IFREG|0644, st_size=143, ...}) = 0
open("/var/lib/dpkg/alternatives/apt", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/apt\napt.1.gz\n/usr/"..., 4096) = 143
stat("/usr/lib/jvm/java-7-oracle/bin/apt", {st_mode=S_IFREG|0755, st_size=7829, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/aptitude", {st_mode=S_IFREG|0644, st_size=1024, ...}) = 0
open("/var/lib/dpkg/alternatives/aptitude", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1024, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/aptitude\naptitude."..., 4096) = 1024
stat("/usr/bin/aptitude-curses", {st_mode=S_IFREG|0755, st_size=3951736, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/assembly-linker", {st_mode=S_IFREG|0644, st_size=110, ...}) = 0
open("/var/lib/dpkg/alternatives/assembly-linker", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=110, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/cli-al\ncli-al.1.gz"..., 4096) = 110
stat("/usr/bin/al", {st_mode=S_IFREG|0755, st_size=73, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/assistant", {st_mode=S_IFREG|0644, st_size=141, ...}) = 0
open("/var/lib/dpkg/alternatives/assistant", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=141, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/assistant\nassistan"..., 4096) = 141
stat("/usr/bin/assistant-qt4", {st_mode=S_IFREG|0755, st_size=987288, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/automake", {st_mode=S_IFREG|0644, st_size=269, ...}) = 0
open("/var/lib/dpkg/alternatives/automake", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=269, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/automake\naclocal\n/"..., 4096) = 269
stat("/usr/bin/automake-1.11", {st_mode=S_IFREG|0755, st_size=259969, ...}) = 0
close(3)    
```

---

### Post by matt_symes on 2012-06-18
Hi

Are you sure that was the last 100 lines and not the first ?

Can you post all of it instead please.

Kind regards

---

### Post by cmcanulty on 2012-06-18
Oh man sorry here are the last 100

```
stat("/usr/bin/gnome-terminal.wrapper", {st_mode=S_IFREG|0755, st_size=1394, ...}) = 0
stat("/usr/bin/koi8rxterm", {st_mode=S_IFREG|0755, st_size=3759, ...}) = 0
stat("/usr/bin/konsole", {st_mode=S_IFREG|0755, st_size=6176, ...}) = 0
stat("/usr/bin/lxterm", {st_mode=S_IFREG|0755, st_size=419, ...}) = 0
stat("/usr/bin/lxterminal", {st_mode=S_IFREG|0755, st_size=59432, ...}) = 0
stat("/usr/bin/uxterm", {st_mode=S_IFREG|0755, st_size=3674, ...}) = 0
stat("/usr/bin/xfce4-terminal.wrapper", {st_mode=S_IFREG|0755, st_size=1124, ...}) = 0
stat("/usr/bin/xterm", {st_mode=S_IFREG|0755, st_size=433408, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/x-window-manager", {st_mode=S_IFREG|0644, st_size=323, ...}) = 0
open("/var/lib/dpkg/alternatives/x-window-manager", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=323, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/x-window-manager\nx"..., 4096) = 323
stat("/usr/bin/kwin", {st_mode=S_IFREG|0755, st_size=6176, ...}) = 0
stat("/usr/bin/metacity", {st_mode=S_IFREG|0755, st_size=569488, ...}) = 0
stat("/usr/bin/muffin", {st_mode=S_IFREG|0755, st_size=10456, ...}) = 0
stat("/usr/bin/openbox", {st_mode=S_IFREG|0755, st_size=350352, ...}) = 0
stat("/usr/bin/xfwm4", {st_mode=S_IFREG|0755, st_size=354296, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/x-www-browser", {st_mode=S_IFREG|0644, st_size=416, ...}) = 0
open("/var/lib/dpkg/alternatives/x-www-browser", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=416, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/x-www-browser\nx-ww"..., 4096) = 416
brk(0x244b000)                          = 0x244b000
stat("/usr/bin/chromium-browser", {st_mode=S_IFREG|0755, st_size=3573, ...}) = 0
stat("/usr/bin/epiphany-browser", {st_mode=S_IFREG|0755, st_size=797688, ...}) = 0
stat("/usr/bin/firefox", {st_mode=S_IFREG|0755, st_size=2722, ...}) = 0
stat("/usr/bin/google-chrome", {st_mode=S_IFREG|0755, st_size=1665, ...}) = 0
stat("/usr/bin/konqueror", {st_mode=S_IFREG|0755, st_size=6184, ...}) = 0
stat("/usr/bin/midori", {st_mode=S_IFREG|0755, st_size=637904, ...}) = 0
stat("/usr/bin/opera", {st_mode=S_IFREG|0755, st_size=89, ...}) = 0
stat("/usr/bin/rekonq", {st_mode=S_IFREG|0755, st_size=6128, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/var/lib/dpkg/alternatives/yacc", {st_mode=S_IFREG|0644, st_size=119, ...}) = 0
open("/var/lib/dpkg/alternatives/yacc", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=119, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "auto\n/usr/bin/yacc\nyaccman\n/usr/"..., 4096) = 119
stat("/usr/bin/bison.yacc", {st_mode=S_IFREG|0755, st_size=41, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
stat("/usr/bin/gedit", {st_mode=S_IFREG|0755, st_size=676336, ...}) = 0
stat("/var/lib/dpkg/alternatives/editor", {st_mode=S_IFREG|0644, st_size=1368, ...}) = 0
open("/var/lib/dpkg/alternatives/editor", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1368, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
read(3, "manual\n/usr/bin/editor\neditor.1."..., 4096) = 1368
stat("/bin/ed", {st_mode=S_IFREG|0755, st_size=47552, ...}) = 0
stat("/bin/nano", {st_mode=S_IFREG|0755, st_size=191960, ...}) = 0
stat("/usr/bin/cream", {st_mode=S_IFREG|0755, st_size=616, ...}) = 0
stat("/usr/bin/emacs23", {st_mode=S_IFREG|0755, st_size=10803128, ...}) = 0
stat("/usr/bin/vim.athena", {st_mode=S_IFREG|0755, st_size=2339192, ...}) = 0
stat("/usr/bin/vim.basic", {st_mode=S_IFREG|0755, st_size=2015392, ...}) = 0
stat("/usr/bin/vim.gnome", {st_mode=S_IFREG|0755, st_size=2392032, ...}) = 0
stat("/usr/bin/vim.gtk", {st_mode=S_IFREG|0755, st_size=2387776, ...}) = 0
stat("/usr/bin/vim.tiny", {st_mode=S_IFREG|0755, st_size=777056, ...}) = 0
close(3)                                = 0
munmap(0x7f9839fe6000, 4096)            = 0
open("/var/log/alternatives.log", O_WRONLY|O_CREAT|O_APPEND, 0666) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=41743, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe6000
fstat(3, {st_mode=S_IFREG|0644, st_size=41743, ...}) = 0
lseek(3, 41743, SEEK_SET)               = 41743
open("/etc/localtime", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=2202, ...}) = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=2202, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9839fe5000
read(4, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\6\0\0\0\6\0\0\0\0"..., 4096) = 2202
lseek(4, -1391, SEEK_CUR)               = 811
read(4, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\6\0\0\0\6\0\0\0\0"..., 4096) = 1391
close(4)                                = 0
munmap(0x7f9839fe5000, 4096)            = 0
lstat("/etc/alternatives/editor", 0x7fff294af430) = -1 ENOENT (No such file or directory)
write(1, "update-alternatives: ", 21)   = 21
write(1, "setting up automatic selection o"..., 41) = 41
write(1, "\n", 1)                       = 1
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2202, ...}) = 0
lstat("/usr/bin/editor", {st_mode=S_IFLNK|0777, st_size=24, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2202, ...}) = 0
write(1, "update-alternatives: ", 21)   = 21
write(1, "using /usr/bin/vim.gnome to prov"..., 74) = 74
write(1, "\n", 1)                       = 1
unlink("/etc/alternatives/editor.dpkg-tmp") = -1 ENOENT (No such file or directory)
symlink("/usr/bin/vim.gnome", "/etc/alternatives/editor.dpkg-tmp") = -1 ENOENT (No such file or directory)
write(2, "update-alternatives: error: ", 28) = 28
open("/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=26258, ...}) = 0
mmap(NULL, 26258, PROT_READ, MAP_SHARED, 4, 0) = 0x7f9839fdf000
close(4)                                = 0
write(2, "error creating symbolic link `/e"..., 64) = 64
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, ": No such file or directory\n", 28) = 28
write(3, "update-alternatives 2012-06-18 0"..., 299) = 299
exit_group(2) 
```

---

### Post by matt_symes on 2012-06-18
Hi

Quick question. What version of Ubuntu (10.04, 11.10 etc) are you using ?

Can you also post the output of

```
ls -l /etc/alternatives/editor
```

and 

```
ls -l /usr/bin/vim.gnome
```

Kind regards

---

### Post by cmcanulty on 2012-06-18
I am running 12.04 gnome classic. This just started out of the blue. I also get the same error all the time if I try to update or install anything in terminal or synaptic.Both started a few days ago.I am posting those errors last

```
[CODE]cmcanulty@Darcy25:~$ ls -l /etc/alternatives/editor
ls: cannot access /etc/alternatives/editor: No such file or directory
cmcanulty@Darcy25:~$ ls -l /usr/bin/vim.gnome
-rwxr-xr-x 1 root root 2392032 May  4 00:25 /usr/bin/vim.gnome
cmcanulty@Darcy25:~$
```[/CODE]


```
E: nfs-common: subprocess installed post-installation script returned error exit status 127
E: initramfs-tools: subprocess installed post-installation script returned error exit status 127

```

---

### Post by matt_symes on 2012-06-18
Hi

> **cmcanulty said:**
> I am running 12.04 gnome classic. This just started out of the blue. I also get the same error all the time if I try to update or install anything in terminal or synaptic.Both started a few days ago.I am posting those errors last

```
[CODE]cmcanulty@Darcy25:~$ ls -l /etc/alternatives/editor
ls: cannot access /etc/alternatives/editor: No such file or directory
cmcanulty@Darcy25:~$ ls -l /usr/bin/vim.gnome
-rwxr-xr-x 1 root root 2392032 May  4 00:25 /usr/bin/vim.gnome
cmcanulty@Darcy25:~$
```[/CODE]

Lets try to create the symlink manually first.

From the terminal...

```
sudo ln -s /usr/bin/gedit /etc/alternatives/editor
```

```
sudo visudo
```

Does that open visudo using gedit ?

If not then delete the symlink and try

```
sudo ln -s /usr/bin/vim.gnome /etc/alternatives/editor
```

then try the visudo command again.

Don't touch update-alternatives command at the moment.

> 
```
E: nfs-common: subprocess installed post-installation script returned error exit status 127
E: initramfs-tools: subprocess installed post-installation script returned error exit status 127

```

^^^ I don't understand this :confused:

Kind regards

---

### Post by cmcanulty on 2012-06-18
It is a stubborn problem 

```
cmcanulty@Darcy25:~$ sudo ln -s /usr/bin/gedit /etc/alternatives/editor
[sudo] password for cmcanulty: 
ln: failed to create symbolic link `/etc/alternatives/editor': No such file or directory
cmcanulty@Darcy25:~$ sudo visudo
visudo: no editor found (editor path = /usr/bin/editor)
cmcanulty@Darcy25:~$
```

---

### Post by matt_symes on 2012-06-18
Hi

Maybe i got that the wrong way around again... Try this

```
sudo ln -s /etc/alternatives/editor /usr/bin/gedit
```

```
sudo visudo
```

Kind regards

---

### Post by cmcanulty on 2012-06-18
```
cmcanulty@Darcy25:~$ sudo ln -s /etc/alternatives/editor /usr/bin/gedit
[sudo] password for cmcanulty: 
ln: failed to create symbolic link `/usr/bin/gedit': File exists
cmcanulty@Darcy25:~$ sudo visudo
visudo: no editor found (editor path = /usr/bin/editor)
cmcanulty@Darcy25:~$ 

```
thanks for all your effort

---

### Post by Cheesemill on 2012-06-18
It's just a shot in the dark but do you actually have an /etc/alternatives folder?

---

### Post by matt_symes on 2012-06-18
Hi

> **Cheesemill said:**
> It's just a shot in the dark but do you actually have an /etc/alternatives folder?

Funny you should say that. It's exactly what i was going to ask because this makes no sense

```
ls -ld /etc/alternatives
```

Kind regards

---

### Post by cmcanulty on 2012-06-18
No
```

cmcanulty@Darcy25:~$ ls -ld /etc/alternatives
ls: cannot access /etc/alternatives: No such file or directory
cmcanulty@Darcy25:~$
```

---

### Post by Cheesemill on 2012-06-18
> **matt_symes said:**
> Funny you should say that. It's exactly what i was going to ask because this makes no sense
It would also explain this:
```
ln: failed to create symbolic link `/etc/alternatives/editor': No such file or directory
```

---

### Post by matt_symes on 2012-06-18
Hi

> It would also explain this:

And why half the strace was missing as well.

Open a terminal and type

```
sudo mkdir /etc/alternatives
```

```
sudo update-alternatives --all
```

and pick your alternatives.

Hopefully that will work.

Kind regards

---

### Post by cmcanulty on 2012-06-18
Now I get something but not editors

```
cmcanulty@Darcy25:~$ sudo mkdir /etc/alternatives
[sudo] password for cmcanulty: 
cmcanulty@Darcy25:~$ sudo update-alternatives --all
There is 1 choice for the alternative appletviewer (providing /usr/bin/appletviewer).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-oracle/bin/appletviewer   1066      auto mode
  1            /usr/lib/jvm/java-7-oracle/bin/appletviewer   1066      manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by Cheesemill on 2012-06-18
Because your /etc/alternatives directory was missing you will have to go through the entire list of applications the alternatives system handles and choose your preferred default for each selection. Just keep choosing until you get back to a prompt.

If you are unsure about any of them then 0 is probably a safe choice.

---

### Post by cmcanulty on 2012-06-18
How do I choose them ? I don't see them listed.

---

### Post by matt_symes on 2012-06-18
Hi

You need to press a number key. Pressing <ENTER> will keep your current configuration for that alternative.

You need to do this all all the alternatives on you system. Once you select one alternative, it will move onto the next alternative.

Here's me selecting the vim editor by pressing the key 4.

```
matthew@matthew-Aspire-7540 ~ % sudo update-alternatives --config editor
[sudo] password for matthew: 
There are 5 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Path                Priority   Status
------------------------------------------------------------
  0            /bin/nano            40        auto mode
  1            /bin/ed             -100       manual mode
  2            /bin/nano            40        manual mode
  3            /usr/bin/gedit       10        manual mode
* 4            /usr/bin/vim.basic   30        manual mode
  5            /usr/bin/vim.tiny    10        manual mode

Press enter to keep the current choice[*], or type selection number: 4
matthew@matthew-Aspire-7540 ~ %
```

Hopefully this will recreate the symlinks for you.

Kind regards

---

### Post by cmcanulty on 2012-06-18
OK but gedit doesn't show up it is installed, how do I add it?

```
cmcanulty@Darcy25:~$ sudo update-alternatives --config editor
[sudo] password for cmcanulty: 
There are 9 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Path                 Priority   Status
------------------------------------------------------------
  0            /usr/bin/vim.gnome    60        auto mode
  1            /bin/ed              -100       manual mode
  2            /bin/nano             40        manual mode
  3            /usr/bin/cream        0         manual mode
  4            /usr/bin/emacs23      0         manual mode
  5            /usr/bin/vim.athena   50        manual mode
  6            /usr/bin/vim.basic    30        manual mode
  7            /usr/bin/vim.gnome    60        manual mode
  8            /usr/bin/vim.gtk      50        manual mode
  9            /usr/bin/vim.tiny     10        manual mode

Press enter to keep the current choice[*], or type selection number: ^Ccmcanulty@Darcy25:~$
```

---

### Post by matt_symes on 2012-06-18
Hi

AFTER you have finished selecting all your alternatives and you get back to the command prompt...

```
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/gedit 80
```

```
sudo update-alternatives --config editor
```

and select gedit.

You should then be good to go (hopefully :) ).

Kind regards

---

### Post by cmcanulty on 2012-06-18
Wow, that worked and now gedit is set. Thanks so much. That is fixed but I am still getting the errors on update and numerous searches haven't helped. And that seems to prevent gnome tweak and ubuntu tweak from opening


```

Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 236: /usr/sbin/update-initramfs: awk: not found
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nfs-common
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by matt_symes on 2012-06-18
Hi

> Wow, that worked and now gedit is set. Thanks so much. That is fixed but I am still getting the errors on update and numerous searches haven't helped

Excellent :) Nicely done as well cheesemill !

Open other threads for your other problems and mark this one as solved. 

You can PM me the links if you like.

Kind regards

---

### Post by cmcanulty on 2012-06-18
Great thanks so much!

---

### Post by Cheesemill on 2012-06-18
> **cmcanulty said:**
> Wow, that worked and now gedit is set. Thanks so much. That is fixed but I am still getting the errors on update and numerous searches haven't helped. And that seems to prevent gnome tweak and ubuntu tweak from opening


```

Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 236: /usr/sbin/update-initramfs: awk: not found
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nfs-common
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Glad we all got there in the end :)

I think you'd be better off starting a new thread about those apt-get errors, you're likely to get better help with a thread title that matches that specific problem. It will also help people in the future when they search for solutions.


Edit - Ninja'd :)

---

