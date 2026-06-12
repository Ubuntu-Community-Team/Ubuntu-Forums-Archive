---
title: "Which version of PHP"
date: 2007-11-26
forum: Programming Talk
---

### Post by DrMega on 2007-11-26
Hi

I am planning to build a website which will be a data driven arrangement using PHP and MySQL.

I plan to have the site hosted by a third party but want to do all the development locally, so off I go to Synaptic to PHP, MySQL and Apache.

The trouble is there seems to be multiple versions of PHP5 and I'm not sure which package is most appropriate.

Also, will I need to install a firewall (if so can someone recommend one)?

I'm used to doing this on Windows. In Ubuntu there seems to be so many ways of doing things.

Could anyone explain the practical differences between PHP5-CGI and libapache2-mod-php5? (the description in php5-cgi says most people would probably want the libapache one).

---

### Post by Kadrus on 2007-11-26
Euuh..read this...the PHP-Apache and Mysql part..it might be helpful..
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
Hope that helped :)

---

### Post by Kadrus on 2007-11-26
And it is the same thing..but if you want go to this thread..read the part where I posted 
[http://ubuntuforums.org/showthread.php?p=3836945#post3836945](http://ubuntuforums.org/showthread.php?p=3836945#post3836945)
Hope anything was handy :)..good luck!

---

### Post by smartbei on 2007-11-26
@Kadrus - editing is nearly always preffered to double-posting.

@OP: The difference between PHP5-CGI and libapache2-mod-php5 is in the way the php interpreter is called by apache. If you don't kno w anything about it then you want the latter package.

There is no need to install a firewall (not exactly sure what this has to do with the other questions).

The easiest way to install a apache-php-mysql server on Gutsy or Fiesty is:
```

sudo tasksel

```
and then selecting a lamp server.

---

### Post by LaRoza on 2007-11-26
If you don't know what version of PHP your host will be using, write the site in PHP4. I have used PHP5 in the past, only to find out my host was PHP4. The main difference is the OO features. PHP4 has only a few basic features, and PHP5 has a Java-like OO scheme.

---

### Post by DrMega on 2007-11-26
> **smartbei said:**
> @Kadrus - editing is nearly always preffered to double-posting.

@OP: The difference between PHP5-CGI and libapache2-mod-php5 is in the way the php interpreter is called by apache. If you don't kno w anything about it then you want the latter package.

There is no need to install a firewall (not exactly sure what this has to do with the other questions).

The easiest way to install a apache-php-mysql server on Gutsy or Fiesty is:
```

sudo tasksel

```
and then selecting a lamp server.

Thanks.

---

### Post by MicahCarrick on 2007-11-27
> If you don't know what version of PHP your host will be using, write the site in PHP4. I have used PHP5 in the past, only to find out my host was PHP4. The main difference is the OO features. PHP4 has only a few basic features, and PHP5 has a Java-like OO scheme.

I would be careful here. PHP5 should be pretty widely supported by now being that PHP4 is officially going to be "no longer supported" I think at the end of this year. Therefore, no more security patches, updates, etc. for PHP4. I would say you should find a host that offers PHP5. Most descent hosting companies will offer PHP5 or both (you may have to tweak which one is being used in your .htaccess).

However, unless you had your heart set on using PHP5's OOP features, you can easily write PHP4/5 compatible code. In fact, you can even use PHP4's objects and they should work in PHP5. You just don't get all the nice features.

---

### Post by DrMega on 2007-11-27
> **MicahCarrick said:**
> I would be careful here. PHP5 should be pretty widely supported by now being that PHP4 is officially going to be "no longer supported" I think at the end of this year. Therefore, no more security patches, updates, etc. for PHP4. I would say you should find a host that offers PHP5. Most descent hosting companies will offer PHP5 or both (you may have to tweak which one is being used in your .htaccess).

However, unless you had your heart set on using PHP5's OOP features, you can easily write PHP4/5 compatible code. In fact, you can even use PHP4's objects and they should work in PHP5. You just don't get all the nice features.

Thanks for the tips. I'm going with PHP5 because obviously its the later version, but I had checked with a few possible web hosts before making the final decision.  Some time ago I used Hostgator.com, and they were good, they now support php5 as do a few others.

---

