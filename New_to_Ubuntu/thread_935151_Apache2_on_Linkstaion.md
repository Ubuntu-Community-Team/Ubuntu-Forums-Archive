---
title: "Apache2 on Linkstaion"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by mickanderson on 2008-10-01
Could somebody give me guidance on whats the simplest way to get my web page showing on apache.
I have loaded apache o.k (all defaults) and can access through internet and it comes up with "It Works " screen.

Have also created a web page that works if I share dir and access directly through windows/firefox.
I have tried changing paths in apache2.conf file to point to new index.html without success. I have not created any virtual servers or anything, do I need too for a simple web site?

Is there a way to point to a specific directory?

:-)

---

### Post by Peter09 on 2008-10-01
Yes,
you need to go into your apache config directories to the sites-available directory. In there you have to put files which direct apache to the site specific directory for each website. Its not that simple, you will need to read the apache documentation around it.

---

### Post by superprash2003 on 2008-10-01
you dont need virtual servers if you are setting up one website only.. go to /var/www and insert your index.html file there and see if it works..

---

### Post by mickanderson on 2008-10-02
Thats working with Aache2-default..

Thanks..

But....Always a but....

Loaded  some photos filled hda1, how can I change my :/var/www/apache2-default# from hda1 to hda3..

This is script on Buffalo-nas to move the local directory which I did. Could somebody covert this to move my /var/www/ directory...

Thanks...


DIR="$(mount | grep hda3 | awk '{print $3}')"
mkdir   ${DIR}/usr
cp -Rdp /usr/local ${DIR}/usr
rm -R   /usr/local
ln -s ${DIR}/usr/local /usr/local

---

### Post by superprash2003 on 2008-10-03
how about mounting the drive to a folder like /media/whatever .. and then edit the default file by changing DocumentRoot from /var/www to /media/whatever.Here's how you do that [http://prash-babu.blogspot.com/2008/05/how-to-install-apache-and-setup.html](http://prash-babu.blogspot.com/2008/05/how-to-install-apache-and-setup.html) .Follow Step 4

---

