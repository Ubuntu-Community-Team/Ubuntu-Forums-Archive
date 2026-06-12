---
title: "apt-get: get download size and install size"
date: 2009-05-15
forum: Repositories &amp; Backports
---

### Post by R33D3M33R on 2009-05-15
Hi,

I wan't to write a bash script that would get the estimated download size of a package (including missing dependencies) and estimated install size. I will use a default ubuntu install as the reference system. Can this be done somehow?

Thank you in advance!

---

### Post by unutbu on 2009-05-16
Maybe this will help you get started:
[http://ubuntuforums.org/showthread.php?t=1154940&highlight=get_dependencies](http://ubuntuforums.org/showthread.php?t=1154940&highlight=get_dependencies)

---

### Post by R33D3M33R on 2009-05-17
Hi,

thanks for the reply. The script you provided in the link works and I will use it. Thanks! 

There is still a question of download size. The apt-get command provides this data, but i'm unable to extract it without downloading and installing everything. The -s switch does not provide download size (it should be a simulation). I was thinking of using apt-get with the -d switch, then getting the size of /var/cache/apt/archives and finally everytime run apt-cache clean to clear the cache. Not so good idea if the disk space is low or running from live CD :(. Any ideas?

---

### Post by unutbu on 2009-05-17
I've modified the script at [http://ubuntuforums.org/showthread.php?t=1154940&highlight=get_dependencies](http://ubuntuforums.org/showthread.php?t=1154940&highlight=get_dependencies) to show both the download size and install size.

---

### Post by R33D3M33R on 2009-05-19
Thanks, I think this is it :)

---

