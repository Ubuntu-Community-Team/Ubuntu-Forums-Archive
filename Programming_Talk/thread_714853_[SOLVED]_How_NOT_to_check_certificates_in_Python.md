---
title: "[SOLVED] How NOT to check certificates in Python?"
date: 2008-03-04
forum: Programming Talk
---

### Post by tseliot on 2008-03-04
Hi all,

I'm trying to do in Python what "wget" does when I type:

```
wget --no-check-certificate url 
```

Basically I'm trying to download this file from Python without having to check the server certificate against the available certificate authorities.

if I do:

```
url = 'https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/'
file = 'ati-driver-installer-8-02-x86.x86_64.run'

urllib.urlretrieve(url, file)
```

I get this:
```
('ati-driver-installer-8-02-x86.x86_64.run', <httplib.HTTPMessage instance at 0xb7c07cec>)
```

and the file is not downloaded.

Any ideas?

Thanks in advance

---

### Post by popch on 2008-03-04
Shouldn't the first parameter (url) contain the ***file name*** ? It ends with a directory.

---

### Post by elithrar on 2008-03-04
[php]
url = 'https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-02-x86.x86_64.run'
file = 'ati-driver-installer-8-02-x86.x86_64.run'

urllib.urlretrieve(url, file)
[/php]

---

### Post by tseliot on 2008-03-04
you're right :redface:

I hadn't used urlretrieve for a long time... and of course last night I misread the documentation.

Thank you all

---

