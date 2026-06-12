---
title: "Trascode problems"
date: 2005-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by jworr on 2005-09-18
I've been cruising the forums and I found a couple threads ([http://www.ubuntuforums.org/showthread.php?t=60359&highlight=transcode](http://www.ubuntuforums.org/showthread.php?t=60359&highlight=transcode))
([http://www.ubuntuforums.org/showthread.php?t=59665&highlight=transcode](http://www.ubuntuforums.org/showthread.php?t=59665&highlight=transcode))

that told me to add

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

to my apt.sources list to get access to transcode and dvdrip, however I can't seem to 
download anything from these two sources

did I miss something?

this is what my current sources.list looks like:

 ## Main archive
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

## Security
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

## Backports
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

---

### Post by benplaut on 2005-09-18
This forum is for HOWTOs and Frequently Asked Questions only  :wink: 
[http://ubuntuforums.org/announcement.php?f=58](http://ubuntuforums.org/announcement.php?f=58)

back to your question, try a "sudo apt-get update" and then insatll the packaged  :)

---

### Post by jworr on 2005-09-18
Sorry my mistake ... but I still have some issues

I ran sudo apt-get update and I got some errors along with some success:

Err [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/universe Packages
  Connection timeout
Err [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/multiverse Packages
  Connection timeout
Get:18 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/restricted Packages [4527B]
Get:19 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages [30.3kB]
Err [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages
  Data socket timed out
Get:20 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages [42.2kB]
Err [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages
  Data socket timed out
Get:21 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/multiverse Packages [438B]
Err [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/restricted Packages
  Connection timeout
Fetched 24.5kB in 18m56s (22B/s)
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/hoary-extras/universe/binary-i386/Packages.gz](ftp://ftp2.caliu.info/backports/dists/hoary-extras/universe/binary-i386/Packages.gz)  Connection timeout
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz](ftp://ftp2.caliu.info/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  Connection timeout
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz)  Data socket timed out
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz](ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz)  Data socket timed out
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz](ftp://ftp2.caliu.info/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz)  Connection timeout
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drogoh on 2005-09-18
Perhaps you should try using different mirrors and try again...

I know the host is reachable from where I am but the Internet is enigmatic and what I can reach maybe you can't and vice versa.

---

