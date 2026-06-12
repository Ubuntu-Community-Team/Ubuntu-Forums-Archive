---
title: "Repositories give error code; (127.255.102.184). - connect (111 Connection refused)"
date: 2006-06-02
forum: Repositories &amp; Backports
---

### Post by Jason_Thames on 2006-06-02
Hello all,

I have just installed Ubuntu build 6.06 LTS and everything for the most part has been working great. I had to disable IPv6 in firefox in order to get it to work with my DNS server, but I expected that I may have needed to do so. I am baffled as to why the repositories can be seen by Synaptic or apt, but will not work? Any help is appreciated...:confused: 

```
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

``` 

Regards,

--Jason

---

