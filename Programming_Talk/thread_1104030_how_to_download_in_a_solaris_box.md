---
title: "how to download in a solaris box"
date: 2009-03-23
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-23
Hi

I am a new unix user.

I need to download this file to my unix box:
[http://sourceforge.net/project/downloading.php?groupname=xampp&filename=xampp-solaris-0.9.sh&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=xampp&filename=xampp-solaris-0.9.sh&use_mirror=voxel)

Could anyone please tell me what shell command I need to use to download it?

Thanks,

Tom

---

### Post by Bachstelze on 2009-03-23
Depends which tools are installed on your system. you can try

```
wget http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh
```

and

```
fetch http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh
```

---

### Post by ikki_72 on 2009-03-23
if you're not running X (GUI to put simply but might not be entirely correct), try```
wget http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh
```
P/S: I got this link from **direct link**'s link.

---

### Post by qmqmqm on 2009-03-23
Thank you but unfortunately none of wget or fetch are installed on the machine...

bash: wget: command not found
bash: fetch: command not found

Are there any other ways to do this?

---

### Post by ghostdog74 on 2009-03-23
solaris doesn't have wget installed. you can get it from sunfreeware.com

---

### Post by ikki_72 on 2009-03-23
From what i read, download the wget package then do```
pkgadd -d package
```

---

### Post by qmqmqm on 2009-03-23
Thank you all.

I have found that I have wget under /usr/sfw/bin, but I get this error:

bash# ./wget [http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh](http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh)
--10:29:24--  [http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh](http://voxel.dl.sourceforge.net/sourceforge/xampp/xampp-solaris-0.9.sh)
           => `xampp-solaris-0.9.sh'
Resolving voxel.dl.sourceforge.net... failed: node name or service name not known.

Does anyone know why this is?

Thanks,

Tom

---

### Post by dwhitney67 on 2009-03-23
Are you on a system that is using a proxy server to gain access to the internet?

If so, you will need to modify /etc/wgetrc with your proxy information.  Look for 'http_proxy', 'ftp_proxy', and 'use_proxy' within that file.

---

### Post by qmqmqm on 2009-03-23
> **dwhitney67 said:**
> Are you on a system that is using a proxy server to gain access to the internet?

If so, you will need to modify /etc/wgetrc with your proxy information.  Look for 'http_proxy', 'ftp_proxy', and 'use_proxy' within that file.

Hi dwhitney67

Yes I found these e lines, but what am I supposed to do with them?

---

### Post by dwhitney67 on 2009-03-24
> **qmqmqm said:**
> Hi dwhitney67

Yes I found these e lines, but what am I supposed to do with them?

Before you do anything with the /etc/wgetrc file, answer the question:  Is your system required to tunnel through a proxy server before accessing the internet???

---

### Post by qmqmqm on 2009-03-24
> **dwhitney67 said:**
> Before you do anything with the /etc/wgetrc file, answer the question:  Is your system required to tunnel through a proxy server before accessing the internet???

I believe so...

---

### Post by dwhitney67 on 2009-03-24
Then you will need to know the URL of the proxy server.  If you run a browser, then this is probably indicated within there as well.

As for the /etc/wgetrc file, the settings would be something similar to:
```

...
http_proxy = http://acme.com:8080/
ftp_proxy = http://acme.com:8080/

# If you do not want to use proxy at all, set this to off.
use_proxy = on
...

```
The format is [http://URL:port](http://URL:port).  Change the "acme.com" and the port number "8080" to whatever your system requires.

You may also be able to get away with simply specifying the following in your ~/.bashrc file.  You may want to try this first:
```

http_proxy=http://acme.com:8080
ftp_proxy=http://acme.com:8080
export http_proxy ftp_proxy

```
Don't forget to source the ~/.bashrc file after any changes.

P.S.  If your proxy server requires user authentication to access the server, then change the format of the proxy statements to be:
```

http://user:password@acme.com:8080

```

---

