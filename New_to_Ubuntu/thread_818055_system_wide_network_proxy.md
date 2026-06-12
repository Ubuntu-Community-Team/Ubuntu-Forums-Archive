---
title: "system wide network proxy??"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Blue Lightning Computers on 2008-06-04
hi all

i have just installed xubuntu 8.04 on a machine and cannot find how to set the system wide network proxy

can someone please let me know how

thanks

---

### Post by gvartser on 2008-06-04
Add the following entry to the global profile:
export http_proxy="http://proxylocation:yourport"

or you could always use the 
System -> Preferences -> Network Proxy. (But this is only user depended.)

Best regz,
/g

---

### Post by Blue Lightning Computers on 2008-06-04
hi

where do i get to the global profile to add this line

there is no system ->preferences ->network proxy on xubuntu i am very familier with setting things on ubuntu just not with the xfce desktop on xubuntu

---

### Post by rally4life on 2008-10-03
Is there a way to get Gnome's Network Proxy Preferences tool in xubuntu?  I can't seem to find it anywhere.  Or some other proxy preferences tool.

---

### Post by FlintZA on 2008-11-19
I'm also looking to an answer for this. Does anyone have a commandline script that can be used to set global proxy preferences (if such a thing exists) or a way to get hold of a GUI that does the same job?

---

### Post by moore.bryan on 2009-06-11
i don't know if this thread is still "live," but you can just install ubuntu-system-service and get network-proxy...

---

### Post by johnm64118 on 2009-12-16
In order to set a global proxy, you need to edit the following files:

I use mc (Midnight Commander) to do this.
Install mc by using:

```
sudo apt-get install mc
```

Then, sudo mc, to browse to and edit the files.

The first file to edit is:
/etc/apt/apt.conf

You should add a line similar to this one. It depends on your proxy server address.
Acquire::http::Proxy "http://192.168.0.1:3128/";

This will allow synaptic to work properly.

In order for wget to work, you need to edit:
/etc/wgetrc

About 1/3 way down, remove the #s and change
the address to your proxy server address.

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://192.168.0.1:3128/](http://192.168.0.1:3128/)
ftp_proxy = [http://192.168.0.1:3128/](http://192.168.0.1:3128/)

# If you do not want to use proxy at all, set this to off.
use_proxy = on

I still set the proxy within Firefox since it doesn't seem
to know this one exists.

I hope this helps!!!

John

---

### Post by ziawiki on 2012-09-12
I tried the "dconf-tools" Gnome package in Xfce and it works.

---

### Post by Toz on 2012-09-12
Old thread. 
Closed.

---

