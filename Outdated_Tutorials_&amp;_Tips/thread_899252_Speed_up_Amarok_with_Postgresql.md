---
title: "Speed up Amarok with Postgresql"
date: 2008-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by bigbrovar on 2008-08-24
Amarok is argueably the best music player in the world. (ok that is my Opinion) But its really that good and i have yet to come across any music player that comes close .with  Wikipedia lookup and lyrics download  Magnatune integration, allowing no-cost full listening of all the music in their catalog, and DRM-free purchasing. sync  with any music player like your ipod or iphone . You can read more about amarok here [http://en.wikipedia.org/wiki/Amarok_(audio](http://en.wikipedia.org/wiki/Amarok_(audio))

one of the downside of amarok is that has  your music  library gets bigger amarok gets slow and unstable.

Startup time take ages. This is because by Default Song collection, which includes specific folders on the filesystem. are stored in an internal SQLite database. The SQLite database struggles with very large music libraries.Thankfully amarok allows you to use an external Database like MySQL and Postgresql. i have tried MySQL before but the speed its gives you is nothing compared to what you get if you use postgresql .ok eneough talk lets get down to business. i am going to describe how i got my amarok to use postgres has database under Ubuntu .

First i installed Postgresql.

```
sudo aptitude install postgresql
```

Then we change the default password for postgres user

```
sudo -u postgres psql -c "ALTER USER postgres WITH PASSWORD '<password>'"
```

*replace *password* with your password

**example**

sudo -u postgres psql -c “ALTER USER postgres WITH PASSWORD ‘<yourpasswordhere>’”

Now we add a user to the postgres Database

```
sudo -u postgres createuser -D -A -P username
```

* username should be your systems user name

**example**

sudo -u postgres createuser -D -A -P bigbrovar

you would be promted for a password for the user you  just created .

Next we create a database for amarok

```
sudo -u postgres createdb -O username amarok
```

* replace username with your systems username. as we did in the last command

**example**

sudo -u postgres createdb -O bigbrovar amarok

Next we configure amarok to use the postgres database we just setup for it .

Open amarok .then go to  **settings/configure amarok /collection**

enter settings then using the username/password and amarok database just created. Set hostname to “localhost” and port to “5432“.

**so using the examples i gave above**

Database = Postgresql

Hostname = localhost

Database = amarok

Username = bigbrovar

Port = 5432

Password = password created for bigbrovar

*note the password should be the password of the user your added to the postgres database and not the Postgresql  password .

Hope it works for you .

This  my first ever guide hope it helps ...

---

### Post by Lucky LIX on 2008-10-13
Although changing the default password didn't work with the command, I just continued with the next steps and everything appears to work fine and MUCH faster than it used to :)
Thanks a lot for this how-to, I might finally consider dropping XMMS..! :o

---

### Post by bigbrovar on 2008-10-28
> **Lucky LIX said:**
> Although changing the default password didn't work with the command, I just continued with the next steps and everything appears to work fine and MUCH faster than it used to :)
Thanks a lot for this how-to, I might finally consider dropping XMMS..! :o

thanks for pointing out the command typo for the change default passwd .. it is fixed now.

---

### Post by bhuvi on 2008-10-28
thanks for the tutorial man

---

### Post by Mr.Tess on 2008-10-28
Great tutorial!!! To bad mysql is not so fast like postgresql...lol thanx

---

### Post by buntunub on 2008-11-05
Worked a treat. Thanks for the great "how to"!

---

