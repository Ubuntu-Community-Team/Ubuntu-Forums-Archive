---
title: "ubuntu 12.04 - Postgresql Error - psql: could not connect to server"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by pmu on 2013-06-22
Hi,

Recently started on Ubuntu. I have installed postgresql on CentOS with no issues, but I dont know where I am going wrong with this one.

I installed postgresql first through the software center. Installed a couple add-ons as well, and tried running the psql command. But saw somewhat un usual error:
```

pmu@thinkpad:~$ psql
psql: server closed the connection unexpectedly
    This probably means the server terminated abnormally
    before or while processing the request.
pmu@thinkpad:~$ psql -h 127.0.0.1 -U pmu
psql: server closed the connection unexpectedly
    This probably means the server terminated abnormally
    before or while processing the request.
pmu@thinkpad:~$ psql -h 127.0.0.1 -U postgres
psql: server closed the connection unexpectedly
    This probably means the server terminated abnormally
    before or while processing the request.
pmu@thinkpad:~$ 
```

Nothing about the same socket being used, or service not started, or some stuff like that which is documented in the postgresql documentation...Just the above error.

So I removed postgresql, again from the Software Center, and then re installed it from command line. Still no go.

So I tried checking if the postgresql process is running, but apparently, no matter what I do, it doesn't start:

```
pmu@thinkpad:~$ sudo service postgresql status
pmu@thinkpad:~$ sudo service postgresql restart
pmu@thinkpad:~$ sudo service postgresql stop
pmu@thinkpad:~$ sudo service postgresql status
pmu@thinkpad:~$ sudo service postgresql start
pmu@thinkpad:~$ sudo service postgresql status
pmu@thinkpad:~$ 
```

There is a postgres user created though as shown below:

```
pmu@thinkpad:~$ sudo -su postgres
postgres@thinkpad:~$ whoami
postgres
```

And it's got a lot of processes associated with it as shown below:

```
postgres@thinkpad:~$ pgrep -u postgres -l
1283 pgpool
1284 logger
1315 pgpool
1316 pgpool
1317 pgpool
1318 pgpool
1319 pgpool
1320 pgpool
1323 pgpool
1324 pgpool
1325 pgpool
................
................
...............
```

The .......... in the above output are more entries for pgpool...35 to be precise as shown below:

```
postgres@thinkpad:~$ pgrep -u postgres -l | grep pgpool | wc -l
35
```


Per a few google searches, there's supposed to be a /usr/loca/pgsql directory that ought to be created, but I dont find that.

initdb is also not installed.

Really confused here, not sure why this is happening. I think I am doing something really stupid, but I am at this pointed completely brain dead to figure out what.

I looked up the postgresql documentation too, but nothing is metioned about this error message.

Any help I will be very thankful.

---

