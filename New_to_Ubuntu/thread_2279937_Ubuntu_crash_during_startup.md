---
title: "Ubuntu crash during startup"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by anbu-s on 2015-05-26
Lately every time i reboot or startup my laptop, I get the ubuntu system crash message as per the screenshot. Not sure what the issue is? Is there a way to fix this? I don't get any other message to diagnose the issue. Where do I start

I'm on ubuntu 14.04.2 LTS 64-bit

---

### Post by Vladlenin5000 on 2015-05-26
You can safely ignore that error.
Normal updates will correct it sooner than later.

---

### Post by cariboo on 2015-05-26
You can disable apport, just change /etc/default/apport enabled=1 to enabled=0.

Open a terminal and type the following command:

```
sudo nano /etc/default/apport
```

change the 1 to 0 press Ctrl-o then Ctrl-x to save and exit

---

### Post by RobGoss on 2015-05-27
> **cariboo said:**
> You can disable apport, just change /etc/default/apport enabled=1 to enabled=0.

Open a terminal and type the following command:

```
sudo nano /etc/default/apport
```

change the 1 to 0 press Ctrl-o then Ctrl-x to save and exit

Is it a wise thing to just ignore the crash report? I would want to find out why I'm receiving this message. Correct me if I'm wrong but can't  you look in the crash folder for this report and does it have the details for this crash report.

---

### Post by deadflowr on 2015-05-27
> **robert159 said:**
> Is it a wise thing to just ignore the crash report? I would want to find out why I'm receiving this message. Correct me if I'm wrong but can't  you look in the crash folder for this report and does it have the details for this crash report.

What message?
Disabling apport disables the crash reporting.
You wouldn't get a message or an error report.

If you feel the need to report a bug, then ubuntu-bug <buggy-package-name-here> should still work.

Apport can be a tad trigger happy any, as anytime you restart unity, it'll report that compiz crashed.
Even though it did not...
As just one example.

---

### Post by v3.xx on 2015-05-27
> Apport is not enabled by default in stable releases,  even if it is installed. The automatic crash interception component of  apport is disabled by default in stable releases for a number of  reasons: 
Apport  collects potentially sensitive data, such as core dumps, stack traces,  and log files. They can contain passwords, credit card numbers, serial  numbers, and other private material. 
[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

---

