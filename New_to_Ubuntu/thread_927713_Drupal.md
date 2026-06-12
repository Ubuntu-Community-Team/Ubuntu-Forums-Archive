---
title: "Drupal"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by uppidada on 2008-09-23
Hi every1.... as i've copied drupal to /var/www ,and then in /var/www/drupal/sites/default/ chmod 777 settings.php.Then as i've tried to install drupal its giving me this error..!! plz help me..
"Your web server does not appear to support any common database types. Check with your hosting provider to see if they offer any databases that Drupal supports."

---

### Post by leg on 2008-09-23
Have you installed and turned on mysql?

---

### Post by uppidada on 2008-09-23
Yah brother.... Using other terminal i've started mysql ... But still the problem persists..

---

### Post by uppidada on 2008-09-23
Plz help me with this....

---

### Post by mevets on 2008-09-23
did you try installing drupal5 via apt? If you try via this method it may prove to be much easier
```

sudo apt-get install drupal5

```

---

### Post by uppidada on 2008-09-27
Yah... even that doesn't work... I've configured drupal perfectly i suppose...
"Your web server does not appear to support any common database types. Check with your hosting provider to see if they offer any databases that Drupal supports." Even googling this isn't solving my pblm.... sumone plz help me with this....

Problem might have been with mysql... or is php posing any problem..??
I've opened up a another terminal and i've 
1.create database abc;
2.use abc;

still the error comes...plz.. help me..

---

### Post by leg on 2008-09-27
Are you pointing to the correct database in the settings.php file? You will need to set the database name and the mysql user to connect with in this file. Should look something like this.
```
$db_url = 'mysql://user:pass@localhost/drupal-default';
```
where user and pass states the username and password to be presented. @localhost states which host can connect and drupal-default is the name of the database. But to be honest the set up process should do this for you. Try adding this info manually into the settings.php to see what happens. Don't forget to swap your details for the username password and database.

---

### Post by uppidada on 2008-09-27
Yah... This really worked... Thnkx fr ur help... But i would like to know why didn't this happen automatically....

---

