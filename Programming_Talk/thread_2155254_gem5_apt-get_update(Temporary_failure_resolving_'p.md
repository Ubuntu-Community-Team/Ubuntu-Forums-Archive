---
title: "gem5 apt-get update(Temporary failure resolving 'ports.ubuntu.com')"
date: 2013-06-17
forum: Programming Talk
---

### Post by DexyDean on 2013-06-17
Hello, I am working on something in gem5 and this is what happens when I try to update. The next thing i want to do is install sysbench but I get this error. It hangs on this part for a while:

0% [Connecting to ports.ubuntu.com]

then I get errors. This is the result and the previous 2 lines of code. I am trying to follow this for more background if needed. I followed every step perfectly. [https://www.youtube.com/watch?v=Oh3NK12fnbg](https://www.youtube.com/watch?v=Oh3NK12fnbg)


root@dexydean-Satellite-L755:/# echo "nameserver 8.8.8.8" > /etc/resolv.conf
root@dexydean-Satellite-L755:/# apt-get update
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) natty InRelease
  
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) natty Release.gpg
  Temporary failure resolving 'ports.ubuntu.com'
Reading package lists... Done      
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/natty/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/natty/InRelease)  

W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release.gpg](http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release.gpg)  Temporary failure resolving 'ports.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.


Thank you!

---

