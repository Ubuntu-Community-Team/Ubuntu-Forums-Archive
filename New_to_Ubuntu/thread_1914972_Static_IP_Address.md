---
title: "Static IP Address???"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Momof9Blessings on 2012-01-25
HI,

The other day, I had problems accessing an online store (I was downloading from the store the night before - fine) the next morning - nothing.....  SO I just used my ftp access and did it that way....

Jump to last night and this morning....  I am trying to access one of my online stores via FireFTP and it's a no go....  all of the info is correct.... ftp address, username and password.....

I even tried it via another ftp program.... and even tried thru the browser window....

I was reading online about this, but realized it was for windows - about having a static IP address.... not sure if this is the correct road....


I can access other sites via ftp.... so it is just this one (and the thing that happened last week)....

We have cable modem (12mb), so that should not be a problem.... and this is on my laptop.....

Thank you

---

### Post by haqking on 2012-01-25
> **Momof9Blessings said:**
> HI,

The other day, I had problems accessing an online store (I was downloading from the store the night before - fine) the next morning - nothing.....  SO I just used my ftp access and did it that way....

Jump to last night and this morning....  I am trying to access one of my online stores via FireFTP and it's a no go....  all of the info is correct.... ftp address, username and password.....

I even tried it via another ftp program.... and even tried thru the browser window....

I was reading online about this, but realized it was for windows - about having a static IP address.... not sure if this is the correct road....


I can access other sites via ftp.... so it is just this one (and the thing that happened last week)....

We have cable modem (12mb), so that should not be a problem.... and this is on my laptop.....

Thank you

If you want a static IP address you need to talk to your ISP, it is nothing to do with your OS.

cheers

---

### Post by Momof9Blessings on 2012-01-25
Then I guess that is wrong title....

I am just reading online about similar problems... that is one person's solution for windows....

---

### Post by Momof9Blessings on 2012-01-25
I read about doing this....

```
lori@Lori-PC:~$ telnet $remoteaddress www.digitalscrapbookpages.com
Trying 173.231.32.84...
telnet: Unable to connect to remote host: Connection timed out

```

The owner of the site (my boss in a way) says that everyone else can access it fine.... that it is just me.... :(

---

### Post by Momof9Blessings on 2012-01-25
ok I just found out how to do this through a terminal....

```
lori@Lori-PC:~$ ftp digitalscrapbookpages.com
Connected to 173-231-32-84.hosted.static.webnx.com.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 10:33. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (digitalscrapbookpages.com:lori): ?????
331 User quality OK. Password required
Password:
530 Login authentication failed
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 

```

I removed my username (?????)

any ideas on what is happening?  What is binary mode???

---

### Post by haqking on 2012-01-25
> **Momof9Blessings said:**
> ok I just found out how to do this through a terminal....

```
lori@Lori-PC:~$ ftp digitalscrapbookpages.com
Connected to 173-231-32-84.hosted.static.webnx.com.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 10:33. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (digitalscrapbookpages.com:lori): ?????
331 User quality OK. Password required
Password:
530 Login authentication failed
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 

```

I removed my username (?????)

any ideas on what is happening?  What is binary mode???

it means as a stream of 1's and 0's as oppose to ASCII file transfer.

It is usually done in ASCII or binary, what one is better depends on the file types being transferred but you should be fine.

Cheers

---

