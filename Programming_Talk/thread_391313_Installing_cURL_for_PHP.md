---
title: "Installing cURL for PHP"
date: 2007-03-23
forum: Programming Talk
---

### Post by nozavroni on 2007-03-23
I apologize if this is the wrong forum. I couldn't find one that seemed to fit my question. What I would like to know is how to install the cURL PHP extension on ubuntu. Is there anything special I need to know?

---

### Post by Mirrorball on 2007-03-23
```
sudo apt-get install php5-curl
```
Restart Apache.

---

### Post by nozavroni on 2007-03-26
doesn't really get any more simple than that, does it? lol... thanks.

---

### Post by scotty69169 on 2009-07-11
I don't have a CDROM on my server. It's a 1U pizza box. How can I install cURL or any other programs/server on my box. Because it keeps asking for a CDROM.
 
Thanks,
 
Scott.

---

### Post by kevjaun on 2009-07-27
@scotty69169 - not a cURL issue, check your software sources

---

### Post by sitthykun on 2010-05-16
thanks ...:)

---

### Post by HughJarse on 2011-07-31
> **Mirrorball said:**
> ```
sudo apt-get install php5-curl
```
Restart Apache.
Woudl have been nice if you added the command to restart apache

---

### Post by soltanis on 2011-08-01
```

sudo service apache2 restart

```

---

### Post by ellenbo on 2012-05-22
Thank you for providing this info!

---

### Post by jdalt on 2012-09-10
As of Ubuntu 12.04 after installing the LAMP server from tasksel I had to do:
```
sudo apt-get install curl libcurl3 libcurl3-dev php5-curl
```To get curl working.

---

