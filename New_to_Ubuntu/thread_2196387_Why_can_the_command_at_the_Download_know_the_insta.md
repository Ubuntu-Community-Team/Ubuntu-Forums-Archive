---
title: "Why can the command at the Download know the installation file in /tmp/install?"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by ruwan2 on 2013-12-29
Hi,

I download an installation tar file at Downloads folder. The official website command is:

tar xvfz /tmp/ccsv5_install setup_CCS_5.x.x.0xxxx.tar.gz

It does not work on the Ubuntu 12.04.

I find another method from a post. It is:


So these steps were taken:
 $ mkdir /tmp/ccsv5_install
 $ cd /tmp/ccsv5_install
 $ tar xvfz ~/Downloads/CCS5.3.0.00090_linux.tar.gz
 

I add these procedures from the original software website:

cd ~/Downloads
./ccs_setup_5.3.0.00090.bin &

My question is:
I don't know why it works. Does "ccs_setup_5.3.0.00090.bin" look for those files in /tmp/ccsv5_install automatically?

What is function of '&' at the end?
Thanks,

---

### Post by ian-weisser on 2013-12-29
> **ruwan2 said:**
> Does "ccs_setup_5.3.0.00090.bin" look for those files in /tmp/ccsv5_install automatically?

Yes, but only that's what the programmer told the .bin file to do. If you move the files somewhere else, the .bin file won't find them. The system won't magically point an application to the files automatically.

> **ruwan2 said:**
> What is function of '&' at the end?

It backgrounds the job. The unfinished job continues to run in the background, while the shell in the foreground gives you a command prompt to do your next task.

---

