---
title: "Set up Amarok to use a MySQL database for multiple users on the same PC"
date: 2007-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by FSHero on 2007-11-05
Hi everybody; the following is a brief "how-to" on how to set up MySQL databases for Amarok, so that multiple users of a computer can have their own databases. There is a big advantage of doing this over SQLLite: if you have many songs (tens of thousands!), then using SQLLite will lead to sluggish performance. The following guide assumes that you have a "fresh" Amarok install; that is, MySQL hasn't been installed yet. *Please tell me if I've made any errors; I'll try to edit this if I have time to correct them.*

I based this on a forum post ([http://ubuntuforums.org/showthread.php?t=440918](http://ubuntuforums.org/showthread.php?t=440918)) on how to set this up for a single user. Two people use my computer, however, and we want to keep our collections separate. I figured out how to do this, so I decided to write the following how-to. I used information on [http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html) too. The following information worked on my Kubuntu Feisty Fawn installation.

First, install mysql by typing at a terminal prompt (e.g. Konsole):

```
$ sudo apt-get install mysql-server mysql-client
```

(or you can use Adept package manager on Kubuntu.)

Now, you need to set the password for the "root" account in MySQL. Note that the accounts for MySQL are completely separate from the user accounts for your system (i.e. the ones you use to log in/out your computer). To set the root password for MySQL:

```
$ mysqladmin -u root password ROOT_PASSWORD_HERE
```
(Choose a password, then substitute ROOT_PASSWORD_HERE above for your chosen password.)

Now, create a database for the first user. The database will store all your musicians, tracks and album names. (I presume... I haven't thought too deeply about it!) Type *(and don't forget the semicolons at the end of the lines!)*:

```

$ mysql -p -u root
CREATE DATABASE user1_amarok;
USE mysql;
GRANT ALL ON user1_amarok.* TO user1@localhost IDENTIFIED BY 'user1_password';
FLUSH PRIVILEGES;
exit

```

(Type your MySQL root password when asked.)

Explanation: First, you create a database called "user1_amarok". (You can substitute user1 for whatever you want, e.g. my database is called fshero_amarok.) Then, (I think...) you choose to use MySQL as the database type. Next, you grant the user "user1" read/write privileges for the database "user1_amarok", simultaneously setting up a password "user1_password" for user1. (Again, these MySQL usernames and passwords are kept separate from your *buntu user accounts.) The username and password will be entered into Amarok later.

To create a database for subsequent users with names "user2", "user3"... and so on, repeat the above steps. That is:

```

$ mysql -p -u root
CREATE DATABASE user2_amarok;
USE mysql;
GRANT ALL ON user2_amarok.* TO user1@localhost IDENTIFIED BY 'user1_password';
FLUSH PRIVILEGES;

```

... and repeat for each subsequent user. (Notice: you don't have to exit MySQL each time you create a user!)

Now, it is time to enter details into each user's Amarok. Log in as the first user (or ask them to log in, if you aren't the first user). Start Amarok, then on the menu go to: Settings -> Configure Amarok. Now, go to the "Collection" section. Choose MySQL from the "Database" combo box. Type in the following details for each text box:
Hostname: 127.0.0.1
Database: user1_amarok;
Port: 3306
Username: user1
Password: user1_password

After you have entered these, click OK. Then, click on Tools --> Rescan collection. If this doesn't work, ensure that under Settings -- Configure Amarok --> Collection section, you have selected the desired folders to be 'watched'.

Now, to set up the other users' Amarok databases, log out of the first user, then log in to the second user / ask them to log you in. Repeat the entry of data into Amarok, substituting user1 for user2, and so on...

Hopefully this will help someone out!

Again, please reply to this thread if I have make a mistake, or performed something in fundamentally the wrong way.

--FSHero

---

