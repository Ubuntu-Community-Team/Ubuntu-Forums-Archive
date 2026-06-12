---
title: "Problem bash: /sbin/ifconfig: cannot execute binary file"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by ymsaputra on 2013-01-14
Dear ALL,

I have a problem in using ifconfig. Previously there is no problem about this. But today suddenly when I type ifconfig as usual this error message appears.

bash: /bin/ifconfig: cannot execute binary file (i don't know why this ifconfig in bin folder)

and then I move ifconfig to sbin folder and then I will get similar error

bash: /sbin/ifconfig: cannot execute binary file

I have already used root user too but the same problem still occurs

What should I do to fix this?

Thank you so much for the answer


Best Regards,

Yuris

---

### Post by von Corax on 2013-01-14
This is purely a guess, but run [FONT=Courier New]ls -l /sbin/ifconfig[/FONT] (or [FONT=Courier New]/bin/ifconfig[/FONT]) and check that the result begins with -r-xr-xr-x (the first hyphen (-) must be there; the others may be 'w's instead.) If you don't see 'x'es, then do [FONT=Courier New]chmod a+x /sbin/ifconfig[/FONT] and see if that fixes the problem.

---

### Post by ymsaputra on 2013-01-14
I check by using  [FONT=Courier New]ls -l /sbin/ifconfig[/FONT] and then I get this result

-rwxr-xr-x 1 ymsaputra ymsaputra 399529 Dec 27 22:57 /sbin/ifconfig

is it true or not?

then I do [FONT=Courier New]chmod a+x /sbin/ifconfig [/FONT]and the same problem is still occured

Thank you

---

### Post by ymsaputra on 2013-01-14
I think the problem is in ymsaputra ymsaputra. In other computer I check that must be root root. Do you know how to change ymsaputra to root?

---

### Post by steeldriver on 2013-01-14
```
sudo chown root:root /sbin/ifconfig
```However since it is already executable for everyone I think you have other issues - how exactly did ifconfig get moved? what else were you doing when things started to go wrong?

Sometimes these kind of binary errors are related to broken/missing libraries I think

---

### Post by ymsaputra on 2013-01-15
Yes, i still can not use ifconfig even I change to root. I can not use netstat too.

I don't know the detail how ifconfig can move to bin, previously I make new hostname by using this command

[COLOR=#808000]sudo hostname ymsaputra and then using sudo su to root[/COLOR]
Is this related to that problem? 

After this goes wrong I don't do anything except just try using ifconfig with several configuration like 

strace /sbin/ifconfig and then I get this result :

ymsaputra@ymsaputra-desktop:~$ strace /sbin/ifconfig
execve("/sbin/ifconfig", ["/sbin/ifconfig"], [/* 39 vars */]) = -1 ENOEXEC (Exec format error)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7745000
_llseek(3, 0, 0xbfcbf0b0, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Exec format error\n", 32strace: exec: Exec format error
) = 32
close(3)                                = 0
munmap(0xb7745000, 4096)                = 0
exit_group(1)                           = ?

I'm stuck in this. What should I do to fix this?

Thank you so much for your help

---

### Post by Impavidus on 2013-01-15
In my case it's```
$ ls -l /sbin/ifconfig
-rwxr-xr-x 1 root root 69572 mrt 31  2012 /sbin/ifconfig
```The first part are the permissions. If it doesn't read as -rwxr-xr-x you can fix it with```

sudo chmod 755 /sbin/ifconfig
``` The "root root" indicates it's owned by root. If this is not the case on your computer you can repair with```

sudo chown root:root /sbin/ifconfig
```However, these errors should only give you the "Permission denied" error message. You got the "Cannot execute binary file" message. Also, your ifconfig is 400kB, whilst mine is just 70kB. Sounds like something is wrong with  that file. Try reinstalling net-tools. That's the package containing ifconfig and netstat.

---

### Post by ymsaputra on 2013-01-15
OK I've already fixed it by re-installing my ubuntu without deleting the installed packaged.

Thank you for new knowledge about Ubuntu from you all.

---

### Post by wolf2600 on 2013-04-28
> **Impavidus said:**
> In my case it's```
$ ls -l /sbin/ifconfig
-rwxr-xr-x 1 root root 69572 mrt 31  2012 /sbin/ifconfig
```The first part are the permissions. If it doesn't read as -rwxr-xr-x you can fix it with```

sudo chmod 755 /sbin/ifconfig
``` The "root root" indicates it's owned by root. If this is not the case on your computer you can repair with```

sudo chown root:root /sbin/ifconfig
```However, these errors should only give you the "Permission denied" error message. You got the "Cannot execute binary file" message. Also, your ifconfig is 400kB, whilst mine is just 70kB. Sounds like something is wrong with  that file. Try reinstalling net-tools. That's the package containing ifconfig and netstat.


I was getting the same error on my Raspberry Pi.  Found that the -ia flags were set for the file (even preventing me from removing/reinstalling net-tools.

do:  lsattr /sbin/ifconfig 
and see if i or a are set.  Then use chattr -ia /sbin/ifconfig to unset them.

---

