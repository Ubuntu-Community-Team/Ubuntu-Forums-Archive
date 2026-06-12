---
title: "PostgreSQL problem"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by Ziki on 2012-08-15
Hi, I havew a strange problem with postgresql. I had install postgresql-9-1 via apt-get and after that happnes nothing I didnot even try it if is it running. After that I downloaded EnterpriseDB instalation file from Postgre official site and isntall some sotware, but I did not know it installs again Postgre and ask mi for password. I entered a password and thought that it will recognize current installation and just exchanged a pass, but happend nothing. After hat i ran 
```

sudo apt-get remove postgresql*

```and 

```

sudo apt-get purge postgresql*

```and 

```

sudo rm -rf /opt/PostgreSQL

```and istall it again 

```

sudo apt-get install postgresql-9-1

```and I cannot start postgres, I run 
```

sudo /etc/init.d/postgresql start

```and nothings happend, whatever command is (start, restart, stop) .

When I tried this
```

sudo -u postgres psql template1

``` i got this
```

psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5434"?

```

How to install it correctly and change password?

P.S. I changed configuration file and uncommented this line ```
listen_addresses = 'localhost'
```

---

