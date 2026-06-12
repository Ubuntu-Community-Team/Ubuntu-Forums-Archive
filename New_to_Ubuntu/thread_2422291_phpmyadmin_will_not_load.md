---
title: "phpmyadmin will not load"
date: 2019-07-05
forum: New to Ubuntu
---

### Post by mwoosley on 2019-07-05
Hello everyone.  It seems like every time I get something to work correctly, I run into yet another roadblock.

While everything seemed to be working fine, I tried to open the web app phpmyadmin and it doesn't open.  It was working correctly when I FIRST installed it over a month ago and now it does not want to work.  I even removed, purged and auto-removed phpmyadmin to load it again.  When I reinstalled the program via the respository, I set everything back up again...

At this point, there is no remembering what I did to cause the program to stop running.

```
sudo apt install phpmyadmin php-mbstring php-gettext
sudo phpenmod mbstring
sudo systemctl restart apache2
sudo mysql
SELECT user,authentication_string,plugin,host FROM mysql.user;

```
from the previous install, my data was already in place with mysql_native_password selected vs auth-socket
No need to alter user or Flush as root and myself were already in the table

Now, when I attempt to connect to the phpmyadmin, I get a 'server refused to connect' message
I utilize the address 'http://192.168.1.200/phpmyadmin' and even the 'https' and still no response.

As stated previously, it's been removed and reinstalled if not once, a couple times.

Thanks in advance for any tips that I might be overlooking.

---

