---
title: "[SOLVED] Permissions query"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by EmperorMoo on 2008-06-06
I am trying to install Postfix onto a server I am setting up (in at the deep end - the best kind of hands-on learning!)

I am getting Permission denied errors when entering 

echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf


So far, I have tried:

running as root
moving other objects into the folder (using mv & cp):  this works fine

the permssions on the folder are drwxr-xr-x

Thanks

---

### Post by hyper_ch on 2008-06-06
```

sudo echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf

```

---

### Post by EmperorMoo on 2008-06-06
I've already tried running it as su, that's my confusion.

---

### Post by hyper_ch on 2008-06-06
```

cat /etc/postfix/sasl/smtpd.conf

```

---

### Post by kpkeerthi on 2008-06-06
What is the permission on the file /etc/postfix/sasl/smtpd.conf ?

```
ls -l /etc/postfix/sasl/smtpd.conf
```

---

### Post by EmperorMoo on 2008-06-06
the cat command gives no such file or directory.  Neither does it appear in the directory.

Doesn't the echo command create the file to which I am sending the output from the command?

---

### Post by hyper_ch on 2008-06-06
it would create it with a single ">" I think...

Well, now that you know the file doesn't exist create it then:

```

sudo touch ....

```

---

### Post by sisco311 on 2008-06-06
Try:
```
sudo sh -c "echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf"
```or
```
echo 'pwcheck_method: saslauthd' | sudo tee -a /etc/postfix/sasl/smtpd.conf > /dev/null
```

---

### Post by EmperorMoo on 2008-06-06
Right, the file is now made using touch ....
Still getting the error on running the echo command, even when full permissions have been granted on smtpd.conf

---

### Post by hyper_ch on 2008-06-06
paste the whole thing here of the command you issue and the error you get.

---

### Post by EmperorMoo on 2008-06-06
Oh the shame!  
I had missed out a folder in the path to the file.  I just noticed as I was copying the code across.

It works now.

Thanks for your help, much appreciated!

---

