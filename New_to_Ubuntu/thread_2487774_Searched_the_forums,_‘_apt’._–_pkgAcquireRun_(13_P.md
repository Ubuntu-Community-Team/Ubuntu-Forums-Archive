---
title: "Searched the forums, ‘_apt’. – pkgAcquire::Run (13: Permission denied) solutions fail"
date: 2023-06-14
forum: New to Ubuntu
---

### Post by gbp00 on 2023-06-14
hello frens
new install
new user
same error on all apps I try.
Guessing this is an easy one, since it's fresh out the box problems.
the idiot manual was regrettably not included in OS

having issues installing anything due to  Download is performed unsandboxed as root as file couldn&#8217;t be accessed by user &#8216;_apt&#8217;. &#8211; pkgAcquire::Run (13: Permission denied)

I tried in this format:

sudo apt-get install ~/Downloads/file-name.deb
sudo apt remove file-name
# NEW METHOD

Attempts:

- allowing .deb to be executable

- chown _apt /var/lib/update-notifier/package-data-downloads/partial/

- sudo chown _apt /var/lib/update-notifier/package-data-downloads/partial/

- chown <your-user-name> somepackage

- sudo chown <your-user-name> somepackage



- Confirm you have apt account.

getent passwd _apt
_apt:x:105:65534::/nonexistent:/usr/sbin/nologin

adduser --force-badname --system --home /nonexistent --no-create-home --quiet _apt || true

adduser: Only root may add a user or group to the system.


- quick & dirty workaround

sudo chmod 777 /var/lib/update-notifier/package-data-downloads/partial


it's not connected to net yet, was hoping to get the network sec up before anything.

do I need to change user permissions, if so how, please?

or do I need to sudo apt-get update and it will fix itself?

---

### Post by aljames2 on 2023-06-14
You could share more info like what Ubuntu release you installed & what package you are trying to install.  Also, including the whole message you received in code tags can help.

I don’t use apt-get for anything, just apt. Either should work.  If you are trying to install a local package you downloaded, perhaps just
```
apt install <package>
```
would work, dropping sudo.

---

### Post by gbp00 on 2023-06-15
A reboot seemed to do the trick, surprisingly... the apt install was not successful for me. Thanks for response.

---

### Post by MAFoElffen on 2023-06-15
> **gbp00 said:**
> A reboot seemed to do the trick, surprisingly... the apt install was not successful for me. Thanks for response.
It's very hard following what you are saying... Slow down and let's break this down into little, single steps...

(Unanswered from above -->) What are you trying to install?

---

