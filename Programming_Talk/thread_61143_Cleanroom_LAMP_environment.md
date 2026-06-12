---
title: "Cleanroom LAMP environment?"
date: 2005-08-30
forum: Programming Talk
---

### Post by Kyral on 2005-08-30
Okay I'm in a PHP4/MySQL class at college. I would like to create a "clean" LAMP environment so that I can test my stuff, but I don't want it broadcasting to the outside world. How would I do this? I know zilch about servers and whatnot

---

### Post by valter on 2005-09-01
I did it so:
installed php4, apche2, libapache2-mod-php4, webmin, webmin-apache ( I recommend not to use bacports for that)
after that you can login to webmin - [https://localhost:10000/](https://localhost:10000/).
And there look for apache server, where you can conf it whit web based GUI (look for Networking and Addresses for disable all other addresses but not localhost).
then with [http://localhost](http://localhost) you should see the folder you have configured to see with apache.
Hope it helps

---

