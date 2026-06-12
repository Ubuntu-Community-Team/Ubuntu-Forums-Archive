---
title: "Proxy Authentication error in apt-get"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by amit.padhy on 2008-08-10
Hello, everyone!!!
i have installed ubuntu8.04 recently, and have been trying to get the repository working..
But when i do a "sudo apt-get ...", it says:
```
Failed to fetch http://ftp.iitm.ac.in/ubuntu/dists/gutsy-security/universe/source/Sources.gz  407 Proxy Authentication Error [IP 10.93.0.35 3128]

```
and similar stuff.
I have also tried modifying http_proxy and ftp_proxy environment variables in  
~/.bashrc and /etc/apt/apt.conf, but to no avail.
What should I do??
Thanks in advance for the help.

---

### Post by fahadsadah on 2008-08-10
Do you have working internet?
Please post the contents of the variables.

PS: Offtopic: this is my 100th post!

---

### Post by acidsolution on 2008-08-10
Try using Synaptic by setting the proxy configuration in the preference-> Networking option 
and than reload and try 
and reply if it works or not

---

### Post by mgmoore on 2008-08-11
I am having the same issue.
Here is the error I'm getting:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.3.3+0.4-0ubuntu0.8.04.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.3.3+0.4-0ubuntu0.8.04.3_all.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu2.1_all.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

when I do an "export" on command line I get:
declare -x http_proxy="http://:8080/"
declare -x no_proxy="localhost,127.0.0.0/8,*.local"

in  system -> pref -> networking proxy I'm using the correct proxy with the correct port, I've tried with and without "details" having information in there.

Help?  :)

---

### Post by StevenHarper on 2008-09-09
> **acidsolution said:**
> Try using Synaptic by setting the proxy configuration in the preference-> Networking option 
and than reload and try 
and reply if it works or not

Doing this worked for me in the Alpha5 of 64bit 8.10

Steve

---

### Post by MegaJim on 2008-09-09
if you're using apt-get on the command line, you need to set the proxy environmental variable in your ~.bashrc file, for example, in my bashrc i have the following:

```
# my proxy
export http_proxy="http://domain-name.com:port"

```

then restart the terminal and have another go.

you need to make sure you have the http:// in the proxy url and the whole thing enclosed in brackets with a colon separating the domain name and port, or apt-get will not understand the address.

On the other hand if you're just using update manager, synaptic or gnome add/remove programs it is enough to configure the proxy from synaptic's network options

---

### Post by Dougga on 2009-10-05
Thanks for this suggestion.

This did the trick for me.
There are numerous threads out here on this topic and most seem to point people to the /etc/apt/apt.conf file which is of no help.

Thanks again.

PS: Is there a way to secure this proxy setting?
    Thanks.

---

