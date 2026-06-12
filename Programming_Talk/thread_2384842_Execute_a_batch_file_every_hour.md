---
title: "Execute a batch file every hour"
date: 2018-02-12
forum: Programming Talk
---

### Post by dam034 on 2018-02-12
Dear users,

I created a batch file. I want to execute it every hour as root user.

The batch file is in /srv/cmd/, I created a symbolic link in /etc/cron.hourly but it doesn't work.

How can I fix?

Thanks

---

### Post by oldos2er on 2018-02-12
Do you mean a bash script? I haven't heard the term batch file in quite a long time.

---

### Post by papibe on 2018-02-12
Hi dam034.

I would start checking the permissions. Could you run these commands and post back the results? (You can copy/paste the text. Please use CODE tags)
```
ls -l /srv/cmd/your_script

ls -ls  /etc/cron.hourly/link_to_your_script
```
Then I would double check (1) you have the proper shebang, (2) that the commands you are executing are in the PATH (which is usually not the same that the default you use for regular users), and finally (3) revise if you have interactive content that won't work on a cron script. 

The easiest way to help you would be to post the script.

Regards.

---

### Post by dam034 on 2018-02-13
These are the commands:

```
root@ubrouter:/srv/cmd# ls -l
totale 8
-rwxrwx--- 1 dam034 apgr 445 feb 12 18:36 aggiornamento.sh
-rwxrwx--- 1 dam034 apgr 320 feb 13 00:54 registro.log

```
```
root@ubrouter:/etc/cron.hourly# ls -l
totale 0
lrwxrwxrwx 1 root root 33 feb 12 18:35 ddns.sh -> /srv/cmd/aggiornamento.sh
```
As you can see, I want to execute the command as root user.


What is the matter?

Thanks

---

### Post by steeldriver on 2018-02-13
Filenames (and I assume this applies to symlinks as well) in the /etc/cron.houly, /etc/cron.daily etc. directories have some particular requirements. Form the DEBIAN SPECIFIC section of `man cron`:

```

       As  described  above, the files under these directories have to be pass
       some sanity checks including the following: be executable, be owned  by
       root,  not  be  writable  by  group or other and, if symlinks, point to
       files owned by root. [B]Additionally, the file names must conform  to  the
       filename  requirements  of  run-parts: they must be entirely made up of
       letters, digits and can only  contain  the  special  signs  underscores
       ('_')  and  hyphens  ('-').  Any  file  that  does not conform to these
       requirements will not be executed by run-parts.  [COLOR=#ff0000]For example, any  file
       containing  dots  will  be  ignored.[/COLOR][/B]

```

---

