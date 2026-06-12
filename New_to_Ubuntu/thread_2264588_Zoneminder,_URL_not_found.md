---
title: "Zoneminder, URL not found"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by Mike_V... on 2015-02-08
After install, my browser inquiry [http://localhost/zm](http://localhost/zm) responds with URL not found. Files for zoneminder located in User/share.. but Apache can't find them? Do I need to provide path?

---

### Post by oldos2er on 2015-02-08
Moved your actual question to its own thread.

Please specify which Ubuntu version you're using.

---

### Post by yancek on 2015-02-08
I used the instructions at the link below to set up zoneminder on 12.04 about a year ago and it worked.  One thing people seem to not do is add www-data to the video group and
then changed owner:group of /dev/video to www-data.[www.data](www.data)

[http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.25.0_the_easy_way](http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.25.0_the_easy_way)

---

