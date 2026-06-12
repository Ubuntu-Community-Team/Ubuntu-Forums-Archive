---
title: "Trim on SSDs in Ubuntu 14.04"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by chris-burmajster on 2014-09-30
Hello Everybody,

I have just bought a new computer which came with an SSD. I did a fresh install of Ubuntu 14.04 64 bit and I would like to know about TRIM. Having done an internet search, it appears that a) my SSD supports trim and b) that Ubuntu 14.04 supports TRIM by default. Do I need to do anything, or is that it? Some sites say that I need to alter a certain file to make TRIM work - is that true? I'm a bit confused.

Many thanks,

Chris

---

### Post by Whoopie on 2014-09-30
The fstrim tool is part of the util-linux package. If you have an Intel or Samsung SSD, it's enabled by default.

> 
$ cat /etc/cron.weekly/fstrim
#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  [https://launchpad.net/bugs/1259829](https://launchpad.net/bugs/1259829)). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all


---

### Post by chris-burmajster on 2014-09-30
Hi Whoopie,

Thanks for your response. I believe that my SSD is a Sandisk. Does that mean that TRIM is not enabled by default? If so, do I need to do anything to enable it, as I understand that TRIM is vital for an SSD.

Thanks,

Chris

---

### Post by centaurusa on 2014-09-30
> **chris-burmajster said:**
> I believe that my SSD is a Sandisk. Does that mean that TRIM is not enabled by default? If so, do I need to do anything to enable it, as I understand that TRIM is vital for an SSD.

Two commands should help.

To check if trim is supported on your SSD (assuming that  the SSD is /dev/sda), run the following command to obtain  information (the -I option) and to identify “TRIM supported” in the  output: 

sudo hdparm -I /dev/sda | grep “TRIM supported”


The fstrim command can be initiated using the command:


 sudo fstrim -v /

 
The command is being run on the root directory (/) with the verbose (-v) option.

For more information see:

[http://linuxnorth.wordpress.com/2014/03/18/trim-your-ssd-down-to-size/](http://linuxnorth.wordpress.com/2014/03/18/trim-your-ssd-down-to-size/)

[http://linuxnorth.wordpress.com/2014/03/20/ssds-the-bigger-picture/](http://linuxnorth.wordpress.com/2014/03/20/ssds-the-bigger-picture/)

---

### Post by chris-burmajster on 2014-09-30
Thank you, centaurusa. 

I have already checked that the Sandisk supports TRIM - it does. So all I need to do is to run [COLOR=#000000]sudo fstrim -v / and that's it? Is it really that easy?

Thanks,

Chris
[/COLOR]

---

### Post by chris-burmajster on 2014-09-30
I've read the 2 links at the bottom of your post and, although they were a bit too technical for me, I understand that I have to run a TRIM command and automate it so that it runs daily. Is that correct? 

Chris

---

### Post by centaurusa on 2014-10-01
[QUOTE=chris-burmajster;13132529I understand that I have to run a TRIM command and automate it so that it runs daily. Is that correct?[/QUOTE]

For early versions of Ubuntu, it was certainly necessary to run the fstrim command in order to free up space for files that had been deleted.  I'm not sure if this is still the case in current versions.  However, running the utility manually or scheduling it to run once a day won't hurt.  Note that you don't *have* to automate the process; you can run fstrim manually any time.  Scheduling just ensures that the process occurs on some sort of regular basis.

---

### Post by chris-burmajster on 2014-10-02
Thanks for confirming that. I have used the links you gave me to schedule the TRIM command once a day. Hopefully, that should maximise the SSD's life.

Chris

---

### Post by Whoopie on 2014-10-02
SanDisk SSDs are also whitelisted, see /sbin/fstrim-all, line 68.

---

### Post by echotech2 on 2014-10-02
If I run:
```
sudo hdparm -I /dev/sda | grep “TRIM supported”
```

I get:
```
dave@dave:~$  sudo hdparm -I /dev/sda | grep “TRIM supported”
[sudo] password for dave: grep: supported”: No such file or directory

dave@dave:~$
```

  Just curious

  --Dave

---

### Post by centaurusa on 2014-10-02
Is your hard drive "sda"?  Note: "...(assuming that  the SSD is /dev/sda)..." in the prior repsonse.

---

### Post by QIII on 2014-10-02
Many SSDs may be whitelisted for fstrim.

By "enabled by default in Ubuntu" it is meant that a weekly cron job is automatically added when you install on an Intel or Samsung SSD.

I moved mine to cron.daily and added an entry for /home, too.

---

### Post by dhostick on 2015-07-05
Hi,

You need to correct the "quotes":

sudo hdparm -I /dev/sda | grep "TRIM supported"

Dave

> **echotech2 said:**
> If I run:
```
sudo hdparm -I /dev/sda | grep “TRIM supported”
```

I get:
```
dave@dave:~$  sudo hdparm -I /dev/sda | grep “TRIM supported”
[sudo] password for dave: grep: supported”: No such file or directory

dave@dave:~$
```

  Just curious

  --Dave

---

