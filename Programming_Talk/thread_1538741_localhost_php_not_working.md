---
title: "localhost php not working"
date: 2010-07-25
forum: Programming Talk
---

### Post by jk1 on 2010-07-25
I've been testing out a twitter oauth app.

I've been having an issue where the index.php page is blank.

If I upload the same script to my webhost, it works perfectly.

Any advice how to get the script to work under the localhost address in Ubuntu Desktop 10.04?

---

### Post by Can+~ on 2010-07-25
Have you installed apache2 and libapache2-mod-php?

Did you put your files inside /var/www?

Did you check if the server is up (sudo service apache2 start)?

Does apache2 have read access to the files inside /var/www (chgrp www-data, chmod g+r)?

---

### Post by jk1 on 2010-07-25
> **Can+~ said:**
> Have you installed apache2 and libapache2-mod-php?

Did you put your files inside /var/www?

Did you check if the server is up (sudo service apache2 start)?

Does apache2 have read access to the files inside /var/www (chgrp www-data, chmod g+r)?

apache2 and libapache2-mod-php are both installed

files are in /var/www

server is up

all files have read access

---

### Post by wojox on 2010-07-25
Have you checked the Apache error logs?

---

### Post by jk1 on 2010-07-25
> **wojox said:**
> Have you checked the Apache error logs?

I did and found a single error throughout the log.  Figured out I needed to install an extension, and it worked!

Thank You!

---

### Post by wojox on 2010-07-25
> **jk1 said:**
> I did and found a single error throughout the log.  Figured out I needed to install an extension, and it worked!

Thank You!

Your Welcome. :D

---

