---
title: "Can't execute program - says cannot be found"
date: 2009-02-22
forum: Programming Talk
---

### Post by maxtor87 on 2009-02-22
Hi guys, new here - hope you're all well.

Just installed a fresh version of ubuntu onto one of laptops and for some reason I can't execute any programs that I compile with gcc.. it just says command not found..

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/sda1 type ext3 (rw,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)

```

And using pysdm it says that it allows files to be executed.. btw I'm fairly n00bish to linux.

Thanks for any help.

---

### Post by cabalas on 2009-02-22
Would you be able to post the command you are using to run the program?  If you are in the directory that the program is in have you tried adding a ./ to the beginning of it, like so:

```
./program_name
```

---

### Post by stefangr1 on 2009-02-22
You do know that the files produced by gcc are named a.out by default? So then you have to execute ./a.out  .

---

### Post by maxtor87 on 2009-02-22
Ooh ok I see, this is what I ran:

```
[michael:~/Documents/C]$ ls
square.c  square.c~
[michael:~/Documents/C]$ gcc square.c -o square
[michael:~/Documents/C]$ ls
square  square.c  square.c~
[michael:~/Documents/C]$ square
bash: square: command not found
[michael:~/Documents/C]$ ./square
	Number		Square of Number

	0		0
...

```

So why does the './' have to be there? I know it means the current directory but it usually assumes you mean the current directory does it not?

Thanks guys! Was confusing me greatly.

---

### Post by cabalas on 2009-02-22
Unfortunately when it comes to running programs it does not assume that it will be in the current directory.  It thinks that any applications you want to run will be in your PATH environment variable unless you specify where the program is.

I hope that makes sense to you, as reading it again I don't think I wrote it all that well but I can't think of a better way to put it.

---

### Post by uprooted on 2009-02-22
i use g++ -o name name.cpp for my c++ progs if that helps

all i have to type after that is ./name

cheers

---

### Post by maxtor87 on 2009-02-22
Cool, thanks - I get it now :)

---

