---
title: "php class datetimezone not found"
date: 2007-04-02
forum: Programming Talk
---

### Post by proalan on 2007-04-02
I'm having a little trouble with the php date functions, i'm not sure whether this is more of a php issue or ubuntu 

I've got the following code to list all the timezones supported by php as I plan on writing some localisation functions later on.

```
$timezone_identifiers = DateTimeZone::listIdentifiers();
for($i=0; $i<count($timezone_identifiers);$i++)
       echo "$timezone_identifiers[$i] \t";
```
    
when i load the page i get the following message

```
Fatal error:Class 'DateTimeZone' not found 
```

the script runs fine and echos a list of locales on my remote server (debian) and also my windows box both running apache2 php version 5.1.6.

I'm wondering if there is a particular module that needs configuring?
my phpinfo tells me that **date** is configured properly and i am able to use the other date related functions without problems.

can someone enlighten me with a solution

---

### Post by Mirrorball on 2007-04-02
These classes are only available for PHP 5.2.

---

### Post by proalan on 2007-04-02
doh! 

guess i'm going to have to compile php form source

cheers mate much apreciated

---

