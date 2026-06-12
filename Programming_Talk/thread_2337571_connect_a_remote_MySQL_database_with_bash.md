---
title: "connect a remote MySQL database with bash"
date: 2016-09-19
forum: Programming Talk
---

### Post by cazz on 2016-09-19
is it possible with bash to connect to a remote MySQL database and run a insert to add information?

That I have see so far is you can do it if MySQL is on the same Linux.


Right now I use Wget to send information from one Linux to another Linux on my Network with help of PHP but I'm not sure if that  is reliable.

That I have done now is this.

One old laptop with Xubuntu that works as a client for iperf3
One virtual server with Xubuntu that works as a server that also have iperf3

I have build a script with help from people here that I run ever 15 min with crontab.
So it run a Network test with iperf3 and then send it with wget to the server that have a apache server with Mysql and PHP that I use GET to receives the information.
The PHP page then save it on MySQL.

But I'm not sure how reliable it is because before I walk home from work I did notice a time that did not have any information at all not even a timestamp

14.00
14.15
14.45
15.00
(where is 14.30)

So I was thinking maybe is more reliable if I can get bash to insert the value in to the MySQL database and skip the wget and PHP
It maybe is some networksproblem so I have to create so if the info is null it still going to insert information but instead of nothing it just add 0

---

### Post by spjackson on 2016-09-20
It is possible provided:
[LIST]
[*]On your client system you need the mysql-client system installed. 
[*]On your server system you need the mysql server to be configured to listen on the network interface. On most LAMP type installations, mysql will only listen on localhost. 
[/LIST]
In this case you could do something like:
```

echo "insert into mytable(mycolumn1, mycolumn2) values ('blah', 'blah');" | mysql --user=myuser --password=mypassword --host=myremotehost mydatabase

```
You would need to consider security implications regarding password and also regarding opening up the mysql server to the network.

An alternative approach is to use ssh to execute a command on the server which avoids the need for the two items listed above, i.e. you can keep the mysql server listening on localhost only.

```

ssh myuser@myremoteserver myscript arg1 arg2

```
where myscript on the server does something like the above insert. You could also do it by invoking mysql on the server directly without using a remote script, e.g.
```

echo ... | ssh myuser@myremoteserver mysql --user=myuser --password=mypassword mydatabase

```

---

### Post by steeldriver on 2016-09-20
^^^ +1

As a variant on the above, you could also consider setting up an SSH tunneled connection to the remote mysql server as described here [MySQL connection over SSH tunnel - how to specify other MySQL server?](http://stackoverflow.com/a/18374012/4440445)

---

### Post by cazz on 2016-09-20
Thanks alot
Well yes the first one is less secure but is not so big secret about the info I have and is never going to use public.

When I get this to work as good as possible I going to change the old laptop to Banana pi (It have 1000 ethernet) and is easy to hide that tiny computer :)

---

