---
title: "Dependency errors"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by andrew cooke on 2012-07-01
Hi,

Just installed Ubuntu (although have used OpenSuse for decades so am not sure if I am in the right group - sorry if not).  When I try to install r-base-core:i386 from the Ubuntu Software Centre I get the following message:

The following packages have unmet dependencies:

r-base-core:i386: Depends: libgfortran3 (>= 4.3) but 4.6.3-1ubuntu5 is to be installed
                  Depends: libgomp1 (>= 4.2.1) but 4.6.3-1ubuntu5 is to be installed
                  Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is to be installed
                  Depends: liblzma5 (>= 5.1.1alpha+20110809) but 5.1.1alpha+20110809-3 is to be installed
                  Depends: libpcre3 (>= 8.10) but 8.12-4 is to be installed
                  Depends: libreadline6 (>= 6.0) but 6.2-8 is to be installed
                  Depends: tcl8.5 (>= 8.5.0) but 8.5.11-1ubuntu1 is to be installed
                  Depends: tk8.5 (>= 8.5.0) but 8.5.11-1 is to be installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed
                  Depends: ucf (>= 3.0) but 3.0025+nmu2ubuntu1 is to be installed

First of all, all those seem to be fine (they are all >= as far as I can tell).  And second, I have no idea how to fix this.  What do I do?

Also - teach me to fish - is there a good source of documentation that would answer questions like this?

Thanks,
Andrew

PS, It's ubuntu 12.04 LTS, 64 bit.

---

### Post by andrew cooke on 2012-07-01
well

  apt-get -o Debug::pkgDepCache::AutoInstall=yes install r-base-core

seems to be working just fine (still running).

as far as i can tell, i am not doing anything odd here - not forcing anything - so i guess the original error is just a bug in the parser of version numbers for the software centre?

andrew

---

### Post by spikoley on 2012-07-01
Try installing it from the shell to see what happens there.  Post any errors.

```
sudo apt-get install r-base-core
```

---

### Post by matt_symes on 2012-07-01
Hi

> r-base-core:i386> PS, It's ubuntu 12.04 LTS, 64 bit.Is there any reason you were installing the 32bit version and not the 64 bit version ?

Maybe this is where the problem lies. It was probably having problems installing the 32 bit libraries for it.

  > apt-get -o Debug:dpkgDepCache::AutoInstall=yes install r-base-coreThis will ensure it installs the corrrect version and dependencies archectiture for your OS. It would have installed the 64 bit version and the 64bit dependencies.

In the final instance though, as spikoley pointed out, you only need

```
sudo apt-get install r-base-core
```Kind regards

---

### Post by andrew cooke on 2012-07-01
huh.  no idea how i ended up with that (i had problems searching for it initially - "R" isn't the easiest thing to find).

indeed, installing at the command line worked.

thanks to all replies (i got the command line from googling just as the other reply arrived, by the looks of the time stamps).

---

