---
title: "[SOLVED] AMSN upgrade"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-10-10
Checked to see if there where another version of AMSN. And there was. But cant seem to make it through the installation procedure. Have downloaded both amsn-0.97.2-1.tcl85.x86.package and amsn-0.97.2-1.tcl84.x86.package. But none of them will run. Followed this simple [howto]("http://www.autopackage.org/docs/howto-install/"). The output and error messages I get:

```
autopackage for "AMSN MSN client"


The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2 ... 

--09:06:25--  http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:06:28 ERROR 404: Not Found.

Download failed.


Attempting download of http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2 ... 

--09:06:28--  http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving www.wildgardenseed.com... 209.25.170.201
Connecting to www.wildgardenseed.com|209.25.170.201|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2 [following]
--09:06:32--  http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Reusing existing connection to www.wildgardenseed.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 896,905 (876K) [application/x-tar]

100%[====================================>] 896,905       41.59K/s    ETA 00:00

09:07:01 (30.43 KB/s) - `autopackage.tar.bz2' saved [896905/896905]

Download completed.


.............................................................................................
autopackage/libexec/autosu-tui: error while loading shared libraries: libglib-2.0.so.0: cannot open shared object file: No such file or directory

Press Enter to close this window.
 
```

Same for the other version:

```
autopackage for "AMSN MSN client"


The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2 ... 

--09:13:22--  http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.

--09:13:35--  http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2
  (try: 2) => `autopackage.tar.bz2'
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
09:13:47 ERROR 403: Forbidden.

Download failed.


Attempting download of http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2 ... 

--09:13:47--  http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving www.wildgardenseed.com... 209.25.170.201
Connecting to www.wildgardenseed.com|209.25.170.201|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2 [following]
--09:13:47--  http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Reusing existing connection to www.wildgardenseed.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 896,905 (876K) [application/x-tar]

100%[====================================>] 896,905      348.43K/s             

09:13:50 (347.50 KB/s) - `autopackage.tar.bz2' saved [896905/896905]

Download completed.


.............................................................................................
autopackage/libexec/autosu-tui: error while loading shared libraries: libglib-2.0.so.0: cannot open shared object file: No such file or directory

Press Enter to close this window.


```

When pressing enter i get prompted with:
[[img]http://bildr.no/thumb/268360.jpeg[/img]](http://bildr.no/view/268360)

Clicking ok deletes the downloaded folder. If I dont click ok and then opening the downloaded directory makes me able to brows to the install script files. Running them seems to get me nowhere... Can anyone give me some tips on how to install the latest AMSN.

---

### Post by Orange_and_Green on 2008-10-10
Hi :)

Well, it seems to be complaining about libglib missing, so a good start might be ```
sudo apt-get install libglib2.0-0 libglib2.0-dev
```

Also, ```
sudo apt-get install build-essential
``` often helps when you try compiling programs on your own.

Good luck :KS

---

### Post by peakshysteria on 2008-10-10
No luck. ```
sudo apt-get install libglib2.0-0 libglib2.0-dev
``` gives me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0 is already the newest version.
libglib2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And then ```
sudo apt-get install build-essential
``` ofcourse gives me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Trying to find a .deb for 64 bit but can't seem to find one... :(

Edit:

found the .deb [here]("http://www.getdeb.net/search.php?search_distro_id=10&keywords=amsn") :) All is good now. Thanks for the help anyway man.

---

### Post by Sycron on 2008-10-10
You can download the debs from getdeb.com .

---

