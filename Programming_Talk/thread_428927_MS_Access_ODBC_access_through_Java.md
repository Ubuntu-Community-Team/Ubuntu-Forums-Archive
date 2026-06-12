---
title: "MS Access ODBC access through Java"
date: 2007-04-30
forum: Programming Talk
---

### Post by abds on 2007-04-30
Hi,

Im totally stumped. I am trying to access a MS Access database through Java. I cant seem to find any drivers or configure ODBC properly. Would be extremely grateful if anyone could point me in the right direction

---

### Post by jlsheehan on 2007-04-30
> **abds said:**
> Hi,

Im totally stumped. Ive been trying to access a MS Access database through Java. I cant seem to find any drivers or configure ODBC properly. Would be extremely grateful if anyone could point me in the right direction

Hi,

The Access ODBC functionality is provided by Windows, UNIX ODBC won't do that.  You have to set up your access database on a windows machine, configure an ODBC connection for it from the control panel and then you can connect to it from anywhere using the sun JDBC ODBC bridge.

Last time I checked (a couple of years ago) there were a some proprietary "Pure Java" Access JDBC drivers which would theoretically work from anywhere, but of course you have to buy them.

Jeff

---

### Post by abds on 2007-04-30
Guess Ive been wasting my time then... Thanks for the prompt reply though

Abdul Basit

---

