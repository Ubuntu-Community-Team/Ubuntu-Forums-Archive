---
title: "any ideas how to move my phpbb3 folder"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-13
I moved my phpbb3 folder /usr/share/phpbb3 to its new location /var/www/phpbb3.

I can access my phpbb3 forum threw this link
[http://localhost/www/index.php](http://localhost/www/index.php)

phpbb3 has a /www file in it phpbb3/www/ where the index.php is located to launch the phpbb3 board.

I want my board to show up from [http://localhost/phpbb3](http://localhost/phpbb3) or something to that effect. I'm not sure how to  go about this. I don't want to have to go threw the /www folder in phpbb3 to access this board. I want to keep is simple and neat.

Any ideas?

Or maybe someone knows the code to put my phpbb3 folder back in its original spot? current location /var/www/phpbb3 to knew location /usr/share/phpbb3 ?

Any help would be awesome i'm kind of stumped right now.

This is my first time setting up a phpbb3 board.

---

### Post by jimmy the saint on 2008-11-13
Have you updated your apache2 config files to reflect the new location?  Also, you may want to look into how to configure your htaccess files.  I'm not an expert so I cannot walk you through these steps, but that is where I would start were I in your shoes.

---

