---
title: "dpkg: error: passing file '/var/lib/dpkg/status' near line 7683 package"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by Abado_Jack_Mtulla on 2014-03-01
I tried removing some packages i had installed and received the following error message

[I]dpkg: error: parsing file '/var/lib/dpkg/status' near line 7683 package 'fonts-tlwg-loma':
 EOF during value of field `Breaks' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I]

I have tried *sudo apt-get install -f* among others i have read online but none is working.

can anyone help me with this?

---

### Post by ibjsb4 on 2014-03-01
Try this

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broke

sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status

sudo apt-get update
```

---

### Post by Abado_Jack_Mtulla on 2014-03-01
Am still getting the following error

[I]E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
[/I]

---

### Post by ibjsb4 on 2014-03-01
Ok, try this

[http://ubuntuforums.org/showthread.php?t=2190797&p=12860782#post12860782](http://ubuntuforums.org/showthread.php?t=2190797&p=12860782#post12860782)

---

### Post by plucky on 2014-03-01
> **Abado_Jack_Mtulla said:**
> Am still getting the following error

[I]E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
[/I]

That is not the same error.

Did you do all the commands that ibjsb4 specified?

Especially this one

```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Post output for ```
 ls /var/lib/dpkg/
```

---

