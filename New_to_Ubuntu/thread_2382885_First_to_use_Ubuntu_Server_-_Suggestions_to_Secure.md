---
title: "First to use Ubuntu Server - Suggestions to Secure and Optimize"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by agriz2 on 2018-01-18
Hi

I was using Centos all the time.
First time i am going to use Ubuntu 16.x server
I am going to use it for API server with Only PHP and MySQL. 

No email, nothing else. Just php and mysql.
Please kindly suggest me how to start, securing and optimizing for high traffic

Thanks a lot.

---

### Post by SeijiSensei on 2018-01-18
You won't need to do anything special.  Ubuntu Server and CentOS run all the same software.  They differ mostly in how packages are maintained and the locations of some files. Whatever steps you took to secure CentOS will apply here as well.

The most likely speed issue will concern MySQL.  I don't know what constitutes "high traffic" in your mind, but you might need to do some tuning of MySQL after watching it in practice.

---

