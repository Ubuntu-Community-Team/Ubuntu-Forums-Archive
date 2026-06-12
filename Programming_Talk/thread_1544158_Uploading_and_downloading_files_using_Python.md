---
title: "Uploading and downloading files using Python"
date: 2010-08-02
forum: Programming Talk
---

### Post by 7raTEYdCql on 2010-08-02
Hello,

I've written a BASH shell script to upload files and download files from a http server.

To Upload files I've used curl -t filename 
"http://server.ip/urlname/"

And to download a simple wget -r "url.name"

Can someone please help me in doing the same in Python.

To download, I'm aware of urllib.urlretreive(..) which can do the job, any suggestions for uploading??

Thanks in advance,
Mehrzad.

---

### Post by anglican on 2010-08-02
> **i.mehrzad said:**
> Hello,

I've written a BASH shell script to upload files and download files from a http server.

To Upload files I've used curl -t filename 
"http://server.ip/urlname/"

And to download a simple wget -r "url.name"

Can someone please help me in doing the same in Python.

To download, I'm aware of urllib.urlretreive(..) which can do the job, any suggestions for uploading??

Thanks in advance,
Mehrzad.How about using curl again, see:

[http://wirelessfun.mobi/wordpress/?p=41](http://wirelessfun.mobi/wordpress/?p=41)

H

---

### Post by StephenF on 2010-08-02
Then there are the pycurl bindings for libcurl if you want to do things "properly".

Having said that it depends on what you really want to do as to whether stepping beyond the Python standard modules is beneficial.

---

### Post by 7raTEYdCql on 2010-08-02
Thank you anglican, that was a good read. I'll read a li'l more on the suprocess module.

@StephenF: I'd prefer to stick to the standard Python modules. I had come across pycurl earlier aswell. Preferred not to use it.

---

