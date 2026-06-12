---
title: "Amarok bug. periodically freezing"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Johnnie_Walker on 2008-06-24
Sometimes, when attempting to play something the stupid player just freezes. It started ti hapen very often. I've restarted it several times, but it still freezes when pushing "play" or just double clicking a song. It used ti happen before, but only when there are enqueued files left, but now it happens all the time. The player is really nice designed, but such an elementary bug is just ridiculous....

---

### Post by billgoldberg on 2008-06-24
If you're on gnome, you will like exaile better (or bmpx).

---

### Post by Johnnie_Walker on 2008-06-24
> **billgoldberg said:**
> If you're on gnome, you will like exaile better (or bmpx).
Exaile is the same crap, mate :( There is something wrong with the system or teh engine. A restart should fix it, but it is annoying to do it 10 times a day, if listening music for a long time.

---

### Post by Johnnie_Walker on 2008-06-24
BMPX seems to be the dumbest of them all :) It can add libraries, but can't play them. I guess it can, but it is directly number one in my ignore list, because of it's complicated structure. It seems that I will rely on good old rhythmbox...

---

### Post by rafaelrc on 2008-06-24
Johnnie, it might be since Amarok runs its way of collecting songs through a SQLlite database, which is not able to handle a large song collection. So in order to make Amarok stable, you'll have to use MySQL. It's very simple. 

First, you'll open a terminal window and type:

```
sudo aptitude install mysql-server
```

During its installation, you'll choose a password for it when you're prompted to type it in.

After that, we'll see if a socket file has been set up:

```
find /var/run/mysqld -name *.sock
```

If nothing appears, please type:

```
touch /var/run/mysqld/mysqld.sock
```

After that, we'll create the amarok database for MySQL using this:

```
mysql -p -u root #use your password
CREATE DATABASE amarok;
USE amarok;
GRANT ALL ON amarok.* TO amarokuser@localhost IDENTIFIED BY 'your password';
FLUSH PRIVILEGES;

```

Then, you'll open Amarok, go to Settings/Configure Amarok/Collection

Choose MySQL

And then we'll insert the name of our newly created database:

Server: localhost
Database: Amarok
User: root
Password: Your password.

Click on "Apply", then "Accept" and restart Amarok. 

Hope this helps!

---

### Post by Johnnie_Walker on 2008-06-24
> **rafaelrc said:**
> Johnnie, it might be since Amarok runs its way of collecting songs through a SQLlite database, which is not able to handle a large song collection. So in order to make Amarok stable, you'll have to use MySQL. It's very simple. 

First, you'll open a terminal window and type:

```
sudo aptitude install mysql-server
```

During its installation, you'll choose a password for it when you're prompted to type it in.

After that, we'll see if a socket file has been set up:

```
find /var/run/mysqld -name *.sock
```

If nothing appears, please type:

```
touch /var/run/mysqld/mysqld.sock
```

After that, we'll create the amarok database for MySQL using this:

```
mysql -p -u root #use your password
CREATE DATABASE amarok;
USE amarok;
GRANT ALL ON amarok.* TO amarokuser@localhost IDENTIFIED BY 'your password';
FLUSH PRIVILEGES;

```

Then, you'll open Amarok, go to Settings/Configure Amarok/Collection

Choose MySQL

And then we'll insert the name of our newly created database:

Server: localhost
Database: Amarok
User: root
Password: Your password.

Click on "Apply", then "Accept" and restart Amarok. 

Hope this helps!
10q for the help. I installed the MySQL, but when entering it in the player's fields an error occurs. Fortunately there is no bug now, but I don't know if it is because or the database or the reinstallation.  However I didn't find a better player for linux and I will use Amarok until it messes up again :(

---

### Post by Johnnie_Walker on 2008-06-28
Although I reinstalled the crap, reconfugured the database, Amarok is doing the same ****:mad: I wonder, is it so hard for the mto make a simple and non-bug player. At least I am sure now, that the problem is not coming from the system or GNOME.

---

