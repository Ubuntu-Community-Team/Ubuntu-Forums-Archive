---
title: "error message when istalling software throu synaptec"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-17
im getting these messages when i install anything
 

any ideas as to whats going on?

---

### Post by Patb on 2008-05-17
Patrick, where it says: "For further details of the failure, please expand the 'terminal' panel below" try doing just that and then post the output.  

Cheers, Pat.

---

### Post by shadow-of-sin on 2008-05-17
Type this in a terminal:
```
sudo apt-get install msttcorefonts
```

Your msttcorefonts haven't been installed properly, hence the error message.

---

### Post by PatrickMoore on 2008-05-17
> **shadow-of-sin said:**
> Type this in a terminal:
```
sudo apt-get install msttcorefonts
```

Your msttcorefonts haven't been installed properly, hence the error message.

when entered interminal i got

```
patrick@patrick-laptop:~$ sudo apt-get install msttcorefonts
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
The following packages were automatically installed and are no longer required:
  anyevent-perl liblzo1 artsbuilder libevent-rpc-perl libgtk1.2 libfame-0.9
  libtaglib2.0-cil libsvga1 libswscale1d libmono-cairo2.0-cil libtagc0
  python-gnome2-extras libavahi1.0-cil libpvm3 python-mutagen libtunepimp5
  libgtk2-ruby1.8 libiso9660-5 libfftw3-3 libgdl-gnome-1-0 libgdl-1-common
  mplayer-skins libglib1.2ldbl libggi2 libgii1 libgconf2-ruby1.8
  libmono-zeroconf1.0-cil libgconf2-ruby libgda3-common libifp4
  libglib2-ruby1.8 libgii1-target-x libglade2-ruby1.8 libcairo-ruby1.8
  libkarma0 python-pyvorbis libgtk1.2-common libatk1-ruby1.8 libpango1-ruby1.8
  libgda3-3 libgdk-pixbuf2-ruby1.8 python-pymad libimlib2 libvcdinfo0
  python-pyogg libnjb5 libgdl-1-0 libofa0 libboo2.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by PatrickMoore on 2008-05-17
> **Patb said:**
> Patrick, where it says: "For further details of the failure, please expand the 'terminal' panel below" try doing just that and then post the output.  

Cheers, Pat.

the  full details look like

---

### Post by Patb on 2008-05-18
Patrick, Shadow's method gave much the same information in a better way.  

From the looks of that error message, your repositories settings may not be right.  Try checking what repositories you are using and set them to ones that are likely to be available.  This link will give you guidance:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

To select the best/fastest source server in Synaptic you may wish to try the method shown here:
[http://www.ubuntu-unleashed.com/2007/09/choose-fastest-apt-repository-with.html](http://www.ubuntu-unleashed.com/2007/09/choose-fastest-apt-repository-with.html)

Cheers, Pat.

---

### Post by Muflon on 2008-05-29
I had the same issue here because I access the internet via a proxy server.  

I fixed the problem by adding the proxy settings to System/Preferences/Network Proxy.  Under Manual Proxy Configuration enter your proxy details and press the Details button to add your authentication.

Start a terminal session and check your http_proxy settings.  Your new proxy settings only get picked up in a new terminal, not an existing terminal shell.

```
env | grep http_proxy
```

You should now have an entry.

You can now uninstall msttcorefonts using

```
sudo apt-get remove msttcorefonts
```

This worked for me but your experience may vary.

Muflon

---

