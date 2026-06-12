---
title: "Disk space problem du"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by fernando@gmail.com on 2011-11-29
I'm on Ubuntu 10.04.3 LTS and:

When I run  **du -sm * | sort -n **

root@crm:/opt# **du -sm * | sort -n**
1       copia.sh
1       lost+found
3       AcertaTelefones.jar
85      teamviewer
90      postgresql-8.1.4
109     datastudio
186     jdk1.6.0
958     dimas281111.out.tar.gz
1967    backup
7403    syonet
9911    db
13520   base

In the left column is the size in megabytes of all itens inside of the /opt directory
Making the sum of all sizes we get  43176 megabytes. About 42,16 GBs.

BUT when I run: **du -sm** (At the same folder)

root@crm:/opt# **du -sm**
91770 

As we can see the sum is 91770 megabytes. Its about  89.61 GBs

Where are those  48594 MBs. Wich is the difference between the total size showed by du in last command and the sum of size of each item of the /opt folder.

As well the **df -m** show the total 
Sist. Arq.           1M-blocos      Usad Dispon.   Uso% Montado em
/dev/sda7               107660     91958     10234  90% /opt


My server is almost outof space and i'm missing somenthing like half of the HDD drive on this joke.

Please someone help

---

### Post by BC59 on 2011-11-29
Go here and check how you can clean the junk files you have:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Most interesting is the command

```
sudo find / -name '*' -size +1G
or
sudo find / -name '*' -size +500M
```

to find the big files.

---

