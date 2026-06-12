---
title: "[SOLVED] signature verification error"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by simontaylor on 2008-09-19
On boot up my desktop shows either a lightbulb or an error exclamation mark. It asks me to update or add information to files. When I do I get:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas how to get around this? My concern is missing out on important updates.

Thanks,

Simon

---

### Post by prshah on 2008-09-19
> **simontaylor said:**
> On boot up my desktop shows either a lightbulb or an error exclamation mark. 

Try:

Open System-Administration-Software Sources-Ubuntu Software, and set the server to be used to "Main Server" from (probably) "Server for New Zealand".

---

### Post by simontaylor on 2008-09-19
some to-ing and fro-ing but seems to have done the trick. What has been lost - which I don't mourn the passing of - are some 'translation NZ-eng' libraries? would they be? 

Thanks,

I was afraid I'd have to jump back into Terminal time!

Simon

---

### Post by simontaylor on 2008-09-22
to update on updating error: now this -

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

not too heinous I hope. And hope also that the main issue was that dealt with by changing software source in administration to ... main.

Thanks again.

Any thoughts regarding the quoted error are appreciated.

Simon

---

### Post by simontaylor on 2008-11-09
upgraded to 8.10 - software sources are "main" but has returned similar error to that cited.

---

### Post by sbolton on 2010-05-26
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422.............

Looks like someone put some pubkey stuff on my box too, they messed it up, looks like I can't get updates. Some people shouldn't monkey with stuff they don't understand.

---

