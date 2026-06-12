---
title: "Making wiki moin moinmoin work"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by AllBuntu on 2006-06-30
So, there is a wiki with 5.05/6.06 though nobody cared for explaining how to make it work! At least, it's been that way until now:

If you want to host your own wiki and has Ubuntu installed, follow the below steps (moin is what ubuntu.com uses for Wiki):
Skill level: know your way around bash

1. Install
sudo apt-get install python2.4-moinmoin
sudo apt-get install apache2

2. Create your own wiki called mywiki
cd /usr/share/moin
sudo mkdir mywiki
sudo cp -R data mywiki
sudo cp -R underlay mywiki
sudo cp server/moin.cgi mywiki
sudo chown www-data.www-data mywiki
sudo chmod -R ug+rwX mywiki
sudo chmod -R o-rwx mywiki

3. Commission moin to find your new wiki
cd /etc/moin
sudo cp moinmaster.py mywiki.py

insert into farmconfig.py, on a line after "wikis = ["
   ("mywiki",  r".*"),

in mywiki.py change the data_dir line to
  data_dir = '/usr/share/moin/mywiki/data'

4. Make apache ready for your wiki
insert into /etc/apache2/sites-available/default
(inside of the "<VirtualHost *>" tag)

### moin
  ScriptAlias /mywiki "/usr/share/moin/mywiki/moin.cgi"
  alias /wiki "/usr/share/moin/htdocs"
  <Directory /usr/share/moin/htdocs>
    Order allow,deny
    allow from all
  </Directory>
### end moin

sudo /etc/init.d/apache2 restart

5. See if it works
[http://127.0.0.1/mywiki](http://127.0.0.1/mywiki)

(they also have a test command)
[http://127.0.0.1/mywiki?action=test](http://127.0.0.1/mywiki?action=test)

Once it works, I am sure you can fix tons of stuff such as style it like the Ubuntu wiki, add ssl and digest authentication, use another name or another directory etcetera. After all, that's why we use Ubuntu!

And, if you happen to be one of those Python-high Germans, please get an apache-integrated ready-to-go wiki into the package, will you?

---

