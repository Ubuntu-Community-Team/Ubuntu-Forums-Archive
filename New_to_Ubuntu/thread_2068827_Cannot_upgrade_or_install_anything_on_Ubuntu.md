---
title: "Cannot upgrade or install anything on Ubuntu"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by sbkucin on 2012-10-10
I am running version 10.4 and for some reason it will not let me upgrade or install anything on Ubuntu.  I tried upgrading from the live cd, but when I go into install I get this message "error auto running, program not found".  Also I can't get any new software, say it cannot be run on my machine, I was able to do this before, not sure what has happened.  Can anyone help me?

---

### Post by drpjkurian on 2012-10-10
> **sbkucin said:**
> I am running version 10.4 and for some reason it will not let me upgrade or install anything on Ubuntu.  I tried upgrading from the live cd, but when I go into install I get this message "error auto running, program not found".  Also I can't get any new software, say it cannot be run on my machine, I was able to do this before, not sure what has happened.  Can anyone help me?

WHy cant you upload the error message screen shot? It will really helpful

---

### Post by DuckHook on 2012-10-10
> tried upgrading from the live cd, but when I go into install I get this message "error auto running, program not found"You must boot with the LiveCD in order to upgrade. Your system cannot be upgraded by the LiveCD while it is running. It *can* be upgraded, while running, by using *update manager*. Have you tried doing so?

> Also I can't get any new software, say it cannot be run on my machine, I was able to do this before, not sure what has happened.Please provide more details. We need to know if some of the upgrading process completed or none at all. What steps did you take? Please recite them in detail and in order.

Open a terminal and type in the following:

```
sudo apt-get update
```...and post the full output to this thread. Then, type in:

```
sudo apt-get check
```...and post the full output to this thread.

---

