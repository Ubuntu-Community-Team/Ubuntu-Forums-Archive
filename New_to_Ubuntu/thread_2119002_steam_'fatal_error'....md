---
title: "steam 'fatal error'..."
date: 2013-02-22
forum: New to Ubuntu
---

### Post by Jainvamoo on 2013-02-22
hi,
wondering if anyone could help...
ive recently installed steam from Ubuntu Software Centre
i tried to open it up...it looked for updates for a split second then gives this dialogue...
(had to write as don't have 'url' of image :S)

> Steam - Fatal Error
Fatal Error : Steam needs to be online to update. Please confirm your network connection and try again.this is really annoying as i know i have an internet connection...wouldn't be writing this if i didn't...
can someone please help...

P.S. my boyfriend told me he had a similar problem with his steam on Windows and had to delete a file and the problem went...

please help...

---

### Post by x64Architecture on 2013-02-22
Try running the following commands in the terminal:

```
cd .steam/ 
rm steam.pid 
cd rm .steampid 
sudo apt-get install xfonts-100dpi xfonts-75dpi
```Then run steam again.

---

### Post by Jaydamis on 2013-02-23
> **x64Architecture said:**
> Try running the following commands in the terminal:

```
cd .steam/ 
rm steam.pid 
cd rm .steampid 
sudo apt-get install xfonts-100dpi xfonts-75dpi
```Then run steam again.

I have the same issue, and tried the above with no success.

I've tried at home on a wired connection, but didn't have time to fool with it, and am now on crappy hotel wifi.  It gets to about 4000KB / 175000KB then throws the error.

---

