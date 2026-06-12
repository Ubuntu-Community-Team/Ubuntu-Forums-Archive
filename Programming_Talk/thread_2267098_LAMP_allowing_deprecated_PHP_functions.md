---
title: "LAMP allowing deprecated PHP functions"
date: 2015-02-27
forum: Programming Talk
---

### Post by Mike_Hanchet on 2015-02-27
Hello,

I recently set up a laptop with LAMP and have noticed that LAMP is allowing deprecated PHP functions to run; for instance, mysql_query.  Since I'm learning PHP (e.g., on-line tutorials, YouTube), I rely on the pop up notices such that I get on my Windows box.  How might I go about fixing this?

Thank you in advance,
MH

---

### Post by spjackson on 2015-02-27
This behaviour is controlled by the configuration setting error_reporting. This is set in /etc/php5/apache2/php.ini. You probably want to set it to  E_ALL | E_STRICT (or whatever value you are using on your Windows box). See [http://php.net/manual/en/errorfunc.configuration.php#ini.error-reporting](http://php.net/manual/en/errorfunc.configuration.php#ini.error-reporting)

---

### Post by Mike_Hanchet on 2015-02-27
Thanks, I'll give that look.

---

