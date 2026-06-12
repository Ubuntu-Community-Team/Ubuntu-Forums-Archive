---
title: "Configuring Lubuntu to use company proxy"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by Bob_Hartung on 2014-05-05
I am fairly new to Lubuntu and come from a Windows background.

I have installed Lubuntu on a couple of old Dell XP PCs. These PCs are intended for mulitiple users with their own logins. I want to set them up so that the users will be redirected to the company proxy server to access the internet. In Windows, this is a fairly simple setting but not so much in Unbuntu.

First of all, Unbuntu apparently has a "Network Proxy" configuration utility right in Preferences but Lubuntu doesn't have anything. Is there supposed to be one?

Most of the information I've found about Unbuntu and proxy use look like this...

Your /etc/environment needs to have the following proxy configuration:

  no_proxy=localhost,127.0.0.0/8,*.local
NO_PROXY=localhost,127.0.0.0/8,*.local
all_proxy=socks://proxy.example.com:8080/
ALL_PROXY=socks://proxy.example.com:8080/
http_proxy=http://proxy.example.com:8080
HTTP_PROXY=http://proxy.example.com:8080
ftp_proxy=http://proxy.example.com:8080
FTP_PROXY=http://proxy.example.com:8080  
https_proxy=http://proxy.example.com:8080
HTTPS_PROXY=http://proxy.example.com:8080
  
You must log out before your desktop environment will refresh it's  environment variables. As all desktop applications are started by the  desktop environment, they subsequently inherit its environment settings.
  Next, you'll need to update your apt configuration. Create a file  called /etc/apt/apt.conf and edit it to contain these declarations:
  
Acquire::http::proxy "http://proxy.example.com:8080/";
Acquire::ftp::proxy "ftp://proxy.example.com:8080/";
Acquire::https::proxy "https://proxy.example.com:8080/";

I've tried this but it doesn't seem to work the way I would expect it. To test I went to Xterm and entered the command ...
sudo apt-get update
All the updates fail with the message "407 Proxy Authentication Required". I expected when the command is launched you'd be prompted once for a username and password and then the
command would continue and finish successfully.

What am I missing?

---

### Post by bapoumba on 2014-05-05
Is 8080 this the correct port ?

---

### Post by Bob_Hartung on 2014-05-06
That is the port our firewall uses. Apparently this is a fairly common practice when a proxy is used.

---

### Post by bapoumba on 2014-05-06
That was not my question :)

Now if the port is correct, you need authentication.

[noparse]http_proxy=http://username:password@proxyhost:port/[/noparse]

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

### Post by Bob_Hartung on 2014-05-06
Then my previous answer was not my answer. :razz:

Our  proxy does require authentication. I tried the command you referenced,  even tried all uppercase (HTTP_PROXY). Unfortunately, that did not seem  to correct the problem. I still got a bunch of errors like this when I  used apt-get...

     W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages)   407  Proxy Authentication Required

Our proxy, which is part of our firewall device, doesn't seem to accept this particular format.

---

### Post by bapoumba on 2014-05-06
Is this a ISA proxy ?
[http://ubuntuforums.org/showthread.php?t=1802306](http://ubuntuforums.org/showthread.php?t=1802306)

Edit: the trailing semicolon is _mandatory_.

---

### Post by Bob_Hartung on 2014-05-06
No, it is a firewall appliance called an Instagate (eSoft). It has a Linux based OS.

---

### Post by bapoumba on 2014-05-06
> **Bob_Hartung said:**
> No, it is a firewall appliance called an Instagate (eSoft). It has a Linux based OS.

I am not familiar with these firewalls. Could you please contact the person in charge and see if they could authorize apt-get ?

---

