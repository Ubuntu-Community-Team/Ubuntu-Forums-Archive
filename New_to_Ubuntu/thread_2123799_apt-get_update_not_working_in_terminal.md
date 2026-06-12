---
title: "apt-get update not working in terminal"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by sudeshkagrawal on 2013-03-09
All was a few days and suddenly apt-get update stopped working on terminal.
I am under a proxy which requires authentication.
My apt.conf file:
Acquire::http::proxy "[http://netmon.iitb.ac.in:80/](http://netmon.iitb.ac.in:80/)";
Acquire::ftp::proxy "[ftp://netmon.iitb.ac.in:80/](ftp://netmon.iitb.ac.in:80/)";
Acquire::https::proxy "[https://netmon.iitb.ac.in:80/](https://netmon.iitb.ac.in:80/)";
ACQUIRE { 

http::proxy "http://<username>:<password>@[netmon.iitb.ac.in:80/]("http://netmon.iitb.ac.in:80/")" 
}

APT 
{
// Options for the downloading routines
Acquire
{
http
{

No-Cache "true";
};
};
}
//Acquire::http::proxy "[http://netmon.iitb.ac.in:80/](http://netmon.iitb.ac.in:80/)";
There shouldn't be a problem with the code in apt.conf since I have been using the same since 2 years.
My .bashrc is also set to export the proxy. I am not sure but it is probably to export the proxy to other environment?
Update is working through synaptic. Currenlty I am using Synaptic to update.
But local sites have stopped opening firefox,chromium and google chrome concurrently i.e. they started happening at the same time.
Before the problem started the status was:
update worked fine
local sites opened in all browsers
but SSL sites (like mail.google.com) did not open in chromium and google chrome though they opened in ff. I used to get error 107 and this problem is still not fixed

OS: Ubuntu 12.10 (Linux 3.5.0-25-generic)
I have windows 8 installed side by side on a different partition.

---

### Post by Mark_in_Hollywood on 2013-03-09
Can you run 

fsck

from the grub OS selection screen? That screen appears before the screen where you would enter your password.

---

### Post by darkcrimson on 2013-03-09
That really stinks you can't apt-get update. Try this and post the output if errors are received:

```
wget http://gb.archive.ubuntu.com/ubuntu/dists/quantal/Release
```

If there's an issue with the proxy not resolving or requiring auth, we'll see it in the output. Hope this helps!

---

### Post by tgalati4 on 2013-03-09
Or your proxy administrator has slapped some rules that are limiting your bandwidth.  Talk with your IT folks.

---

