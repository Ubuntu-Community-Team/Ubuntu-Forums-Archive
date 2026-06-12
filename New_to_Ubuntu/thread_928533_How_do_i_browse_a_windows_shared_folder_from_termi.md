---
title: "How do i browse a windows shared folder from terminal"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by alpdo on 2008-09-24
How do i browse a windows shared folder from terminal.... and then run dos  progroms from there...????

---

### Post by RealPSL on 2008-09-26
I am not sure what you mean by running dos commands but the [smbclient]("http://learnlinux.tsf.org.za/courses/build/net-admin/ch08s02.html") tool will help you browse shares from the terminal.

---

### Post by Nepherte on 2008-09-26
The command is:
```
smbclient //computername/sharedfolder
```
or
```
smbclient //ipaddress/sharedfolder
```

---

### Post by Sycron on 2008-09-26
or ```
nautilus //ip_address
```

---

### Post by alpdo on 2008-09-29
ive have tried smbclient but all i can do is browse files 
i was able to run programs

---

