---
title: "PgAdmin III issues"
date: 2010-08-14
forum: Programming Talk
---

### Post by badaveil on 2010-08-14
I want to learn more about web-GIS and successfully installed PostGIS, PostgreSQL, Tomcat6 and GeoServer in my Ubuntu 10.4LTS computer. Since I'm a GUI-man:-\", I got PgAdmin installed too. Using PgAdmin, I managed to add a new server using the following properties-

description:test
hostname:localhost
port:5432
SSL:blank
maintenance database: posgres 
username:me
password:abc123
store password:no
restore environment?:no
connection?:no

Server(1)/test(localhost:5432) was successfully created just that there is a red cross at the dbase icon, don't know what that means.

To do a server test, I rightclick server icon/connect/enter password/ok but got following result:

An error has occurred:

Error connecting to the server: FATAL:  password authentication failed for user "me"
FATAL:  password authentication failed for user "me"

I was told "Looks like, there is some basic flaws with your ROOT user/pass for the postgres"

Can anyone advice me how to create that test database?
Thanks

badaveil

---

