---
title: "What is difference between XAMPP and lamp servers"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by kamrava on 2013-06-19
Hello

What is difference between [XAMPP]("http://andyhat.co.uk/2012/07/installing-xampp-32bit-ubuntu-11-10-12-04/") and lamp servers ?

For installing XAMPP server i have followed [this article]("http://andyhat.co.uk/2012/07/installing-xampp-32bit-ubuntu-11-10-12-04/").

For installing lamp server we need to run :

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install lamp-server^[/FONT][/COLOR]
```


Regards

---

### Post by dan08 on 2013-06-19
The "X" in XAMPP stands for Cross-Platform, while "L" in LAMP stand for Linux. If your installing XAMPP on a Linux system then its basically the same as a LAMP server, except that XAMPP also includes perl. The benefit of XAMPP is that it can be installed on different platforms (I'm running it on Windows 7).

---

### Post by matt_symes on 2013-06-19
Hi

Install Lamp and not xampp and get the benefits of automatic updates and package management.

I also seem to recall the security was less tighter in xampp as well. Others will correct me if my memory fails here.

Kind regards

---

### Post by andyhat on 2013-06-20
As mentioned in the other responses there are good reasons to use XAMPP and LAMP configurations. 
The XAMPP install is supposed to be portable and can be started and stoped easily when required. It also has different security settings and come ready configured with extra tools. However it's not goos to use it for public web servers only for development and testing.
The LAMP system includes the same basic compnonent (Apache, MySQL and PHP) can be more difficult to configure. I can be more secure, easier to update and can be used for public webservers.

---

