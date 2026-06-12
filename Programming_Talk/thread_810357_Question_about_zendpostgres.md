---
title: "Question about zend/postgres"
date: 2008-05-28
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-05-28
Hey guys

I've been porting some old websites that use zend & postgre sql over to my new webserver ( PHP5 & apache2 ) and have found that the pages that use the database can get data from the database but still display this error:

```
**Warning**:  PDO::__construct() [[function.PDO---construct]("http://www.mbc-recruitment.co.uk/search/function.PDO---construct")]: SQLSTATE[IM001]: Driver does not support this function: driver does not support setting attributes in **/var/www/websitename/application-200711271538/modules/default/classes/Database.php** on line **13**
```

I checked and the lines in that are in that file read:

```
try { 
                $param = array(PDO::ATTR_PERSISTENT => false); 
                if(!$GLOBALS['db'][$dsn] = new Database($dsn, null, null, $param)) { 
                    throw new FatalException('Unable to connect to database');
```

is this because my server has persistent connection on? or something else?

Please help!

Mike

---

### Post by deuce868 on 2008-05-28
Did you try removing the params and see if that got rid of the error?

---

