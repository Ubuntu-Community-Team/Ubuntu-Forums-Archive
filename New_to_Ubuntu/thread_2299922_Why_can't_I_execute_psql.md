---
title: "Why can't I execute psql?"
date: 2015-10-22
forum: New to Ubuntu
---

### Post by ScorpioTiger on 2015-10-22
I have Postgres installed. I know it's running because an application that uses it is working.

When I change to the directory with psql and attempt to use it, I get this message;
The program 'psql' can be found in the following packages:
 * postgresql-client-common
 * postgres-xc-client
Try: apt-get install <selected package>

What's going on? I can see psql right there in the directory listing.

---

### Post by shadytv on 2015-10-22
So how did you install postgresql in the first place? Did you follow the instructions on the website?

```
apt-get install postgresql-9.4
```

[http://www.postgresql.org/download/linux/ubuntu/](http://www.postgresql.org/download/linux/ubuntu/)

---

### Post by sandyd on 2015-10-22
> **ScorpioTiger said:**
> I have Postgres installed. I know it's running because an application that uses it is working.

When I change to the directory with psql and attempt to use it, I get this message;
The program 'psql' can be found in the following packages:
 * postgresql-client-common
 * postgres-xc-client
Try: apt-get install <selected package>

What's going on? I can see psql right there in the directory listing.

Small explanation:

Normally when you run a command (i.e. 'sudo'), the shell looks in the directories you set as your $PATH to see if the command exists.
You can get your PATH by running the following
```

echo $PATH
```
That outputs something like
```

/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

```

The colons are a delimiter when there are multiple directories.

As a result, the shell cannot run the program because the folder you are currently in is not part of your PATH.

You can run programs that are not in your PATH either by relative or direct paths
In this case, you can either

a) Use "./" to indicate that you want to run a program in the current folder
i.e.
```

./psql
```

b) Find the full path to the program
```

pwd ## shows current path
## Insert the output of pwd before psql
*ouput*/psql
```

There are also some other ways such as using '~' as a reference to your home folder/etc

Side note: Normally, packages that you install from apt will automatically have their executables installed in one of the folders in a user's default $PATH.

---

### Post by ainars2 on 2015-10-23
Great explanation sandyd, helped me too! Thanks!

---

### Post by ScorpioTiger on 2015-10-23
Thanks so much. That explains it. Postgres was installed as part of an Alfresco install and I guess it failed to add the paths. I had figured that that may have been the case, but assumed that by being in the folder where PSQL is that it would look there first (perhaps a legacy of years of Windows use). Using ./psql worked for me.

---

