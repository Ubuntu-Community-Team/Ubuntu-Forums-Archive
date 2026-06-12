---
title: "Cygwin EC2 Ubuntu Installlation MySQL, PHP, Apache, Tomcat"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by joseph32 on 2014-06-29
Hi,

Pretty upset with my inability. Perhaps, someone could help me connect to EC2 AMI Ubuntu.

 My security group is listening on port 22 for SSH. I downloaded my PEM file, which is present in the '/' directory of Cygwin. I typed the following into Cygwin:

[TABLE]
[TR]
[TD="bgcolor: #ffffff, align: left"]ssh -i test-ec2-pem.pem PUBLIC_DNS
[/TD]
[/TR]
[/TABLE]

Where "PUBLIC_DNS" is the public dns shown having clicked on the running instance. Cygwin's response is:
[TABLE]
[TR]
[TD="bgcolor: #ffffff, align: left"]JHodges@JHodges-PC / 
$ ssh -i PUBLIC_DNS
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions [COLOR=red]0755[/COLOR] [COLOR=#00a000]**for**[/COLOR] [COLOR=navy]'ec2.pem'[/COLOR] are too open.
It is required that your [COLOR=#00a000]**private**[/COLOR] key files are NOT accessible by others.
This [COLOR=#00a000]**private**[/COLOR] key will be ignored.
bad permissions: ignore key: ec2.pem
Permission denied (publickey).
[/TD]
[/TR]
[/TABLE]


 I also tried to use PuTTYGen to generate a private key file (.ppk) with the test-ec2-pem.pem file. 

 I've also tried:
[TABLE]
[TR]
[TD="bgcolor: #ffffff, align: left"]ssh -i test-ec2-pem.pem Ubuntu@PUBLIC_DNS
[/TD]
[/TR]
[/TABLE]


Many other variations of the kind. Since I am running on Cygwin I guess I am just shooting in the dark.

Perhaps, someone could enlighten me on how this is done. Cheers!

---

