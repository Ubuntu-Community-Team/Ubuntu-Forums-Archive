---
title: "apt-get update - error"
date: 2007-07-19
forum: Programming Talk
---

### Post by zoobave on 2007-07-19
Hi, 
    When i give "apt-get update" command, i got the following errors. How can i resolve it?


```
root@dvm-desktop:/home/dvm# apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_IN
Get:2 http://in.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://in.archive.ubuntu.com feisty/main Translation-en_IN
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_IN
Ign http://security.ubuntu.com feisty-security/universe Translation-en_IN
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com feisty/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com feisty/universe Translation-en_IN
Ign http://in.archive.ubuntu.com feisty/multiverse Translation-en_IN
Get:3 http://in.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://in.archive.ubuntu.com feisty-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com feisty-updates/restricted Translation-en_IN
Get:4 http://security.ubuntu.com feisty-security Release [50.9kB]
Hit http://in.archive.ubuntu.com feisty Release
Hit http://in.archive.ubuntu.com feisty-updates Release
Hit http://in.archive.ubuntu.com feisty/main Packages
Hit http://in.archive.ubuntu.com feisty/restricted Packages
Ign http://in.archive.ubuntu.com feisty/main Sources
Hit http://in.archive.ubuntu.com feisty/restricted Sources
Hit http://in.archive.ubuntu.com feisty/universe Packages
Hit http://in.archive.ubuntu.com feisty/universe Sources
Hit http://in.archive.ubuntu.com feisty/multiverse Packages
Hit http://in.archive.ubuntu.com feisty/multiverse Sources
Hit http://in.archive.ubuntu.com feisty-updates/main Packages
Hit http://in.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://in.archive.ubuntu.com feisty-updates/main Sources
Get:5 http://security.ubuntu.com feisty-security/main Packages [52.1kB]
Hit http://in.archive.ubuntu.com feisty-updates/restricted Sources
Get:6 http://in.archive.ubuntu.com feisty/main Sources [385kB]
95% [6 Sources gzip 0] [5 Packages 28416/52.1kB 54%]
gzip: stdin: not in gzip format
Err http://in.archive.ubuntu.com feisty/main Sources
  Sub-process gzip returned an error code (1)
Get:7 http://security.ubuntu.com feisty-security/restricted Packages [6360B]
Get:8 http://security.ubuntu.com feisty-security/main Sources [9496B]
Get:9 http://security.ubuntu.com feisty-security/restricted Sources [953B]
Get:10 http://security.ubuntu.com feisty-security/universe Packages [19.7kB]
Get:11 http://security.ubuntu.com feisty-security/universe Sources [2522B]
Get:12 http://security.ubuntu.com feisty-security/multiverse Packages [5412B]
Get:13 http://security.ubuntu.com feisty-security/multiverse Sources [836B]
Fetched 148kB in 4s (34.1kB/s)
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@dvm-desktop:/home/dvm#

```




Regards,
Zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---

### Post by smartbei on 2007-07-19
This is the wrong place for this question. Try the General Help Forum.

---

