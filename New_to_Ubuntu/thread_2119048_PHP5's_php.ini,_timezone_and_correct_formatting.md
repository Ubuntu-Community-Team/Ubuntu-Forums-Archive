---
title: "PHP5's php.ini, timezone and correct formatting"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-22
The chron daemon sent me this:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysql.so' - /usr/lib/php5/20090626+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0

and [netsearching]("https://www.linuxquestions.org/questions/linux-server-73/phpinfo-stops-on-showing-date-module-information-861160/") that I found I have to add code about the timezone.

The supported timezone as listed at the PHP pages is written as:

America/Los_Angeles

and the php.ini file, under the [Date] section has:

[Date]
; Defines the default timezone used by the date functions
; [http://php.net/date.timezone](http://php.net/date.timezone)
date.timezone = America/Los_Angeles
; above line added 22-feb-2013 original lines is - **;date.timezone =**

so my question is: 

because the line reads:

date.timezone

does that mean that the 

America/Los_Angeles needs something in front of it (the date code) and is the "date" separated from the "timezone" by a period "."? Or by a "/"? And if you know what is the "code" for the "date." part?

---

