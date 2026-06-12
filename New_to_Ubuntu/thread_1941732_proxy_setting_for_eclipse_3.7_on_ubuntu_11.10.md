---
title: "proxy setting for eclipse 3.7 on ubuntu 11.10"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by huu2011 on 2012-03-16
Hello again.
Please,any one with idea how to set up eclipse 3.7 to work with proxy server on ubuntu 11.10?
Any help will appreciate it is a month now keep trying without success.
thank you again
huu

---

### Post by huu2011 on 2012-03-16
please experts,anyone with eclipse working on proxy setting?

thank you again
huu

---

### Post by banskt on 2012-05-17
Well, I found a workaround:

Add the following lines to /etc/eclipse.ini file: 
> -Dorg.eclipse.ecf.provider.filetransfer.excludeContributors=org.eclipse.ecf.provider.filetransfer.httpclient
-Dhttp.proxyPort=xxxx
-Dhttp.proxyHost=yourproxy.domain.com
-Dhttp.proxyUser=xxxxx
-Dhttp.proxyPassword=xxxxxx
-Dhttp.nonProxyHosts=localhost|127.0.0.1
Save, and restart eclipse

[Checked working for eclipse 3.7 on Ubuntu 12.04, so it should possibly work on 11.10]

Reference: [https://bugs.eclipse.org/bugs/show_bug.cgi?id=281472#c7](https://bugs.eclipse.org/bugs/show_bug.cgi?id=281472#c7)

---

