---
title: "Perl IO::Socket::INET: error"
date: 2005-12-11
forum: Programming Talk
---

### Post by pr0fess0r on 2005-12-11
Hi all

I'm trying to setup a connection to a Hypersonic SQL database on Ubuntu Linux.
I've installed HSQLDB-BER from [http://sourceforge.net/projects/hsqldb-ber/](http://sourceforge.net/projects/hsqldb-ber/) and the server seems to start OK, but I get this error running the sample.pl script:

DBI connect('hostname=localhost:9111;url=ber:hsqldb:play','sa',...) failed: Failed to open socket to server: IO::Socket::INET: connect: Connection refused at sample.pl line 27
Failed to connect: (104) Failed to open socket to server: IO::Socket::INET: connect: Connection refused

The line of code is:

$dsn = "dbi:JDBC:hostname=localhost:9111;url=ber:hsqldb:play";

What can cause the IO::Socket::INET:  error, and can you suggest ways to debug it?
many thanks in advance

---

### Post by amohanty on 2005-12-11
You will need to verify if port 9111 is open or not. First make sure that if you have FireStarter running that it allows stuff for port 9111 through. Then use nmap to make sure that its open:

```

sudo apt-get install nmap
sudo nmap -vv -sS -p 9111 <your ip address>
```

If its not open or is open and you still cannot get through there might be some problem with the db server startup. I havent used it so cant help you there, but if it logs stuff, look at the logs.

HTH

---

### Post by pr0fess0r on 2005-12-11
Thnaks amohanty, I did have the port wrong :)
cheers

---

