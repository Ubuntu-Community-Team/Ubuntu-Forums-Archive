---
title: "Cannot update ClamAV"
date: 2017-01-26
forum: New to Ubuntu
---

### Post by ferfykins on 2017-01-26
I tried "freshclam"

and got this error

ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).



^i tried it on my root account and using sudo
this error with sudo:
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

---

### Post by bearlake on 2017-01-26
> **ferfykins said:**
> I tried "freshclam"

and got this error

ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).



^i tried it on my root account and using sudo
this error with sudo:
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

Hi,

To update the virus definitions use this.

```
sudo freshclam
```

---

### Post by ferfykins on 2017-01-26
> **bearlake said:**
> Hi,

To update the virus definitions use this.

```
sudo freshclam
```
 
i already tried sudo freshclam

i get this error:

ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

---

### Post by lisati on 2017-01-26
If you have clamtk open when running freshclam, you might need to close it before freshclam will work.

---

### Post by ferfykins on 2017-01-26
> **lisati said:**
> If you have clamtk open when running freshclam, you might need to close it before freshclam will work.
 
i closed clamtk and still get same error :'(

---

### Post by Perfect Storm on 2017-01-27
Try 
```
killall freshclam
```

---

### Post by ferfykins on 2017-01-27
That fixed it, thanks so much Artificial intelligence :)

---

