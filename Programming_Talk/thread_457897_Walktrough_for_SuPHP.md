---
title: "Walktrough for SuPHP"
date: 2007-05-29
forum: Programming Talk
---

### Post by HovardKr on 2007-05-29
Hi!

I need some help to configure a webserver for internal use (just for website development). I have set up an old computer and installed latest Ubuntu desktop version. I have also installed Apache2, PHP5 and PhpMyAdmin.

Since there are som issues with users permissions I would really like to install SuPHP. But now after two days of not being able to install it on my own, I would be happy if someone could help me with an walktrough. I am pretty new to Ubuntu and Linux, but I understand how it works, and I am learning... :)

**Keywords**: Clean Ubuntu desktop installation, clean Apache2 installation and clean PHP5 installation...

What is next step...?

(Sorry for any bad spelling)

:popcorn:

---

### Post by jonny.allred on 2007-08-20
suPHP is easily installed using apt-get or aptitude.  Just search suphp and find the required files.

jonny@longboardersunite:~$ apt-cache search suphp                               libapache-mod-suphp - Apache module to run php scripts with the owner permissions
libapache2-mod-suphp - Apache2 module to run php scripts with the owner permissions
suphp-common - Common files for mod suphp

Check the apache logs in var/log/apache2/error.log if you get any internal server errors.  They are very informative.

Also, note that the suphp config file is /etc/suphp/suphp.conf.

Check out 
[http://www.howtoforge.com/apache2_suphp_php4_php5_p2]("http://www.howtoforge.com/apache2_suphp_php4_php5_p2")
and
[http://wiki.apache.org/httpd/PrivilegeSeparation]("http://wiki.apache.org/httpd/PrivilegeSeparation")
for more info.

---

### Post by cordoval on 2010-11-03
I have not found much help so far and I am trying to set suphp with ubuntu same as you now Ubuntu Maverick 10.10 and no success.

Please help

thanks

Luis

---

### Post by petrovicivan on 2011-03-14
Here is [http://hartlessbydesign.com/blog/view/196-ubuntu-1004-suphp-and-phpmyadmin]("http://hartlessbydesign.com/blog/view/196-ubuntu-1004-suphp-and-phpmyadmin")

---

### Post by silv3rm00n on 2011-11-27
Suphp installation guide :

[http://www.binarytides.com/blog/install-suphp-on-ubuntu-linux/]("http://www.binarytides.com/blog/install-suphp-on-ubuntu-linux/")

---

