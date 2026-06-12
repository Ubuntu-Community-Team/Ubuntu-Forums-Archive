---
title: "Update Key error"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-06-06
I get this error when I update my system. I still can get updates but not the ones from these repositories, apparently.

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Could somebody explain if it's important or not and if I need to fix it and how?

Thanks.

.

---

### Post by drs305 on 2008-06-06
> **Sealbhach said:**
> Could somebody explain if it's important or not and if I need to fix it and how?
.

The error message is telling you that there are some authentication errors for some of the repositories in synaptic/sources.list

You can try to clear the errors by running what it says in the message:
```
sudo apt-get update
```

In simple terms, some respositories issue 'keys' to verify that the files are actually coming from their repository. Apparently at some point the keys changed and now your computer isn't sure it's talking to the correct source.

---

### Post by Sealbhach on 2008-06-06
Thanks, but this is actually the error I got after

```
sudo apt-get update
```

which I copied and pasted from the terminal.

I also ran

```
sudo aptitude update
```

and got the same.

Just wondering if it's a general message everybody gets or if it's something I need to fix.

Is there a way for me to update the keys?


.

---

### Post by Duck2006 on 2008-06-06
try.

sudo apt-get update
sudo apt-get upgrade

It may help.

---

### Post by iaculallad on 2008-06-06
Execute the commands below on your terminal:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Sealbhach on 2008-06-06
Thanks, that cleared some of them, there's just this one left.

```

W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

I really appreciate your help.


.

---

### Post by iaculallad on 2008-06-06
Try to change directory to /etc/apt and locate if you have a folder name **sources.list.d**, try to remove the files present inside the folder and redo the command below:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by NeQaSh on 2008-06-07
WHITH My Respect 2 all above solutions

only this solution here

[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

SOLVE my same problem PERMENANTELY

:guitar: >> :lolflag:

---

### Post by Sealbhach on 2008-06-07
> **NeQaSh said:**
> WHITH My Respect 2 all above solutions

only this solution here

[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

SOLVE my same problem PERMENANTELY

:guitar: >> :lolflag:

Yes, that worked. Thannk you very much.

Sealbhach.


.

---

### Post by kumarnat on 2009-11-28
Yes the last solution solved my problem too, no more errors...

Thanks.

---

### Post by chudder on 2009-11-29
> **iaculallad said:**
> Execute the commands below on your terminal:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

Worked for me, Thanks!

---

