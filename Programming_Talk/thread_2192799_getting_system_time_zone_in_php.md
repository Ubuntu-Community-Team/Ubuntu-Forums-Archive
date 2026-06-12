---
title: "getting system time zone in php"
date: 2013-12-09
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-12-09
seems the new version of php in 13.10 does not like not setting the time zone when you call the date function
i could just get the time  zone from the client, but i am using the number as a id and i don't want to allow duplicates
extremely unlikely to have more than one time zone for this use, but rather not let it me possible.
i came up with this code (don't care about windows server support)
```
date_default_timezone_set('UTC');
$GMT=intval(exe('date +%z',true))*36;
$FILENAME=date("M_j_Y~G-i-s",filemtime("$CANDIR/".$file)+$GMT);
```
is there a better way to do this? i would like it to work on slightly older php versions also (>=5.0) as well on multiple distros like centOS, debian, fedora, etc.

---

### Post by CharlesA on 2013-12-09
When I deal with the dates, I just use the timezone the server is in and set that in php.ini.

Does that no longer work?

---

### Post by pqwoerituytrueiwoq on 2013-12-09
that is the method it wants you to use, i would rather not have to add that to the installation instructions

---

### Post by CharlesA on 2013-12-09
> **pqwoerituytrueiwoq said:**
> that is the method it wants you to use, i would rather not have to add that to the installation instructions

Oh ok. Whenever I do an install, I just run a sed one-liner to fix the timezone.

```
sed -i 's/;date.timezone =/date.timezone = America\/New_York/' /etc/php5/fpm/php.ini
```

The path would be different depending on what you are using php for. I am running php5-fpm with Nginx, in this example.

To each their own though. :)

---

### Post by pqwoerituytrueiwoq on 2013-12-09
not quite what i meant, this is in a github project i have i wanted it to work with current and older versions of PHP, for example Ubuntu 10.04 through 13.10, and i know centOS uses some REALLY old stuff
would this be a good way to do it?
```
               $GMT=0;
                if(ini_get('date.timezone')==='' && version_compare(phpversion(), '5.1', '>')){
                        Print_Message("Warning, Guessing Time Zone",'<a href="http://www.php.net/manual/en/datetime.configuration.php#ini.date.timezone">date.$
                        date_default_timezone_set('UTC');
                        $GMT=intval(exe('date +%z',true))*36;
                }
               // call date function
```

---

