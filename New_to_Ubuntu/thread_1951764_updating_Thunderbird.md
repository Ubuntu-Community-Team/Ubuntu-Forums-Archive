---
title: "updating Thunderbird"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by kenmac2 on 2012-04-03
Hi,
I have downloaded the latest version of Thunderbird, but need to know how to install the update.

kenmac2

---

### Post by santosh83 on 2012-04-03
> **kenmac2 said:**
> Hi,
I have downloaded the latest version of Thunderbird, but need to know how to install the update.

kenmac2

I presume you have downloaded version 11.0.1 of Thunderbird distributed at [https://www.mozilla.org/en-US/thunderbird/](https://www.mozilla.org/en-US/thunderbird/)?

It's distributed as a tarred and bzip'ed archive, which you can extract to any folder using
```
tar xjvf *file_name*
```
where you replace *file_name* with the name of the download file. I suggest you install under a sub-directory in your home directory. Then you can create a shortcut in your menu for the executable inside the extracted directory, usually named 'thunderbird.sh' in Linux I think.

---

### Post by mike555 on 2012-04-03
It is better to use the PPA for thunderbird and let the package manager install it , that way it will update with all the rest of your programs .
[https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

---

### Post by kenmac2 on 2012-04-03
Thanks Mike,
I was wondering how to get the update info into the update repository.
I have now done the job.

kenmac2

---

