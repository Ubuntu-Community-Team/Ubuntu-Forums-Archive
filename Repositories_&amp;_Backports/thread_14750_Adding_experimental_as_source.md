---
title: "Adding experimental as source"
date: 2005-02-09
forum: Repositories &amp; Backports
---

### Post by tr3y on 2005-02-09
My current apt.sources file looks like this:

```
trey@salamander:/etc/apt$ cat sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050131)]/ unsta ble main restricted


deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse

#deb http://security.ubuntu.com/ubuntu hoary-security main restricted
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse
``` 

I'd like to get sylpheed-claws-gtk2 packages from experimental.  Can I add experimental sources to my existing list?  Will that mess up my currently installled files and updating?

If I can do this, what's the syntax?

Thanks.

---

