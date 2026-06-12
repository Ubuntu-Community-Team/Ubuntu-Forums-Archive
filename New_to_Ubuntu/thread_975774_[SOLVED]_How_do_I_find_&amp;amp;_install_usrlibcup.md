---
title: "[SOLVED] How do I find &amp;amp; install /usr/lib/cups/backend/epson ?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by simontaylor on 2008-11-08
Dear Ubu,

After upgrading to 8.10 my printer won't work.

Can you please instruct me on how to find and install the missing files: /usr/lib/cups/backend/epson ?

Thank you,

Simon

---

### Post by JeppeM on 2008-11-08
Do you have CUPS installed? (Check in synapics undr system ---> administration) :)

---

### Post by simontaylor on 2008-11-08
cups 1.3.9-2 

seems like all dependencies are present and accounted for.

---

### Post by simontaylor on 2008-11-08
tried to update package info for foomatic - which a search for 'epson backend' yielded and received the following:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by simontaylor on 2008-11-08
went to system>admin>software sources to check settings - because of cited error report: now on attempting to update, this:
> 
Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by simontaylor on 2008-11-08
I appear to have found and downloaded the relevant Gutenprint 5.0.1? driver for Epson C90 printer - it's sitting on my desktop (in a folder called 'opt')... I don't know how to install it. Help please.

through System> Admin> Printing - I deleted my printer ... I thought, wrongly, that it might be automatically found with the relevant software ... No. 

A little help would be appreciated.

Best,

Simon

---

### Post by simontaylor on 2008-11-09
[http://www.linuxquestions.org/questions/ubuntu-63/pls-help-me-install-epson-c90-printer-driver-602578/](http://www.linuxquestions.org/questions/ubuntu-63/pls-help-me-install-epson-c90-printer-driver-602578/)

go to cups - as per instructions in link above - add printer - choose C68 as driver model (CUPS v1.3.x) (is listed as Gutenprint + CUPS (first C68 on list))

---

