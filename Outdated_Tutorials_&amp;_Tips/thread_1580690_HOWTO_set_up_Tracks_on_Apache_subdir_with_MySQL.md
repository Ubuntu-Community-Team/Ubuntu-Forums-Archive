---
title: "HOWTO: set up Tracks on Apache subdir with MySQL"
date: 2010-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by carandraug on 2010-09-23
Hi

I've spent quite some time now setting up this web application named [Tracks]("http://www.getontracks.org/") (it's free as in freedom under the GPL). It helps to keep track of many projects and the actions needed for each of them. You can create contexts such as ''home'', ''tired'', ''work'', ''library'' or whatever so you know what actions you should do when you are on which context. You can also have  recurrent actions and if you think you can only do something tomorrow or next week, there's 2 handy buttons (+1 and +7) to have the action go away and come back later. There's also a mobile phone login page which should load faster.

I've spent a lot of time getting it to work properly and I'm now sharing my experience. Already did it on their [own wiki]("http://www.getontracks.org/wiki/Linux-Ubuntu/") but had some problems with the syntax there.

These instructions will install and set a production environment of Tracks 1.7.1 on a fresh install of Ubuntu 10.04. Tracks will be served by Phusion Passenger through Apache in a subdir of its own. MySQL will be used for the database.

**Note:** the [COLOR="Red"]text on red[/COLOR] are some of the main things that may be different for each set up. Things such as passwords, usernames or filenames.

**[SIZE="4"]1 - Installing all dependencies[/SIZE]**
```

$ sudo tasksel install lamp-server
$ sudo aptitude install ruby libdbd-mysql-ruby rake libopenssl-ruby libapache2-mod-passenger

```

**[SIZE="4"]2 - Download and set permissions for tracks[/SIZE]**
```

$ wget http://github.com/bsag/tracks/zipball/1.7.1
$ unzip [COLOR="Red"]./bsag-tracks-1.7.1-0-g13db454.zip[/COLOR]
$ sudo mv [COLOR="Red"]./bsag-tracks-6aff172[/COLOR] /var/lib/tracks
$ sudo cp /var/lib/tracks/config/database.yml.tmpl /var/lib/tracks/config/database.yml
$ sudo cp /var/lib/tracks/config/site.yml.tmpl /var/lib/tracks/config/site.yml 
$ sudo chown -R www-data:root /var/lib/tracks
$ sudo find /var/lib/tracks -type d -exec chmod 700 '{}' \;
$ sudo find /var/lib/tracks -type f -exec chmod 600 '{}' \;
$ sudo find /var/lib/tracks/script -type f -exec chmod 700 '{}' \;
$ sudo ln -s /var/lib/tracks/public /var/www/tracks

```

**Note:** the zip and extracted directory filenames will probably be different
**Note:** it's not possible (or easily done for someone like me) to move the configuration files to ''/etc'' as is usual in Ubuntu and Debian without having to change the code. If such is desired, at least the file ''tracks/config/boot.rb'' will require some editing. Same goes about having most of it on ''/usr/share'' and only the public data on ''/var/lib/tracks''

The ''find'' and ''chmod'' commands will set permissions as ''700'' for all directories and files inside the ''script'' directory. All other files will have permissions set to ''600''. All the files will be owned by the user ''www-data'' which is the user that runs Apache

**[SIZE="4"]3 - Create MySQL database[/SIZE]**
```

$ sudo mysql -u root -p
mysql> CREATE DATABASE [COLOR="Red"]tracks[/COLOR];
Query OK, 1 row affected (0.03 sec)

mysql> GRANT ALL PRIVILEGES ON [COLOR="Red"]tracks[/COLOR].* TO '[COLOR="Red"]tracksuser[/COLOR]'@'localhost' IDENTIFIED BY '[COLOR="Red"]trackspassword[/COLOR]' WITH GRANT OPTION;
Query OK, 0 rows affected (0.08 sec)

mysql> quit;
Bye 

```

**Note:** if you choose a different database name, MySQL user to access the database or different password, they'll have to be change accordingly here and on the following. It's not difficult to do so, just requires a bit of extra attention.

**[SIZE="4"]4 - Configure tracks[/SIZE]**
The file ''tracks/config/database.yml'' needs to be edited. Edit ONLY the production section
```

production:
  adapter: mysql
  database: [COLOR="Red"]tracks[/COLOR]
  host: localhost
  username: [COLOR="Red"]tracksuser[/COLOR]
  password: [COLOR="Red"]trackspassword[/COLOR]

```


The file ''tracks/config/site.yml'' needs to be edited. Choose a new salt word and set the correct time zone. The only things that need to be changed on the file are the lines with:
```

salt: ''[COLOR="Red"]change-me[/COLOR]'' 

```
```

time_zone: ''[COLOR="Red"]UTC[/COLOR]''

```

The first one is some random word used for the encryptation. It's not a password, just write something random. the second one is the base time-zone. If there's more than one user it's possible to change it from the web browser on a user basis. To get a list of available time zones, use the command
```
$ sudo rake --rakefile=/var/lib/tracks/Rakefile time:zones:local
```

**[SIZE="4"]5 - Populate database[/SIZE]**
```
$ sudo sh -c "cd /var/lib/tracks/; rake --rakefile=/var/lib/tracks/Rakefile db:migrate RAILS_ENV=production"
```

**[SIZE="4"]6 - Configure and restart apache[/SIZE]**
```
$ echo "RailsBaseURI /tracks" | sudo tee /etc/apache2/conf.d/tracks.conf
$ sudo mv /var/lib/tracks/public/.htaccess /var/lib/tracks/public/.dontneedhtaccess
$ sudo /etc/init.d/apache2 restart
```

Open the URL [http://localhost/tracks](http://localhost/tracks) to start tracks. You'll need to create and admin account first. From the admin account you can create as many users as you want.

Whatever is the URL of your webserver, just add ''/tracks'' to access it remotely.

---

